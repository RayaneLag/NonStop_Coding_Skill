# Guide de coding CRM NonStop — Candidats & Clients

Référence complète du coding. Les exemples sont anonymisés.

## Sommaire
1. Principes et définitions des champs
2. Fiche candidat : tous les champs
3. Quel Candidate status choisir
4. Modèles de coding par profil (desk pharma / santé)
5. Fiche contact client
6. Fiche client (entreprise)
7. Checklists
8. Erreurs fréquentes

---

## 1. Principes et définitions des champs

Une fiche est bien codée quand quelqu'un d'autre la retrouve par filtre (**Market + Industry + Skills + localisation**) sans lire le CV.

Les quatre champs de classification ont une définition officielle dans le CRM (infobulle ⓘ) :

| Champ | Ce qu'il décrit | Exemples |
|---|---|---|
| **Markets** | La famille de métier : le type de travail que la personne fait au quotidien. Pas la séniorité, pas le secteur de l'employeur, pas les produits ni les technologies. Sur un client, décrit les **personnes qu'il recrute**, pas l'entreprise. | Sales & BD, Production & Manufacturing, Quality Assurance |
| **Industries** | Le secteur principal de l'entreprise (ce qu'elle fabrique ou vend). Sur une personne : les secteurs où elle a acquis de l'expérience. | Pharmaceutical, Medical Devices, Diagnostics |
| **Specialisms** | Un focus plus étroit à l'intérieur d'un Market : sous-discipline, aire thérapeutique, domaine produit. | Oncology, Steriles, Cardiovascular, OTC & Consumer Health |
| **Coded Skills** | Outils, systèmes, méthodes, normes ou compétences concrètes et démontrables utilisés dans le travail. | GMP, CAPA, LEAN, KAM, CRM, SAP |

Règles qui en découlent :
- **Market = le métier, Industry = le secteur.** Un délégué pharmaceutique = Market *Sales & BD* + Industry *Pharmaceutical* (jamais Market « Pharmacy », réservé aux pharmaciens).
- **Plusieurs valeurs autorisées partout** : on code tous les Markets et Industries réellement pertinents (ex. un technicien : 2 Markets, 4 Industries).
- **Coded Skills = du concret**, idéalement 3 à 8, tirés du CV ou de l'appel. Les codes courts existent (SREP, FSE, KAM, MSL, HO/GP…) : choisir dans la liste, **ne jamais inventer**.
- **Tout ce qui a un astérisque (\*) est bloquant** à l'enregistrement ; le reste n'est pas obligatoire techniquement mais conditionne la recherche.

---

## 2. Fiche candidat : tous les champs

Création via **Create person** (toggle *Candidate* activé). On dépose le CV ou on colle l'URL LinkedIn puis **Parse** : le CRM pré-remplit, on corrige ensuite. Contrôler d'abord les doublons (nom, mail, téléphone).

