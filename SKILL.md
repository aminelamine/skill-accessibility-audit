---
name: accessibility-audit
description: >
  Skill spécialisée en accessibilité numérique et audit RGAA 4.1.2 pour interfaces web.
  Utilise cette skill dès que l'utilisateur mentionne : accessibilité, RGAA, WCAG, audit, conformité,
  déclaration d'accessibilité, lecteur d'écran, contraste, alternative textuelle, WAI-ARIA, focus,
  navigation clavier, composant accessible, ou demande de vérifier / auditer / checker une interface,
  un composant, du code HTML/CSS/JS sous l'angle de l'accessibilité.
  Également déclenchée pour : "est-ce que ce bouton est accessible ?", "comment rendre ce formulaire
  accessible ?", "checklist accessibilité", "critère 4.1", "taux de conformité", "déclaration légale".
  Fonctionne en 5 modes : Audit, Review, Guide, Checklist, Déclaration.
---

# Accessibility Audit — RGAA 4.1.2

Skill spécialisée pour l'audit, la vérification et la conception d'interfaces web accessibles,
basée sur le RGAA 4.1.2 (106 critères, 13 thématiques).

---

## Choix du mode

Détermine le mode selon le contexte et la demande :

| Mode | Quand l'utiliser | Output principal |
|---|---|---|
| **Audit** | Audit complet d'une page ou d'un ensemble de pages | Grille critères, taux de conformité |
| **Review** | Vérification ciblée d'un composant ou d'un bout de code | Liste de problèmes priorisés + corrections |
| **Guide** | Question sur un critère, une technique, un pattern | Explication + exemple de code correct/incorrect |
| **Checklist** | Besoin d'une liste de vérification pour un type de composant | Checklist thématique par profil |
| **Déclaration** | Rédaction ou vérification d'une déclaration d'accessibilité | Document structuré selon les obligations légales |

---

## MODE : AUDIT

### Processus

1. **Identifier le périmètre** : type de page, fonctionnalités clés, contexte d'usage
2. **Lire** `references/rgaa-criteres.md` pour les 13 thématiques et leurs critères
3. **Lire** `references/audit-methodology.md` pour le processus d'audit et le calcul de conformité
4. **Évaluer** chaque critère applicable avec le statut : **C** (Conforme) / **NC** (Non conforme) / **NA** (Non applicable)
5. **Calculer** le taux de conformité : `(C / (C + NC)) × 100` — les NA sont exclus
6. **Produire** la grille + synthèse + recommandations priorisées

### Format de sortie — Grille d'audit

```markdown
## Audit RGAA 4.1.2 — [Nom de la page/composant]
**Date :** [date]  
**Auditeur :** [profil]  
**Périmètre :** [description]

### Taux de conformité : XX %
Critères conformes : X | Non conformes : X | Non applicables : X

---

### Thématique 1 — Images
| Critère | Intitulé | Statut | Observations |
|---------|----------|--------|--------------|
| 1.1 | Alternative textuelle sur images porteuses d'info | NC | `<img>` sans alt détecté ligne 42 |
| 1.2 | Images décoratives sans alternative | C | — |

### Thématique 3 — Couleurs
| Critère | Intitulé | Statut | Observations |
|---------|----------|--------|--------------|
| 3.2 | Contraste texte normal (4.5:1) | NC | #757575 sur #FFF → ratio 4.48:1 |

---

### Problèmes critiques (à corriger en priorité)
1. [NC critique] ...
2. [NC critique] ...

### Recommandations
- ...
```

### Niveaux de sévérité
- 🔴 **Bloquant** : empêche l'accès à une fonctionnalité (ex. formulaire non navigable au clavier)
- 🟠 **Majeur** : dégrade fortement l'expérience (ex. contraste insuffisant sur texte courant)
- 🟡 **Mineur** : gène sans bloquer (ex. title redondant avec le contenu visible)

---

## MODE : REVIEW

### Processus

1. **Analyser** le code ou la description du composant fourni
2. **Lire** `references/design-patterns.md` pour les patterns WAI-ARIA et anti-patterns fréquents
3. **Identifier** les non-conformités critère par critère
4. **Produire** une liste de problèmes avec : critère RGAA, sévérité, code incorrect, code corrigé

### Format de sortie — Review de composant

```markdown
## Review accessibilité — [Nom du composant]

### ❌ Problème 1 — [Titre court]
- **Critère RGAA :** 11.1 (Formulaires)
- **Sévérité :** 🔴 Bloquant
- **Profil impacté :** Utilisateurs de lecteurs d'écran
- **Code actuel :**
  ```html
  <input type="text" placeholder="Votre email">
  ```
- **Problème :** Pas de label associé. Le placeholder ne remplace pas un label.
- **Correction :**
  ```html
  <label for="email">Adresse e-mail</label>
  <input type="text" id="email" name="email" autocomplete="email">
  ```
- **Référence :** [RGAA 11.1](https://accessibilite.numerique.gouv.fr/methode/criteres-et-tests/#11.1)

---

### ✅ Points conformes
- Focus visible sur les boutons (critère 10.7)
- Ordre de lecture cohérent (critère 9.1)
```

