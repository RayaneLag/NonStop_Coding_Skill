---
name: nonstopcoding
description: Fait le « coding » de fin de journée dans le CRM NonStop Consulting pour un recruteur. Passe en revue uniquement les appels du jour du consultant connecté, lit chaque transcript, comprend le contexte, puis recode la fiche candidat, contact client ou client (Markets, Industries, Specialisms, Coded Skills, Seniority, Candidate status, Employment, etc.) selon le guide de coding NonStop et laisse une note structurée de l'appel ; pour un répondeur, laisse la note « Message vocal envoyé » et prépare un mail de suivi dans les brouillons Outlook. Utilise ce skill dès que l'utilisateur parle de coding CRM, de « coder mes appels », de mettre à jour ses fiches après ses calls, de sa fin de journée sur le CRM NonStop, de notes d'appel à saisir, ou de fiches « Person coding needed », même s'il ne cite pas le nom du skill.
---

# NonstopCoding — coding de fin de journée du CRM NonStop

Le recruteur passe sa journée au téléphone. Le soir, chaque appel doit se traduire dans le CRM par :
1. une fiche **correctement codée** (pour qu'un collègue la retrouve par filtre Market + Industry + Skills + localisation sans lire le CV) ;
2. une **note structurée** qui raconte ce qui s'est dit.

Ton rôle : faire ce travail à sa place, **en autonomie**, de façon fiable, **uniquement sur ses propres appels**, puis lui rendre un récapitulatif clair.

Avant de coder quoi que ce soit, lis [references/guide-coding.md](references/guide-coding.md) : c'est la règle du jeu (définition des champs, valeurs autorisées, modèles par profil, erreurs fréquentes). Le modèle de note est dans [references/modele-note.md](references/modele-note.md).

## Étape 0 — Choisir le mode d'accès au CRM

Deux modes existent ; détermine lequel est disponible au début de la session.

1. **MCP du CRM NonStop (prioritaire s'il existe).** Cherche avec ToolSearch des outils dont le nom ou la description évoque le CRM NonStop (mots-clés : `nonstop`, `crm`, `candidate`, `calls`). S'ils existent, utilise-les : c'est plus rapide et plus fiable que le navigateur.
2. **Claude in Chrome (sinon).** Le recruteur est déjà connecté au CRM dans son Chrome. Charge le skill `chrome-browser` puis les outils `mcp__claude-in-chrome__*`. Travaille dans un nouvel onglet, ne ferme pas ses onglets.

Le détail de chaque mode (où trouver les appels, comment éditer une fiche) est dans [references/acces-crm.md](references/acces-crm.md).

Si aucun des deux n'est disponible, dis-le en une phrase et propose au recruteur de coller les transcripts dans la conversation : tu produiras alors le coding et les notes prêts à saisir.

## Étape 1 — Identifier le consultant et lister SES appels du jour

**Règle absolue : tu ne traites que les appels passés par le consultant connecté au CRM.** Le CRM affiche aussi les appels des autres consultants. Ceux-là, tu ne les lis pas, tu ne les codes pas et tu n'y laisses aucune note, même si la fiche concernée est la même. Coder les appels d'un collègue écraserait son travail et ses notes.

1. **Identifie le consultant connecté** avant tout : nom et prénom du compte ouvert dans le CRM (menu profil, avatar, en-tête de page, ou outil « utilisateur courant » du MCP). Exemple : si le compte connecté est « Prénom NOM », seuls les appels dont le consultant / l'auteur / le propriétaire de l'appel est « Prénom NOM » sont à traiter.
2. Annonce-le en une ligne : « Consultant connecté : Prénom NOM ». Si tu ne parviens pas à l'identifier avec certitude, **arrête-toi et demande** au recruteur son nom tel qu'il apparaît dans le CRM : mieux vaut une question qu'un coding sur les appels d'un autre.
3. Récupère les appels **de ce consultant** pour **la date du jour** (ou la date indiquée). Utilise le filtre consultant / utilisateur du CRM s'il existe, **et** vérifie quand même, appel par appel, que le nom du consultant correspond exactement. Un appel dont le consultant est différent ou inconnu est exclu et listé dans le récapitulatif (« appels ignorés »).
4. Construis une liste de travail : heure, nom du contact, type de fiche (candidat / contact client / client), durée, transcript disponible ou non.
5. Annonce en une ligne combien d'appels tu vas traiter, puis enchaîne sans attendre.

Regroupe les appels multiples vers la même personne : une seule mise à jour de fiche, qui tient compte de tous les échanges, et une note par appel significatif.

## Étape 2 — Pour chaque appel : comprendre

1. **Lis le transcript en entier.** Ne te contente pas du début : la motivation, le salaire ou la dispo arrivent souvent en fin d'appel.
2. **Ouvre la fiche liée** et lis son coding actuel, ses notes précédentes et son CV/LinkedIn s'il est attaché. Le transcript ne dit pas tout : le CV complète les Industries traversées et les Skills.
3. **Classe l'appel :**
   - *Échange réel avec un candidat* → coding candidat complet.
   - *Échange avec un contact chez un client/prospect* → coding contact client (+ mise à jour de la fiche client si l'appel apporte du nouveau : besoins, BD status, Client status).
   - *Répondeur / messagerie vocale* (transcript qui ne contient qu'une annonce de messagerie et/ou le message du consultant, ou pas de transcript sur un appel court sans interlocuteur) → pas de recoding, statut inchangé (laisse `Needs Call` s'il y était). Note **« Message vocal envoyé »** puis **brouillon de mail de suivi** dans Outlook : voir l'étape 5 bis.
   - *Mauvais numéro / personne hors cible* → note, et `Not Relevant / Dead` seulement si c'est clairement définitif.

## Étape 3 — Décider du coding

Applique le guide. Les points qui font la différence :

- **Markets = le métier, Industries = le secteur.** « Pharmaceutical » n'est jamais un Market ; « Pharmacy » est réservé aux pharmaciens. Pour un client, Markets = les métiers qu'il **recrute**.
- **Plusieurs valeurs** dès qu'elles sont réellement pertinentes (tous les secteurs traversés dans Industries).
- **Coded Skills : 3 à 8, concrets, pris dans la liste du CRM.** N'invente jamais un code. Si le skill que tu voudrais n'existe pas dans la liste, prends le plus proche ou n'en mets pas.
- **Candidate status cohérent avec l'appel** (table dans le guide). Un contact client est toujours `Do not headhunt`.
- **Employment** : passe de `TBD` à `Live` ou `Left` dès que l'appel a confirmé la situation.
- **Seniority** déduite de l'expérience réelle (années, management), pas du titre seul.
- Remplis aussi les champs « à mettre » quand l'appel les donne : Target location, Contract type, Languages, Source, Specialisms.

**Principe de prudence :** tu complètes et tu corriges ce que l'appel ou le CV établit clairement. Tu n'écrases pas une donnée existante plausible par une supposition. En cas de doute réel, laisse le champ tel quel et signale-le dans le récapitulatif : une fiche incomplète se corrige en 10 secondes, une fiche faussement codée pollue les recherches de toute l'équipe.

## Étape 4 — Appliquer dans le CRM

Le recruteur t'a autorisé à enregistrer **directement**, sans validation fiche par fiche. Enregistre chaque fiche dès qu'elle est prête, puis passe à la suivante.

Ce que tu ne fais **pas**, même en autonomie, parce que c'est irréversible ou que ça touche d'autres personnes — tu le signales dans le récapitulatif à la place :
- supprimer une fiche, une note ou un document ;
- fusionner des doublons (`Merge`) ;
- envoyer un e-mail, un SMS ou un message (les mails de suivi restent en **brouillon** dans Outlook) ;
- lire, coder ou annoter un appel passé par un autre consultant ;
- réattribuer une fiche qui appartient à un collègue (une fiche sans propriétaire ou créée par le recruteur peut être mise à son nom) ;
- passer `GDPR` à `Consent given` sans accord explicite dans le transcript ;
- modifier `Headhunt` ou les conditions commerciales d'un client.

Si une sauvegarde est refusée (champ obligatoire `*` manquant, erreur), corrige si l'info est disponible ; sinon, note-le et continue avec l'appel suivant. Ne bloque jamais toute la session sur une fiche.

## Étape 5 — Laisser la note

Ajoute une **note avec sujet** sur la fiche, en suivant [references/modele-note.md](references/modele-note.md). Écris en français, factuel, au style télégraphique d'un recruteur. Ne recopie pas le transcript : synthétise. N'invente aucun chiffre ; si le salaire ou la dispo n'ont pas été abordés, écris « non abordé ».

## Étape 5 bis — Répondeur : note + brouillon de mail Outlook

Pour chaque appel tombé sur un répondeur :

1. **Note sur la fiche**, sujet `Message vocal envoyé`, corps : `Appel le <date> à <heure> – répondeur, message vocal laissé. Mail de suivi préparé.`
2. **Récupère l'e-mail** du contact sur sa fiche CRM (préférer l'adresse `personal` pour un candidat, `work` pour un contact client). S'il n'y a aucune adresse, ne cherche pas ailleurs : écris dans la note « pas d'e-mail sur la fiche » et signale-le dans le récapitulatif.
3. **Rédige le mail de suivi** selon [references/modele-mail.md](references/modele-mail.md), personnalisé avec ce que la fiche et les notes précédentes disent (poste, raison de l'appel). Signe au nom du consultant connecté.
4. **Dépose-le dans les Brouillons Outlook du consultant — sans l'envoyer.** Le consultant relit et envoie lui-même. Accès à Outlook : outil MCP Outlook / Microsoft 365 s'il existe (création de brouillon), sinon Outlook Web dans Chrome (« Nouveau message », remplir À / Objet / Corps, puis fermer la fenêtre pour qu'Outlook l'enregistre dans Brouillons, ou bouton « Enregistrer le brouillon »). Détails dans [references/acces-crm.md](references/acces-crm.md). Ne clique jamais sur « Envoyer ».
5. Vérifie que le brouillon apparaît bien dans le dossier Brouillons, avec le bon destinataire.

## Étape 6 — Récapitulatif final

Quand tous les appels sont traités, rends un récapitulatif unique :

```
## Coding du <date> — Prénom NOM — <N> appels traités

| Heure | Fiche | Type | Statut | Principales modifications |
|---|---|---|---|---|
| 09:42 | Prénom NOM | Candidat | Live Active | Markets +Quality Assurance ; Skills GMP, CAPA, LEAN ; Employment TBD→Live |
| 10:15 | Prénom NOM | Candidat | Needs Call | Répondeur – note « Message vocal envoyé » ; brouillon Outlook prêt |

### Brouillons Outlook à relire et envoyer
- Prénom NOM — adresse@… — objet du mail

### À vérifier par toi
- Appels ignorés (autre consultant ou consultant inconnu) : <nombre>
- Répondeurs sans e-mail sur la fiche : …
- Doublons possibles : …
- Employeur client avec Headhunt: No (ne pas approcher) : …
- Champs laissés vides faute d'info : …
- Sauvegardes échouées : …

### Relances à prévoir
- Prénom NOM — <prochaine étape et date évoquées pendant l'appel>
```

Les relances viennent de la rubrique « Prochaine étape » des notes : c'est ce qui sert le plus au recruteur le lendemain matin.

## Confidentialité

Les transcripts et les fiches contiennent des données personnelles de candidats. Ne les copie nulle part ailleurs que dans le CRM et dans le récapitulatif de la conversation. N'écris pas de fichier contenant ces données sur le disque, sauf si le recruteur le demande.
