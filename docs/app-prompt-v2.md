# APP PROMPT V2 — Aliveness Map (MVP)

Rewritten from the Brand Brief, scoped to an MVP, incorporating the review in
`docs/aliveness-map-review.md`.

---

## How to use this

**Recommendation: start a new Rork project with Prompt 1 rather than iterating on
`comealive.rork.app`.**

V1 was a ~2,000-word first prompt covering ten surfaces. Rork builds best from one
focused flow and gets progressively harder to steer as the surface area grows — a
bloated first prompt is the most common cause of an app that resists iteration.
The V2 changes are structural (different core loop, different completion flow,
three screens deleted), so steering the existing build there costs more prompts
than rebuilding the base.

Keep the old project. Clone it if you want the design language as reference.

Then paste the prompts **in order, one at a time**, testing between each. Do not
paste Prompt 1 and Prompt 2 together — the queue exists to protect the base.

---

## One decision to make before Prompt 1

V1 said "mobile-first web app" but you built on Rork, which produces a real
mobile app. Pick deliberately:

- **Rork Pro / Expo** — iOS + Android from one codebase. Correct default here.
  Everything in this spec is standard app surface: forms, lists, a calendar date,
  local notifications.
- **Rork Max / Swift** — only worth it if you later want a home-screen widget
  showing "your experiment this week," or Live Activities. Neither is MVP.

**Go Pro/Expo.** Nothing in this MVP needs native iOS.

---

## What changed from V1, and why

| V1 | V2 | Why |
|---|---|---|
| Core concept framed around "one unavailable source of love, intimacy, validation" | Deleted entirely | Different customer than the brief's. Governed the whole V1 build. |
| DESIRABLE = "attractive, magnetic, expressive, **noticed, chosen**, confident" | DESIRABLE = "expressive, magnetic, confident, unhidden — as *I* experienced it" | The brief names desirable as one of the four, so the word stays. But "noticed/chosen" scores her by other people's verdict, inside a product about a woman who lost herself organizing around other people. |
| Home screen centred on rating + reflecting | Home screen centred on **scheduling the next experience** | The brief's own argument: the bottleneck is doing, not knowing. She can already list what makes her come alive (V1 asks her to, in onboarding). She isn't doing it. |
| 4 × 1–10 sliders as the primary capture | "Would I do this again even if nobody knew?" as the primary capture | Your own note said this question is extremely important. It is — it's binary, fast, honest, and it strips external validation. Sliders demand 10-point resolution nobody has, at the moment her energy is lowest. |
| Daily check-in (3 questions) + home reflection box | One optional line, post-experience only | ~120 reflection inputs vs ~8 experiences over 30 days is ten times more thinking than living — the enemy the brief names, with a UI. |
| 1 experience per week in **each** of 4 areas (≈17/month) | 1 experience per week | 4/week is impossible for a woman with no unclaimed time, and setting a target she'll miss is not a no-shame product. |
| 2D interactive Aliveness Map | Ranked evidence list | ~9 items across 4 dimensions reveals nothing a sorted list wouldn't. Most expensive screen, least information. Build it when a real user says the list isn't enough. |
| Onboarding collects her guesses, never uses them | **Day 30 reveals guess vs. evidence** | This is the brief's entire thesis returned to her in her own data. You already collect both halves. |
| Experiments Library as a browsable tab | A "give me ideas" sheet inside the scheduler | It's a unblocking tool, not a destination. As a tab it becomes another place to browse instead of act. |
| 30 days promises "THIS IS WHAT YOU LEARNED" | 30 days promises proof she can act | At 6–10 data points, the bigger promise can't be kept. |
| Product COME ALIVE / app ALIVENESS MAP / 3 taglines | **Aliveness Map** / "Live your way back to yourself" | Concrete, ownable, searchable. Best line in the brief. |

---

# PROMPT 1 — The core loop

> Paste this into a new Rork project. Build nothing else until this works.

