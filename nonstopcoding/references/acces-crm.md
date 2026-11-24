# Accéder au CRM NonStop

Deux modes. Utilise le MCP s'il est disponible, sinon Claude in Chrome.

## Mode A — MCP du CRM NonStop

1. Découvre les outils : `ToolSearch` avec les mots-clés `nonstop crm`, puis `calls`, `candidate`, `person`, `client`, `note`. Charge tous ceux qui servent en **un seul** appel `select:`.
2. Lis la description de chaque outil chargé avant de l'utiliser : les noms exacts et les paramètres dépendent de l'implémentation du MCP.
3. Enchaînement type :
   - lister les appels du jour du recruteur (filtre date + utilisateur) ;
   - pour chaque appel, récupérer le transcript et l'identifiant de la fiche liée ;
   - lire la fiche (champs + notes + CV) ;
   - mettre à jour les champs ;
   - créer la note avec sujet.
4. Pour les champs à liste fixe (Markets, Industries, Specialisms, Coded Skills, statuts), utilise si possible l'outil qui liste les valeurs autorisées, et prends la valeur exacte renvoyée. Ne passe jamais une valeur inventée.
5. Si une écriture renvoie une erreur de validation, lis le message, corrige une fois, sinon signale-la dans le récapitulatif.

## Mode B — Claude in Chrome (navigateur du recruteur)

1. Charge le skill `chrome-browser`, puis les outils Chrome en un seul `ToolSearch` (`tabs_context_mcp`, `tabs_create_mcp`, `navigate`, `computer`, `read_page`, `find`, `form_input`, `get_page_text`).
2. Regarde les onglets ouverts (`tabs_context_mcp`). Si le CRM est déjà ouvert, récupère son URL ; ouvre un **nouvel onglet** pour travailler, sans toucher à ceux du recruteur.
3. **Liste des appels du jour** : dans le CRM, ouvre la vue des appels / de l'activité du jour (historique d'appels, tableau de bord ou onglet Calls), filtrée sur le recruteur et la date. Lis-la avec `get_page_text` ou `read_page` plutôt qu'en capture d'écran.
4. **Transcript** : ouvre chaque appel ; le transcript est accessible depuis l'appel ou depuis la fiche liée. Récupère-le avec `get_page_text` (fais défiler ou développe la zone si le texte est tronqué).
5. **Édition de la fiche** : ouvre la fiche, clique sur le bouton d'édition, puis remplis :
   - les listes à choix multiple (Markets, Industries, Specialisms, Coded Skills) : tape le début de la valeur dans le champ, puis **choisis l'option exacte proposée** par la liste déroulante. Si aucune option ne correspond, n'ajoute rien ;
   - les listes simples (Candidate status, Employment, Seniority…) avec `form_input` ;
   - enregistre, puis vérifie avec `read_page` que les valeurs sont bien sauvegardées.
6. **Note** : ajoute la note depuis la fiche (bouton d'ajout de note), remplis le sujet et le corps, enregistre.
7. Si une page de connexion apparaît, arrête et demande au recruteur de se reconnecter : ne saisis jamais d'identifiant ni de mot de passe.
8. Ne clique sur aucun bouton de suppression, de fusion (*Merge*) ou d'envoi de message.

### Apprendre l'interface

À la première utilisation, l'emplacement exact des menus n'est pas connu. Prends le temps d'explorer avec `read_page` (filtre `interactive`) et `find`. Une fois le chemin trouvé (où sont les appels du jour, où est le transcript, où est le bouton d'édition), garde-le en mémoire pour le reste de la session. Si l'outil de mémoire persistante est disponible, propose au recruteur de l'enregistrer pour les prochaines fois.
