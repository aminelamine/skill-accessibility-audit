# Changelog

## [1.0.0] — 2026-03-13

### Initial release

**Skill**
- 5 modes opérationnels : Audit, Review, Guide, Checklist, Déclaration
- Orchestrateur principal (`SKILL.md`) avec détection automatique du mode
- Adaptation au profil utilisateur : designer, développeur, PM, débutant

**Base de connaissance**
- `rgaa-criteres.md` : 13 thématiques, 106 critères, tests clés, anti-patterns, niveaux de sévérité
- `audit-methodology.md` : processus d'audit complet, calcul du taux de conformité, déclaration légale, outils recommandés
- `design-patterns.md` : patterns WAI-ARIA pour 9 composants (bouton, modale, formulaire, onglets, accordéon, carrousel, tableau, menu, notification), anti-patterns fréquents, classes CSS utilitaires, checklists par profil
- `rgaa-glossaire.md` : 63 termes officiels extraits du PDF RGAA 4.1.2 (source : DINUM), couverture 100%

**Environnements de test**
- Desktop : NVDA + Firefox, JAWS + Firefox/IE, VoiceOver + Safari
- Mobile : TalkBack + Chrome, VoiceOver + Safari

**Périmètre**
- RGAA 4.1.2 uniquement (WCAG 2.1 niveaux A et AA)
- Interfaces web HTML uniquement
