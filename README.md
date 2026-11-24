# NonStop_Coding_Skill

Claude skill **NonstopCoding**: the end-of-day coding of the NonStop Consulting CRM, done by Claude.

Every evening, Claude:
1. identifies the consultant logged in to the CRM and fetches **only their** calls of the day (never other consultants' calls);
2. reads each transcript and understands the context of the call;
3. recodes the candidate, client contact or client record according to the NonStop coding guide (Markets, Industries, Specialisms, Coded Skills, Seniority, Candidate status, Employment…);
4. leaves a structured call note on the record;
5. on a voicemail: note "Voice mail sent" and a follow-up email saved in the consultant's **Outlook drafts** (never sent);
6. hands back a summary: records changed, drafts to send, points to check, follow-ups to plan.

CRM notes and follow-up emails are written in French, because the CRM, the team and the candidates work in French.

## CRM access

- **Claude in Chrome**: Claude works in the recruiter's Chrome, already logged in to the CRM.
- **NonStop CRM MCP**: used first whenever it is available in Claude.

## Guardrails

Even in autonomous mode, Claude never touches another consultant's calls, sends no email (drafts only), deletes nothing, does not merge duplicates, sends no message, does not reassign a colleague's record and does not change GDPR consent without explicit agreement. These cases are flagged in the summary.

## Contents

```
nonstopcoding/
├── SKILL.md                     # main workflow
└── references/
    ├── coding-guide.md          # coding rules (fields, values, templates, mistakes)
    ├── note-template.md         # call note template
    ├── email-template.md        # follow-up email after a voicemail
    └── crm-access.md            # MCP mode, Chrome mode, Outlook drafts
```

## Installation

**Claude Code**: copy the `nonstopcoding` folder into `~/.claude/skills/`.

**Claude (app / claude.ai)**: zip the `nonstopcoding` folder and import it in *Settings → Capabilities → Skills*.

## Usage

At the end of the day, simply type:

```
start coding
```

Claude processes all of the logged-in consultant's calls of the day, with no further questions.

**To let it run after you leave:** the PC must not go to **sleep**, otherwise everything stops (Claude, Chrome, network). Turning off the screen or locking the session (Win + L) is fine. Also allow the CRM and Outlook in the Claude in Chrome extension beforehand, so that no permission request blocks the session.
