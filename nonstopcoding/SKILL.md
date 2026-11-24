---
name: nonstopcoding
description: Fait le « coding » de fin de journée dans le CRM NonStop Consulting pour un recruteur. Passe en revue tous les appels du jour, lit chaque transcript, comprend le contexte, puis recode la fiche candidat, contact client ou client (Markets, Industries, Specialisms, Coded Skills, Seniority, Candidate status, Employment, etc.) selon le guide de coding NonStop, et laisse une note structurée de l'appel. Utilise ce skill dès que l'utilisateur parle de coding CRM, de « coder mes appels », de mettre à jour ses fiches après ses calls, de sa fin de journée sur le CRM NonStop, de notes d'appel à saisir, ou de fiches « Person coding needed », même s'il ne cite pas le nom du skill.
---

# NonstopCoding — coding de fin de journée du CRM NonStop

Le recruteur passe sa journée au téléphone. Le soir, chaque appel doit se traduire dans le CRM par :
1. une fiche **correctement codée** (pour qu'un collègue la retrouve par filtre Market + Industry + Skills + localisation sans lire le CV) ;
2. une **note structurée** qui raconte ce qui s'est dit.

Ton rôle : faire ce travail à sa place, **en autonomie**, de façon fiable, puis lui rendre un récapitulatif clair.

Avant de coder quoi que ce soit, lis [references/guide-coding.md](references/guide-coding.md) : c'est la règle du jeu (définition des champs, valeurs autorisées, modèles par profil, erreurs fréquentes). Le modèle de note est dans [references/modele-note.md](references/modele-note.md).

## Étape 0 — Choisir le mode d'accès au CRM

Deux modes existent ; détermine lequel est disponible au début de la session.

1. **MCP du CRM NonStop (prioritaire s'il existe).** Cherche avec ToolSearch des outils dont le nom ou la description évoque le CRM NonStop (mots-clés : `nonstop`, `crm`, `candidate`, `calls`). S'ils existent, utilise-les : c'est plus rapide et plus fiable que le navigateur.
2. **Claude in Chrome (sinon).** Le recruteur est déjà connecté au CRM dans son Chrome. Charge le skill `chrome-browser` puis les outils `mcp__claude-in-chrome__*`. Travaille dans un nouvel onglet, ne ferme pas ses onglets.

Le détail de chaque mode (où trouver les appels, comment éditer une fiche) est dans [references/acces-crm.md](references/acces-crm.md).

Si aucun des deux n'est disponible, dis-le en une phrase et propose au recruteur de coller les transcripts dans la conversation : tu produiras alors le coding et les notes prêts à saisir.

## Étape 1 — Lister les appels du jour

- Récupère tous les appels **du recruteur** pour **la date du jour** (ou la date qu'il indique).
- Construis une liste de travail : heure, nom, type de fiche (candidat / contact client / client), durée, transcript disponible ou non.
- Annonce en une ligne combien d'appels tu vas traiter, puis enchaîne sans attendre.

Regroupe les appels multiples vers la même personne : une seule mise à jour de fiche, qui tient compte de tous les échanges, et une note par appel significatif.

## Étape 2 — Pour chaque appel : comprendre

1. **Lis le transcript en entier.** Ne te contente pas du début : la motivation, le salaire ou la dispo arrivent souvent en fin d'appel.
2. **Ouvre la fiche liée** et lis son coding actuel, ses notes précédentes et son CV/LinkedIn s'il est attaché. Le transcript ne dit pas tout : le CV complète les Industries traversées et les Skills.
3. **Classe l'appel :**
   - *Échange réel avec un candidat* → coding candidat complet.
   - *Échange avec un contact chez un client/prospect* → coding contact client (+ mise à jour de la fiche client si l'appel apporte du nouveau : besoins, BD status, Client status).
   - *Messagerie / pas de réponse / appel de moins de ~30 s sans contenu* → pas de recoding ; note courte « Tentative d'appel – messagerie » et statut inchangé (laisse `Needs Call` s'il y était).
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
- envoyer un e-mail, un SMS ou un message depuis le CRM ;
- réattribuer une fiche qui appartient à un collègue (une fiche sans propriétaire ou créée par le recruteur peut être mise à son nom) ;
- passer `GDPR` à `Consent given` sans accord explicite dans le transcript ;
- modifier `Headhunt` ou les conditions commerciales d'un client.

Si une sauvegarde est refusée (champ obligatoire `*` manquant, erreur), corrige si l'info est disponible ; sinon, note-le et continue avec l'appel suivant. Ne bloque jamais toute la session sur une fiche.

## Étape 5 — Laisser la note

Ajoute une **note avec sujet** sur la fiche, en suivant [references/modele-note.md](references/modele-note.md). Écris en français, factuel, au style télégraphique d'un recruteur. Ne recopie pas le transcript : synthétise. N'invente aucun chiffre ; si le salaire ou la dispo n'ont pas été abordés, écris « non abordé ».

## Étape 6 — Récapitulatif final

Quand tous les appels sont traités, rends un récapitulatif unique :

```
## Coding du <date> — <N> appels traités

| Heure | Fiche | Type | Statut | Principales modifications |
|---|---|---|---|---|
| 09:42 | Prénom NOM | Candidat | Live Active | Markets +Quality Assurance ; Skills GMP, CAPA, LEAN ; Employment TBD→Live |

### À vérifier par toi
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