---

## MODE : GUIDE

### Processus

1. **Identifier** le critère ou le concept demandé
2. **Lire** `references/rgaa-criteres.md` si besoin de la définition exacte du critère
3. **Lire** `references/rgaa-glossaire.md` pour la définition officielle d'un terme (63 entrées, source PDF officiel)
4. **Lire** `references/design-patterns.md` pour les patterns d'implémentation
4. **Adapter** le niveau d'explication au profil de l'interlocuteur :
   - **Designer** → focus sur les décisions de conception, les contraintes visuelles, les patterns UX
   - **Développeur** → focus sur l'implémentation HTML/ARIA, les tests techniques
   - **PM / Chef de projet** → focus sur les obligations légales, les risques, les priorisations
   - **Débutant** → vulgarisation, analogies, pas de jargon technique sans explication

### Format de sortie

```markdown
## [Critère X.X] — [Intitulé]

**En une phrase :** [Explication simple]

**Pourquoi ça compte :** [Impact utilisateur concret — quel profil de handicap est affecté]

**Ce qui est exigé :**
[Description précise de la règle RGAA]

**Exemple incorrect :**
```html
<!-- code -->
```
❌ Pourquoi c'est non conforme : ...

**Exemple correct :**
```html
<!-- code -->
```
✅ Pourquoi ça fonctionne : ...

**Cas limites & edge cases :**
- ...

**Outils pour tester :**
- [outil + méthode]
```

---

## MODE : CHECKLIST

### Processus

1. **Identifier** le composant ou la thématique (formulaire, modal, tableau, navigation, multimédia…)
2. **Sélectionner** les critères RGAA applicables depuis `references/rgaa-criteres.md`
3. **Adapter** le niveau de détail au profil demandeur
4. **Produire** la checklist en Markdown (copiable dans Notion) ET en format tabulaire (copiable dans Sheets)

### Composants couverts par défaut
Formulaires, modales/dialogs, tableaux de données, menus de navigation, carrousels,
accordéons, onglets, tooltips, notifications/alertes, lecteurs vidéo, PDF intégrés.

### Format de sortie — Markdown (Notion)

```markdown
## ☑️ Checklist accessibilité — [Composant] (RGAA 4.1.2)

### Structure & Sémantique
- [ ] Critère 8.2 — Le code source est valide (pas d'attributs dupliqués, balises correctement imbriquées)
- [ ] Critère 9.1 — L'information est structurée avec les balises sémantiques appropriées

### Navigation clavier
- [ ] Critère 12.8 — Chaque page a un ordre de tabulation cohérent
- [ ] Critère 10.7 — Le focus est visible sur tous les éléments interactifs

### [Suite selon le composant]
```

### Format de sortie — Tabulaire (Sheets)

```
Critère | Thématique | Description | Statut | Observations | Priorité
11.1 | Formulaires | Chaque champ a un label explicite | ☐ | | Haute
11.2 | Formulaires | Les champs obligatoires sont indiqués | ☐ | | Haute
```

---

## MODE : DÉCLARATION

### Processus

1. **Lire** `references/audit-methodology.md` — section Déclaration d'accessibilité
2. **Collecter** les informations nécessaires : nom du site, date d'audit, taux de conformité, non-conformités, dérogations
3. **Produire** la déclaration structurée selon les obligations légales françaises

### Mentions obligatoires
- État de conformité (totalement / partiellement / non conforme)
- Résultats de l'audit (taux, liste des non-conformités)
- Contenus non accessibles et raisons (NC, dérogation charge disproportionnée, contenu tiers)
- Moyens de contact pour signaler un problème
- Voie de recours (Défenseur des droits)

### Format
Markdown structuré prêt à être intégré dans une page web dédiée `/accessibilite`.

---

## Rappels transversaux

**Scope RGAA 4.1.2**
- 106 critères de contrôle, 13 thématiques, ~2,5 tests par critère
- Basé sur WCAG 2.1 niveaux A et AA
- Concerne uniquement les interfaces web (HTML) — pas les apps natives
- Version 5 du RGAA prévue fin 2026 : les travaux en cours restent valides

**Base de référence pour les tests AT**
- Desktop : NVDA + Firefox, JAWS + Firefox/IE, VoiceOver + Safari
- Mobile : TalkBack + Chrome (Android), VoiceOver + Safari (iOS)

**Rappel légal**
- Obligatoire pour les organismes publics et certaines entreprises privées (CA > 250M€)
- Sanction : jusqu'à 25 000 € par service non conforme
- Schéma pluriannuel + plan d'action annuel obligatoires

---

## Références

- Critères et tests détaillés → `references/rgaa-criteres.md`
- Processus d'audit et conformité → `references/audit-methodology.md`
- Patterns WAI-ARIA et outils → `references/design-patterns.md`
- **Glossaire officiel complet (63 termes)** → `references/rgaa-glossaire.md`
- Source officielle en ligne : https://accessibilite.numerique.gouv.fr/methode/
- PDF source : RGAA-v4_1_2.pdf (fourni par l'utilisateur)
