# NonStop CRM coding guide — Candidates & Clients

Complete coding reference. Examples are anonymised.

## Contents
1. Principles and field definitions
2. Candidate record: all fields
3. Which Candidate status to choose
4. Coding templates by profile (pharma / healthcare desk)
5. Client contact record
6. Client record (company)
7. Checklists
8. Common mistakes

---

## 1. Principles and field definitions

A record is well coded when someone else can find it by filtering (**Market + Industry + Skills + location**) without reading the CV.

The four classification fields have an official definition in the CRM (ⓘ tooltip):

| Field | What it describes | Examples |
|---|---|---|
| **Markets** | The job family: the type of work the person does day to day. Not seniority, not the employer's sector, not products or technologies. On a client, it describes the **people it hires**, not the company. | Sales & BD, Production & Manufacturing, Quality Assurance |
| **Industries** | The company's main sector (what it makes or sells). On a person: the sectors where they gained experience. | Pharmaceutical, Medical Devices, Diagnostics |
| **Specialisms** | A narrower focus within a Market: sub-discipline, therapeutic area, product area. | Oncology, Steriles, Cardiovascular, OTC & Consumer Health |
| **Coded Skills** | Tools, systems, methods, standards or concrete, demonstrable skills used in the job. | GMP, CAPA, LEAN, KAM, CRM, SAP |

Resulting rules:
- **Market = the job, Industry = the sector.** A pharmaceutical sales rep = Market *Sales & BD* + Industry *Pharmaceutical* (never Market "Pharmacy", which is reserved for pharmacists).
- **Several values allowed everywhere**: code every Market and Industry that is genuinely relevant (e.g. a technician: 2 Markets, 4 Industries).
- **Coded Skills = concrete**, ideally 3 to 8, taken from the CV or the call. Short codes exist (SREP, FSE, KAM, MSL, HO/GP…): pick from the list, **never invent**.
- **Anything with an asterisk (\*) blocks saving**; the rest is not technically mandatory but drives search results.

---

## 2. Candidate record: all fields

Created via **Create person** (*Candidate* toggle on). Drop the CV or paste the LinkedIn URL then **Parse**: the CRM pre-fills, you correct afterwards. Check for duplicates first (name, email, phone).

| Field | Mandatory | Possible values / how to fill |
|---|---|---|
| First name / Last name | Yes | First name, then LAST NAME. No prefix such as "Dr" and no code in the name. |
| Job title | Yes | Exact title of the current job, in French if the candidate writes it that way (e.g. « Délégué Pharmaceutique »). |
| Markets | Yes | Fixed list (~149 values). Pharma desk: Sales & BD, Production & Manufacturing, Quality Assurance, Quality Control, Maintenance, Validation, Pharmacy, Medical Doctors, Medical Affairs, Regulatory Affairs, Supply Chain… |
| Industries | Yes | Fixed list (~70). Pharma desk: Pharmaceutical, Medical Devices, Diagnostics, Biotechnology, Nutraceutical, CMO, Cosmetics, Hospitals, Medical Care, Life Science (OTC goes through Specialism). |
| Employer | Yes | Existing company from the list (otherwise *Add new*). Not employed → *Unemployed*; unknown → *Unknown*. Check the Clients tab before approaching an employee of a client. |
| Employment | Yes | **Live** (still works there) · **Left** (has left) · **TBD** (not verified). |
| Candidate status | Yes | Head Hunt · Live Active · Live Speculative · Looking Soon · Needs Call · Not Active · Not looking / found own job · Not Relevant / Dead · Placed · Do not headhunt (see §3). |
| Address | Yes | At least city + country (e.g. "Bordeaux, France"), postcode if known. |
| Phone + description | Country code mandatory | +33 code and number; description: mobile, work, WhatsApp, Work mobile, Personal Mobile, Direct Line, Home Line. |
| Email + description | No | personal or work. |
| Source | No (should be filled) | Real origin: LinkedIn, CVDatabase - HelloWork, CVDatabase - APEC, AdResponse - HelloWork / APEC / LinkedIn, Professional registry (doctors), Canvassed, Referral… |
| Target location | No (should be filled) | Areas where they accept to work (several allowed). |
| Contract type | No (should be filled) | Permanent, Contract, Freelance, Temporary, Part-time, Homebased/Remote, Consultant, VRP /Agent. |
| Languages | No (should be filled) | French + other languages spoken. |
| Seniority | No (should be filled) | Junior/entry-level · Associate/intermediate · Specialist/experienced · Senior/lead · Manager/supervisor · Director · Vice President · Senior VP · Executive VP · Chief Officer. |
| Specialisms | No (should be filled) | Therapeutic area or sub-field: Oncology, Cardiovascular, CNS, Dermatology, Diabetology, Respiratory, OTC & Consumer Health, Generics, Phytotherapy, Homeopathy, Steriles, Solid Dose, Injectables… |
| Coded Skills | No (should be filled) | See templates by profile (§4). |
| Certifications | No | For a qualified medical rep: **Visiteur medical**. Also MBA, PMP… |
| LinkedIn profile URL | No (should be filled) | Full profile URL. |
| GDPR | No | Consent given · Consent pending · Consent rejected. |
| Compliant | No | Fully · Partly · No. |
| Client contact | — | Leave off for a pure candidate. |