| Champ | Obligatoire | Valeurs possibles / comment remplir |
|---|---|---|
| First name / Last name | Oui | Prénom, puis NOM. Pas de préfixe type « Dr » ni de code dans le nom. |
| Job title | Oui | Intitulé exact du poste actuel, en français si le candidat l'écrit ainsi (ex. « Délégué Pharmaceutique »). |
| Markets | Oui | Liste fixe (~149 valeurs). Desk pharma : Sales & BD, Production & Manufacturing, Quality Assurance, Quality Control, Maintenance, Validation, Pharmacy, Medical Doctors, Medical Affairs, Regulatory Affairs, Supply Chain… |
| Industries | Oui | Liste fixe (~70). Desk pharma : Pharmaceutical, Medical Devices, Diagnostics, Biotechnology, Nutraceutical, CMO, Cosmetics, Hospitals, Medical Care, Life Science (OTC passe par Specialism). |
| Employer | Oui | Entreprise existante dans la liste (sinon *Add new*). Sans emploi → *Unemployed* ; inconnu → *Unknown*. Vérifier l'onglet Clients avant d'approcher un salarié d'un client. |
| Employment | Oui | **Live** (y travaille encore) · **Left** (a quitté) · **TBD** (non vérifié). |
| Candidate status | Oui | Head Hunt · Live Active · Live Speculative · Looking Soon · Needs Call · Not Active · Not looking / found own job · Not Relevant / Dead · Placed · Do not headhunt (voir §3). |
| Address | Oui | Au minimum ville + pays (ex. « Bordeaux, France »), code postal si connu. |
| Téléphone + description | Indicatif obligatoire | Indicatif +33 et numéro ; description : mobile, work, WhatsApp, Work mobile, Personal Mobile, Direct Line, Home Line. |
| Email + description | Non | personal ou work. |
| Source | Non (à mettre) | Origine réelle : LinkedIn, CVDatabase - HelloWork, CVDatabase - APEC, AdResponse - HelloWork / APEC / LinkedIn, Professional registry (médecins), Canvassed, Referral… |
| Target location | Non (à mettre) | Zones où il accepte de travailler (plusieurs possibles). |
| Contract type | Non (à mettre) | Permanent, Contract, Freelance, Temporary, Part-time, Homebased/Remote, Consultant, VRP /Agent. |
| Languages | Non (à mettre) | French + autres langues parlées. |
| Seniority | Non (à mettre) | Junior/entry-level · Associate/intermediate · Specialist/experienced · Senior/lead · Manager/supervisor · Director · Vice President · Senior VP · Executive VP · Chief Officer. |
| Specialisms | Non (à mettre) | Aire thérapeutique ou sous-domaine : Oncology, Cardiovascular, CNS, Dermatology, Diabetology, Respiratory, OTC & Consumer Health, Generics, Phytotherapy, Homeopathy, Steriles, Solid Dose, Injectables… |
| Coded Skills | Non (à mettre) | Voir modèles par profil (§4). |
| Certifications | Non | Pour un VM/délégué diplômé : **Visiteur medical**. Aussi MBA, PMP… |
| LinkedIn profile URL | Non (à mettre) | URL complète du profil. |
| GDPR | Non | Consent given · Consent pending · Consent rejected. |
| Compliant | Non | Fully · Partly · No. |
| Client contact | — | Laisser désactivé pour un candidat pur. |

