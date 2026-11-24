# Accessing the NonStop CRM

Two modes. Use the MCP if it is available, otherwise Claude in Chrome.

## Mode A — NonStop CRM MCP

1. Discover the tools: `ToolSearch` with the keywords `nonstop crm`, then `calls`, `candidate`, `person`, `client`, `note`. Load all the useful ones in **one** `select:` call.
2. Read each loaded tool's description before using it: exact names and parameters depend on the MCP's implementation.
3. Typical sequence:
   - identify the current user ("me" / "current user" / profile tool);
   - list today's calls **of this user** (date + user filter), then re-check the consultant field of each call;
   - for each call, get the transcript and the linked record's ID;
   - read the record (fields + notes + CV);
   - update the fields;
   - create the note with a subject.
4. For fixed-list fields (Markets, Industries, Specialisms, Coded Skills, statuses), use the tool that lists allowed values if possible, and take the exact value it returns. Never pass an invented value.
5. If a write returns a validation error, read the message and fix it once; otherwise flag it in the summary.

## Mode B — Claude in Chrome (the recruiter's browser)

1. Load the `chrome-browser` skill, then the Chrome tools in a single `ToolSearch` (`tabs_context_mcp`, `tabs_create_mcp`, `navigate`, `computer`, `read_page`, `find`, `form_input`, `get_page_text`).
2. Look at the open tabs (`tabs_context_mcp`). If the CRM is already open, take its URL; open a **new tab** to work in, without touching the recruiter's tabs.
3. **Logged-in consultant**: find the name shown in the CRM header, profile menu or avatar. That name (Firstname LASTNAME) is the filter.
4. **Today's call list**: open the calls / activity view for the day (call history, dashboard or Calls tab). Apply the consultant/user filter if there is one, then read the list with `get_page_text` or `read_page` and check the consultant / user / "Made by" column of each row. Drop any row whose consultant is not exactly the logged-in consultant.
5. **Transcript**: open each call; the transcript is reachable from the call or from the linked record. Get it with `get_page_text` (scroll or expand the area if the text is truncated).
6. **Editing the record**: open the record, click the edit button, then fill in:
   - multi-select lists (Markets, Industries, Specialisms, Coded Skills): type the start of the value in the field, then **pick the exact option offered** by the dropdown. If no option matches, add nothing;
   - single-select lists (Candidate status, Employment, Seniority…) with `form_input`;
   - save, then check with `read_page` that the values are saved.
7. **Note**: add the note from the record (add-note button), fill in the subject and body, save.
8. If a login page appears, stop and ask the recruiter to log back in: never type a username or password.
9. Never click a delete, merge (*Merge*) or message-sending button.

## Outlook drafts (follow-up emails after a voicemail)

**Option 1 — Outlook / Microsoft 365 MCP.** Search with ToolSearch (`outlook`, `mail draft`, `microsoft 365`). If there is a draft-creation tool, use it (recipient, subject, body). Never use a send tool.

**Option 2 — Outlook Web in Chrome.**
1. Open a new tab on Outlook Web (`outlook.office.com/mail` for a work account, unless the recruiter already has an Outlook tab open: then reuse its URL).
2. Click "New email". Fill in **To** (the email from the record), **Subject**, then the **body**.
3. Save as a draft: "…" menu → "Save draft", or close/cancel the compose window choosing to **keep** the draft. Outlook Web also saves automatically after a few seconds.
4. Open the **Drafts** folder and check that the email is there with the right recipient.
5. **Never** click "Send". If a dialog offers to send, close it.

If Outlook asks for a login, stop and ask the recruiter to log in themselves.

### Learning the interface

On first use, the exact location of the menus is unknown. Take time to explore with `read_page` (`interactive` filter) and `find`. Once the path is found (where today's calls are, where the transcript is, where the edit button is), keep it in mind for the rest of the session. If the persistent memory tool is available, offer the recruiter to save it for next time.
