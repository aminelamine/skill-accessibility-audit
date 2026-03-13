# Patterns WAI-ARIA, anti-patterns fréquents & bonnes pratiques

Référence pour le mode Review et Guide de la skill accessibility-audit.

---

## 1. Principes fondamentaux WAI-ARIA

### La règle n°1 d'ARIA
**N'utilise pas ARIA si l'élément HTML natif peut faire le travail.**

```html
<!-- ❌ ARIA inutile : utiliser l'élément natif -->
<div role="button" tabindex="0" onclick="submit()">Envoyer</div>

<!-- ✅ Élément natif : clavier, focus, sémantique inclus -->
<button type="submit">Envoyer</button>
```

### Les 5 règles d'ARIA (résumé)
1. Utiliser les éléments HTML natifs en priorité
2. Ne pas modifier la sémantique native d'un élément (sauf raison valable)
3. Tous les composants ARIA interactifs doivent être accessibles au clavier
4. Ne pas supprimer la sémantique d'un élément visible et focusable avec `role="presentation"` ou `aria-hidden`
5. Tous les éléments interactifs doivent avoir un nom accessible

---

## 2. Patterns de composants courants

### 2.1 Bouton (Button)

```html
<!-- ✅ Bouton standard -->
<button type="button">Ouvrir le menu</button>

<!-- ✅ Bouton avec icône seulement -->
<button type="button" aria-label="Fermer la fenêtre">
  <svg aria-hidden="true" focusable="false">...</svg>
</button>

<!-- ✅ Bouton toggle -->
<button type="button" aria-expanded="false" aria-controls="menu-id">
  Menu principal
</button>

<!-- ❌ Anti-pattern -->
<div class="btn" onclick="...">Cliquer</div>
<!-- Pas focusable au clavier, pas de sémantique -->
```

**Critères RGAA :** 7.1, 7.3, 11.9

---

### 2.2 Modale / Dialog

```html
<!-- ✅ Pattern modale conforme -->
<button type="button" aria-haspopup="dialog" aria-controls="modal-id">
  Ouvrir la modale
</button>

<div role="dialog" 
     id="modal-id" 
     aria-labelledby="modal-title" 
     aria-describedby="modal-desc"
     aria-modal="true">
  <h2 id="modal-title">Titre de la modale</h2>
  <p id="modal-desc">Description du contenu ou de l'action.</p>
  
  <!-- Contenu -->
  
  <button type="button" aria-label="Fermer la modale">✕</button>
</div>
```

**Comportement clavier obligatoire :**
- `Tab` / `Shift+Tab` : circulation dans la modale uniquement (focus trap)
- `Échap` : fermeture de la modale
- Au closing : retour du focus sur l'élément déclencheur
- À l'ouverture : focus placé sur le premier élément interactif ou sur `role="dialog"`

**Critères RGAA :** 7.1, 7.3, 12.9

---

### 2.3 Menu de navigation

```html
<!-- ✅ Menu principal -->
<nav aria-label="Navigation principale">
  <ul>
    <li><a href="/" aria-current="page">Accueil</a></li>
    <li><a href="/produits">Produits</a></li>
    <li>
      <!-- Sous-menu -->
      <button aria-expanded="false" aria-controls="sous-menu-services">
        Services
      </button>
      <ul id="sous-menu-services" hidden>
        <li><a href="/services/design">Design</a></li>
        <li><a href="/services/dev">Développement</a></li>
      </ul>
    </li>
  </ul>
</nav>

<!-- ✅ Lien actif -->
<a href="/page-actuelle" aria-current="page">Page actuelle</a>
```

**Critères RGAA :** 9.2, 12.1, 12.6, 12.8

---

### 2.4 Formulaire complet

```html
<form novalidate>
  <!-- Groupe de champs liés -->
  <fieldset>
    <legend>Informations de contact</legend>
    
    <!-- Champ texte avec label explicite -->
    <div class="field">
      <label for="nom">
        Nom de famille
        <span aria-hidden="true" class="required-indicator">*</span>
      </label>
      <input type="text" 
             id="nom" 
             name="nom"
             autocomplete="family-name"
             required
             aria-required="true"
             aria-describedby="nom-hint nom-error">
      <span id="nom-hint" class="hint">Tel qu'il apparaît sur votre pièce d'identité</span>
      <span id="nom-error" role="alert" class="error" hidden>
        Ce champ est obligatoire
      </span>
    </div>
    
    <!-- Email -->
    <div class="field">
      <label for="email">Adresse e-mail <span aria-hidden="true">*</span></label>
      <input type="email" 
             id="email" 
             name="email"
             autocomplete="email"
             required
             aria-required="true">
    </div>
  </fieldset>
  
  <!-- Bouton de soumission explicite -->
  <button type="submit">Envoyer le formulaire</button>
  
  <!-- Note sur les champs obligatoires -->
  <p><span aria-hidden="true">*</span> Champs obligatoires</p>
</form>
```

**Critères RGAA :** 11.1 à 11.13

---

### 2.5 Accordéon