After creating or updating: add a **note with a subject** (call summary or CV source) and make sure the record is in the recruiter's name.

---

## 3. Which Candidate status to choose

| Status | When to use it |
|---|---|
| Live Active | Actively looking, available for processes. |
| Live Speculative | Open to a great opportunity without actively looking. |
| Looking Soon | Will be looking in the coming months (end of assignment, relocation…). |
| Needs Call | Record created, not yet qualified by phone. |
| Head Hunt | Target profile in a job, to approach (direct approach). |
| Not Active | Not interested at the moment. |
| Not looking / found own job | Found a job on their own. |
| Not Relevant / Dead | Off-target profile or unreachable for good. |
| Placed | Placed by NonStop. |
| Do not headhunt | Person not to be approached: client contact or employee of a client whose company has an active account manager **and** signed terms. |

Clues in a transcript (the candidates speak French):
- « je cherche », « je suis en recherche active », « j'ai des entretiens ailleurs » (I'm looking, actively searching, interviewing elsewhere) → **Live Active**
- « je suis bien mais si c'est mieux payé / plus près… », « pourquoi pas » (I'm fine but if it pays better / is closer…, why not) → **Live Speculative**
- « ma mission se termine en mars », « on déménage cet été » (my assignment ends in March, we're moving this summer) → **Looking Soon**
- « pas pour l'instant », « rappelez-moi dans un an » (not for now, call me back in a year) → **Not Active**
- « j'ai signé ailleurs », « je commence lundi chez X » (I signed elsewhere, I start Monday at X) → **Not looking / found own job** (+ Employer updated if known)

---

## 4. Coding templates by profile

Adapt Specialisms and Skills to each candidate's CV and call.

| Profile | Markets | Industries | Specialisms | Coded Skills | Seniority |
|---|---|---|---|---|---|
| Pharmaceutical sales rep / pharmacy rep | Sales & BD | Pharmaceutical (+ Nutraceutical, OTC if relevant lab) | Therapeutic area(s) promoted: OTC & Consumer Health, Phytotherapy, Homeopathy, Dermatology… | SREP, CRM, Field, KAM (if key accounts), HO/GP depending on target | Associate/intermediate (Specialist/experienced if 5+ years) |
| Production / maintenance technician | Production & Manufacturing, Maintenance | Industrial, Pharmaceutical, Medical Devices… (every sector worked in) | — or Steriles / Solid Dose if pharma | Technician, Electrical, Electronics, ElecEng, Testing, FSE | Associate/intermediate |
| Industrial pharmacist / operational QA | Production & Manufacturing, Quality Assurance, Pharmacy | Pharmaceutical | Steriles | GMP, CAPA, Validation, LEAN, SAP | Junior/entry-level to Specialist |
| Process engineer / project manager | Production & Manufacturing, Maintenance, General Engineering, Validation | Pharmaceutical, Life Science | Steriles, Lean MNG | LEAN, Six Sigma, CAPA, GMP | Associate/intermediate |
| Quality consultant | Quality Assurance | Pharmaceutical, Biotechnology | — | QMS, GMP, LEAN | Associate/intermediate |
| Medical oncologist | Medical Doctors | Medical Care, Hospitals | Oncology | Physician | Specialist/experienced (Source: Professional registry) |

For a hospital doctor, the Employer is the hospital (e.g. "CENTRE HOSPITALIER <CITY>") and the Contract type is *Permanent* if they hold a tenured post.

Example of a well-coded sales rep: Sales & BD / Pharmaceutical / SREP, CRM, E2E, Export.

---

## 5. Client contact record (the person at the client)

A client contact is a Person record with the **Contact** toggle on and **Client contact** set to Yes. It keeps all the candidate fields above, plus:

| Field | How to fill |
|---|---|
| Employer | The exact client (the right site / entity: "<Client> France \| <City> \| France"), Employment *Live*. |
| Contact type (mandatory once Client contact is on) | HR - Recruiter/TA/MSP · HR - Associate · HR - Manager/Head of · Int Rec/RPO · Department - Line MGR/ Head of · Department - Associate · Department - Administrator · Manager · Plant Manager / Managing Director · Procurement. |
| Hiring type | Perm and/or Contingent / Flexible workers. |
| Hiring location | Areas where they hire (e.g. Hauts-de-France). |
| Candidate status | **Do not headhunt** (and Contact methods "Do not headhunt") **only if** the company has an active account manager **and** signed terms. Otherwise the company is not an active client: status that matches the call, like a normal candidate. |
| Markets | Their own job (an HR person = Recruitment; a sales director = Sales & BD). |
| Industries | The client's + their own (e.g. Diagnostics, Pharmaceutical, HR & Recruitment). |
| Phone / email | Direct line (*Direct Line*) and work email (*work*). |
| Source | Canvassed, LinkedIn, Apollo.io… |

**"Person coding needed"** tasks flag contacts created without Markets, Industries, Seniority or Contact type: complete them first. Some imported names carry a prefix (e.g. "SALESDIR - Firstname Lastname"): do not remove it yourself, flag it to the recruiter.

---

## 6. Client record (the company)

Created via **Create client** in the Clients module. The CRM shows potential duplicates at the top of the form: check them and use *Merge* rather than creating a duplicate (in autonomous mode: flag, do not merge).

| Field | Mandatory | Possible values / how to fill |
|---|---|---|
| Company name | Yes | Official name + site if several entities (e.g. "<Group> France (HQ)", "<Group> <City>"). |
| Employer type | Yes | Headquarters · Affiliate · Manufacturing · R&D or Lab · Distribution · CRO · Consultancy · Hospital/HealthCentre · Local government · MSP · RPO · Owner / Public Agency · Contractor / Construction Company. |
| Address | Yes | Full site address (the Headquarter is derived). |
| Industries | Yes | What the company makes or sells (e.g. a diagnostics lab: Diagnostics, Pharmaceutical). |
| Markets | Yes | The jobs it **hires for**, not its sector (e.g. Production & Manufacturing, Sales & BD, Quality Assurance, R&D…). |
| Source | No (should be filled) | LinkedIn, Apollo.io, Canvassed, Referral, Indeed, Welcome To The Jungle, Website, Proactive, Snitem.fr… |
| LinkedIn url / Website / Careers page | No (should be filled) | Company page, website and careers page URLs. |
| Contact number + description | No (should be filled) | Switchboard: description *switchboard*. |
| Contact email | No | Generic addresses (HR, switchboard). |
| Specialism | No (should be filled) | Product area (e.g. Molecular Biology; an OTC lab: OTC & Consumer Health). |
| Client status | No (should be filled) | Open vacancies · Working on vacancies · Vacancies coming soon · No leads identified · Blocked · Payment issues. |
| BD status | No (should be filled) | New prospect → Chasing lead(s) → Meeting scheduled → Meeting follow up → Terms requested → Terms signed → Account managed; *Re-establishing contact* for an account to revive. |
| Hiring type | No (should be filled) | Perm and/or Contingent / Flexible workers. |
| Account manager | No | Consultant who manages the account. |
| Business developer | No | Consultant who develops the account (the recruiter, if it is their prospect). |
| Hiring location | No (should be filled) | Country / region where it hires. |
| Headhunt | No (should be filled) | Yes / No. **No** = its employees must not be approached, **only if** an active colleague is Account manager **and** terms are signed. Account manager empty or marked `(left)` = the No does not count (see SKILL.md, "Headhunt: No / Do not headhunt"). |
| Coded Skills | No | Skills of the profiles it hires (e.g. IndEng, FSE, AppEng, ElecEng, IVD…). |
| Financial ID | No | SIREN/SIRET if known. |

Commercial terms (*Terms agreed*, e.g. Permanent 17 %) and the star rating (*Grade*) are not in the form: they are updated elsewhere. Do not touch them.

Clues from a client call for Client status / BD status (the clients speak French):
- « on a deux postes ouverts », « on recrute un… » (we have two open positions, we're hiring a…) → Client status *Open vacancies*
- « on va ouvrir des postes au T1 » (we'll open positions in Q1) → *Vacancies coming soon*
- « on n'a rien en ce moment » (nothing at the moment) → *No leads identified*
- a meeting booked → BD status *Meeting scheduled*; a request for terms → *Terms requested*

---

## 7. Checklists

### Candidate
- [ ] Duplicate checked (name, email, phone); if duplicate → flag
- [ ] Name, Job title, Employer + Employment, Address
- [ ] Markets (job) + Industries (sectors worked in)
- [ ] Specialisms + 3 to 8 Coded Skills from the list
- [ ] Seniority, Contract type, Languages, Target location
- [ ] Candidate status consistent with the call
- [ ] Phone with description, email, Source, LinkedIn URL
- [ ] Employer checked in Clients (Headhunt: No → also check Account manager + terms signed: both filled = do not approach; account manager empty or left = the No does not count)
- [ ] Note with subject + record in the recruiter's name

### Client
- [ ] Duplicates suggested by the CRM checked
- [ ] Company name + site, Employer type, Address
- [ ] Industries (what it sells) + Markets (what it hires)
- [ ] Specialism, Coded Skills of the profiles hired
- [ ] Client status + BD status up to date
- [ ] Hiring type, Hiring location, Headhunt Yes/No
- [ ] Switchboard, LinkedIn, website, careers page, Source
- [ ] Business developer = the recruiter; contacts created and linked with a Contact type

---

## 8. Common mistakes

- Putting the sector in Markets ("Pharmaceutical" is not a job) or the job in Industries.
- Coding a client by its sector in Markets instead of the jobs it hires for.
- Leaving Employment on *TBD* after a call that confirmed the current job.
- Sales rep records with no Seniority, Specialisms or Skills: they come out badly in searches.
- Leaving a client contact of an active client (active account manager + signed terms) on *Live Active* instead of *Do not headhunt*.
- Putting a client contact on *Do not headhunt* when their company has no active account manager or no signed terms.
