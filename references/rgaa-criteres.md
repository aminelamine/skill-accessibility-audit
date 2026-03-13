# RGAA 4.1.2 — Critères et thématiques de référence

Source officielle : https://accessibilite.numerique.gouv.fr/methode/criteres-et-tests/

## Structure : 13 thématiques, 106 critères

---

## 1. Images

**Enjeu principal :** Fournir une alternative textuelle à toute image porteuse d'information pour les utilisateurs qui ne voient pas les images (lecteurs d'écran, texte seul).

| Critère | Intitulé | Niveau | Points de vigilance |
|---------|----------|--------|---------------------|
| 1.1 | Chaque image porteuse d'information a une alternative textuelle | A | `alt`, `aria-label`, `aria-labelledby` |
| 1.2 | Chaque image de décoration est ignorée par les AT | A | `alt=""` + `role="presentation"` ou `aria-hidden="true"` |
| 1.3 | L'alternative textuelle est pertinente | A | Ne pas décrire l'apparence, décrire la fonction/information |
| 1.4 | Chaque image CAPTCHA a une alternative | A | Alternative sonore ou autre moyen obligatoire |
| 1.5 | Chaque image-lien a une alternative textuelle décrivant la destination | A | |
| 1.6 | Les images-objets complexes ont une description détaillée | A | Graphiques, schémas, infographies |
| 1.7 | La description détaillée d'une image complexe est pertinente | A | |
| 1.8 | Images textes : préférer le texte stylé CSS | AA | Sauf logo / marque |
| 1.9 | Images textes et texte ont même information | AA | |

**Tests clés — 1.1 :**
1. Repérer `<img>`, `role="img"`, `<area>`, `<input type="image">`, `<svg>`, `<object type="image/…">`, `<embed>`
2. Vérifier présence d'au moins une alternative : `alt`, `aria-label`, `aria-labelledby`, `<title>` dans SVG
3. Pour SVG : vérifier aussi `role="img"` sur la balise `<svg>`
4. Images décoratives : `alt=""` obligatoire (attribut vide, pas absent)

---

## 2. Cadres (Frames & iFrames)

| Critère | Intitulé | Niveau |
|---------|----------|--------|
| 2.1 | Chaque cadre a un titre pertinent | A |
| 2.2 | Le titre de chaque cadre est pertinent | A |

**Test :** `<iframe title="Carte Google Maps — Localisation de l'agence">` — titre descriptif obligatoire.

---

## 3. Couleurs

**Enjeu principal :** Ne pas transmettre d'information par la couleur seule. Assurer un contraste suffisant.

| Critère | Intitulé | Niveau | Ratio exigé |
|---------|----------|--------|-------------|
| 3.1 | L'information ne repose pas que sur la couleur | A | — |
| 3.2 | Contraste texte normal (< 18pt / < 14pt gras) | AA | ≥ 4.5:1 |
| 3.3 | Contraste texte grand (≥ 18pt / ≥ 14pt gras) | AA | ≥ 3:1 |

**Cas limites :**
- Logos et textes décoratifs : exemptés
- Texte dans les images : soumis aux mêmes ratios
- Composants UI (bordure de champ, icône de bouton) : ratio ≥ 3:1 (critère 1.4.11 WCAG, hors RGAA A/AA mais bonne pratique)
- Taille "grand texte" : 18pt normal ≈ 24px, 14pt gras ≈ 18.5px

**Outils :** Color Contrast Analyser (Paciello Group), WCAG Contrast Checker (Firefox extension), Figma A11y Annotation Kit.

---

## 4. Multimédia

| Critère | Intitulé | Niveau |
|---------|----------|--------|
| 4.1 | Chaque média temporel pré-enregistré a une alternative | A |
| 4.2 | Les sous-titres synchronisés sont présents (vidéo) | A |
| 4.3 | La transcription textuelle est présente (audio) | A |
| 4.4 | La transcription textuelle est présente (vidéo) | AA |
| 4.5 | Les sous-titres sont pertinents | AA |
| 4.6–4.9 | Audiodescription (vidéo) | A/AA |
| 4.10 | Contrôle de la lecture automatique | A |
| 4.11 | Contrôle des sons déclenchés automatiquement | A |
| 4.12 | Contrôle des fonctionnalités du lecteur (clavier) | A |
| 4.13 | Chaque objet Flash/Silverlight a une alternative | A |

**Point de vigilance design :** Toute vidéo avec déclenchement automatique + son doit avoir un bouton d'arrêt visible et accessible au clavier.

---

## 5. Tableaux

