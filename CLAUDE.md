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
- **AI Mastermind mirrors Boss.** The AI Mastermind calendar shows the Boss-program calls on the Boss calendar (Boss Training, Boss Office Hours, Boss Office Hours with Hailey, BOSS installation calls) plus its own Mastermind calls. When one of those Boss calls changes, make the same change on AI Mastermind. **Exception: Mashore Method Office Hours.** The Boss calendar shows the same Mashore Method Office Hours as Mastery (Mon/Tue/Thu 9-10 am, Fri 1-2 pm), but AI Mastermind must NOT; it only has its own "Mashore Method Support Office Hours". If you are not sure whether a Boss change should also go on Mastermind, ask the user instead of mirroring. The Wednesday call is named "Boss Training" on both. On Mastermind, the Monday 9-10 am Mastermind call is "Mastermind Coaching Call" (not a generic "Coaching Call"), so it is not confused with Krista.s Monday 8 am Coaching Call.
- **The Wednesday "Mastery Coaching Call" belongs only on Elite and Mastery.** This is intentional.
- **30 Day Success Plan, Friday 10 am "Graduation" is intentionally grayed out and not clickable, every week.** It is there as a motivator, with the note "If you are ready to graduate this Friday, please let Vickee know by Thursday at 3 pm PST." Do not add a link or unlock it unless the user asks. Also on the Success Plan, Vickee's Thursday call ("Success Mindset & Time Management", Thu 9 am PST) was removed on Oct 22, 2026; do not restore it unless the user asks.
- **Success Plan office hours (changed Oct 23, 2026).** The Success Plan's Tuesday 8 am and Thursday 8 am calls (formerly "Implementation Class and Q&A" and "Video Breakdown") are both named "Success Plan Office Hours" and keep their links. Friday's 7-8 am Office Hours was removed. Monday's Success Plan Office Hours is 12:00-1:30 pm PST, with the badge "First 30 minutes exclusive to Success Plan students" (changed Oct 25, 2026); the shared portion (12:30-1:30) is shown on the Mastery calendar as Monday Office Hours 12:30-1:30 pm PT. Elite shows the same Monday Office Hours 12:30-1:30 pm PT as Mastery. The Success Plan Monday call uses the same Zoom link as the Mastery/Elite Monday Office Hours (`…j/86844179805`).
- **Power Hour with Vickee (added Oct 23, 2026):** 9:00 am, link `https://us06web.zoom.us/j/85181544892` (same room as Vickee's other calls). It is on the Fridays of all 9 calendars, and on Wednesdays too on the 30 Day Success Plan only. The Wednesday one was removed from Boss and AI Mastermind on Oct 28, 2026; do not re-add it there unless the user asks. Blue card; time label follows each file's style (PST on Boss, AI Mastermind and Success Plan, PT elsewhere).
- **Announcements:** Boss and AI Mastermind have an Announcements spot at the top of the page, above the Reminder. To add one, copy an entire `<div class="cwk-announce">...</div>` block and edit the text. Newest goes first. Ask which page(s) it should go on.

## Temporary / one-off items

Memory does not carry between people or computers, so track anything dated here. When you add a one-off item (holiday closure, special event, dated announcement), add a line below. When you remove it, delete the line. If a date below has passed, tell the user it is ready to remove.

- **Temporary Wednesday Boss Training link, week of Oct 19, 2026 only.** For Wed Oct 21 the Boss Training call (Boss + AI Mastermind) uses `https://us06web.zoom.us/meeting/register/Qt5TdMyJR9CwXyzsJ6UYow`. After Oct 21, tell the user it is ready to switch back, and replace that link with the original `https://us06web.zoom.us/meeting/register/LxdyHKZWTqG7dDr0asiMug` on both the Boss and AI Mastermind calendars. NOTE: on Oct 19 Dina also pointed AI Mastermind.s Monday 9 am "Mastermind Coaching Call" at the same Boss Training link, so it currently uses the temporary link too. Ask the user whether that Monday call should switch back with Boss Training before changing it. The Wednesday Mastery Coaching Call (Elite + Mastery) was NOT changed and keeps its normal link.
- **Magazine Skill Follow-Up with Doug: every Friday for a couple of weeks, starting Fri Oct 23, 2026** (11:00 am PST). It shows as the Friday "Magazine Skill Follow-Up" call (link `…register/L8KgnZtuS-a6VeoyLw4WHA`) and as a pinned announcement at the top of Boss + AI Mastermind. The original Nov 6 date was dropped on Oct 20 when the start moved up to Oct 23. The last session date was not given: ask the user, and remove both the Friday call and the announcement after the final session.
- **Mashore Method Office Hours links expire Nov 6, 2026.** The current M/T/Th 9-10 am link (`…j/82553606438`) and Friday 1-2 pm link (`…j/87217563574`) are on Elite, CAB, AI CAB, AI For Agents, KMO, Mastery and Boss (Boss shows them as "Mashore Method Office Hours", Mon/Tue/Thu 9-10 am PST and Fri 1-2 pm PST; AI Mastermind does not have them). New links will be sent after Nov 6; replace every occurrence when they arrive (the AI Mastermind "Mashore Method Support Office Hours" use different links and are not part of this). From Nov 6 on, remind the user these links are expired.
- **Team retreat announcement on the 30 Day Success Plan, Tue-Fri Nov 10-13, 2026.** A yellow card at the top of the page (above the Reminder) says "Tuesday-Friday, November 10-13: Our team will be away for a team retreat, training, and planning!" Remove it after Nov 13, 2026. The calls in those four days were NOT changed; ask the user if any should be changed or removed for the retreat week. (This page's announcement card is a plain `cwk-announce` with one line of text and no heading, unlike the Boss and AI Mastermind ones.)
- **TEMPORARY "Summit Skill Competition" on Boss + AI Mastermind (added Oct 23, 2026).** Monday 9:00-10:00 am (formerly Mastermind's "Mastermind Coaching Call" on AI Mastermind) and Wednesday 9:00 am (formerly "Boss Training") both use `…register/Qt5TdMyJR9CwXyzsJ6UYow` and are named "Summit Skill Competition" on both calendars. EXCEPTION (Oct 25, 2026): on AI Mastermind only, the Monday call is titled "Special Mastermind Call for the Summit Skill Competition Part 2" so students know it is their Mastermind call; Wednesday stays "Summit Skill Competition". When restoring, Monday goes back to "Mastermind Coaching Call". The user did not say how long it lasts: ask, and then restore the names ("Mastermind Coaching Call", "Boss Training"). The Wednesday link was already the temporary Boss Training link (first item above); the original is `…register/LxdyHKZWTqG7dDr0asiMug`. Ask the user which links to restore.
- **Book Club is off the calendars for now.** The regular Tuesday "KMC Book Club" was removed on Oct 5, 2026, and the one-off "KMC Book Club - The Thinking Effect" placeholder (Wed Oct 28) was removed from all 9 calendars on Oct 21, 2026, because the boss is deciding the future and best time for Book Club. Do not add any Book Club back unless the user says so.
- **KMC Student Panel Call on the 30 Day Success Plan, Thu Nov 5, 2026, 9:00 am PST.** It is a locked placeholder (grayed out, no link, badges "Thu, Nov 5" and "Locked until Nov 5") so students can not join yet. The user first said Nov 5 but also wrote Nov 9 in the same message; Nov 5 (a Thursday) was used. Confirm the date, add the real link when it is sent, and unlock it (make it a clickable link and drop the "Locked" badge) on the day of the call. Remove it after the call unless it repeats.

## Creating a new calendar

Copy the simplest similar file (`boss-support-calendar.html` is a good template), then change the `<title>`, the `<h1>`, and the calls. Use a descriptive filename like `<name>-support-calendar.html`. After it is pushed, the page is live at the URL pattern above. Give the user the embed snippet for GHL, and add the file to the table in this document.
