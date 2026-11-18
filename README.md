# Campus Stores

Campus Stores is a Product Engineer work sample set at a fictional campus media equipment desk. Work through a club’s screening, from equipment pickup to a partial return and the next morning’s handover. Open **Candidate brief** in the app for the assignment.

## Run the app

Open `index.html` in a modern browser. The app includes its scripts, styles, and icons and can run offline.

To serve it over local HTTP, run this from the repository folder and visit `http://localhost:8000`.

```sh
python3 -m http.server 8000 --bind 127.0.0.1
```

Each browser stores its own sample shift locally when browser storage is available. **Restart sample shift** restores the fictional starting records.

## Source

- `index.html` contains the desk layout, candidate brief, and bundled icons.
- `app.js` contains the sample records and interactions.
- `styles.css` defines the desktop and mobile layouts.

Icon license notices are in [third-party/lucide-LICENSE.txt](third-party/lucide-LICENSE.txt).


## My change: a "Still out" panel

**What I changed.** A panel under the shift banner, visible on every tab, listing every loan that is still out. Each row shows the unit, slip number, club and request, holder and due time. It says how far past due or how long until due, and the most overdue loan sorts first. Changes are in `app.js` (`outstandingLoans`, `outstanding`, a per-phase `at` time and a `dueAt` map), `index.html` (one `<section>`) and `styles.css`.

**Why.** On the Saturday 9:00 am handover I had to work out what was still out. That answer was spread across three places: an open slip in the Loan register (in Kabir's name), an "On loan" badge in Inventory, and a free-text Desk book note. Due times were plain strings (`"Fri 8 pm"`), so the app never flagged that the adapter was overdue.

**Same job, with the panel.**
- 3:45 pm: after issuing the kit, the panel shows everything out and due in 4 h 15 min.
- 7:30 pm: after returning the projector and speaker, it shows only the adapter, due in 30 min.
- 9:00 am: it opens with the adapter at the top, *Overdue 13 h*, plus the Debate Union microphone due in 1 h. I know what to look for before Leela speaks.

**What I kept.** One slip per physical unit and the approval checks at issue time. They are what stop the wrong item leaving the desk, so I only added visibility.

**Second small change: confirm the unit on return.** The two adapters (AD-12, AD-15) are identical and share bin C4, but "Record return" used to close a slip with one click and no check. Now it asks "Unit handed back", listing the same-type units with model and bin. If the unit picked doesn't match the slip, the app warns inline and keeps the slip open. The Saturday task is to "close the loan for the right item", and this is the step that checks it. The code is `returnForm()` and the `[data-return]` submit branch in `app.js`.

**What it does not solve.** The slip still names Kabir as holder although Leela has the adapter. Moving custody to her, so the panel shows who holds it now, would be the next change.

**How I would know it helped at a real counter.** Time how long an incoming shift takes to say what is outstanding, with and without the panel, and count how many tabs they open to check. For the unit check, count returns where the slip closed against a different unit than the one handed back, before and after.

**One thing that worked well.** *(Replace with your own evidence from your shift. For example: the issue form refused a unit outside the approved request, which stopped a wrong item leaving the desk.)*

## Submit your work

1. [Fork Campus Stores](https://github.com/virinchi-healthcare/campus-stores/fork) into your GitHub account. Complete the candidate brief and push your changes to your public fork. In your README, point reviewers to your work and explain the decision you made.
2. In your fork, open **Commits**, select the final commit you want reviewed, and copy the page URL. It should look like `https://github.com/YOUR-USERNAME/campus-stores/commit/COMMIT-SHA`.
3. [Submit your work through the Google Form](https://docs.google.com/forms/d/e/1FAIpQLScvzoh1R4WS-SkiwAVBQbMvniieJYSoOEfLMyVo5CyjOvYUgQ/viewform). Your **roll number**, **email ID**, and **final commit link from your public fork** are required. Enter your roll number and email ID in the form only.