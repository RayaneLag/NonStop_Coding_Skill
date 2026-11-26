---
name: nonstopcoding
description: Main trigger — as soon as the user types "start coding" (any casing, alone or inside a sentence), launch this skill immediately. Performs the end-of-day "coding" in the NonStop Consulting CRM for a recruiter. Reviews only the logged-in consultant's calls of the day, reads every transcript, understands the context, then recodes the candidate, client contact or client record (Markets, Industries, Specialisms, Coded Skills, Seniority, Candidate status, Employment, etc.) according to the NonStop coding guide and leaves a structured call note; for a voicemail, leaves the note "Voice mail sent" and prepares a follow-up email in the Outlook drafts. Use this skill whenever the user talks about CRM coding, "coding my calls", updating records after calls, end-of-day work in the NonStop CRM, call notes to enter, or "Person coding needed" records, even if they do not name the skill.
---

# NonstopCoding — end-of-day coding in the NonStop CRM

The recruiter spends the day on the phone. In the evening, every call must turn into two things in the CRM:
1. a **correctly coded** record, so a colleague can find it by filtering Market + Industry + Skills + location without reading the CV;
2. a **structured note** that tells what was said.

Your job: do this work for them, **autonomously** and reliably, **only on their own calls**, then hand back a clear summary.

## Trigger: "start coding"

When the consultant types **"start coding"**, they start the coding session and usually **leave their desk** right after. Therefore:
- start immediately, without asking for confirmation or a date (default: today);
- go through every call to the end without waiting for answers; a call that causes a problem is noted in the summary, then you move on to the next one;
- only stop and wait for the consultant when continuing would be risky: the logged-in consultant cannot be identified, or a login page appears for the CRM or Outlook;
- as soon as the last call is done, post the final summary **immediately** in the Claude Code conversation (step 6), without waiting for a message. It must stand on its own, because the consultant may read it later.

Before coding anything, read [references/coding-guide.md](references/coding-guide.md): it is the rulebook (field definitions, allowed values, templates by profile, common mistakes). The note template is in [references/note-template.md](references/note-template.md).

## Language

The CRM, the candidates and the consultant work in French. Write CRM notes and follow-up emails **in French**, using the French templates in the reference files exactly as given. Exception: the voicemail note is just `Voice mail sent` (subject and body), nothing else. Write the final summary in the language the consultant uses with you. Field values (Markets, Skills, statuses…) are the CRM's English labels.

## Step 0 — Choose the CRM access mode

Two modes exist; work out which one is available at the start of the session.

1. **NonStop CRM MCP (preferred if it exists).** Use ToolSearch to look for tools whose name or description refers to the NonStop CRM (keywords: `nonstop`, `crm`, `candidate`, `calls`). If they exist, use them: it is faster and more reliable than the browser.
2. **Claude in Chrome (otherwise).** The recruiter is already logged in to the CRM in their Chrome. Load the `chrome-browser` skill, then the `mcp__claude-in-chrome__*` tools. Work in a new tab and do not close their tabs.

Details for each mode (where to find the calls, how to edit a record) are in [references/crm-access.md](references/crm-access.md).

If neither is available, say so in one sentence and offer to let the recruiter paste the transcripts into the conversation: you will then produce the coding and the notes ready to enter.

## Step 1 — Identify the consultant and list THEIR calls of the day

**Absolute rule: you only process calls made by the consultant logged in to the CRM.** The CRM also shows other consultants' calls. You do not read them, code them or leave any note on them, even when the record is the same. Coding a colleague's calls would overwrite their work and notes.

