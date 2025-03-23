---
layout: layout/mon.njk

title: "Titre du second MON du temps 3"
authors:
  - Laura Vietor

date: 1971-01-01
tags:
  - "temps 3"

description: "Un MON traitant d'un sujet."
---

<script>
const hamming_rows = [
    [1, 0, 1, 0, 1, 0, 1],
    [0, 1, 1, 0, 0, 1, 1],
    [0, 0, 0, 1, 1, 1, 1]
]

function demo_hamming() {
	console.log("clicked")
    const answers = [
        document.querySelector("#hamming_ans_1"),
        document.querySelector("#hamming_ans_2"),
        document.querySelector("#hamming_ans_3"),
        document.querySelector("#hamming_ans_4"),
        document.querySelector("#hamming_ans_5"),
        document.querySelector("#hamming_ans_6"),
        document.querySelector("#hamming_ans_7"),
    ].map((element) => element.checked)

    let error = hamming_rows.map(function (row) {
        let sum = 0;
        for (let i = 0; i < 7; i++) {
            sum += row[i] * answers[i];
        }

        return sum % 2;
    }).map((val, i) => val * 2 ** i)
    .reduce((a, b) => a + b, 0);

    if (error) {
        answers[error - 1] = !answers[error-1];
    }

    var result_div = document.querySelector("#hamming_result_div");
    var result_elem = document.querySelector("#hamming_result");
    var lie_div = document.querySelector("#hamming_lie_div");
    var lie_elem = document.querySelector("#hamming_lie");

    result_elem.innerHTML = 8 * answers[0] + 4 * answers[1] + 2 * answers[2] + answers[3];

    result_div.hidden = false;

    if (error) {
      lie_elem.innerHTML = error;

      lie_div.hidden = false;
    } else {
      lie_div.hidden = true;
    }
}
</script>

{% prerequis %}

Mon [MON précédent](../temps3.1/), qui explique certaines notions utilisées dans celui-ci également.
Quelques connaissances d'algèbre : vecteurs, produits scalaires, polynômes.

{% endprerequis %}

Dans ce second MON sur des question d'intégrité des données, je m'intéresse aux algorithmes permettant d'encoder des données de sorte à pouvoir corriger des pertes d'information lors d'une transmission ou du stockage de données.

## Le problème

Lorsque l'on transmet des données (ou stocke) des données, comme vu dans le MON précédent, il arrive souvent qu'il y ait des erreurs de transmissions, des données effacées... mais si détecter ces erreurs permet de demander à renvoyer les données quand c'est possible, quand la probabilité d'erreur est trop haute, quand cela se produit sur du stockage de données, comme un CD, un DVD ou encore un disque dur, ou quand le message provient d'un satellite à des centaines de kilomètres, on ne peut rien faire. Il faudrait donc pouvoir reconstruire les données correctes : c'est là qu'interviennent les codes correcteurs d'erreurs.

Là encore, le but va être d'ajouter des informations supplémentaires sur les données, mais beaucoup plus que pour de la seule détection d'erreurs ; en effet, il faut pouvoir savoir non seulement s'il y a une erreur, mais également où se trouvent les erreurs et quelles étaient les valeurs d'origine.

Dans la suite, je parlerai de "message" ; c'est simplement un autre nom pour des données, mais qui accentue l'idée de transmission.

## Vocabulaire

- Symbole : dans mon MON précédent, je parlais de chiffre et de bits. En fait, pour généraliser l'idée d'une unité de données, on va parler de lettre ou de symbole. Ainsi, selon le contexte, un symbole peut être un bit, un chiffre de 0 à 9, une lettre de a à z, un signe de ponctuation... Différents codes correcteurs peuvent utiliser différent symboles comme unités de base, et on verra que si certains opèrent avec des bits, d'autres opèrent avec des octets, par exemple.
- Redondance : comme pour les codes détecteurs d'erreurs, on parle de redondance pour les informations ajoutées aux données. Cependant, dans le cadre des codes correcteurs, il est intéressant d'en parler comme le rapport de la taille de ce que l'on a ajouté sur la taille totale avec les données, puisque plus il y a de données plus on va rajouter d'information, ce n'est pas un unique nombre de longueur fixe quelle que soit la quantité de données.
- Distance : en général, on va chercher à corriger les messages "invalides" (donc modifiés pendant leur transmission) reçus par le message valide "le plus proche". Pour cela, il faut une notion de "proche", c'est-à-dire de distance. Ici, on va dire que la distance entre deux messages est le nombre de lettres (ou symboles) qui diffèrent : la distance entre "Hello" et "World" est donc de 4. Cette distance est appelée *distance de Hamming*.