| Critère | Intitulé | Niveau |
|---------|----------|--------|
| 5.1 | Tableau de données complexe → résumé | A |
| 5.2 | En-têtes de lignes/colonnes identifiés (`<th>`) | A |
| 5.3 | Pas de tableau de mise en page avec balisage de données | A |
| 5.4 | `<caption>` ou `summary` pour les tableaux de données | A |
| 5.5 | Le titre/résumé est pertinent | A |
| 5.6 | En-têtes liées aux cellules (`scope`, `id/headers`) | A |
| 5.7 | Les en-têtes sont pertinentes | A |
| 5.8 | Tableaux de mise en page : linéarisation cohérente | A |

---

## 6. Liens

| Critère | Intitulé | Niveau |
|---------|----------|--------|
| 6.1 | Chaque lien a un intitulé | A |
| 6.2 | L'intitulé de chaque lien est explicite | A |

**Anti-pattern fréquent :**
```html
<!-- ❌ -->
<a href="/article">Lire la suite</a>

<!-- ✅ -->
<a href="/article">Lire la suite <span class="sr-only">de l'article "Titre de l'article"</span></a>
<!-- ou -->
<a href="/article" aria-label="Lire la suite de l'article : Titre de l'article">Lire la suite</a>
```

**Exception :** Un lien peut être ambigu s'il est accompagné d'un contexte lisible (titre de section dans le même paragraphe, cellule de tableau adjacente).

---

## 7. Scripts

| Critère | Intitulé | Niveau |
|---------|----------|--------|
| 7.1 | Chaque script est compatible avec les AT | A |
| 7.2 | Chaque contenu généré par script a une alternative | A |
| 7.3 | Chaque script est contrôlable par clavier | A |
| 7.4 | Les changements de contexte initiés par script sont prévisibles | A |
| 7.5 | Les messages de statut sont restitués par les AT | AA |

**7.5 — Patterns courants :**
- `role="status"` pour les messages non-critiques (ex : "Sauvegardé")
- `role="alert"` ou `aria-live="assertive"` pour les erreurs critiques
- `aria-live="polite"` pour les mises à jour non-urgentes

---

## 8. Éléments obligatoires

| Critère | Intitulé | Niveau |
|---------|----------|--------|
| 8.1 | La page a un doctype valide | A |
| 8.2 | Le code source est valide | A |
| 8.3 | La langue par défaut est définie (`lang`) | A |
| 8.4 | La langue est pertinente | A |
| 8.5 | Chaque page a un titre (`<title>`) | A |
| 8.6 | Le titre de la page est pertinent | A |
| 8.7 | Les changements de langue dans le contenu sont indiqués (`lang` local) | AA |
| 8.8 | Les changements de sens de lecture sont indiqués (`dir`) | A |
| 8.9 | Les balises ne sont pas utilisées à des fins de présentation | A |
| 8.10 | Les changements de contexte au focus sont prévisibles | A |

---

## 9. Structuration de l'information

| Critère | Intitulé | Niveau |
|---------|----------|--------|
| 9.1 | Structure de titres cohérente (H1–H6) | A |
| 9.2 | La structure du document est cohérente (landmarks) | A |
| 9.3 | Les listes sont correctement balisées | A |
| 9.4 | Les citations sont balisées (`<blockquote>`, `<q>`) | A |

**Landmarks obligatoires (critère 9.2) :**
`<header role="banner">`, `<nav role="navigation">`, `<main role="main">`, `<footer role="contentinfo">`, `<aside role="complementary">`, `<form role="search">` (pour la recherche globale)

**Règle des titres :** Une seule balise `<h1>` par page. Pas de saut de niveau (ex : h1 → h3 sans h2).

---

## 10. Présentation de l'information

| Critère | Intitulé | Niveau |
|---------|----------|--------|
| 10.1 | L'information n'est pas véhiculée uniquement par la mise en forme | A |
| 10.2 | Structure visible ≠ ordre DOM (si pertinent) | A |
| 10.3 | Pas de texte justifié | AA |
| 10.4 | Taille des textes redimensionnable (200%) | AA |
| 10.5 | Déclarations CSS `!important` ne bloquent pas les préférences utilisateur | A |
| 10.6 | Pas de défilement horizontal à 320px | AA |
| 10.7 | Focus visible sur tous les éléments interactifs | AA |
| 10.8 | Focus non supprimé par CSS | A |
| 10.9 | Espacement du texte modifiable sans perte de contenu | AA |
| 10.10 | Contenus au survol/focus contrôlables | AA |
| 10.11 | Pas de contenu en mouvement non contrôlable | A |
| 10.12 | Ordre de lecture cohérent | A |
| 10.13 | Textes cachés utiles aux AT | A |
| 10.14 | Les textes cachés sont correctement restitués | A |