1. **Identify the logged-in consultant** first: first and last name of the account open in the CRM (profile menu, avatar, page header, or the MCP's "current user" tool). Example: if the logged-in account is "Firstname LASTNAME", only calls whose consultant / author / owner is "Firstname LASTNAME" are processed.
2. State it in one line: "Logged-in consultant: Firstname LASTNAME". If you cannot identify them with certainty, **stop and ask** the recruiter for their name as it appears in the CRM: a question is better than coding someone else's calls.
3. Fetch **this consultant's** calls for **today** (or the given date). Use the CRM's consultant / user filter if there is one, **and** still check, call by call, that the consultant name matches exactly. A call whose consultant is different or unknown is excluded and listed in the summary ("skipped calls").
4. Build a work list: time, contact name, record type (candidate / client contact / client), duration, transcript available or not.
5. State in one line how many calls you will process, then carry on without waiting.

Group several calls to the same person: one record update that takes all exchanges into account, and one note per meaningful call.

## Step 2 — For each call: understand

1. **Read the whole transcript.** Do not stop at the beginning: motivation, salary or availability often come at the end of the call.
2. **Open the linked record** and read its current coding, previous notes and attached CV/LinkedIn if any. The transcript does not say everything: the CV fills in the Industries and Skills.
3. **Classify the call:**
   - *Real conversation with a candidate* → full candidate coding.
   - *Conversation with a contact at a client/prospect* → client contact coding (+ update of the client record if the call brings something new: needs, BD status, Client status).
   - *Voicemail* (a transcript that only contains a voicemail greeting and/or the consultant's message, or no transcript on a short call with nobody on the line) → no recoding, status unchanged (leave `Needs Call` if it was there). Note **"Voice mail sent"** then a **follow-up email draft** in Outlook: see step 5b.
   - *Wrong number / off-target person* → note, and `Not Relevant / Dead` only if it is clearly final.

## Step 3 — Decide the coding

Apply the guide. The points that make the difference:

- **Markets = the job, Industries = the sector.** "Pharmaceutical" is never a Market; "Pharmacy" is reserved for pharmacists. For a client, Markets = the jobs it **hires for**.
- **Several values** whenever they are genuinely relevant (every sector worked in goes into Industries).
- **Coded Skills: 3 to 8, concrete, taken from the CRM list.** Never invent a code. If the skill you want is not in the list, pick the closest one or leave it out.
- **Candidate status consistent with the call** (table in the guide). A client contact is always `Do not headhunt`.
- **Employment**: switch from `TBD` to `Live` or `Left` as soon as the call has confirmed the situation.
- **Seniority** derived from real experience (years, management), not from the title alone.
- Also fill the "should be filled" fields when the call provides them: Target location, Contract type, Languages, Source, Specialisms.

### Headhunt: No / Do not headhunt — check whether it really applies

A client record with `Headhunt: No` (or a candidate the CRM switches to `Do not headhunt` on save because of their employer) is **not enough on its own**. Each time you meet it, open the employer's client record and check two fields (consultant's rule since 26/11/2026):

- **Account manager(s)**: a colleague's name, empty, or a name marked `(left)`.
- **Terms signed**: BD status `Terms signed` / `Account managed`, or `Terms agreed` ticked with a rate.

Then:

| Account manager | Terms | Result |
|---|---|---|
| Active colleague | Signed | **Strictly forbidden to approach.** Status stays `Do not headhunt`, no follow-up email draft, flag it in the summary. |
| Empty, or only colleagues marked `(left)` | Any | **The Do not headhunt does not count** (the account manager has left the company). The candidate can be approached: keep the status that matches the call, prepare the follow-up draft as usual. If the CRM set `Do not headhunt` automatically on save, set the right status again explicitly and check it stuck. |
| Active colleague | Not signed | Not covered by the rule: do not approach by default, keep the status, and flag it in the summary for the consultant to decide. |

This only concerns candidates employed at a client. A **client contact** (Contact toggle / Client contact = Yes) stays `Do not headhunt` in every case. Never change the client's own `Headhunt` field or its terms.

**Caution principle:** you complete and correct what the call or the CV clearly establishes. You do not overwrite plausible existing data with a guess. When in real doubt, leave the field as it is and flag it in the summary: an incomplete record is fixed in 10 seconds, a wrongly coded record pollutes the whole team's searches.

## Step 4 — Apply in the CRM

The recruiter has authorised you to save **directly**, without record-by-record approval. Save each record as soon as it is ready, then move on to the next one.

What you do **not** do, even autonomously, because it is irreversible or affects other people — flag it in the summary instead:
- delete a record, a note or a document;
- merge duplicates (`Merge`);
- send an email, SMS or message (follow-up emails stay as **drafts** in Outlook);
- read, code or annotate a call made by another consultant;
- reassign a record that belongs to a colleague (a record with no owner, or created by the recruiter, can be put in their name);
- set `GDPR` to `Consent given` without explicit agreement in the transcript;
- change `Headhunt` or a client's commercial terms.

If a save is rejected (missing mandatory `*` field, error), fix it if the information is available; otherwise note it and continue with the next call. Never block the whole session on one record.

## Step 5 — Leave the note

Add a **note with a subject** to the record, following [references/note-template.md](references/note-template.md). Write in French, factual, in a recruiter's telegraphic style. Do not copy the transcript: summarise. Never invent a figure; if salary or availability were not discussed, write « non abordé ».

## Step 5b — Voicemail: note + Outlook email draft

For each call that went to voicemail:

1. **Note on the record**: subject `Voice mail sent`, body `Voice mail sent`. Nothing more: no date, no time, no email address, no mention of the draft or of a missing email. This applies to every voicemail / no-answer call (consultant's rule since 26/11/2026).
2. **Get the contact's email** from their CRM record (prefer the `personal` address for a candidate, `work` for a client contact). If there is no address, do not look elsewhere: no draft, and flag it in the summary only (the note stays `Voice mail sent`).
3. **Write the follow-up email** using [references/email-template.md](references/email-template.md), personalised with what the record and previous notes say (job, reason for the call). Sign in the name of the logged-in consultant.
4. **Put it in the consultant's Outlook Drafts — without sending it.** The consultant reviews and sends it themselves. Outlook access: an Outlook / Microsoft 365 MCP tool if one exists (draft creation), otherwise Outlook Web in Chrome ("New email", fill To / Subject / Body, then close the window so Outlook saves it to Drafts, or use "Save draft"). Details in [references/crm-access.md](references/crm-access.md). Never click "Send".
5. Check that the draft appears in the Drafts folder with the right recipient: the draft list must show the email address, not just "[Draft]". In Outlook Web, the typed address only counts once it has been validated with Enter and turned into a recipient chip (see [references/crm-access.md](references/crm-access.md)).

## Step 6 — Final summary

As soon as every call is processed, immediately write a single summary in the Claude Code conversation:

```
## Coding for <date> — Firstname LASTNAME — <N> calls processed

| Time | Record | Type | Status | Main changes |
|---|---|---|---|---|
| 09:42 | Firstname LASTNAME | Candidate | Live Active | Markets +Quality Assurance; Skills GMP, CAPA, LEAN; Employment TBD→Live |
| 10:15 | Firstname LASTNAME | Candidate | Needs Call | Voicemail – note "Voice mail sent"; Outlook draft ready |

### Outlook drafts to review and send
- Firstname LASTNAME — address@… — email subject

### For you to check
- Skipped calls (other consultant or unknown consultant): <number>
- Voicemails with no email on the record: …
- Possible duplicates: …
- Client employer with Headhunt: No — strictly forbidden (active account manager + terms signed): …
- Client employer with Headhunt: No — not applied (account manager empty or left): …
- Client employer with Headhunt: No — to decide (active account manager, no terms signed): …
- Fields left empty for lack of information: …
- Failed saves: …

### Follow-ups to plan
- Firstname LASTNAME — <next step and date mentioned during the call>
```

The follow-ups come from the « Prochaine étape » section of the notes: that is what helps the recruiter most the next morning.

## Confidentiality

Transcripts and records contain candidates' personal data. Do not copy them anywhere other than the CRM and the summary in the conversation. Do not write files containing this data to disk unless the recruiter asks for it.