{% details "Messages de longueurs différentes" %}
Notre définition de distance ne fonctionne que sur des messages de même longueur car on ne va en pratique comparer avec cette méthode que des messages de même longueur. Il y a également des définitions qui prennent en compte les différences de longueur et des opérations autre que le remplacement d'un symbole par un autre, telle que la *distance de Levenshtein*.
{% enddetails %}

## Quelques exemples de codes correcteurs

Je vais commencer par présenter quelques exemples de codes correcteurs, là encore pour montrer les grandes idées, avant de parler plus généralement de grandes catégories et de leurs avantages et inconvénients.

### Codes de répétition

L'une des options proposées en introduction quand on reçoit un message incorrect est de simplement demander à répéter le message, donc pourquoi ne pas envoyer plusieurs fois le message sans attendre de demande ? C'est le principe des codes de répétition, qui vont simplement envoyer `n` copies de chaque symbole du message d'origine. Par exemple, au lieu de `Do_It`, on enverra `DDDooo___IIIttt`. Pour corriger une erreur, on retient tout simplement quel caractère est le plus courant parmi chaque groupe de `n` caractères. En général on prend un nombre impair de répétitions de sorte à s'assurer qu'une majorité existe.

Ce type de codes est bien évidemment très lourd : on multiplie la quantité d'information à transmettre par le nombre de répétitions ! Cependant, il permet aussi de corriger à chaque symbole un nombre d'erreurs allant jusqu'à la moitié du nombre de répétitions. Il sont donc peu utilisés en tant que tels, puisque les erreurs sont rarement aussi communes.

### Codes de Hamming

Avant d'expliquer le principe des codes de Hamming, je vous propose une petite activité très classique :

{% details "Activité" %}
<div id="hamming_demo">
  Le principe est simple : choisissez un nombre entre 0 et 15 inclus, puis répondez aux questions suivantes. Vous avez le droit de mentir à *une* question. Quand vous avez fini de répondre, appuyez sur "Deviner !" et admirez le résultat !
  <ol>
    <li>Votre nombre est-il supérieur ou égal à 8 ? <input id="hamming_ans_1" type="checkbox"/></li>
    <li>Votre nombre est-il 4, 5, 6, 7, 12, 13, 14 ou 15 ? <input id="hamming_ans_2" type="checkbox"/></li>
    <li>Votre nombre est-il 2, 2, 6, 7, 10, 11, 14 ou 15 ? <input id="hamming_ans_3" type="checkbox"/></li>
    <li>Votre nombre est-il impair ? <input id="hamming_ans_4" type="checkbox"/></li>
    <li>Votre nombre est-il 1, 2, 4, 7, 9, 10, 12 ou 15 ? <input id="hamming_ans_5" type="checkbox"/></li>
    <li>Votre nombre est-il 1, 2, 5, 6, 8, 11, 12 ou 15 ? <input id="hamming_ans_6" type="checkbox"/></li>
    <li>Votre nombre est-il 1, 3, 4, 6, 8, 10, 13 ou 15 ? <input id="hamming_ans_7" type="checkbox"/></li>
  </ol>

  <button id="hamming_demo_button" type="button" onclick="demo_hamming()" class="btn">Deviner !</button>

  <div id="hamming_result_div" hidden>
    Votre nombre est <span id="hamming_result"></span>.
  </div>
  <div id="hamming_lie_div" hidden>
    Vous avez menti à la question <span id=hamming_lie></span>
  </div>
