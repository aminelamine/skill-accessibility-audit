# 🔍 Skill — Audit Accessibilité RGAA 4.1.2

Skill Claude spécialisée en accessibilité numérique et audit RGAA 4.1.2 pour interfaces web.  
Conçue pour être utilisée dans [Claude.ai Projects](https://claude.ai) ou via l'API Anthropic.

---

## 📦 Installation

### Via Claude.ai (interface)
1. Télécharger le fichier `accessibility-audit.skill`
2. Dans Claude.ai → **Settings → Skills → Install from file**
3. La skill est active pour toutes les conversations du projet

### Via l'API
Copier le contenu de `SKILL.md` dans le `system_prompt` de votre appel API.  
Charger les fichiers `references/*.md` selon le mode utilisé.

---

## 🎯 Ce que fait cette skill

5 modes opérationnels couvrant l'ensemble du cycle de conception et de validation :

| Mode | Quand l'utiliser | Pour qui | Output |
|------|-----------------|----------|--------|
| ☑️ **Checklist** | **Avant** — en phase de conception | Designer, PO | Liste de critères RGAA à respecter pour un composant donné |
| 🔍 **Review** | **Pendant** — en cours de développement | Développeur, designer | Problèmes priorisés 🔴🟠🟡 sur un composant précis + corrections |
| 📋 **Audit** | **Après** — en validation avant mise en prod | PM, lead, auditeur | Grille RGAA complète sur un ensemble de pages, taux de conformité |
| 📖 **Guide** | À tout moment — question sur un critère ou une technique | Tous profils | Explication adaptée au profil + exemples de code correct/incorrect |
| 📄 **Déclaration** | En fin d'audit complet — document légal | PM, responsable qualité | Document structuré selon les obligations légales françaises |

> **Checklist ≠ Review ≠ Audit** — ce ne sont pas trois façons de faire la même chose.  
> La Checklist cadre la conception *en amont*, la Review corrige un composant *en cours de dev*,  
> l'Audit évalue la conformité globale *avant la mise en prod*.

---

## 💬 Types d'inputs acceptés

**Pas besoin de code pour utiliser cette skill.** Elle accepte plusieurs formats :

| Input | Exemple | Modes compatibles |
|-------|---------|------------------|
| **Code HTML** | Coller le code source d'un composant | Review, Audit |
| **Description en langage naturel** | "J'ai une modale avec un bouton fermer sans label" | Review, Checklist, Guide |
| **Screenshot** | Uploader une capture d'écran d'une interface | Review, Audit |
| **URL publique** | "Audite l'accessibilité de cette page : https://..." | Audit |
| **Nom d'un composant** | "Checklist pour un menu de navigation" | Checklist, Guide |

---

## 📁 Structure

```
skill-accessibility-audit/
├── SKILL.md                          ← Orchestrateur principal (5 modes)
├── accessibility-audit.skill         ← Package installable (.skill)
├── references/
│   ├── rgaa-criteres.md              ← 13 thématiques, 106 critères, tests clés
│   ├── audit-methodology.md          ← Processus d'audit, calcul conformité, déclaration légale
│   ├── design-patterns.md            ← Patterns WAI-ARIA, composants, anti-patterns, outils
│   └── rgaa-glossaire.md             ← Glossaire officiel complet (63 termes, source PDF RGAA 4.1.2)
└── README.md
```

---

## 📚 Base de connaissance

La skill utilise **exclusivement le RGAA 4.1.2** comme référentiel d'audit.
WCAG et WAI-ARIA sont des sources sous-jacentes — jamais des référentiels parallèles.

| Source | Rôle dans la skill |
|--------|-------------------|
| **RGAA 4.1.2** (DINUM) | Seul référentiel d'audit — tous les critères, statuts C/NC/NA, taux de conformité |
| **WCAG 2.1** (W3C) | Base internationale du RGAA — mentionné en contexte uniquement, jamais dans les outputs |
| **WAI-ARIA 1.1** (W3C) | Guide d'implémentation technique — utilisé pour guider le code, jamais dans les grilles d'audit |
| **EN 301-549 V2.1.2** | Norme européenne de référence — contexte réglementaire uniquement |

Source officielle RGAA : [accessibilite.numerique.gouv.fr](https://accessibilite.numerique.gouv.fr/methode/)

### Périmètre
- ✅ Interfaces web HTML (HTML5, CSS3, JavaScript)
- ❌ Applications mobiles natives (référentiel distinct : EN 301-549)
- ❌ Progiciels et mobilier urbain numérique

---

## 🔧 Environnements de test (base de référence RGAA)

### Desktop
| AT | Navigateur | OS |
|----|-----------|-----|
| NVDA (dernière version) | Firefox | Windows |
| JAWS (version n-1) | Firefox ou IE | Windows |
| VoiceOver (dernière version) | Safari | macOS |

### Mobile
| AT | Navigateur | OS |
|----|-----------|-----|
| TalkBack (dernière version) | Chrome | Android |
| VoiceOver (dernière version) | Safari | iOS |

---

## 📋 Exemples d'utilisation

### Mode Checklist — avant de concevoir
```
Génère une checklist RGAA pour un composant "menu de navigation"
en sortie Markdown et tabulaire (Sheets).
```

### Mode Review — pendant le dev
```
Vérifie l'accessibilité de cette modale.
Donne-moi les non-conformités par ordre de sévérité avec les corrections.
[coller le code ou décrire le composant]
```

### Mode Audit — en validation
```
Audite l'accessibilité de cette page : https://exemple.fr/contact
```

### Mode Guide — à tout moment
```
Explique le critère 11.1 du RGAA à un designer qui ne connaît pas le code.
```

### Mode Déclaration — après un audit complet
```
Aide-moi à rédiger la déclaration d'accessibilité de notre site.
Audit réalisé sur 8 pages. Taux de conformité : 73%. Organisme : Acme Corp.
[fournir la liste des critères NC et les URLs auditées]
```

---

## ⚠️ Statut RGAA 5

> La version 5 du RGAA est en cours de rédaction, avec une publication prévue **fin 2026**.  
> Les travaux de mise en accessibilité en cours restent valides et ne doivent pas être suspendus.  
> [Plus d'infos sur le RGAA 5](https://design.numerique.gouv.fr/articles/2026-03-02-rgaa5/)

---

## 🤝 Contribution

Pull requests bienvenues pour :
- Corrections de définitions ou de critères
- Ajout de patterns de composants manquants
- Mise à jour vers le RGAA 5 (dès publication)
- Traduction des références en anglais (WCAG direct)

---

## 📄 Licence

Les contenus issus du RGAA officiel sont sous [licence etalab-2.0](https://github.com/etalab/licence-ouverte/blob/master/LO.md).  
Le reste du code et des templates est sous licence MIT.
