# ShiftMe — Product Requirements Document

**What it is:** an app that finds out what's actually draining a working mom by collecting the small annoying things as they happen, then showing her the six real reasons underneath them — ranked by how OFTEN they hit, not how loud they are.

**Who it's for:** employed mothers, roughly 30–45, burned out, capable, with zero uninterrupted time.

**The one-sentence promise:** "I'm exhausted" becomes "I never get one uninterrupted hour" — and the second one you can fix in a week.

---

## The rule that drives every decision

She does not have 45 free minutes. Not tonight, not Saturday, not ever. That's literally her biggest problem.

So the app never asks for a long sitting. It collects in five-second bites all month, then hands her a nearly-finished list to edit. Editing when tired is easy. Creating when tired is impossible.

**If a feature needs more than 3 minutes of her attention at once, it goes to a later phase or gets cut.**

---

## Core features (the full list, before we cut it down)

1. **The Friction Button** — one tap, speak or type one line: "that just cost me something." Five seconds, in the car, in the hallway.
2. **The Pile** — everything she's captured, with the date and time on each one.
3. **The Monthly Run** — the app groups her captures into 6-ish "real reasons" (mechanisms) and she confirms or fixes them.
4. **The Flip** — each real reason turned into what she actually wants.
5. **The Friday Test** — one yes/no question a week: did the thing happen?
6. **The Count** — the app counts how often each reason showed up. This is the part a paper worksheet can never do.
7. **The Top Three** — this month's changes, on her phone's home screen.
8. **Run History** — after several months, "this reason has shown up every single time." That's the structural one.
9. **The Ask** — turns a reason into one sentence she can send to her husband or her boss, because most of her fixes need someone else to agree.
10. **Accounts and private storage** — her list is the most private thing on her phone. It has to be locked down.

---

## Phased roadmap

### PHASE 1 — THE FOOD STAND (build today)

*A food stand sells one thing, and it's good. No menu, no seating, no staff.*

**One screen. One button. That's the whole app.**

She opens it, taps the big button, types or speaks one line, and it's saved to a list she can scroll. Nothing else exists yet — no accounts, no cloud, no AI.

**What we build:**
- A single screen with a large "That just cost me something" button
- A text box that opens when she taps it, and a Save button
- The saved lines listed underneath, newest first, each with a date
- Saved on the phone itself (no internet needed)

**Why this first:** if she won't tap the button, nothing else in this document matters. This is the cheapest possible way to find that out. It also produces the raw material every later phase depends on.

**Done when:** you can tap, type, save, close the app, reopen it, and your list is still there.

**Testing, in this order:**
1. App opens with no red error screen
2. Button opens the box; Save adds the line to the list
3. (No internet calls yet — nothing to test)
4. (No accounts yet — nothing to secure)

---

### PHASE 2 — THE SMALL RESTAURANT (week 2–3)

*Now there are tables, a short menu, and someone remembers your order. Still one person in the kitchen.*

She gets an account so her list follows her between phones, and the app starts giving something back instead of only taking.

**What we add:**
- Sign up / log in (already wired in this codebase via Supabase)
- Her captures save to the cloud, private to her
- **The Monthly Run:** after ~20 captures, a button appears — "You've got 23. Ready to see what's underneath?" It walks her through grouping them into about six real reasons. Phase 2 does this by hand: she drags similar ones together and names the group.
- **The Flip:** for each group, one line — what she wants instead
- **The Friday Test:** she writes one checkable thing per top reason; Friday, the app asks yes or no

**Why now:** Phase 1 proves she'll capture. Phase 2 proves the payoff is worth having — grouping her own mess into six named reasons is the moment people describe as the lights coming on.

**Done when:** she can go from 20 loose captures to three written changes without leaving the app.

**Testing, in this order:**
1. Every screen opens with no errors, signed in and signed out
2. Every button and form works — sign up, save, group, name, check off
3. Real internet calls work — sign out, sign back in on a different phone, her list is there
4. Security — sign in as a second test user and confirm you cannot see the first user's list. This is non-negotiable before anyone real uses it.

---

### PHASE 3 — THE FULL RESTAURANT (month 2+)

*Front of house and back of house. Specials. Regulars who come back every month.*

The app stops being a notebook and starts knowing things she doesn't.

**What we add:**
- **The Count** — the app counts each reason's captures and ranks by frequency, then tells her the uncomfortable truth: *"You logged this 14 times in three weeks. The thing you called your biggest problem, you logged twice."*
- **AI grouping** — instead of dragging by hand, the app proposes the six reasons and she corrects them. Cuts the monthly run from 45 minutes to about 12.
- **Home screen widget** — her three changes, where she'll actually see them
- **Run History** — "this reason has appeared in all six of your runs." The structural ones.
- **The Ask** — one sendable sentence per reason
- **Paid plan** — free is capture plus one run; paid is the counting, the history, and the comparison across runs. We charge for the memory, not the exercise.

**Why last:** every one of these needs months of her real data to be worth anything. Building them in month one means building them against fake data and guessing wrong.

**Testing, in this order:**
1. Every screen loads clean, including with zero captures and with 500
2. All buttons and forms work, including payment
3. Real calls work — AI grouping, payment provider, widget refresh
4. Security — payment handled by the provider so card numbers never touch us; re-check that no user can reach another user's data; her captures are the most private thing on her phone and must be treated that way

---

## What we deliberately will NOT build

These will kill it with this audience:

- **Streaks.** One broken streak and she uninstalls. She already has plenty of evidence she's failing.
- **Mood tracking / gratitude prompts.** She's been handed these and they didn't work. That's why she's here.
- **A community feed.** She does not want to read other people's problems.
- **Push notifications beyond the Friday question.** Missing a week must be silent and free.

---

## How we'll know it's working

- **Phase 1:** does she tap the button more than 3 times in her first week?
- **Phase 2:** does she finish a run and write three changes?
- **Phase 3:** does she come back and run it a second month? That one is the whole business.
