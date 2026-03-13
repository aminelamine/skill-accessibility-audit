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

5 modes opérationnels, adaptés à différents profils (designer, développeur, PM, débutant) :

| Mode | Déclencheur | Output |
|------|-------------|--------|
| **Audit** | "Audite cette page / ce composant" | Grille RGAA complète, taux de conformité C/NC/NA |
| **Review** | "Vérifie l'accessibilité de ce code" | Problèmes priorisés 🔴🟠🟡 + corrections |
| **Guide** | "Explique le critère X / comment implémenter Y" | Explication adaptée au profil + exemples |
| **Checklist** | "Checklist accessibilité pour [formulaire / modale…]" | Markdown (Notion) + tabulaire (Sheets) |
| **Déclaration** | "Aide-moi à rédiger ma déclaration d'accessibilité" | Document structuré + mentions légales |

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

La skill est construite sur les sources officielles :

- **RGAA 4.1.2** — Référentiel général d'amélioration de l'accessibilité  
  [accessibilite.numerique.gouv.fr](https://accessibilite.numerique.gouv.fr/methode/)
- **WCAG 2.1** niveaux A et AA (50 critères de succès)
- **WAI-ARIA 1.1** — Patterns de composants (APG)
- **EN 301-549 V2.1.2** — Norme européenne de référence

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

### Mode Audit
```
Audite ce composant de formulaire pour sa conformité RGAA 4.1.2 :
[coller le code HTML]
```

### Mode Review
```
Vérifie l'accessibilité de cette modale pour un profil développeur.
Donne-moi les non-conformités par ordre de sévérité avec les corrections.
[coller le code]
```

### Mode Guide
```
Explique le critère 11.1 du RGAA à un designer qui ne connaît pas le code.
```

### Mode Checklist
```
Génère une checklist RGAA pour un composant "tableau de données"
en sortie Markdown et tabulaire (Sheets).
```

### Mode Déclaration
```
Aide-moi à rédiger la déclaration d'accessibilité de notre site.
Taux de conformité : 73%. Organisme : Acme Corp.
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
