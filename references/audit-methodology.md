# Méthodologie d'audit RGAA 4.1.2

Source : https://accessibilite.numerique.gouv.fr/ressources/methodologie-de-test/

---

## 1. Prérequis d'un audit RGAA

### Qui peut auditer ?
- Auditeur interne formé au RGAA
- Prestataire spécialisé (certification Opquast, formation RGAA officielle)
- L'auto-audit est possible mais limité — recommander un audit externe pour la conformité légale

### Ce que l'audit couvre
- Pages HTML d'un site web
- Pas les apps mobiles natives (référentiel distinct : EN 301-549 parties 5, 6, 7, 8, 11)
- Pas les progiciels ni le mobilier urbain numérique

---

## 2. Périmètre de l'audit

### Échantillon de pages (audit légal)
Un audit de conformité RGAA doit couvrir un **échantillon représentatif** :

| Type de page | Obligatoire ? |
|---|---|
| Page d'accueil | ✅ |
| Page de mentions légales | ✅ |
| Page de plan du site | ✅ |
| Page de contact | ✅ |
| Page d'aide / FAQ | ✅ si elle existe |
| Page de connexion / inscription | ✅ si elle existe |
| Au moins une page de contenu représentative | ✅ |
| Au moins une page avec formulaire | ✅ |
| Pages avec fonctionnalités spécifiques (carte, tableau, vidéo…) | ✅ si elles existent |

**Règle :** minimum 5 pages, idéalement 15 pour un audit complet. L'échantillon est défini en concertation avec le responsable du site.

---

## 3. Processus d'audit pas à pas

