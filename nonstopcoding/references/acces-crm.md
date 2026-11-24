# Accéder au CRM NonStop

Deux modes. Utilise le MCP s'il est disponible, sinon Claude in Chrome.

## Mode A — MCP du CRM NonStop

1. Découvre les outils : `ToolSearch` avec les mots-clés `nonstop crm`, puis `calls`, `candidate`, `person`, `client`, `note`. Charge tous ceux qui servent en **un seul** appel `select:`.
2. Lis la description de chaque outil chargé avant de l'utiliser : les noms exacts et les paramètres dépendent de l'implémentation du MCP.
3. Enchaînement type :
   - identifier l'utilisateur courant (outil « me » / « current user » / profil) ;
   - lister les appels du jour **de cet utilisateur** (filtre date + utilisateur), puis revérifier le champ consultant de chaque appel ;
   - pour chaque appel, récupérer le transcript et l'identifiant de la fiche liée ;
   - lire la fiche (champs + notes + CV) ;
   - mettre à jour les champs ;
   - créer la note avec sujet.
4. Pour les champs à liste fixe (Markets, Industries, Specialisms, Coded Skills, statuts), utilise si possible l'outil qui liste les valeurs autorisées, et prends la valeur exacte renvoyée. Ne passe jamais une valeur inventée.
5. Si une écriture renvoie une erreur de validation, lis le message, corrige une fois, sinon signale-la dans le récapitulatif.

## Mode B — Claude in Chrome (navigateur du recruteur)

1. Charge le skill `chrome-browser`, puis les outils Chrome en un seul `ToolSearch` (`tabs_context_mcp`, `tabs_create_mcp`, `navigate`, `computer`, `read_page`, `find`, `form_input`, `get_page_text`).
2. Regarde les onglets ouverts (`tabs_context_mcp`). Si le CRM est déjà ouvert, récupère son URL ; ouvre un **nouvel onglet** pour travailler, sans toucher à ceux du recruteur.
3. **Consultant connecté** : repère le nom affiché dans l'en-tête, le menu profil ou l'avatar du CRM. C'est ce nom (Prénom NOM) qui sert de filtre.
4. **Liste des appels du jour** : ouvre la vue des appels / de l'activité du jour (historique d'appels, tableau de bord ou onglet Calls). Applique le filtre consultant/utilisateur s'il existe, puis lis la liste avec `get_page_text` ou `read_page` et vérifie la colonne consultant / utilisateur / « Made by » de chaque ligne. Écarte toute ligne dont le consultant n'est pas exactement le consultant connecté.
5. **Transcript** : ouvre chaque appel ; le transcript est accessible depuis l'appel ou depuis la fiche liée. Récupère-le avec `get_page_text` (fais défiler ou développe la zone si le texte est tronqué).
6. **Édition de la fiche** : ouvre la fiche, clique sur le bouton d'édition, puis remplis :
   - les listes à choix multiple (Markets, Industries, Specialisms, Coded Skills) : tape le début de la valeur dans le champ, puis **choisis l'option exacte proposée** par la liste déroulante. Si aucune option ne correspond, n'ajoute rien ;
   - les listes simples (Candidate status, Employment, Seniority…) avec `form_input` ;
   - enregistre, puis vérifie avec `read_page` que les valeurs sont bien sauvegardées.
7. **Note** : ajoute la note depuis la fiche (bouton d'ajout de note), remplis le sujet et le corps, enregistre.
8. Si une page de connexion apparaît, arrête et demande au recruteur de se reconnecter : ne saisis jamais d'identifiant ni de mot de passe.
9. Ne clique sur aucun bouton de suppression, de fusion (*Merge*) ou d'envoi de message.

## Brouillons Outlook (mails de suivi après répondeur)

**Option 1 — MCP Outlook / Microsoft 365.** Cherche avec ToolSearch (`outlook`, `mail draft`, `microsoft 365`). S'il existe un outil de création de brouillon, utilise-le (destinataire, objet, corps). N'utilise jamais un outil d'envoi.

**Option 2 — Outlook Web dans Chrome.**
1. Ouvre un nouvel onglet sur Outlook Web (`outlook.office.com/mail` pour un compte professionnel, sauf si le recruteur a déjà un onglet Outlook ouvert : reprends alors son URL).
2. Clique « Nouveau message ». Remplis **À** (l'e-mail de la fiche), **Objet**, puis le **corps**.
3. Enregistre en brouillon : menu « … » → « Enregistrer le brouillon », ou ferme/annule la fenêtre de rédaction en choisissant de **conserver** le brouillon. Outlook Web enregistre aussi automatiquement après quelques secondes.
4. Ouvre le dossier **Brouillons** et vérifie que le mail y est avec le bon destinataire.
5. Ne clique **jamais** sur « Envoyer ». Si une boîte de dialogue propose d'envoyer, ferme-la.

Si Outlook demande une connexion, arrête-toi et demande au recruteur de se connecter lui-même.

### Apprendre l'interface

À la première utilisation, l'emplacement exact des menus n'est pas connu. Prends le temps d'explorer avec `read_page` (filtre `interactive`) et `find`. Une fois le chemin trouvé (où sont les appels du jour, où est le transcript, où est le bouton d'édition), garde-le en mémoire pour le reste de la session. Si l'outil de mémoire persistante est disponible, propose au recruteur de l'enregistrer pour les prochaines fois.