</div>
{% enddetails %}

Vous l'aurez peut-être deviné, si on est capable de retrouver la bonne réponse malgré le mensonge, c'est grâce à un code correcteur, et en particulier grâce à un code de Hamming !
En théorie, pour deviner un nombre entre 0 et 15, il suffit de 4 questions. Mais si l'on autorise un mensonge, ces 4 questions ne suffisent plus, donc on doit en poser trois de plus pour obtenir plus d'informations.

Les codes de Hamming sont donc des codes qui opèrent avec des bits, et reposent sur le principe de *parité* expliqué dans mon MON précédent : un message encodé sera d'une longueur de `2^n - 1` bits, dont `n` bits de parités, qui sont calculés de sorte à ce que, dans le message final, pour chacun de ces bits, le calcul de la parité d'une moitié spécifique du message qui inclue un et un seul de ces bits donne 0. Cela nous permet de corriger un unique bit d'erreur.

{% note "Choix des moitiés à regarder" %}
Pour choisir quelle moitié du message doit être prise en compte pour calculer un bit de parité, on va en fait regarder l'écriture binaire des nombres de `1` à `2^n-1`, et chacun des bits sera calculé à partir de la parité des bits dont les positions dans le message ont un `1` à un endroit particulier dans leur écriture binaire : pour un message de 7 bits, un des bits de parité sera pour les bits aux position 1, 3, 5 et 7, qui s'écrivent en binaire `xx1` ou `x` peut être remplacé par `0` ou `1`, un autre pour les bits aux positions 2, 3, 6 et 7 (`x1x` en binaire), et un dernier pour les bits aux position 4, 5, 6 et 7 (`1xx` en binaire).
Pour que chacun des bits de parités n'interviennent qu'une fois, il faut donc qu'ils soient aux positions 1, 2 et 4. Plus généralement, on utilisera les bits dont la position est une puissance de 2.
{% endnote %}

Il existe également une variante, appelée codes de Hamming étendus, où on ajoute un dernier bit qui contrôle la parité du message entier : cela permet en fait de détecter s'il y a deux erreurs, ce que les codes de Hamming pas étendus ne permettent pas. (Ils ajouteraient même une troisième erreur dans ce cas !)

De nos jours, les codes de Hamming sont utilisés par exemple dans la mémoire RAM à codes correcteurs d'erreurs, mais sont autrement délaissés au profit de codes capables de corriger plus d'erreurs.

On peut montrer que les codes de Hamming non-étendus sont ce que l'on appelle des codes *parfaits*. Concrètement, cela veut dire qu'on ne peut pas faire de code capable de corriger une unique erreur en utilisant moins de redondance que ces codes.

{% details %}

Les codes dont j'ai parlé ici sont les codes de Hamming *binaires*, qui opèrent sur des bits comme éléments du corps fini à deux éléments.
Si vous vous souvenez des groupes finis du MON précédent, les corps finis sont un concept similaire, sauf qu'au lieu d'avoir uniquement une opération qui se comporte comme l'addition, on a deux opérations qui se comportent comme l'addition et la multiplication.

Il est possible de généraliser les codes de Hamming à d'autres corps finis, mais on les retrouve alors généralement sous le nom de codes BCH (pour Bose-Chaudhuri-Hocquenghem).

{% enddetails %}

### Codes de Hadamard

Les codes de Hadamard sont un peu particuliers puisqu'ils ont une redondance *très* élevée : pour un message faisant originellement `n` bits, on ajoute `2^n - n` bits, pour obtenir un message de `2^n` bits ! Cependant, cela leur donne une excellente capacité de correction d'erreurs, puisqu'ils sont capables de corriger à coup sûr des messages dont un quart aurait été corrompu, et avec une très bonne probabilité des messages dont moins de la moitié aurait été corrompue !