```html
<!-- ✅ Pattern accordéon -->
<div class="accordion">
  <h3>
    <button type="button"
            aria-expanded="true"
            aria-controls="section-1-content"
            id="section-1-header">
      Section 1 — Titre
    </button>
  </h3>
  <div id="section-1-content"
       role="region"
       aria-labelledby="section-1-header">
    <p>Contenu de la section 1</p>
  </div>
  
  <h3>
    <button type="button"
            aria-expanded="false"
            aria-controls="section-2-content"
            id="section-2-header">
      Section 2 — Titre
    </button>
  </h3>
  <div id="section-2-content"
       role="region"
       aria-labelledby="section-2-header"
       hidden>
    <p>Contenu de la section 2</p>
  </div>
</div>
```

**Critères RGAA :** 7.1, 7.3

---

### 2.6 Onglets (Tabs)

```html
<!-- ✅ Pattern onglets ARIA -->
<div class="tabs">
  <div role="tablist" aria-label="Sections du produit">
    <button role="tab" 
            aria-selected="true" 
            aria-controls="panel-description"
            id="tab-description"
            tabindex="0">
      Description
    </button>
    <button role="tab" 
            aria-selected="false" 
            aria-controls="panel-specs"
            id="tab-specs"
            tabindex="-1">
      Spécifications
    </button>
  </div>
  
  <div role="tabpanel" 
       id="panel-description" 
       aria-labelledby="tab-description">
    <p>Contenu description</p>
  </div>
  
  <div role="tabpanel" 
       id="panel-specs" 
       aria-labelledby="tab-specs"
       hidden>
    <p>Contenu spécifications</p>
  </div>
</div>
```

**Comportement clavier :**
- `Tab` : entre dans la zone d'onglets, puis dans le panneau actif
- `←` / `→` : navigue entre les onglets (pas Tab)
- `Espace` / `Entrée` : active l'onglet sélectionné

**Critères RGAA :** 7.1, 7.3

---

### 2.7 Notification / Alerte

```html
<!-- ✅ Message d'erreur critique (restitué immédiatement) -->
<div role="alert">
  Erreur : votre session a expiré. Veuillez vous reconnecter.
</div>

<!-- ✅ Message de succès (restitué poliment, sans interrompre) -->
<div role="status" aria-live="polite">
  Vos modifications ont été enregistrées.
</div>

<!-- ✅ Progression (live region) -->
<div aria-live="polite" aria-atomic="true">
  Chargement en cours : 45 %
</div>
```

**Règle :** `role="alert"` ≡ `aria-live="assertive"` → interrompt le lecteur d'écran. À réserver aux erreurs critiques.

**Critères RGAA :** 7.5

---

### 2.8 Tableau de données

```html
<!-- ✅ Tableau simple -->
<table>
  <caption>Tarifs des abonnements 2024</caption>
  <thead>
    <tr>
      <th scope="col">Formule</th>
      <th scope="col">Prix mensuel</th>
      <th scope="col">Stockage</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Starter</th>
      <td>9 €</td>
      <td>10 Go</td>
    </tr>
  </tbody>
</table>

<!-- ✅ Tableau complexe (en-têtes multiples) -->
<table>
  <caption>Planning de l'équipe</caption>
  <thead>
    <tr>
      <th id="col-nom" scope="col">Nom</th>
      <th id="col-lundi" scope="col">Lundi</th>
      <th id="col-mardi" scope="col">Mardi</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th id="row-alice" scope="row">Alice</th>
      <td headers="col-lundi row-alice">Bureau</td>
      <td headers="col-mardi row-alice">Télétravail</td>
    </tr>
  </tbody>
</table>
```

**Critères RGAA :** 5.1 à 5.8

---

### 2.9 Carrousel / Slider

```html
<!-- ✅ Pattern carrousel -->
<section aria-label="Actualités" aria-roledescription="carrousel">
  <div aria-live="polite" aria-atomic="false">
    <article aria-label="Actualité 1 sur 3" aria-roledescription="diapositive">
      <!-- Contenu de la diapositive -->
    </article>
  </div>
  
  <div class="controls">
    <button type="button" aria-label="Diapositive précédente">←</button>
    <button type="button" aria-label="Diapositive suivante">→</button>
    <button type="button" aria-label="Arrêter la lecture automatique">⏸</button>
  </div>
  
  <!-- Indicateurs de position -->
  <div role="tablist" aria-label="Diapositives">
    <button role="tab" aria-selected="true" aria-label="Diapositive 1"></button>
    <button role="tab" aria-selected="false" aria-label="Diapositive 2"></button>
    <button role="tab" aria-selected="false" aria-label="Diapositive 3"></button>
  </div>
</section>
```

**Critères RGAA :** 4.10, 13.8

---

## 3. Anti-patterns fréquents et corrections

### 3.1 Images