```
Build a private, mobile-first app called ALIVENESS MAP.

Tagline: Live your way back to yourself.

TARGET USER
A woman in her 40s or 50s who has built a full life around being needed —
mother, partner, professional — and feels disconnected from who she is outside
those roles. She is not unhappy. She is not in crisis. She has a good life and
doesn't feel like herself in it.

THE IDEA THE APP IS BUILT ON
You cannot think your way back to yourself. You have to live your way back.
She already knows how to reflect. What she doesn't do is act. So this app is not
a journal and not a tracker — it is a lab notebook for running small experiments
on her own real life and collecting evidence about what makes her feel like
herself.

Every design decision should resolve toward one question:
"Did this app get one real experience onto her calendar this week?"

CORE FUNCTION — build this flow and nothing else yet

1. HOME
   The whole screen answers one question: what's my experiment this week?

   If nothing is scheduled, the screen is mostly empty and says:
     "What will you try this week?"
     [ Plan an experience ]
   Do not offer a text box here. There is nothing to write about yet.

   If something is scheduled, show it large and calm:
     the experience name, the day, and [ I did it ].
   Below, small and quiet: "Week 2 of 4" and the count of experiences so far.

2. PLAN AN EXPERIENCE
   Three fields, one screen:
   - What will you try?  (free text)
   - When?  (a real date, defaulting to the next 7 days)
   - Optional: "I want to see whether this makes me feel..." — she can tap any
     of the four dimensions below.

   Include a small link: "I don't know what to try." Tapping it opens a sheet of
   eight prompts she can tap to prefill the name field:
     MOVE — a physical challenge, something that asks your body to show up.
     CREATE — make something with no requirement that it be useful.
     EXPLORE — go somewhere unfamiliar.
     CONNECT — time with someone who energises you.
     EXPRESS — wear, dance, speak, perform, photograph, show yourself.
     PLAY — something with no productive purpose at all.
     COURAGE — something slightly scary you've been postponing.
     SENSORY — water, music, food, nature, art, beauty, touch.
   These are provocations, not prescriptions. Never rank or recommend them.

3. CAPTURE — what happens after [ I did it ]
   This is the most important screen in the app. It must be completable in two
   taps by a tired woman at 10pm.

   Question 1, large, alone on the screen:
     "Would you do this again even if nobody knew you did it?"
     [ YES ]  [ MAYBE ]  [ NO ]

   Question 2:
     "What did it give you most?"
     Pick one:
     DESIRABLE — I felt expressive, magnetic, confident, unhidden.
     CAPABLE — I felt competent, strong, courageous, able.
     ALIVE — I felt curious, playful, energised, awake, present.
     EMBODIED — I felt in my body instead of in my head.
     (Definitions matter: all four are how SHE felt, never how she was received.
     Never use the words "noticed" or "chosen".)

   Question 3, clearly optional and skippable:
     "What surprised you?" — one line of text.

   Then: "You're collecting evidence." and a single button [ Plan the next one ].
   Never end this flow on a dead end.

4. EVIDENCE
   A second tab. Not a chart, not a dashboard, not a graph.
   A list of everything she has done, newest context but ordered by signal:
   the YES answers first, then MAYBE, then NO. Each row shows the experience
   name, its dimension, and her surprise line if she wrote one.
   Let her filter by the four dimensions and by Yes / Maybe / No.
   At the top, one plain sentence, no styling tricks:
   "So far, X of Y experiences were ones you'd do again."

DESIGN
Mood: warm, spacious, unhurried. Premium and quiet.
It should feel like something between a private journal, a personal laboratory,
and a beautifully made field guide. Generous whitespace. Serif for the questions
she is asked, clean sans for everything else. Typography and space should make
reflection feel important without demanding much of it.

Avoid entirely: corporate productivity aesthetics, health-dashboard visuals,
progress rings, badges, trophies, streaks, confetti, red warning states, and any
gamification. If she misses a week nothing turns red and nothing breaks.

Make it feel alive: smooth transitions between screens, buttons that respond to
touch, the capture flow moving question to question with a gentle animation.
Prioritise polish and smoothness over adding anything.

TONE
Warm, direct, adult. Never clinical, never chirpy, never therapeutic-jargon.
Never tell her something is wrong with her. Her roles are not the problem — the
premise is that those roles can coexist with a self that still has to be
actively discovered.
Empty and inactive states are compassionate and unpressured, e.g.
"Your experiment is still here when you're ready."

TECHNICAL
- Auth with private per-user accounts. Her data is visible only to her.
- Persistent storage; create, edit and delete experiences.
- Structure the data model so a user can later run more than one 30-day round,
  and so dimensions could later be customised. Do not build either yet.

SCOPE — do not build any of this yet
No daily check-in. No home-screen journal box. No 1–10 sliders. No visual or
2D map. No photos. No weekly review. No manifesto. No social or sharing. No AI.
No notifications. Keep it to the flow above and make that part excellent.
```

---

# PROMPT 2 — Onboarding and the guess

> Only after Prompt 1's loop works end to end.