Pour cela, il faut s'intéresser aux messages en tant que vecteurs de bits : pour encoder un message, on va calculer son produit scalaire avec tous les vecteurs binaires (tous les vecteurs de bits) possibles de même taille, puis prendre le reste modulo 2 : cela nous donne `2^n` bits, qui seront le message final à envoyer. Souvent, on élimine les vecteurs dont le premier bit est 0, puisqu'ils ne nous donnent aucune information sur le premier bit du message : cela permet de diviser par 2 la taille du message codé, sans en diminuer les capacités de correction.

À cause de leur très grande redondance, ces codes sont utilisés uniquement quand la probabilité d'erreurs est très grande, notamment quand on envoie des satellites dans l'espace. Par exemple, un tel code a été utilisé par la sonde Mariner 9 envoyée sur Mars par la NASA en 1970.

### Codes de Reed-Solomon

Le dernier exemple que je vais aborder va être celui des codes de Reed-Solomon. Contrairement aux codes de Hamming et de Hadamard, ils sont souvent utilisés avec des symboles autres que seulement 0 et 1.
Cette fois-ci, les messages sont vu comme des polynômes, comme pour les CRC vus dans le MON précédent, mais avec des coefficients allant en général jusqu'à 255, et les codes de Reed-Solomon reposent sur le fait que `n+1` points d'abscisses distinctes définissent un unique polynôme de degré `n` ou moins.

Dans leur formulation d'origine, un code de Reed-Solomon correspondait à choisir un nombre de points `n` plus grand que la longueur `l` du message à encoder, calculer la valeur du polynôme à ces points, et envoyer ces valeurs. Pour décoder, il fallait alors, pour chaque ensemble de `l` points, calculer le polynôme de degré `l-1` passant par ces points, et là encore prendre celui qui ressortait le plus souvent, ce qui permet de corriger au plus `(n - l)/2` erreurs. Cependant, c'est très coûteux, à cause du nombre de polynômes à calculer, et le message d'origine n'apparaissait pas directement dans le message codé. D'autres méthodes reposant sur le même principe ont donc été développées depuis, mais font appel à des mathématiques encore plus avancées donc je préfère ne pas les détailler ici. Simplement, je mentionnerai que, en général, on envoie alors un polynôme dont les coefficients de plus haut degré sont les symboles d'origine et dont les coefficients de plus bas degrés sont calculés de sorte à ce que le polynôme final ait des racines connues.

Ces codes ont un intérêt majeur : en plus de corriger des modifications du message, ils permettent également de retrouver des symboles effacés, et sont optimaux parmi les codes ayant cette propriété. C'est pour cette raison qu'ils sont très utilisés, notamment dans les codes QR, les CD et les DVD.

{% note "CIRC" %}
Pour les CD et les DVD, ce qui est utilisé est en fait un "CIRC", pour *cross-interleaved Reed-Solomon code*. Cela consiste en fait à encoder une première fois les données avec un code de Reed-Solomon, les entrelacer pour mélanger les blocs de données, puis réencoder avec un second code de Reed-Solomon. Sur les disques optiques, une rayure pourrait effacer beaucoup de données adjacentes, donc le fait de les entrelacer permet qu'une telle rayure affecte peu un grand nombre de blocs, chacun parfaitement capable de réparer les quelques erreurs engendrées, au lieu d'effacer un bloc entier de données qui seraient alors irrécupérables.
{% endnote %}

## Quelques grandes catégories de codes correcteurs

Parmi les codes correcteurs, on retrouve différentes catégories qui ont chacune des intérêts particuliers. J'en ai à vrai dire déjà mentionné une, les codes BCH, mais ce n'est pas la première dont je vais parler ici.

### Les codes linéaires et leurs descendants

Les codes linéaires tirent leur nom de l'algèbre linéaire : ils consistent à faire de l'ensemble des messages valides un sous-espace vectoriel de tous les messages possibles.
Ils constituent en fait la grande majorité des codes correcteurs, et tous les codes présentés ci-dessus sont linéaires, à l'exception des codes de Hadamard qui ne le sont que sous certaines conditions.

