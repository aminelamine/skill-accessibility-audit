# Contribuer à skill-accessibility-audit

Merci de tester la skill ! Ce fichier explique comment partager un retour utile
et comment proposer une amélioration directement dans le repo.

---

## 📝 Donner un retour (feedback utilisateur)

Le moyen le plus simple : **ouvrir une Issue GitHub** avec le template ci-dessous.

👉 [Nouvelle issue →](../../issues/new)

### Template de feedback

```
**Mode utilisé**
[ ] Audit   [ ] Review   [ ] Guide   [ ] Checklist   [ ] Déclaration

**Profil**
[ ] Designer   [ ] Développeur   [ ] PM   [ ] Autre : ___

**Contexte / cas concret**
(Ex : "audit d'un formulaire de connexion", "checklist pour une modale de confirmation")

**Ce qui a bien fonctionné**

**Ce qui a manqué ou surpris**

**Suggestion d'amélioration (optionnel)**
```

> Pas besoin d'être exhaustif. Même un retour en 3 lignes est utile.

---

## 🔧 Proposer une amélioration (Pull Request)

Les contributions sont bienvenues sur :

- **`references/rgaa-criteres.md`** — correction de critères, ajout de tests ou d'anti-patterns
- **`references/design-patterns.md`** — nouveaux composants WAI-ARIA, patterns manquants
- **`references/audit-methodology.md`** — outils, processus, calculs
- **`references/rgaa-glossaire.md`** — corrections de définitions officielles
- **`SKILL.md`** — ajustement des modes, prompts, comportements

### Process

1. Fork le repo
2. Crée une branche : `fix/nom-du-correctif` ou `feat/nom-de-la-feature`
3. Modifie le fichier concerné
4. Ouvre une Pull Request avec une description courte de ce que tu changes et pourquoi

### Règles de contribution

- Les définitions du glossaire doivent rester fidèles au PDF RGAA 4.1.2 officiel (source DINUM)
- Les patterns WAI-ARIA doivent référencer l'APG (Authoring Practices Guide) quand possible
- Pas de contenu généré sans vérification sur les critères RGAA — l'exactitude prime

---

## 🗺️ Roadmap ouverte

Ces sujets sont identifiés pour les prochaines itérations :

- [ ] Mise à jour vers RGAA 5 (publication prévue fin 2026)
- [ ] Traduction des références en anglais (WCAG direct)
- [ ] Ajout de cas de test concrets par composant
- [ ] Patterns spécifiques aux SPAs (React, Vue) — gestion du focus dynamique

Tu travailles sur un de ces sujets ? Ouvre une issue pour qu'on coordinate.

---

## 📄 Licence

En contribuant, tu acceptes que tes modifications soient publiées sous les mêmes licences que le projet :
- Contenus RGAA officiels → [licence etalab-2.0](https://github.com/etalab/licence-ouverte/blob/master/LO.md)
- Reste du projet → MIT
