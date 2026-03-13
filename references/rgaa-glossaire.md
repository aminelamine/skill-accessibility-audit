# Glossaire officiel RGAA 4.1.2

> **Source :** Référentiel général d'amélioration de l'accessibilité — version 4.1.2  
> Direction interministérielle du numérique (DINUM)

**Usage :** Consulter en mode Guide (définition exacte), Audit (qualifier un cas limite), Review (justifier un NC).

---

## Alternative textuelle (image)

L'alternative textuelle d'une image est déterminée selon l'ordre de priorité suivant :

1. Passage de texte associé via `aria-labelledby` (pour `<img>`, `<svg>`, `role="img"`, etc.)
2. Contenu de l'attribut `aria-label`
3. Contenu de l'attribut `alt` (pour `<img>`, `<area>`, `<input type="image">`)
4. Contenu de l'attribut `title`

**Types d'alternatives selon la nature de l'image :**
- Image porteuse d'information : l'alternative apporte l'information véhiculée
- Image de décoration : aucune alternative ne doit être restituée (`alt=""`)
- Image CAPTCHA : l'alternative décrit seulement la nature et la fonction de l'image

**Note importante :** En cas de conflit entre plusieurs attributs, c'est la valeur réellement 
restituée par les technologies d'assistance de la base de référence qui prévaut.

---

## Ambigu pour tout le monde

L’intention ne peut être déterminée à partir du lien et de toute l’information de la page web
présentée à l’utilisateur en même temps que ce lien (c’est-à-dire qu’un lecteur sans limitation
fonctionnelle ne connaîtrait pas la fonction d’un lien avant de l’activer). Exemple : le mot « goyave »
dans la phrase suivante utilisé comme lien : « L’une des exportations importantes est la goyave ». Ce
lien pourrait conduire à une définition de la goyave, à un graphe présentant une liste des quantités
de goyaves exportées ou à une photo de personnes récoltant la goyave. Jusqu’à ce que le lien soit
activé, tout utilisateur est dans l’incertitude et une personne handicapée n’est donc pas
désavantagée.

---

## Audiodescription synchronisée (média temporel)

Narration ajoutée (via un fichier son) à une piste sonore pour décrire les détails visuels importants qui
ne peuvent être compris à partir de la piste sonore principale seulement. L’audiodescription doit être
synchronisée avec le média temporel par un dispositif applicatif lié au lecteur lui-même ou fourni par
le développement par exemple avec JavaScript.
Note 1 : l’audiodescription d’une vidéo fournit de l’information à propos des actions, des
personnages, des changements de scènes, du texte apparaissant à l’écran et d’autres contenus
visuels.
Note 2 : dans une audiodescription standard, la narration est ajoutée durant les pauses qui existent
dans le dialogue. (Voir aussi audiodescription étendue.)
Note 3 : lorsque toute l’information de la vidéo est déjà donnée dans la piste audio, aucune
audiodescription supplémentaire n’est requise.

---

## Bouton (formulaire)

Élément d’un formulaire qui permet d’effectuer une action prédéfinie. Par exemple, le bouton de
soumission d’un formulaire permet l’envoi au serveur des informations collectées pour leur
traitement. L’intitulé d’un bouton doit décrire l’action qui résulte de son activation (par exemple :
« Lancer votre recherche », « Envoyer votre message »).
En HTML, il y a trois types de boutons de formulaire :
- Balise <input> de type submit, reset ou button ;
- Balise <input> de type image ;
- Balise <button>.
Il est également possible de restituer un bouton à l’aide du rôle WAI-ARIA button.
L’intitulé du bouton peut être de six types :
- Le contenu du passage de texte associé au bouton via l’attribut WAI-ARIA aria-labelledby
lorsqu’il est présent ;
- Le contenu de l’attribut aria-label lorsqu’il est présent ;
- Le contenu de l’attribut alt d’un bouton de type image ;
- Le contenu de l’attribut value des boutons de type submit, reset ou button ;
- Le contenu de la balise <button> ;
- L

---

## Captcha

Test permettant de distinguer un être humain d'un ordinateur, utilisé pour protéger l'accès 
à certains services en ligne contre les robots.