| Anti-pattern | Correction |
|---|---|
| `<img src="logo.png">` sans `alt` | Ajouter `alt="Logo [Nom de la marque]"` ou `alt=""` si décoratif |
| `<img alt="image">` | Alternative non pertinente — décrire le contenu ou la fonction |
| `<img alt="bannière accueil">` sur image déco | `alt=""` + éventuellement `role="presentation"` |
| `<svg>` sans `role="img"` ni titre | Ajouter `role="img"` + `<title>` ou `aria-label` |
| Background CSS pour image porteuse d'info | Déplacer en `<img>` avec alt, ou ajouter du texte masqué |

### 3.2 Liens

| Anti-pattern | Correction |
|---|---|
| `<a href="#">Cliquez ici</a>` | Intitulé explicite ou `aria-label` |
| `<a href="/article">Lire la suite</a>` (×10) | Ajouter contexte via `.sr-only` ou `aria-label` |
| `<a href="javascript:void(0)">` | Utiliser `<button>` si pas de navigation |
| Liens vides `<a href="/page"></a>` | Ajouter du texte ou `aria-label` |

### 3.3 Formulaires

| Anti-pattern | Correction |
|---|---|
| `placeholder` seul sans `label` | Ajouter un `<label>` — le placeholder disparaît à la saisie |
| Labels génériques "Champ 1" | Labels descriptifs et uniques |
| `aria-placeholder` | Non standard — utiliser `placeholder` + `label` |
| Erreurs indiquées par couleur seule | Ajouter icône + texte d'erreur |
| `required` seul sans indication visuelle | Indiquer visuellement + `aria-required="true"` |

### 3.4 Focus & Clavier

| Anti-pattern | Correction |
|---|---|
| `outline: none` sur `:focus` | Créer un focus custom visible : `outline: 3px solid #005fcc` |
| `tabindex="1"`, `tabindex="2"`… | Utiliser uniquement `tabindex="0"` et `tabindex="-1"` |
| Éléments interactifs non focusables | Ajouter `tabindex="0"` + gestion clavier |
| Modales sans focus trap | Implémenter le piège de focus (Tab circulaire dans la modale) |
| Focus perdu à la fermeture d'un composant | Renvoyer le focus sur l'élément déclencheur |

### 3.5 ARIA

| Anti-pattern | Correction |
|---|---|
| `aria-hidden="true"` sur élément focusable | Ne jamais combiner les deux |
| `role="button"` sur `<div>` sans `tabindex` | Utiliser `<button>` natif |
| `aria-label` et texte visible différents | Aligner — le label doit contenir le texte visible (critère 13.12) |
| ARIA sur éléments HTML natifs qui n'en ont pas besoin | Supprimer — natif suffit |
| `aria-live` vide puis rempli vs rempli puis modifié | La live region doit être dans le DOM au chargement, vide |

---

## 4. Classes utilitaires recommandées

### Texte masqué visuellement mais lisible par AT

```css
/* ✅ Pattern .sr-only — ne pas utiliser display:none ni visibility:hidden */
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}

/* ✅ Version focusable (pour skip links) */
.sr-only-focusable:focus {
  position: static;
  width: auto;
  height: auto;
  margin: 0;
  overflow: visible;
  clip: auto;
  white-space: normal;
}
```

### Focus visible accessible

```css
/* ✅ Focus accessible et esthétique */
:focus-visible {
  outline: 3px solid #005fcc;
  outline-offset: 2px;
  border-radius: 2px;
}

/* Masquer le focus pour la souris (navigateurs modernes) */
:focus:not(:focus-visible) {
  outline: none;
}
```

---

## 5. Checklist rapide par profil

### Pour les designers
- [ ] Contrastes texte/fond ≥ 4.5:1 (normal) et ≥ 3:1 (grand)
- [ ] Information jamais véhiculée par la couleur seule
- [ ] Focus visible et esthétique défini dans le design system
- [ ] États interactifs (hover, focus, active, disabled, error) designés
- [ ] Textes alternatifs définis dans les specs (pas laissés aux devs)
- [ ] Ordre de lecture logique dans les maquettes
- [ ] Composants complexes documentés avec comportement clavier
- [ ] Labels de formulaires toujours visibles (pas uniquement placeholder)

### Pour les développeurs
- [ ] HTML sémantique natif en priorité, ARIA en renfort uniquement
- [ ] `alt` sur toutes les images (`alt=""` pour les décoratives)
- [ ] Labels associés à tous les champs (`for`/`id` ou `aria-labelledby`)
- [ ] Ordre Tab cohérent avec l'ordre visuel
- [ ] Focus visible non supprimé
- [ ] NVDA + Firefox : tester les composants interactifs
- [ ] Validation HTML (validator.w3.org)
- [ ] Pas de piège clavier

### Pour les PM / Responsables produit
- [ ] Audit RGAA planifié avec un professionnel qualifié
- [ ] Déclaration d'accessibilité publiée sur le site
- [ ] Schéma pluriannuel et plan d'action annuel rédigés
- [ ] Processus de recueil des retours utilisateurs (bouton/page dédiée)
- [ ] Accessibilité incluse dans les critères de recette
- [ ] Budget et planning intégrés dès la phase de conception
