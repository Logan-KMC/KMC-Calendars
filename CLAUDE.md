# KMC Calendars

Static HTML support calendars for Krista Mashore Coaching students. One `.html` file = one calendar. The `main` branch is **live**: GitHub Pages republishes it within a minute or two of every push, and the pages are embedded in GoHighLevel (GHL).

- Repo: `Logan-KMC/KMC-Calendars`
- Live URL pattern: `https://logan-kmc.github.io/KMC-Calendars/<file>.html`
- GHL embed snippet:
  ```html
  <p>
    <iframe
      src="https://logan-kmc.github.io/KMC-Calendars/<file>.html"
      style="width: 100%; height: 1000px; border: 0px;"
    ></iframe>
  </p>
  ```

## Workflow (always follow, every time)

Several people edit this repo from their own computers, so your local copy may be out of date. Pushing to `main` makes a change live for students immediately, so **nothing goes live until the user says so.**

1. **At the start of every task, before touching any file:** run `git pull --rebase` so you are working from the latest live version. Do this for each new request to change a calendar, not just once per session, because someone else may have pushed in between. If it fails or reports conflicts, stop and tell the user. Do not guess.
2. Make the change. Preview the page in a browser if you can, and check the hard rules below.
3. Commit with a clear message saying what changed and why.
4. **Never push automatically.** After committing, tell the user the change is saved on their computer only and is **not live yet**, then wait. Push only after the user says "push it live" (or clearly says the same thing in other words). Replies like "looks good", "ok" or "thanks" are not permission to push. If the user spots a mistake before then, fix it with a new commit; nothing has gone live, so there is no harm done. When they do say to push: run `git pull --rebase` again, then `git push origin main`. If the push is rejected, pull and retry once. If it still fails, stop and ask.
5. Never force-push, never rewrite history that has been pushed, never delete branches.

## Calendars

| File | Calendar |
|---|---|
| `mashore-blueprint-cab-support-calendar.html` | CAB Support Calendar |
| `Elite-blueprint-support-calendar.html` | Elite Support Calendar |
| `mastery-calendar-updated.html` | Mastery Support Calendar (uses `kmcal-` class prefix) |
| `ai-cab-support-calendar.html` | AI CAB Support Calendar |
| `ai-for-agents-blueprint-support-calendar.html` | AI For Agents Blueprint Support Calendar |
| `ai-mastermind-call-calendar.html` | AI Mastermind Call Calendar |
| `kmo-calendar.html` | KMO Calendar |
| `30-day-success-plan.html` | 30 Day Success Plan |
| `boss-support-calendar.html` | Boss Support Calendar |

Every file except Mastery uses the `cwk-` class prefix. Mastery uses `kmcal-` for the same structure (`kmcal-call`, `kmcal-n`, `kmcal-t`, ...). Keep this table current when a calendar is added or renamed.

## Page structure

Five day columns (`cwk-day`, MON to FRI). Each call is `<a class="cwk-call cwk-<color>" href="...">` containing a name (`cwk-n`), a time (`cwk-t`), and optionally a `cwk-badge`. Order calls in a day by start time. Convention: Coaching Calls are `cwk-pink`, Mashore Method Office Hours are `cwk-navy`.

For time zones, match the label the file already uses (`PT` in most files, `PST` in Boss and 30 Day Success Plan).

## Hard rules (each one prevents a bug that already happened)

- **Every real link must keep `target="_blank" rel="noopener noreferrer"`.** The pages run inside a GHL iframe. Without `target="_blank"`, tapping a link navigates inside the nested frame and phones can't open Zoom.
- **Never invent a link.** If no link was given, use `<div class="cwk-call cwk-soon">` (not an `<a>`) with a badge such as "Link Coming Soon", and tell the user it is unlinked. The `.cwk-soon` CSS exists in Boss, AI Mastermind and 30 Day Success Plan; copy those four rules into any other file that needs it.
- **Skin in the Game is one banner at the top of the page**, never a card repeated in each day column.
- The Google Fonts `<link>` and the `<style>` block stay in `<head>`.
- Don't touch calls, days or hosts that weren't part of the request. These are live schedules students rely on.

## Standing rules between calendars

- **Shared calls use the same link everywhere** (the Monday 8 am Coaching Call, Mashore Method Office Hours, and others). When a shared link or time changes, search every file for the old link (`grep`) and update every occurrence, unless told to change only one calendar.
- **AI Mastermind mirrors Boss.** The AI Mastermind calendar shows every call on the Boss calendar plus its own Mastermind calls. When the Boss call list changes, make the same change on AI Mastermind. Names can differ slightly (Wednesday's "Boss Training with Krista" is "Krista's Boss Coaching Call" on Mastermind).
- **The Wednesday "Mastery Coaching Call" belongs only on Elite and Mastery.** This is intentional.
- **Announcements:** Boss and AI Mastermind each have an Announcements section below the grid. To add one, copy an entire `<div class="cwk-announce">...</div>` block and edit the text. Newest goes first. Ask which page(s) it should go on.

## Temporary / one-off items

Memory does not carry between people or computers, so track anything dated here. When you add a one-off item (holiday closure, special event, dated announcement), add a line below. When you remove it, delete the line. If a date below has passed, tell the user it is ready to remove.

- **Tuesday Vickee call canceled for Oct 6, 2026 only.** The Tuesday 10 am Vickee call is shown grayed out with a "Canceled Today" badge on 8 calendars (Success Plan, Elite, CAB, AI CAB, AI For Agents, KMO, Mastery, and "Mindset & Momentum Call" on AI Mastermind, which uses the same Zoom link `https://us06web.zoom.us/j/85181544892`). Once Oct 6 has passed, tell the user it needs to be restored: make it a clickable link again with that Zoom link, put back its original color (`cwk-blue`, `cwk-pink` on KMO, `kmcal-blue` on Mastery), and remove the badge. Or revert the commit titled "Cancel Tuesday Vickee Mindset call for Oct 6".
- Boss + AI Mastermind announcement "Magazine & Newsletter Skill Workshop with Doug" (workshop Oct 7, follow-up Nov 6, 2026): remove after Nov 6, 2026.
- **Mashore Method Office Hours links expire Nov 6, 2026.** The current M/T/Th 9-10 am link (`…j/82553606438`) and Friday 1-2 pm link (`…j/87217563574`) are on Elite, CAB, AI CAB, AI For Agents, KMO and Mastery. New links will be sent after Nov 6; replace every occurrence when they arrive (the AI Mastermind "Mashore Method Support Office Hours" use different links and are not part of this). From Nov 6 on, remind the user these links are expired.
- "KMC Book Club - The Thinking Effect" placeholder on **Wednesday, Oct 28, 10 am PST** on all 9 calendars (unlinked, "Link Coming Soon"). When the link arrives, make it a real link. Remove it after Oct 28 unless told otherwise. The regular Tuesday "KMC Book Club" (first Tuesday monthly) was removed from all calendars on Oct 5, 2026 because the boss is deciding the future and best time for Book Club. Do not restore a Tuesday Book Club unless the user says so.

## Creating a new calendar

Copy the simplest similar file (`boss-support-calendar.html` is a good template), then change the `<title>`, the `<h1>`, and the calls. Use a descriptive filename like `<name>-support-calendar.html`. After it is pushed, the page is live at the URL pattern above. Give the user the embed snippet for GHL, and add the file to the table in this document.