### Étape 1 — Préparation
- Définir l'échantillon de pages avec le client
- Configurer l'environnement de test (voir section 5)
- Préparer la grille d'audit (tableur ou outil dédié)
- Identifier les fonctionnalités critiques (tunnel d'achat, formulaire de contact, recherche…)

### Étape 2 — Test automatique (premier balayage)
Utiliser des outils automatiques pour identifier rapidement les problèmes évidents.
**Attention : les outils automatiques ne couvrent que ~30% des critères RGAA.**

Outils recommandés :
- **WAVE** (wave.webaim.org ou extension) → analyse visuelle des erreurs
- **axe DevTools** (extension Chrome/Firefox) → résultats structurés par critère WCAG
- **Lighthouse** (Chrome DevTools > Accessibility) → score rapide
- **Validateur W3C** (validator.w3.org/nu/) → validité du code HTML
- **WCAG Contrast Checker** (extension Firefox) → contrastes automatiques

### Étape 3 — Test manuel (critique)
Incontournable. Tester :

**Navigation clavier seule :**
- Tab / Shift+Tab : navigation entre éléments interactifs
- Entrée / Espace : activation des boutons, liens, cases à cocher
- Flèches : navigation dans les menus, selects, widgets complexes
- Échap : fermeture des modales, menus

**Inspection du code :**
- Vérifier les attributs ARIA (présence, valeurs, cohérence)
- Vérifier la hiérarchie des titres (HeadingsMap)
- Vérifier les labels de formulaires (for/id, aria-labelledby)
- Vérifier les alternatives textuelles des images

**Test avec lecteur d'écran (critères JavaScript / ARIA) :**
Se référer à l'environnement de test défini (section 5).

### Étape 4 — Notation des critères

Pour chaque critère applicable :
- **C (Conforme)** : tous les tests du critère sont validés sur toutes les pages de l'échantillon
- **NC (Non conforme)** : au moins un test du critère échoue sur au moins une page
- **NA (Non applicable)** : le critère ne peut pas s'appliquer à ce site/page (ex. critère vidéo si pas de vidéo)

**Règle de sévérité :**
Un critère est NC si une seule instance de non-conformité est détectée sur l'ensemble de l'échantillon.

### Étape 5 — Calcul du taux de conformité

```
Taux de conformité = (Nombre de critères C / (Nombre de critères C + Nombre de critères NC)) × 100
```

Les critères NA sont exclus du calcul.

**Seuils de conformité légale :**
- **< 50%** → Non conforme (à mentionner dans la déclaration)
- **50–99%** → Partiellement conforme
- **100%** → Totalement conforme

**Exemple :**
- 60 critères C, 20 NC, 26 NA
- Taux = 60 / (60 + 20) × 100 = **75%** → Partiellement conforme

### Étape 6 — Rapport d'audit

Le rapport doit contenir :
1. Contexte de l'audit (périmètre, échantillon, date, auditeur)
2. Environnement de test utilisé
3. Taux de conformité global + par thématique
4. Grille détaillée (critère, statut, observations, pages concernées)
5. Synthèse des non-conformités (priorisées par impact)
6. Recommandations de correction

---

## 4. Déclaration d'accessibilité

### ⚠️ Prérequis — Ce qu'une déclaration n'est PAS

Une déclaration d'accessibilité **ne peut pas être rédigée** à partir de :
- L'audit d'une page unique
- L'audit d'un composant isolé (bouton, formulaire, modale…)
- Un taux de conformité estimé sans audit formalisé
- Une évaluation automatique seule (WAVE, Lighthouse, axe…)

Elle est le **document de synthèse final** d'un audit complet, mené sur un échantillon
représentatif de pages selon la méthodologie RGAA. Publier une déclaration sans cette base
expose l'organisme à un risque juridique et constitue une fausse information pour les utilisateurs.

**Prérequis obligatoires avant rédaction :**

| Élément | Requis ? |
|---|---|
| Audit réalisé sur un échantillon de pages (min. 5) | ✅ |
| Liste des URL auditées | ✅ |
| Taux de conformité calculé selon la formule RGAA (`C / (C + NC) × 100`) | ✅ |
| Liste des critères NC avec description et pages concernées | ✅ |
| Date et auteur/organisme de l'audit | ✅ |
| AT et navigateurs utilisés pour les tests | ✅ |
| Dérogations éventuelles justifiées | Si applicable |

### Obligations légales
Obligatoire pour :
- Les organismes publics (État, collectivités, EPA…)
- Les entreprises privées dont le CA dépasse 250 millions d'euros (loi ELAN)

### Structure de la déclaration

```markdown
# Déclaration d'accessibilité

[Nom de l'organisation] s'engage à rendre [nom du service numérique] accessible,
conformément à l'article 47 de la loi n° 2005-102 du 11 février 2005.

## État de conformité

[Nom du service] est [totalement / partiellement / non] conforme avec le référentiel général
d'amélioration de l'accessibilité (RGAA) version 4.1, en raison des [non-conformités /
dérogations] énumérées ci-dessous.

## Résultats des tests

L'audit de conformité réalisé le [date] par [organisme auditeur] révèle que :
- XX % des critères du RGAA sont respectés.

## Contenus non accessibles

### Non-conformités
[Liste des critères NC avec description]

### Dérogations pour charge disproportionnée
[Si applicable : description + justification de la charge]

### Contenus non soumis à l'obligation d'accessibilité
[Si applicable : ex. contenus tiers, archives antérieures à 2012…]

## Établissement de cette déclaration

Cette déclaration a été établie le [date].

### Technologies utilisées pour la réalisation du site
- HTML5
- CSS3
- JavaScript
- [Autres frameworks/CMS]

### Agents utilisateurs, technologies d'assistance et outils utilisés pour vérifier l'accessibilité
[Liste des combinaisons AT/navigateur utilisées]

### Pages du site ayant fait l'objet de la vérification de conformité
[Liste des URL auditées]

## Retour d'information et contact

Si vous n'arrivez pas à accéder à un contenu ou à un service, vous pouvez contacter
le responsable de [nom du service] pour être orienté vers une alternative accessible ou
obtenir le contenu sous une autre forme.

- **E-mail :** [adresse]
- **Téléphone :** [numéro]
- **Adresse postale :** [adresse]

## Voie de recours

Cette procédure est à utiliser dans le cas suivant : vous avez signalé au responsable
du site internet un défaut d'accessibilité qui vous empêche d'accéder à un contenu ou
à un de ses services et vous n'avez pas obtenu de réponse satisfaisante.

Vous pouvez :
- Écrire un message au [Défenseur des droits](https://formulaire.defenseurdesdroits.fr/)
- Contacter le délégué du Défenseur des droits dans votre région
- Envoyer un courrier par la poste (gratuit, ne pas mettre de timbre) :
  Défenseur des droits — Libre réponse 71120 — 75342 Paris CEDEX 07
```

### Mentions complémentaires obligatoires
- Schéma pluriannuel de mise en accessibilité (3 ans) avec plan d'action annuel
- Accessible via la page `/accessibilite` du site
- Mise à jour obligatoire à chaque audit ou modification substantielle

---

## 5. Environnement de test (Base de référence)

### Desktop — Combinaison 1 (référence principale)

| Technologie d'assistance | Navigateur | OS |
|---|---|---|
| NVDA (dernière version) | Firefox | Windows |
| JAWS (version n-1) | Firefox ou IE | Windows |
| VoiceOver (dernière version) | Safari | macOS |

### Desktop — Combinaison 2 (alternative)

| Technologie d'assistance | Navigateur | OS |
|---|---|---|
| JAWS (version n-1) | Firefox | Windows |
| NVDA (dernière version) | Firefox ou IE | Windows |
| VoiceOver (dernière version) | Safari | macOS |

Un composant est **compatible accessibilité** s'il fonctionne correctement dans **au moins une** des combinaisons.

### Mobile

| Combinaison | AT | Navigateur | OS |
|---|---|---|---|
| 1 | TalkBack (dernière version) | Chrome | Android |
| 2 | VoiceOver (dernière version) | Safari | iOS |

Site grand public : tester les deux combinaisons mobile.

### Environnement maîtrisé
Si le site est destiné à un parc informatique connu (intranet, agents publics), utiliser uniquement les configurations réellement déployées dans cet environnement.

---

## 6. Outils d'audit recommandés

### Inspection générale
| Outil | Usage | Lien |
|---|---|---|
| DevTools (F12) | Inspection code, arbre d'accessibilité | Natif |
| WAVE | Analyse visuelle, erreurs WCAG | wave.webaim.org |
| axe DevTools | Analyse structurée, critères WCAG | Extension Chrome/FF |
| Lighthouse | Score rapide | Chrome DevTools |

### Contrastes
| Outil | Usage |
|---|---|
| Color Contrast Analyser | Application desktop, pipette sur n'importe quel écran |
| WCAG Contrast Checker | Extension Firefox, analyse automatique de la page |

### Structure & Navigation
| Outil | Usage |
|---|---|
| HeadingsMap | Plan des titres H1–H6 |
| Web Developer Toolbar | Désactiver CSS, visualiser structure |
| Tab key | Navigation clavier manuelle |

### Lecteurs d'écran
| Outil | Plateforme | Gratuité |
|---|---|---|
| NVDA | Windows | Gratuit |
| JAWS | Windows | Payant (licence) |
| VoiceOver | macOS / iOS | Natif |
| TalkBack | Android | Natif |
| Narrator | Windows | Natif (moins utilisé) |

### Validation
| Outil | Usage |
|---|---|
| W3C Validator | Validité HTML |
| PAC 2021 | Accessibilité PDF |

### Tests spécifiques
| Outil | Usage |
|---|---|
| PEAT | Flashes / risque épileptique |
| Ace by DAISY | Accessibilité EPUB |
