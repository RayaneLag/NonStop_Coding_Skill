# NonStop_Coding_Skill

Skill Claude **NonstopCoding** : le coding de fin de journée du CRM NonStop Consulting, fait par Claude.

Chaque soir, Claude :
1. récupère tous les appels du jour du recruteur dans le CRM ;
2. lit chaque transcript et comprend le contexte de l'appel ;
3. recode la fiche candidat, contact client ou client selon le guide de coding NonStop (Markets, Industries, Specialisms, Coded Skills, Seniority, Candidate status, Employment…) ;
4. laisse une note structurée de l'appel sur la fiche ;
5. rend un récapitulatif : fiches modifiées, points à vérifier, relances à prévoir.

## Accès au CRM

- **Claude in Chrome** : Claude travaille dans le Chrome du recruteur, déjà connecté au CRM.
- **MCP du CRM NonStop** : utilisé en priorité dès qu'il est disponible dans Claude.

## Garde-fous

Même en mode autonome, Claude ne supprime rien, ne fusionne pas de doublons, n'envoie aucun message, ne réattribue pas la fiche d'un collègue et ne touche pas au consentement RGPD sans accord explicite. Ces cas sont signalés dans le récapitulatif.

## Contenu

```
nonstopcoding/
├── SKILL.md                     # workflow principal
└── references/
    ├── guide-coding.md          # règles de coding (champs, valeurs, modèles, erreurs)
    ├── modele-note.md           # modèle de note d'appel
    └── acces-crm.md             # mode MCP et mode Chrome
```

## Installation

**Claude Code** : copier le dossier `nonstopcoding` dans `~/.claude/skills/`.

**Claude (app / claude.ai)** : zipper le dossier `nonstopcoding` et l'importer dans *Paramètres → Capacités → Skills*.

Puis, en fin de journée : « Fais le coding de mes appels du jour ».