```
Add a short onboarding flow, shown once before the home screen.

Screen 1
  What makes you come alive?
  You don't have to figure it out today. For the next 30 days you're going to
  experiment with your own life.
  [ Begin my experiment ]

Screen 2
  Four things we're paying attention to. Keep it brief and unhurried.
  DESIRABLE — I feel expressive, magnetic, confident, unhidden.
  CAPABLE — I feel competent, strong, courageous, able to handle something hard.
  ALIVE — I feel curious, playful, inspired, energised, present.
  EMBODIED — I feel in my body rather than in my head.
  [ Continue ]

Screen 3 — this one matters, store the answer permanently
  "Before we start: what do you already suspect makes you feel more alive?"
  She can add as many entries as she likes, free text, custom entries always
  allowed. Show a few faint examples that clear on typing and are never
  presented as options to pick from: creating something, swimming, dancing,
  deep conversations, being somewhere new, music, learning something, dressing
  well, being playful.

  Save these as HER HYPOTHESIS. Never show them again during the 30 days —
  they are not a to-do list and must not become one. They are used once, at the
  end.

  [ Start day 1 ]

Then land her on the home screen with nothing scheduled and the prompt to plan
her first experience.
```

---

# PROMPT 3 — Weekly nudge

```
Once every 7 days, show a single quiet screen when she opens the app.

  YOUR WEEK
  Show the one or two experiences she completed, each with the dimension it gave
  her and whether she'd do it again. If she completed none, say only:
  "No experiments this week. That happens." — nothing more.

  Ask exactly one question:
  "What do you want more of next week?"  (one line, skippable)

  Then: [ Plan next week's experience ] going straight into the planner.

One experience a week is the whole target. Never ask for more than one. Never
show a streak, a completion percentage, or a missed-week indicator.
```

---

# PROMPT 4 — Day 30: the reveal

> This is the payoff screen. Build it carefully.

```
At the end of the 30 days, show a slow, deliberate final sequence — one idea per
screen, tapping to advance.

Screen 1
  "Thirty days ago you guessed."
  Show HER HYPOTHESIS from onboarding, exactly as she wrote it.

Screen 2
  "Here's what actually happened."
  Show the experiences she'd do again even if nobody knew, ordered by dimension.

Screen 3
  "You were right about..." — the overlap between her guess and her YES answers.
  "And you didn't expect..." — her YES answers that weren't in her guess.
  If there's no overlap either way, say so plainly and warmly. Don't force it.

Screen 4
  Her strongest source of each: DESIRABLE, CAPABLE, ALIVE, EMBODIED.
  Where there's not enough evidence for one, say "not enough evidence yet" —
  never invent a result from a single data point.

Screen 5
  "Five things worth repeating." Her five YES experiences.

Screen 6
  One question, saved: "What are you no longer willing to abandon?"
  [ Start another 30 days ]

The tone here is evidence, not celebration. No confetti, no score, no grade.
The point she should feel is: you didn't think your way to this, you lived it.
```

---

# PROMPT 5 — Privacy, then polish

```
Add a Settings screen with:
- Export all my data (her experiences, answers and reflections, as a file)
- Delete my account and everything in it, permanently, with one confirmation
- A short plain-English line: "This is private. Only you can see it. It is never
  used to train anything and never shared with anyone."

Then a polish pass across the whole app: consistent spacing and type scale,
smooth transitions everywhere, responsive touch feedback on every button, and
correct behaviour on small phones. Prioritise the feel of the capture flow above
everything else — that's the screen she'll use most.
```

---

# PROMPT 6 — One reminder, only if you want it

```
Add a single weekly local notification, on a day and time she chooses in
Settings, defaulting to Sunday evening:
"What will you try this week?"

That is the only notification the app ever sends. No daily reminders, no nudges
about missed experiences, no re-engagement messaging.
```

---

## Deliberately not in the MVP

Keep this list — it's the queue, and the reason to leave things out is that
they're not free.

- **The visual Aliveness Map.** Earn it with data volume. Revisit if a real user
  at day 30 says the list isn't telling her enough.
- **1–10 sliders on four dimensions.** If you want intensity later, add a single
  optional 1–5 on the *one* dimension she picked. Not four.
- **Daily check-in.** If you ever add it back, the only question worth keeping
  is "what am I craving right now?" — the other two point backward.
- **Photos, the manifesto, multiple rounds, custom dimensions, sharing with a
  therapist or partner, AI pattern recognition.** All post-MVP. The data model
  in Prompt 1 leaves room for the last three.

---

## Two things this prompt still can't fix

**The app assumes she'll do the experiments.** Nothing in a build de-risks that,
and it's the assumption the whole business rests on. Before you spend more
prompts here: five women, one group thread, 30 days, you sending the weekly
question by hand. If four of five schedule something in week one, the app is
worth building out. If two do, the bottleneck is permission, not tooling, and the
product is a different shape.

**Nothing here decides what Aliveness Map is commercially.** A single-player app
that ends after 30 days has churn designed into it — Prompt 4 ends on "start
another 30 days" precisely because of that, but a second round isn't a business
model. Whether this is a free wedge into a cohort, a paid app, or the artifact
attached to a content channel changes what gets built next. Decide it before
Prompt 7 exists.