Cette formulation leur apporte deux propriétés intéressantes : ils sont faciles à décrire, puisque le codage est une application linéaire, à laquelle correspond donc une matrice, et il existe une méthode systématique, bien que souvent trop lourde en pratique, pour corriger les erreurs, le décodage par syndrome.
Ce dernier consiste à calculer une certaine valeur qui est là encore une fonction linéaire du message codé, appelé syndrome, que l'on peut ensuite utiliser directement pour trouver les erreurs à l'aide d'une table de correspondances. Le problème, c'est que la taille de cette table croît extrêmement vite.

Cependant, cette formulation extrêment simple pose quelques inconvénients : j'ai évoqué plus haut l'idée de code *parfait*. La théorie des codes linéaires en général ne donne pas d'algorithme permettant de construire des codes parfaits.

Les codes cycliques corrigent cet inconvénient en ajoutant une restriction : il faut que l'ensemble des messages valides soit stable par rotation. C'est-à-dire que si on prend un message valide, et que l'on déplace sa première lettre à la toute fin, on obtient un autre message valide. Cette restriction nous permet en fait d'avoir quelques propriétés supplémentaires, notamment une méthode pour créer des codes binaires parfaits. Mais là encore, ce n'est pas suffisant : tout d'abord, ces codes ne corrigent qu'une erreur par message, et cela ne fonctionne qu'avec des codes binaires.

C'est là qu'interviennent enfin les codes dits BCH, qui donnent des méthodes pour créer des codes permettant de corriger plusieurs erreurs et avec des symboles non-binaires. Ils reposent beaucoup sur la représentation des messages comme polynômes à coefficients dans des corps finis et permettent de créer assez facilement des codes très intéressants, mais pas toujours parfaits. En fait, les codes de Reed-Solomon sont une sous-catégorie de codes BCH qui sont eux parfaits.

### Les codes d'effacement

Un autre type possible d'erreurs sont les erreurs d'effacement, où il y a une perte d'une partie du message, et pas simplement une modification. Les codes qui permettent de corriger ce type d'erreurs, comme les codes de Reed-Solomon, sont appelés des codes d'effacement. Si les codes de Reed-Solomon sont optimaux dans ce cas-là, ils fonctionnent sur des messages de taille fixé (en pratique, un message est découpé en blocs de taille fixe, et chaque bloc est encodé avec un code de Reed-Solomon), et donnent un résultat de taille fixe permettant de corriger un nombre fixe d'effacements. Il existe cependant également des codes qui sont capables de produire une quantité arbitraire de redondance pour un message donné dont seulement une partie légèrement supérieure à la longueur du message initial permet de reconstituer ce message initial, ce sont les codes dits fontaines.

### Les codes convolutifs et les turbo codes.

Enfin, tous les codes que j'ai présenté plus tôt sont des codes dits par bloc, ce qui veut dire qu'ils fonctionnent sur les messages de taille fixe, et que pour encoder un message de taille arbitraire, il faut le découper en plusieurs blocs qui seront envoyés les uns à la suite des autres. Mais il existe également certains codes, comme les codes convolutifs et les turbo codes, qui fonctionnent sur des messages de taille arbitraire sans avoir à les découper. C'est ce type de code, parfois en combinaison avec des code par bloc, qui est utilisé pour les réseaux mobiles, notamment.

## Post-mortem

Malheureusement, je me suis rendue compte que les codes correcteurs d'erreurs étaient un domaine bien trop vaste et surtout complexe mathématiquement pour, déjà en ce qui me concerne, les explorer plus que superficiellement, mais également pour en parler dans ce compte-rendu d'une façon satisfaisante. Cependant, je trouve intéressant d'avoir une idée de comment on arrive à transmettre et stocker tant de données sans erreurs dans notre monde actuel.

## Références

- [But what are Hamming codes? The origin of error correction](https://youtu.be/X8jsijhllIA) sur la chaîne Youtube 3Blue1Brown, une explication animée des codes de Hamming, qui m'ont donné envie de faire ce MON
- [Codage d'un signal audionumérique sur un support optique](https://zanotti.univ-tln.fr/cd/cd.pdf) par J.-P. Zanotti, un rapport de recherche de l'INRIA sur le CD