**Exigence RGAA :** Toute image CAPTCHA doit avoir une alternative (ex. : version sonore, 
autre moyen non visuel permettant d'accéder au même service). L'alternative textuelle de 
l'image décrit seulement la nature et la fonction (`alt="Code de sécurité anti-spam"`).

**Critères associés :** 1.4, 13.5

---

## Champ de saisie de formulaire

Objet d’un formulaire permettant à l’utilisateur :
- De saisir des données textuelles ou préformatées :
  - input type="text" ;
  - input type="password" ;
  - input type="search" ;
  - input type="email" ;
  - input type="number" ;
  - input type="tel" ;
  - input type="url" ;
  - textarea.
- De sélectionner des valeurs prédéfinies :
  - input type="checkbox" ;
  - input type="radio" ;
  - input type="date" ;
  - input type="range" ;
  - input type="color" ;
  - input type="time" ;
  - input type="month" ;
  - input type="week" ;
  - input type="datetime-local" ;
  - select ;
  - datalist ;
  - optgroup ;
  - option.
- De télécharger des fichiers :
  - input type="file".
- Ou d’afficher des résultats :
  - output ;
  - progress ;
  - meter.
- Les balises possédant un rôle WAI-ARIA permettant de restituer un champ de formulaire sont
également couvertes par cette définition :
  - progressbar ;
  - slider ;
  - spinbutton ;
  - textbox ;
  - listbox ;
  - searchbox ;
  - combobox ;
  - option ;
  - checkbox ;
  - radio ;
  - switch.
- Les objets de formulair

---

## Compatible avec l'accessibilité

Un contenu ou composant est compatible avec l'accessibilité lorsqu'il fonctionne avec les technologies d'assistance et les fonctions d'accessibilité des navigateurs que les utilisateurs sont susceptibles d'utiliser.

Pour être compatible, le composant doit être pleinement fonctionnel — en termes de restitution et de fonctionnalités — sur au moins une des combinaisons technologie d'assistance / navigateur de la base de référence (environnement de test).

**Conditions :**
- Fonctionner sur au moins 1 combinaison AT/navigateur de la base de référence
- Restitution correcte (nom, rôle, valeur, état fidèlement exposés)
- Toutes les fonctionnalités accessibles au clavier

---

## Composant d'interface

Élément avec lequel l'utilisateur peut interagir : boutons, liens, champs de formulaire, menus déroulants, cases à cocher, curseurs, etc.

Peut être un élément HTML natif (`<button>`, `<input>`, `<select>`) ou un élément géré via JavaScript et WAI-ARIA.

**Exigences RGAA :** Tout composant d'interface doit :
- Avoir un nom accessible (critère 7.1)
- Être accessible au clavier (critère 7.3)
- Avoir un rôle, un état et une valeur correctement exposés aux AT

---

## Conforme

Un critère est **conforme** (C) s'il est validé sur toutes les pages de l'échantillon d'audit.

Si un critère est invalidé sur une seule page, il est **non conforme** (NC) pour l'ensemble de l'audit.

Un critère est **non applicable** (NA) s'il ne peut pas être testé (ex. : critère multimédia sur un site sans vidéo).

**Calcul du taux :** `(C / (C + NC)) × 100` — les NA sont exclus du calcul.

---

## Contenu alternatif

Contenu venant se substituer à un autre apportant la même information mais pouvant être présenté
de façon différente. Ce contenu peut être de forme textuelle mais également être lui-même structuré
à l’aide de balises. Un contenu alternatif devra respecter l’ensemble des critères du RGAA qui lui sont
applicables pour être considéré comme une alternative accessible à l’élément qu’il remplace.
Exemple : un tableau de données peut être le contenu alternatif d’une image bitmap (balise
<canvas>) affichant un graphique statistique.
Contenu caché
Les technologies d’assistance (notamment les lecteurs d’écran) ne restituent pas le contenu masqué
via les propriétés :
- display avec la valeur none (display: none) ;
- visibility avec la valeur hidden (visibility: hidden) ;
- font-size avec la valeur 0 (font-size:0) ;
- Attribut HTML5 hidden ;
- Attribut WAI-ARIA aria-hidden="true".
Tous les contenus utilisant une ou plusieurs de ces propriétés et attributs sont applicables pour le
critère 10.8.
Con

---

## Contenu cryptique

Contenu dont la signification n'est pas immédiatement accessible sans explication. Exemples : art ASCII, émoticônes textuels (`:-)`, `XD`), abréviations non conventionnelles, syntaxe codée.

**Exigence RGAA (critère 13.6) :** Tout contenu cryptique doit avoir une alternative compréhensible via `title`, une définition dans le contexte, ou un autre mécanisme accessible.

---

## Contraste

Opposition marquée entre la luminosité d’une couleur de premier plan et d’une couleur d’arrière-
plan. Le rapport de contraste est basé sur la différence de luminance relative entre l’arrière-plan et le
premier plan selon la règle : (L1 + 0,05) / (L2 + 0,05) où L1 est la luminance relative la plus claire et L2 la
luminance relative la plus sombre. La luminosité est calculée selon la formule suivante : L = 0,2126 * R
+ 0,7152 * G + 0,0722 * B. Où R, G et B sont définis par :
- Si R sRGB ≤ 0,03928 alors R = R sRGB /12,92 sinon R = ((R sRGB +0,055)/1,055) ^ 2,4 ;
- Si G sRGB ≤ 0,03928 alors G = G sRGB /12,92 sinon G = ((G sRGB +0,055)/1,055) ^ 2,4 ;
- Si B sRGB ≤ 0,03928 alors B = B sRGB /12.92 sinon B = ((B sRGB +0,055)/1,055) ^ 2,4.
et R sRGB, G sRGB et B sRGB sont définis par :
- R sRGB = R8bit/255 ;
- G sRGB = G8bit/255 ;
- B sRGB = B8bit/255.
Le caractère « ^ » est l’opérateur de puissance.
Note : la mesure de contraste concerne le texte, le texte en image, le texte et le texte en im

---

## Couleur d'arrière-plan contiguë et couleur contiguë

**Couleur d'arrière-plan contiguë :** couleur d'arrière-plan directement en contact avec le bord extérieur du composant d'interface ou de l'élément graphique.

**Couleur contiguë :** couleur adjacente à un autre élément, sans espace ni bordure intermédiaire.

Ces notions servent à évaluer le contraste des composants UI et éléments graphiques (critères 3.2, 3.3) en tenant compte de la couleur de fond environnante.

**Exemple :** Un bouton blanc avec bordure bleue sur fond blanc → la couleur d'arrière-plan contiguë est le fond blanc extérieur à la bordure.

---

## Décoration, image de décoration

Image sans valeur informative, purement esthétique ou décorative, n'apportant aucune information nécessaire à la compréhension du contenu.

**Implémentation correcte :**
- `<img>` : `alt=""` (attribut vide obligatoire, sans `title`)
- `<svg>` : `aria-hidden="true"`, dépourvue de `<title>`
- `background-image` CSS : naturellement ignorée des AT

**Distinction clé :** C'est le rôle de l'image dans son contexte qui détermine si elle est décorative, pas son apparence. Critère associé : 1.2

---

## Élément graphique

Élément faisant appel à une représentation visuelle telle que des images, des pictogrammes ou des
graphiques.
Cet élément peut être composé d’une ou plusieurs parties dont la visibilité est nécessaire à sa
compréhension (par exemple chaque point sur chaque ligne d’un graphique de statistiques).

---

## Ensemble de pages

Pages web liées les unes aux autres par des liens et constituant un ensemble cohérent à l’intérieur
d’un site web. Par exemple, les pages d’une rubrique spécifique, les pages d’un blog, les pages
d’administration d’un compte client sont autant d’ensembles de page.
Note : la page d’accueil d’un site web peut constituer, à elle seule, un « ensemble de pages » du fait
de son unicité.

---

## En-tête de colonne ou de ligne

Contenu d’une cellule dans un tableau de données (la première cellule d’une colonne ou d’une ligne,
généralement) qui sert d’intitulé pour la totalité ou une partie des cellules de la colonne ou de la
ligne. Une colonne ou une ligne peut contenir plusieurs en-têtes (en-tête intermédiaire). Lorsque les
en-têtes s’appliquent à l’ensemble d’une ligne ou d’une colonne, ils peuvent être structurés avec une
balise <th> ou une balise pourvue d’un attribut WAI-ARIA role="rowheader" ou
role="columnheader". Dans le cas contraire, seule une balise <th> peut être utilisée.
Note : seule la balise <th> étant totalement supportée par l’ensemble des technologies d’assistance, il
est fortement recommandé de privilégier cette solution lors de la mise en œuvre afin d’éviter de
nombreuses vérifications dans les différentes combinaisons prévues dans l’environnement de test (ou
« base de référence »).
Environnement maîtrisé
Tout environnement dans lequel l’accès à l’information, les technologies, les condit

---

## Étiquette de champ de formulaire

Texte à proximité du champ de formulaire permettant d’en connaître la nature, le type ou le format
des informations attendues. L’étiquette peut être associée au champ de formulaire de plusieurs
manières :
- Par l’utilisation d’une balise <label> ;
- Par l’utilisation de l’attribut WAI-ARIA aria-label ;
- Par l’utilisation d’une liaison entre le texte et le champ par l’attribut WAI-ARIA aria-
labelledby ;
- Par l’utilisation de l’attribut title.
Note importante : lorsque plusieurs de ces techniques sont présentes sur un même champ, le calcul
du « nom accessible », c’est-à-dire ce qui sera restitué, obéit à un ordre strict :
- aria-labelledby ;
- Sinon aria-label ;
- Sinon <label> ;
- Sinon title.
Cet ordre doit être utilisé pour l’évaluation de la pertinence de l’étiquette (critère 11.2). Par exemple,
même dans le cas de la présence d’un <label>, c’est le passage de texte référencé par aria-
labelledby qui doit être pris en compte.
Référence : Accessible name and description calculation

---

## Fonctionnalité de contrôle d'un média temporel

Possibilité pour l'utilisateur de contrôler la lecture d'un média temporel par le clavier et tout dispositif de pointage. Les fonctionnalités obligatoires minimales sont :

- **Lecture, pause ou stop** : obligatoire sur tout média temporel
- **Activation/désactivation du son** : obligatoire si le média a du son
- **Contrôle des sous-titres** : obligatoire si le média a des sous-titres
- **Contrôle de l'audiodescription** : obligatoire si le média a une audiodescription

Chaque fonctionnalité doit être accessible au clavier et à tout dispositif de pointage, et les contrôles doivent être accessibles aux technologies d'assistance (nom et rôle corrects).

**Critères associés :** 4.10 (contrôle de la lecture automatique), 4.12 (contrôle des fonctionnalités du lecteur)

---

## Image bitmap

(élément <canvas>) ;
- Image vectorielle (élément <svg>).
Lien composite :
En HTML, le « nom accessible » correspond au texte constitué à partir de l’ensemble :
- du texte contenu dans le lien ;
- du texte contenu dans les éléments enfant du lien ;
- du contenu de l’alternative textuelle de la ou des images comprises dans le lien.
Dans le cas d’un lien SVG (version 1.1), le « nom accessible » est obtenu comme suit :
- Passage de texte associé par l’attribut WAI-ARIA aria-labelledby ;
- Sinon, contenu de l’attribut WAI-ARIA aria-label ;
- Sinon, contenu de l’élément <title> enfant direct du lien ;
- Sinon, contenu de l’attribut xlink:title ;
- Sinon, contenu texte d’un ou plusieurs éléments <text>.
Il faut cependant être vigilant car cet algorithme de calcul n’est pas encore pris en compte et effectif
au sein des différents lecteurs d’écran. À ce jour, le support est disponible avec VoiceOver, mais
incomplet ou lacunaire avec JAWS et NVDA. Si bien que le plus petit dénominateur commun s

---

## Image-lien

Image utilisée comme unique contenu d'un lien. L'alternative textuelle doit décrire la **destination du lien**, pas l'image.

```html
<!-- ❌ Décrit l'image -->
<a href="/accueil"><img src="maison.png" alt="Icône maison"></a>

<!-- ✅ Décrit la destination -->
<a href="/accueil"><img src="maison.png" alt="Retour à l'accueil"></a>
```

**Critère associé :** 1.5

---

## Image objet

Image incorporée ou générée par une balise <object>.
Image porteuse d’information
Image qui véhicule une information nécessaire à la compréhension du contenu auquel elle est
associée.
Note 1 : lorsque l’image est le seul contenu d’un lien, son alternative est l’intitulé du lien. Dans ce cas,
l’alternative de l’image devrait être évaluée avec la thématique « Liens ».
Note 2 : lorsqu’un bouton de formulaire, inséré avec l’élément <button>, ne contient qu’une image
(balise <img>, <object>, <embed>, <canvas> ou <svg>), l’alternative de l’image est l’intitulé du bouton.
Deux cas peuvent se présenter :
- Le bouton est contrôlé par son type, par exemple, le type submit ou reset, et fait partie d’un
formulaire. Dans ce cas, le bouton image doit être évalué avec la thématique « Formulaires » ;
- Le bouton est contrôlé par un dispositif JavaScript. Dans ce cas, le bouton image doit être
évalué avec la thématique « Scripts ».
Image réactive
- Image réactive côté client (attribut usemap) : image d

---

## Image porteuse d'information

Image qui véhicule une information nécessaire à la compréhension du contenu, non disponible par un autre moyen sur la page.

**Exemples :** graphique de données, photo illustrant un contenu sans légende suffisante, pictogramme fonctionnel, logo avec texte, image-lien.

**Distinction avec image de décoration :**
- Porteuse d'information → `alt` renseigné et pertinent
- Décoration → `alt=""`

**Critères associés :** 1.1 (présence de l'alternative), 1.3 (pertinence)

---

## Image réactive

- Image réactive côté client (attribut usemap) : image divisée en zones cliquables ou neutres
(attribut nohref) ;
- Image réactive côté serveur (attribut ismap) : image pour laquelle le navigateur transmet au
serveur les coordonnées du pointeur, chaque jeu de coordonnées correspondant à une
ressource (page web). L’image réactive côté serveur est extrêmement rare.
Note : en HTML5, l’attribut ismap est obsolète et non conforme pour les boutons de type image
(input type="image").
Image-test
Image servant dans un test, captcha ou une image servant de test dans un quiz ou un jeu.
Exemple : une série d’images présente un détail issu de tableaux célèbres ; il faut reconnaître le titre
et le peintre de chaque tableau. Dans cette situation, il n’est pas possible de donner une alternative
pertinente (par exemple le nom du tableau et/ou du peintre) sans rendre le test inutilisable.
L’alternative doit alors se contenter de donner la possibilité d’identifier l’image, par exemple “image 1
du test”.

---

## Image texte

Image affichant du texte.
Note : il n’est pas recommandé d’utiliser des images-textes. Lorsqu’il est possible de reproduire les
mêmes effets en CSS, le critère 1.8 impose que le texte soit reproduit en texte CSS, ou qu’un
mécanisme de remplacement permette à l’utilisateur de remplacer ces images par du texte stylé en
CSS.
Image texte objet
Image générée par la balise <object> et affichant du texte.
Image véhiculant une information (donnée par la couleur)
Image dont tout ou partie du contenu transmet visuellement une information par l’intermédiaire
d’une couleur uniquement.
Indication de champ obligatoire
Indication textuelle ou graphique (icône) permettant à l’utilisateur de savoir que la saisie d’un champ
est obligatoire préalablement à la saisie.
Note : Dans le cas où cette indication n’est pas réalisée de manière textuelle explicite (icône, “*”, “!”,
etc.), l’explication de la signification de cette indication doit se situer, visuellement et dans l’ordre du
code source, avant la pre

---

## Image vectorielle (balise SVG)

(élément <svg>).
Lien composite :
En HTML, le « nom accessible » correspond au texte constitué à partir de l’ensemble :
- du texte contenu dans le lien ;
- du texte contenu dans les éléments enfant du lien ;
- du contenu de l’alternative textuelle de la ou des images comprises dans le lien.
Dans le cas d’un lien SVG (version 1.1), le « nom accessible » est obtenu comme suit :
- Passage de texte associé par l’attribut WAI-ARIA aria-labelledby ;
- Sinon, contenu de l’attribut WAI-ARIA aria-label ;
- Sinon, contenu de l’élément <title> enfant direct du lien ;
- Sinon, contenu de l’attribut xlink:title ;
- Sinon, contenu texte d’un ou plusieurs éléments <text>.
Il faut cependant être vigilant car cet algorithme de calcul n’est pas encore pris en compte et effectif
au sein des différents lecteurs d’écran. À ce jour, le support est disponible avec VoiceOver, mais
incomplet ou lacunaire avec JAWS et NVDA. Si bien que le plus petit dénominateur commun sur
lequel il est possible de se reposer p

---

## Indication de sens de lecture

Information permettant d'identifier le sens de lecture d'un contenu dont le sens naturel n'est pas gauche-droite (arabe, hébreu, etc.).

En HTML, l'attribut `dir` indique le sens :
- `dir="ltr"` → gauche à droite
- `dir="rtl"` → droite à gauche

**Exigence RGAA (critère 8.8) :** Quand le sens de lecture d'un contenu diffère du sens général de la page, il doit être signalé avec `dir` sur l'élément concerné.

---

## Intitulé de lien

Texte qui identifie un lien. Déterminé dans cet ordre de priorité :
1. Passage de texte via `aria-labelledby`
2. Attribut `aria-label`
3. Attribut `alt` (si lien image)
4. Attribut `title`
5. Texte visible du lien

**Exigence RGAA (critères 6.1 et 6.2) :** L'intitulé doit exister et être explicite — permettre de comprendre fonction et destination sans contexte.

**Anti-pattern :** Liens "Lire la suite", "Cliquez ici" répétés sans différenciation → non conformes.

---

## Landmarks

WAI-ARIA propose des rôles permettant d’indiquer les zones principales (régions) du document. Ces
rôles sont très profitables aux utilisateurs de lecteurs d’écran notamment, mais également aux
utilisateurs de la navigation au clavier qui peuvent ainsi bénéficier de fonctionnalités de navigation
rapide dans la structure du document.
Les rôles doivent être définis dans le document en fonction de la nature de la zone :
- La zone d’en-tête doit avoir un attribut WAI-ARIA role="banner" ;
- Le menu de navigation principal doit avoir un attribut WAI-ARIA role="navigation" ;
- La zone de contenu principal doit avoir un attribut WAI-ARIA role="main" ;
- La zone de pied de page doit avoir un attribut WAI-ARIA role="contentinfo" ;
- La zone de moteur de recherche sur le site doit avoir un attribut WAI-ARIA role="search".
Note 1 : Si la plupart des lecteurs d’écran mettent à disposition ces fonctionnalités, les navigateurs
n’ont pas encore proposé de fonctionnalité de navigation dédiée pour les ut

---

## Légende de tableau

Texte associé à un tableau qui en décrit le contenu ou la fonction. Implémentée avec `<caption>`, placée immédiatement après la balise `<table>`.

```html
<table>
  <caption>CA par trimestre 2024</caption>
  ...
</table>
```

**Exigence RGAA (critère 5.4) :** Chaque tableau de données doit avoir un titre. `<caption>` est la méthode recommandée.

**Critères associés :** 5.4 (présence), 5.5 (pertinence)

---

## Lien d'évitement ou d'accès rapide

Lien permettant de naviguer directement vers les zones importantes (contenu principal, navigation, recherche), en sautant les blocs répétés.

**Exigence RGAA (critère 12.1) :** Au moins un lien d'évitement vers le contenu principal. Visible au focus clavier (critère 12.7).

```html
<a href="#main" class="skip-link">Aller au contenu</a>
<main id="main">...</main>
```

Le lien peut être masqué visuellement et n'apparaître qu'au focus clavier (`.sr-only-focusable`).

---

## Lien ou bouton adjacent

Lien ou bouton présenté de manière adjacente à un élément dans la page. Le lien ou bouton doit être
adjacent visuellement dans la représentation graphique (CSS activé) et dans le code HTML. Dans le
code HTML, le lien ou bouton doit se situer juste avant ou juste après l’élément auquel il est
adjacent.
Liens d’évitement ou d’accès rapide
Liens dont la fonction est de permettre de naviguer à l’intérieur de la page (lien d’évitement, lien
d’accès au formulaire de recherche ou au menu…). Ces liens peuvent soit permettre d’accéder à une
zone de la page (lien d’accès rapide) ou de sauter une zone dans la page (lien d’évitement).
Note 1 : Un lien d’évitement ou d’accès rapide fonctionnel est un lien dont l’activation permet de
reprendre la lecture et la navigation clavier à partir de la cible du lien lors de l’utilisation des
navigateurs et des aides techniques retenus dans l’environnement de test (ou « base de référence »)
de l’audit.
Note 2 : les liens d’évitements ou d’accès rapide doivent

---

## Liste

des fonctionnalités obligatoires de contrôle de la consultation :
  - L’objet multimédia doit toujours avoir les fonctionnalités suivantes, au minimum : lecture,
pause ou stop ;
  - Si l’objet multimédia a du son, il doit avoir une fonctionnalité d’activation / désactivation
du son ;
  - Si l’objet multimédia a des sous-titres, il doit avoir une fonctionnalité de contrôle de
l’apparition / disparition des sous-titres ;
  - Si l’objet multimédia a une audiodescription, il doit avoir une fonctionnalité de contrôle de
l’apparition / disparition de l’audiodescription.
- Chaque fonctionnalité doit être accessible par le clavier, via la touche de tabulation, et par
tout dispositif de pointage au moins.
- Chaque fonctionnalité doit être activable par le clavier et par tout dispositif de pointage, au
moins.
Note : s’il n’y a pas de son à un média temporel, il n’est pas utile de mettre une fonctionnalité
d’activation / désactivation du son. Si cette fonctionnalité est cependant présente et qu’elle
néce

---

## Média non temporel

Contenu qui ne se déroule pas dans le temps, consultable via un plugin (Flash, Java, Silverlight…) ou
via les éléments svg et canvas ; par exemple, une carte interactive en Flash, une application Flash ou
Java, un diaporama sont des médias non temporels. Un média non temporel peut contenir des
médias temporels (un lecteur Flash qui propose une liste de vidéos à consulter, par exemple).
Note : l’utilisation du paramètre wmode pour un objet Flash avec les valeurs "transparent" et "opaque"
invalide de fait le critère 4.13. En effet, l’utilisation de ces valeurs a pour conséquence que l’animation
Flash vue du côté des utilisateurs de lecteur d’écran est invisible.
Média temporel (type son, vidéo et synchronisé)
- Média temporel seulement audio : contenu sonore (Wav, Mp3…) ;
- Média temporel seulement vidéo : images ou photos en mouvement ou en séquence ;
- Média temporel synchronisé : flux audio ou vidéo synchronisé avec un autre format pour
présenter de l’information et/ou comportant des

---

## Média synchronisé

Média temporel combinant une piste audio et une piste vidéo synchronisées. Exemple type : vidéo avec bande-son.

**Distinctions :**
- Seulement audio : podcast, MP3
- Seulement vidéo : animation silencieuse
- Synchronisé : vidéo avec son (le plus courant)

**Exigences RGAA (thématique 4) :** Sous-titres obligatoires (critère 4.2), audiodescription si contenu visuel important (critère 4.6).

---

## Média temporel

(type son, vidéo et synchronisé)
- Média temporel seulement audio : contenu sonore (Wav, Mp3…) ;
- Média temporel seulement vidéo : images ou photos en mouvement ou en séquence ;
- Média temporel synchronisé : flux audio ou vidéo synchronisé avec un autre format pour
présenter de l’information et/ou comportant des composants temporels interactifs. Un média
temporel peut être consulté de 2 manières différentes :
- Fichier à télécharger consultable avec un logiciel externe à la page web ;
- Contenu embarqué dans la page web et consultable dans la page web via :
  - Un plugin (par exemple une vidéo diffusée par un lecteur Flash) ;
  - L’élément <video> (par exemple une vidéo) ;
  - L’élément <audio> (par exemple un podcast) ;
  - L’élément <svg> (par exemple un dessin animé vectoriel) ;
  - L’élément <canvas> (par exemple un dessin animé en image bitmap) ;
  - L’élément <bgsound> pour diffuser un arrière-plan sonore à la page web.
Un média temporel peut être diffusé en temps réel ou être proposé en l

---

## Message de statut

Un message de statut informe l’utilisateur d’un changement de contenu dans la page sans
interrompre son activité principale (il n’y a pas de changement de contexte par exemple un
repositionnement du focus sur le message).
Un message de statut peut informer sur :
- Le succès ou le résultat d’une action ;
- L’état occupé d’une application ;
- L’état de progression d’un processus ;
- L’existence d’erreur.
Modifier ou annuler les données et les actions effectués
Procédés par lesquels un utilisateur peut modifier les données qu’il a saisies, faire annuler sa saisie ou
faire annuler les actions découlant de sa saisie par exemple annuler une commande ou un virement
bancaire.
Note : La page contenant un formulaire qui modifie ou supprime des données, ou qui transmet des
réponses à un test ou un examen, ou dont la validation a des conséquences financières ou juridiques,
doit indiquer explicitement la durée pendant laquelle l’utilisateur peut demander l’annulation de sa
saisie. Elle devra égalem

---

## Motif de conception

Un motif de conception (Design Pattern) est un modèle défini dans le document WAI-ARIA 1.1
Authoring Practices qui décrit la structure, les rôles et propriétés et le comportement clavier que doit
respecter un composant JavaScript (widget).
Il est recommandé que les composants développés en JavaScript utilisant des attributs WAI-ARIA
correspondant à un motif de conception respectent celui-ci. Attention cependant, les motifs de
conception ne sont pas tous adaptés à un usage non applicatif, en particulier pour les sites proposant
un affichage en contexte mobile.
Note 1 : compte tenu du manque de support de certaines propriétés et de certains rôles WAI-ARIA et
de la grande variabilité des situations dans lesquelles un composant JavaScript peut être proposé, il
est possible d’adapter des motifs de conception à des contextes ou des utilisations particulières.
Dans ce cas, le motif de conception adapté doit :
- Respecter la structure générale : par exemple un ensemble de panneaux (rôle WAI-AR

---

## Nom accessible

» restitué par les technologies d’assistance.
Dans le cas d’un lien HTML, le « nom accessible » est obtenu selon l’ordre suivant :
- passage de texte associé par l’attribut WAI-ARIA aria-labelledby ;
- sinon, contenu de l’attribut WAI-ARIA aria-label ;
- sinon, contenu du lien ;
- sinon, contenu de l’attribut title.
Cet ordre doit être utilisé pour déterminer ce qui constitue l’intitulé du lien. Par exemple :
- en cas de présence conjointe d’un attribut WAI-ARIA aria-label et d’un attribut WAI-ARIA
aria-labelledby, c’est le passage de texte référencé par l’attribut WAI-ARIA aria-labelledby
qui doit être considéré comme l’intitulé ;
- en cas de présence conjointe d’un attribut WAI-ARIA aria-label et d’un contenu dans le lien,
c’est le contenu de l’attribut WAI-ARIA aria-label qui doit être considéré comme l’intitulé.
Référence : Accessible name and description calculation.
Dans le cas où le « nom accessible » est obtenu à partir du contenu du lien, celui-ci sera variable en
fonction des

---

## Passage de texte

associé via l’attribut WAI-ARIA aria-labelledby pour les balises :
  - <img> ;
  - <input type="image"> ;
  - <svg> ;
  - <object type="image/…"> ;
  - <embed type="image/…"> ;
  - <canvas> ;
  - balises possédant un attribut WAI-ARIA role="img".
- Sinon, contenu de l’attribut WAI-ARIA aria-label pour les éléments :
  - <img> ;
  - <area> ;
  - <input type="image"> ;
  - <svg> ;
  - <object type="image/…"> ;
  - <embed type="image/…"> ;
  - <canvas> ;
  - balises ouvrantes possédant un attribut WAI-ARIA role="img".
- Sinon, contenu de l’attribut alt pour les balises :
  - <img> ;
  - <area> ;
  - <input type="image">.
- Sinon, contenu de l’attribut title pour les balises :
  - <img> ;
  - <input type="image"> ;
  - <object type="image/…"> ;
  - <embed type="image/…">.
Cet ordre doit être utilisé pour déterminer ce qui constitue l’alternative textuelle.
Néanmoins, en cas de support partiel de l’algorithme de calcul du « nom accessible », c’est la valeur
réellement restituée par les technologies d’assistance utilisées dans l’envir

---

## Plan du site

;
- Moteur de recherche.
2.3.15T
Tableau de données
Un tableau de données est une structure introduite par une balise <table> ou lorsqu’il est
correctement restitué par les technologies d’assistance par une balise pourvue d’un attribut WAI-
ARIA role="table". Cette balise permet de structurer des informations en lignes et en colonnes via
des cellules de données et des cellules d’en-têtes.
Tableau de données ayant un titre
Tableau de données ayant un attribut ou contenant une balise dont le contenu fait office de titre.
Tableau de données précédé ou suivi d’un passage de texte associé au tableau faisant office de titre.
Dans la mesure où il est bien correctement restitué et associé par les technologies d’assistance au
tableau de données, le titre associé peut être :
- Dans une balise <caption> ;
- Dans un attribut title ;
- Dans un attribut WAI-ARIA aria-label ;
- Dans une balise associée au tableau de données via un attribut WAI-ARIA aria-labelledby sur
le tableau.
Note : seule la bali

---

## Présentation de l'information

Mise en forme visuelle : couleur, taille, typographie, positionnement, style. Distincte de la structure sémantique.

**Principe RGAA (thématique 10) :** L'information ne doit pas être véhiculée uniquement par la présentation.

**Exemples de non-conformité :**
- Champs obligatoires signalés en rouge uniquement (couleur seule)
- Titres stylés en gras sans balise `<h>` (style seul)
- Contenu important visible à l'écran mais absent du DOM

---

## Prise de focus

La prise de focus est l’état renvoyé par un élément qui reçoit l’attention suite à une action de
l’utilisateur. Il y a trois moyens en HTML de donner le focus à un élément :
- En activant l’élément par un dispositif de pointage (exemple : souris) ;
- En atteignant l’élément par la touche tabulation ou majuscule + tabulation ;
- En activant l’élément par un raccourci clavier (accesskey).
Certains éléments reçoivent naturellement le focus, par exemple : <a href>, <area href>, <button>,
<input>, <object>, <select>, <label>, <legend>, <optgroup>, <option> et <textarea>. Le
comportement de l’élément, lors de la prise de focus, dépend de sa nature ; un lien, par exemple,
devra être activé après la prise de focus (sauf utilisation de script). En revanche, un élément de
formulaire, comme <textarea>, devra autoriser la saisie suite à la prise de focus. Les éléments
<label> et <legend> ne reçoivent la prise de focus que via le pointeur souris. Pour l’élément <label>,
le comportement attendu est

---

## Raccourci clavier d'une seule touche

Raccourci activé par une seule touche (lettre, chiffre, ponctuation) sans modificateur (Ctrl, Alt, Maj).

**Problème :** Activé accidentellement par les utilisateurs de logiciels de reconnaissance vocale ou de claviers adaptés.

**Exigence RGAA (critère 12.10) :** L'utilisateur doit pouvoir désactiver le raccourci, le reconfigurer avec une touche non-caractère, ou le désactiver au focus sur un composant.

---

## Rôle WAI-ARIA

Attribut `role` définissant la nature sémantique d'un élément HTML pour les technologies d'assistance.

**Catégories :**
- Structure : `banner`, `main`, `navigation`, `contentinfo`, `complementary`, `region`
- Widget : `button`, `checkbox`, `dialog`, `listbox`, `menu`, `slider`, `tab`, `tooltip`
- Live region : `alert`, `status`, `log`

**Règle :** Ne jamais attribuer un `role` contredisant la sémantique native HTML sauf nécessité avérée. Voir règle n°1 d'ARIA dans `design-patterns.md`.

---

## Script

.
Note 1 : l’audiodescription d’une vidéo fournit de l’information à propos des actions, des
personnages, des changements de scènes, du texte apparaissant à l’écran et d’autres contenus
visuels.
Note 2 : dans une audiodescription standard, la narration est ajoutée durant les pauses qui existent
dans le dialogue. (Voir aussi audiodescription étendue.)
Note 3 : lorsque toute l’information de la vidéo est déjà donnée dans la piste audio, aucune
audiodescription supplémentaire n’est requise.
Bouton (formulaire)
Élément d’un formulaire qui permet d’effectuer une action prédéfinie. Par exemple, le bouton de
soumission d’un formulaire permet l’envoi au serveur des informations collectées pour leur
traitement. L’intitulé d’un bouton doit décrire l’action qui résulte de son activation (par exemple :
« Lancer votre recherche », « Envoyer votre message »).
En HTML, il y a trois types de boutons de formulaire :
- Balise <input> de type submit, reset ou button ;
- Balise <input> de type ima

---

## Structure du document

Ensemble d’éléments permettant de définir les grandes zones d’une page HTML telles que la zone
d’en-tête de la page, les zones de navigation principale et secondaire, la zone de contenu principal et
la zone de pied de page.
Système de navigation
Tout procédé permettant une navigation dans le site ou dans une page, les systèmes de navigation
retenus sont :
- Menu de navigation principal ;
- Table des matières ;
- Plan du site ;
- Moteur de recherche.
2.3.15T

---

## Tableau de données

Un tableau de données est une structure introduite par une balise <table> ou lorsqu’il est
correctement restitué par les technologies d’assistance par une balise pourvue d’un attribut WAI-
ARIA role="table". Cette balise permet de structurer des informations en lignes et en colonnes via
des cellules de données et des cellules d’en-têtes.
Tableau de données ayant un titre
Tableau de données ayant un attribut ou contenant une balise dont le contenu fait office de titre.
Tableau de données précédé ou suivi d’un passage de texte associé au tableau faisant office de titre.
Dans la mesure où il est bien correctement restitué et associé par les technologies d’assistance au
tableau de données, le titre associé peut être :
- Dans une balise <caption> ;
- Dans un attribut title ;
- Dans un attribut WAI-ARIA aria-label ;
- Dans une balise associée au tableau de données via un attribut WAI-ARIA aria-labelledby sur
le tableau.
Note : seule la balise <caption> étant complètement supporté par l’ensem

---

## Tableau de données complexe

Un tableau de données est une structure introduite par une balise <table> ou lorsqu’il est
correctement restitué par les technologies d’assistance par une balise pourvue d’un attribut WAI-
ARIA role="table".
Lorsqu’un tableau de données contient des en-têtes qui ne sont pas répartis uniquement sur la
première ligne et/ou la première colonne de la grille ou dont la portée n’est pas valable pour
l’ensemble de la colonne ou de la ligne, on parle de tableau de données complexe. Il est alors
nécessaire de fournir un « résumé » permettant d’en expliquer sa nature et sa structure afin d’en
faciliter la consultation pour des utilisateurs de technologies d’assistance par exemple.

---

## Tableau de mise en forme

Technique qui utilise un élément HTML (balise <table>) pour contrôler l’affichage d’informations via
des cellules (balise <td>).
Taille des caractères
Valeur attribuée aux polices de caractères présentes sur une page web.
Texte stylé
Texte dont la mise en forme est contrôlée par une feuille de styles.
Titre
Élément HTML (balise h) à 6 niveaux de hiérarchie (de h1 pour le titre le plus important à h6 pour le
moins important) ou élément HTML ayant les attributs WAI-ARIA role="heading" et aria-level
permettant de structurer l’information d’un contenu web.
Assurer une stricte hiérarchie entre les titres d’une page web est une bonne pratique, mais la
présence de sauts hiérarchiques n’invalide pas le critère tant que cette hiérarchie plus lâche reste
cohérente (un titre <h3> peut ainsi venir directement après un titre <h1>, par exemple). La hiérarchie
de titres ne doit pas obligatoirement contenir un titre <h1>. Même si ces pratiques ne sont pas
encouragées, elles n’invalident pas le critère

---

## Technologie d'assistance

Logiciel ou matériel permettant aux personnes handicapées d'accéder aux contenus numériques.

**Base de référence RGAA (desktop) :**
- NVDA + Firefox (Windows, gratuit)
- JAWS + Firefox ou IE (Windows, payant)
- VoiceOver + Safari (macOS, natif)

**Base de référence mobile :**
- TalkBack + Chrome (Android)
- VoiceOver + Safari (iOS)

**Autres AT :** Dragon (reconnaissance vocale), plages braille, ZoomText.

La base de référence définit les combinaisons AT/navigateur utilisées pour valider la conformité.

---

## Texte caché

Texte présent dans le HTML mais non affiché visuellement. Peut être restitué ou non par les AT selon la technique utilisée.

**Masquage accessible (restitué par AT) :**
```css
.sr-only { position: absolute; width: 1px; height: 1px;
  margin: -1px; overflow: hidden; clip: rect(0,0,0,0); }
```

**Masquage excluant les AT :**
- `display: none` → non restitué
- `visibility: hidden` → non restitué
- `aria-hidden="true"` → non restitué

**Critères associés :** 10.13 (textes cachés utiles aux AT), 10.14 (correctement restitués)

---

## Texte de remplacement

Contenu textuel ou structuré se substituant à un contenu non accessible, fournissant la même information autrement. Distinct de l'alternative textuelle d'une image.

Formes possibles : texte adjacent visible, lien vers une page alternative, mécanisme permettant d'obtenir le contenu en texte.

**Usage typique :** Remplacement d'un tableau complexe par une description textuelle équivalente, ou d'un PDF inaccessible par une version HTML.

---

## Texte stylé

Texte dont la mise en forme est contrôlée par une feuille de styles.

---

## Titre

Élément HTML (balise h) à 6 niveaux de hiérarchie (de h1 pour le titre le plus important à h6 pour le
moins important) ou élément HTML ayant les attributs WAI-ARIA role="heading" et aria-level
permettant de structurer l’information d’un contenu web.
Assurer une stricte hiérarchie entre les titres d’une page web est une bonne pratique, mais la
présence de sauts hiérarchiques n’invalide pas le critère tant que cette hiérarchie plus lâche reste
cohérente (un titre <h3> peut ainsi venir directement après un titre <h1>, par exemple). La hiérarchie
de titres ne doit pas obligatoirement contenir un titre <h1>. Même si ces pratiques ne sont pas
encouragées, elles n’invalident pas le critère.
Note : les titres visuellement cachés via CSS sont considérés comme présents et valident le critère 9.1.
Titre de cadre
Contenu de l’attribut title de la balise <iframe> ou <frame> permettant de connaître la nature du
contenu diffusé via le cadre lorsque l’utilisateur navigue de cadre en cadre ou affiche l

---

## Transcription textuelle (média temporel)

Contenu textuel associé à un média temporel par la technique appropriée (texte codé en HTML ou
dans un fichier texte qui se trouve dans la même page ou consultable suivant un lien). Ce contenu
donne accès à l’utilisateur (de manière indépendante de la consultation de l’objet multimédia) à :
- La totalité de ce qui y est exprimé oralement ;
- Toutes les informations descriptives nécessaires à une compréhension équivalente de l’action.
Ces informations textuelles doivent être présentées dans l’ordre chronologique de leur apparition
dans le média temporel.
Note : la transcription textuelle doit se situer à l’extérieur de la balise <object>.

---

## Type de document

Ensemble de données de référence qui permet aux agents utilisateurs de connaître les
caractéristiques techniques des langages utilisés sur la page web (balise doctype).
Type et format de données
Indication concernant le type et le format des données attendus lors de la saisie d’un champ de
formulaire. Par exemple :
- Date (jj/mm/aaaa) ;
- Montant en euros ;
- Code postal (5 chiffres : ex. 75001).
Note importante : lorsque le type de champ de formulaire propose un masque de saisie, par exemple
les champs date ou time, l’indication de format n’est pas nécessaire.
2.3.16U
Uniquement à des fins de présentation
Uniquement à des fins de présentation : utilisation de balises HTML pour une finalité différente de
celle prévue dans les spécifications (au regard du type de document déclaré). Exemples : utilisation
des balises h à seule fin de créer un effet typographique ; utilisation de la balise <blockquote> à seule
fin de mettre un paragraphe en retrait, etc.
Note 1 : l’utilisation d’éléments

---

## Zone cliquable

(balise <area>) possédant un attribut href ;
- Image objet (balise <object>) ;
- Image bitmap (balise <canvas>) ;
- Image vectorielle (balise <svg>).
Note importante : il est rappelé que l’utilisation de deux liens adjacents (lien image et lien texte) et
identiques constitue une gêne importante pour l’utilisateur. Même si cela ne constitue pas une non-
conformité, cet usage devrait être évité. Une manière de traiter ce type de liens est d’inclure l’image
dans le lien texte de façon à constituer un lien composite, ce qui évitera la redondance.
Vous pouvez consulter à ce sujet la technique H2 : Combining adjacent image and text links for the
same resource.
Lien dont la nature n’est pas évidente
Lien qui peut être confondu avec un texte normal lorsqu’il est signalé uniquement par la couleur par
certains types d’utilisateurs ne percevant pas ou mal les couleurs. Par exemple, dans ce texte
“Nouvelle grève à la SNCF”, si le mot “grève” est un lien signalé uniquement par la couleur, sa nature

---

## Zone d'en-tête

Zone en haut du document contenant généralement le titre du site, le logo, la navigation principale et les liens d'accès rapide. Répétée sur toutes les pages.

**Implémentation correcte (critère 9.2) :**
```html
<header role="banner">
  <!-- Logo, titre, navigation principale -->
</header>
```

Un seul `role="banner"` par page. Le `<header>` de sections internes ne doit pas avoir `role="banner"`.

---

## Zone de contenu principal

Zone contenant les principaux contenus de la page, là où se trouvent les informations et
fonctionnalités de fond (donc en dehors des menus, de la recherche ou des zones secondaires de
publicités, actualités connexes…).
Note : Cette zone est unique dans la page. Elle peut être difficile à déterminer sur certaines pages
particulières, comme la page d’accueil.
Voir la définition technique fournie par WAI-ARIA : Main (role).
Zone d’en-tête
Zone située en haut du document et contenant généralement le titre du document, un logo, un
slogan…
Note : Attention à ne pas confondre cette zone d’en-tête, unique dans le site, avec tout contenu
pouvant être balisé en HTML5 avec l’élément <header>.
Voir la définition technique fournie par WAI-ARIA : Banner (role).
Zone de pied de page
Il s’agit des informations concernant le fonctionnement du site ou les informations légales. On y
trouve par exemple les mentions légales, les crédits, les conditions d’utilisation, le plan du site et
éventuellement la pa

---

## Zone de formulaire de recherche

Zone dédiée au moteur de recherche. Correspond au landmark `search`.

```html
<form role="search" aria-label="Recherche sur le site">
  <label for="q">Rechercher</label>
  <input type="search" id="q" name="q">
  <button type="submit">Lancer</button>
</form>
```

Permet aux lecteurs d'écran de naviguer directement vers la recherche.

**Critères associés :** 12.5 (moteur de recherche disponible), 12.6 (zones identifiées)

---

## Zone de navigation principale

Zone contenant les liens de navigation principale. Correspond au landmark `navigation`.

```html
<nav aria-label="Navigation principale">
  <ul>
    <li><a href="/" aria-current="page">Accueil</a></li>
    <li><a href="/produits">Produits</a></li>
  </ul>
</nav>
```

Si plusieurs `<nav>` sur la page, chacun doit avoir un `aria-label` distinct.

**Critères associés :** 9.2 (landmarks), 12.2 (navigation cohérente), 12.6 (zones identifiées)

---

## Zone de pied de page

Il s’agit des informations concernant le fonctionnement du site ou les informations légales. On y
trouve par exemple les mentions légales, les crédits, les conditions d’utilisation, le plan du site et
éventuellement la page accessibilité.
Note : Attention à ne pas confondre cette zone de pied de page, unique dans le site, avec tout
contenu pouvant être balisé en HTML5 avec l’élément <footer>.
Voir la définition technique fournie par WAI-ARIA : Contentinfo (role).
Zone (d’une image réactive)
Zone cliquable ou zone non cliquable d’une image réactive côté client ou zone cliquable d’une image
réactive côté serveur.
Zone non cliquable
Région d’une image réactive à laquelle aucune action n’est associée. Une zone non cliquable côté
client est contenue dans une balise <area> :
- Avec l’attribut nohref lorsque le code HTML de la page n’est pas du HTML5 ;
- Sans attribut href en HTML5.
Les balises <area> sont contenus dans la balise <map>.
nvironnement de test (ou « base de référence ») pour la

---