**10.7 / 10.8 — Anti-pattern fréquent :** `outline: none` ou `outline: 0` sur `:focus` sans alternative visible.

**10.9 — Test :** Injecter via bookmarklet ou extension les propriétés CSS :
```css
* { line-height: 1.5 !important; letter-spacing: 0.12em !important; word-spacing: 0.16em !important; }
```
Le contenu ne doit pas déborder ou disparaître.

---

## 11. Formulaires

**Thématique la plus riche en non-conformités.**

| Critère | Intitulé | Niveau |
|---------|----------|--------|
| 11.1 | Chaque champ a un label | A |
| 11.2 | Chaque label est correctement relié au champ | A |
| 11.3 | Regroupement de champs similaires (`<fieldset>` + `<legend>`) | A |
| 11.4 | `<legend>` pertinente | A |
| 11.5 | Champs de même nature regroupés | A |
| 11.6 | Champs obligatoires indiqués | A |
| 11.7 | Indication des champs obligatoires pertinente | A |
| 11.8 | Les champs ont le bon type et autocomplete | AA |
| 11.9 | Intitulé du bouton de soumission explicite | A |
| 11.10 | Contrôle de saisie : erreurs identifiées | A |
| 11.11 | Suggestions de correction | AA |
| 11.12 | L'utilisateur peut vérifier et corriger avant soumission | AA |
| 11.13 | Finalité des champs personnels (`autocomplete`) | AA |

**Pattern label correct :**
```html
<!-- Méthode 1 : for/id (préférable) -->
<label for="nom">Nom de famille <span aria-hidden="true">*</span></label>
<input type="text" id="nom" name="nom" required aria-required="true" autocomplete="family-name">

<!-- Méthode 2 : aria-labelledby -->
<span id="label-nom">Nom de famille</span>
<input type="text" aria-labelledby="label-nom" autocomplete="family-name">

<!-- Méthode 3 : aria-label (dernier recours) -->
<input type="text" aria-label="Nom de famille" autocomplete="family-name">
```

**Champs obligatoires — ne pas utiliser uniquement la couleur rouge.**

---

## 12. Navigation

| Critère | Intitulé | Niveau |
|---------|----------|--------|
| 12.1 | Liens d'évitement / d'accès rapide | A |
| 12.2 | Les liens d'évitement sont fonctionnels | A |
| 12.3 | Plan du site | AA |
| 12.4 | Page de plan du site cohérente | AA |
| 12.5 | Moteur de recherche | AA |
| 12.6 | Les zones répétées sont identifiées par des landmarks ou des titres | A |
| 12.7 | Les liens d'évitement sont visibles au focus | A |
| 12.8 | L'ordre de tabulation est cohérent | A |
| 12.9 | Pas de piège clavier | A |
| 12.10 | Raccourcis clavier à une touche désactivables ou reconfigurables | A |
| 12.11 | Mécanismes d'authentification accessibles | A |

**12.1 — Skip links :** Minimum requis : lien "Aller au contenu principal" visible au focus, ciblant `<main>` ou son équivalent.

**12.9 — Piège clavier :** Toute modale, menu ou widget JavaScript doit permettre de revenir au flux principal (Échap ou logique cohérente).

---

## 13. Consultation

| Critère | Intitulé | Niveau |
|---------|----------|--------|
| 13.1 | Délai de session : avertissement et prolongation | A |
| 13.2 | Pas d'ouverture automatique de nouvelle fenêtre sans avertissement | A |
| 13.3 | Chaque document en téléchargement a son format et son poids indiqués | A |
| 13.4 | Chaque document a une version accessible ou une alternative | A |
| 13.5 | CAPTCHA : alternative non visuelle | A |
| 13.6 | Chaque contenu cryptique a une alternative | A |
| 13.7 | Les changements brusques de luminosité < 3 flashes/s | A |
| 13.8 | Contenus en mouvement contrôlables | A |
| 13.9 | Pas de défilement infini sans contrôle | A |
| 13.10 | Gestes complexes : alternative avec pointeur simple | A |
| 13.11 | Actions déclenchées au relâchement du pointeur (pas au press) | A |
| 13.12 | Étiquettes visibles correspondent aux noms accessibles | A |

---

## Résumé des thématiques par fréquence de non-conformité

| Rang | Thématique | Taux de NC typique |
|------|------------|-------------------|
| 1 | Formulaires (11) | Très élevé |
| 2 | Images (1) | Élevé |
| 3 | Couleurs (3) | Élevé |
| 4 | Navigation (12) | Élevé |
| 5 | Structuration (9) | Moyen |
| 6 | Scripts (7) | Moyen |
| 7 | Présentation (10) | Moyen |
| 8–13 | Autres | Variable |