Après création ou mise à jour : ajouter une **note avec sujet** (résumé d'appel ou source du CV) et s'assurer que la fiche est au nom du recruteur.

---

## 3. Quel Candidate status choisir

| Statut | Quand l'utiliser |
|---|---|
| Live Active | Cherche activement, dispo pour des process. |
| Live Speculative | Ouvert à une belle opportunité sans chercher activement. |
| Looking Soon | Va chercher dans les prochains mois (fin de mission, déménagement…). |
| Needs Call | Fiche créée, pas encore qualifiée au téléphone. |
| Head Hunt | Profil cible en poste, à approcher (approche directe). |
| Not Active | Pas intéressé actuellement. |
| Not looking / found own job | A trouvé un poste seul. |
| Not Relevant / Dead | Profil hors cible ou injoignable durablement. |
| Placed | Placé par NonStop. |
| Do not headhunt | Contact client ou personne à ne pas approcher. |

Indices dans un transcript :
- « je cherche », « je suis en recherche active », « j'ai des entretiens ailleurs » → **Live Active**
- « je suis bien mais si c'est mieux payé / plus près… », « pourquoi pas » → **Live Speculative**
- « ma mission se termine en mars », « on déménage cet été » → **Looking Soon**
- « pas pour l'instant », « rappelez-moi dans un an » → **Not Active**
- « j'ai signé ailleurs », « je commence lundi chez X » → **Not looking / found own job** (+ Employer mis à jour si connu)

---

## 4. Modèles de coding par profil

Adapter Specialisms et Skills au CV et à l'appel de chaque candidat.

| Profil | Markets | Industries | Specialisms | Coded Skills | Seniority |
|---|---|---|---|---|---|
| Délégué pharmaceutique / VM officine | Sales & BD | Pharmaceutical (+ Nutraceutical, OTC si labo concerné) | Aire(s) thérapeutique(s) promue(s) : OTC & Consumer Health, Phytotherapy, Homeopathy, Dermatology… | SREP, CRM, Field, KAM (si grands comptes), HO/GP selon cible | Associate/intermediate (Specialist/experienced si 5 ans+) |
| Technicien de production / maintenance | Production & Manufacturing, Maintenance | Industrial, Pharmaceutical, Medical Devices… (tous les secteurs traversés) | — ou Steriles / Solid Dose si pharma | Technician, Electrical, Electronics, ElecEng, Testing, FSE | Associate/intermediate |
| Pharmacien industriel / AQ opérationnelle | Production & Manufacturing, Quality Assurance, Pharmacy | Pharmaceutical | Steriles | GMP, CAPA, Validation, LEAN, SAP | Junior/entry-level à Specialist |
| Ingénieur / chef de projet process | Production & Manufacturing, Maintenance, General Engineering, Validation | Pharmaceutical, Life Science | Steriles, Lean MNG | LEAN, Six Sigma, CAPA, GMP | Associate/intermediate |
| Consultant(e) qualité | Quality Assurance | Pharmaceutical, Biotechnology | — | QMS, GMP, LEAN | Associate/intermediate |
| Médecin oncologue | Medical Doctors | Medical Care, Hospitals | Oncology | Physician | Specialist/experienced (Source : Professional registry) |

Pour un médecin hospitalier, l'Employer est l'hôpital (ex. « CENTRE HOSPITALIER <VILLE> ») et le Contract type *Permanent* s'il est titulaire.

Exemple de délégué bien codé : Sales & BD / Pharmaceutical / SREP, CRM, E2E, Export.

---

## 5. Fiche contact client (la personne chez le client)

Un contact client est une fiche Person avec le toggle **Contact** activé et **Client contact** sur Oui. Elle garde tous les champs candidat ci-dessus, plus :

| Champ | Comment remplir |
|---|---|
| Employer | Le client exact (le bon site / l'entité : « <Client> France \| <Ville> \| France »), Employment *Live*. |
| Contact type (obligatoire dès que Client contact est activé) | HR - Recruiter/TA/MSP · HR - Associate · HR - Manager/Head of · Int Rec/RPO · Department - Line MGR/ Head of · Department - Associate · Department - Administrator · Manager · Plant Manager / Managing Director · Procurement. |
| Hiring type | Perm et/ou Contingent / Flexible workers. |
| Hiring location | Zones où il recrute (ex. Hauts-de-France). |
| Candidate status | **Do not headhunt**, et Contact methods sur « Do not headhunt ». |
| Markets | Son propre métier (un RH = Recruitment ; un directeur commercial = Sales & BD). |
| Industries | Celles du client + la sienne (ex. Diagnostics, Pharmaceutical, HR & Recruitment). |
| Téléphone / email | Ligne directe (*Direct Line*) et mail pro (*work*). |
| Source | Canvassed, LinkedIn, Apollo.io… |

Les tâches **« Person coding needed »** signalent des contacts créés sans Markets, Industries, Seniority ni Contact type : à compléter en priorité. Certains noms importés portent un préfixe (ex. « SALESDIR - Prénom Nom ») : ne pas le retirer de toi-même, le signaler au recruteur.

---

## 6. Fiche client (l'entreprise)

Création via **Create client** dans le module Clients. Le CRM affiche les doublons potentiels en haut du formulaire : les vérifier et utiliser *Merge* plutôt que créer un doublon (en mode autonome : signaler, ne pas fusionner).

| Champ | Obligatoire | Valeurs possibles / comment remplir |
|---|---|---|
| Company name | Oui | Nom officiel + site si plusieurs entités (ex. « <Groupe> France (HQ) », « <Groupe> <Ville> »). |
| Employer type | Oui | Headquarters · Affiliate · Manufacturing · R&D or Lab · Distribution · CRO · Consultancy · Hospital/HealthCentre · Local government · MSP · RPO · Owner / Public Agency · Contractor / Construction Company. |
| Address | Oui | Adresse complète du site (le Headquarter se déduit). |
| Industries | Oui | Ce que l'entreprise fabrique ou vend (ex. un labo de diagnostic : Diagnostics, Pharmaceutical). |
| Markets | Oui | Les métiers qu'elle **recrute**, pas son secteur (ex. Production & Manufacturing, Sales & BD, Quality Assurance, R&D…). |
| Source | Non (à mettre) | LinkedIn, Apollo.io, Canvassed, Referral, Indeed, Welcome To The Jungle, Website, Proactive, Snitem.fr… |
| LinkedIn url / Website / Careers page | Non (à mettre) | URL de la page entreprise, du site et de la page carrières. |
| Contact number + description | Non (à mettre) | Standard : description *switchboard*. |
| Contact email | Non | Adresses génériques (RH, standard). |
| Specialism | Non (à mettre) | Domaine produit (ex. Molecular Biology ; un labo OTC : OTC & Consumer Health). |
| Client status | Non (à mettre) | Open vacancies · Working on vacancies · Vacancies coming soon · No leads identified · Blocked · Payment issues. |
| BD status | Non (à mettre) | New prospect → Chasing lead(s) → Meeting scheduled → Meeting follow up → Terms requested → Terms signed → Account managed ; *Re-establishing contact* pour un compte à relancer. |
| Hiring type | Non (à mettre) | Perm et/ou Contingent / Flexible workers. |
| Account manager | Non | Consultant qui gère le compte. |
| Business developer | Non | Consultant qui développe le compte (le recruteur, si c'est son prospect). |
| Hiring location | Non (à mettre) | Pays / région où il recrute. |
| Headhunt | Non (à mettre) | Yes / No. **No** = interdiction d'approcher ses salariés. |
| Coded Skills | Non | Compétences des profils recrutés (ex. IndEng, FSE, AppEng, ElecEng, IVD…). |
| Financial ID | Non | SIREN/SIRET si connu. |

Les conditions commerciales (*Terms agreed*, ex. Permanent 17 %) et la note étoilée (*Grade*) ne sont pas dans le formulaire : elles sont mises à jour ailleurs. Ne pas y toucher.

Indices d'un appel client pour Client status / BD status :
- « on a deux postes ouverts », « on recrute un… » → Client status *Open vacancies*
- « on va ouvrir des postes au T1 » → *Vacancies coming soon*
- « on n'a rien en ce moment » → *No leads identified*
- un RDV fixé → BD status *Meeting scheduled* ; demande des conditions → *Terms requested*

---

## 7. Checklists

### Candidat
- [ ] Doublon vérifié (nom, mail, téléphone) ; si doublon → signaler
- [ ] Nom, Job title, Employer + Employment, Address
- [ ] Markets (métier) + Industries (secteurs traversés)
- [ ] Specialisms + 3 à 8 Coded Skills issus de la liste
- [ ] Seniority, Contract type, Languages, Target location
- [ ] Candidate status cohérent avec l'appel
- [ ] Téléphone avec description, email, Source, URL LinkedIn
- [ ] Employeur vérifié dans Clients (Headhunt: No = on n'approche pas)
- [ ] Note avec sujet + fiche au nom du recruteur

### Client
- [ ] Doublons proposés par le CRM vérifiés
- [ ] Company name + site, Employer type, Address
- [ ] Industries (ce qu'il vend) + Markets (ce qu'il recrute)
- [ ] Specialism, Coded Skills des profils recrutés
- [ ] Client status + BD status à jour
- [ ] Hiring type, Hiring location, Headhunt Yes/No
- [ ] Standard (switchboard), LinkedIn, site, page carrières, Source
- [ ] Business developer = le recruteur ; contacts créés et rattachés avec Contact type

---

## 8. Erreurs fréquentes

- Mettre le secteur dans Markets (« Pharmaceutical » n'est pas un métier) ou le métier dans Industries.
- Coder un client par son secteur dans Markets au lieu des métiers qu'il recrute.
- Laisser Employment sur *TBD* après un appel qui a confirmé le poste actuel.
- Fiches de délégués sans Seniority, Specialisms ni Skills : elles sortent mal des recherches.
- Laisser un contact client en *Live Active* au lieu de *Do not headhunt*.
