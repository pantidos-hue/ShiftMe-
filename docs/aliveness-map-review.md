# Review — Brand Brief + App Prompt V1 (Aliveness Map / Come Alive)

Reviewed: the Google Doc containing the Brand Brief, App Prompt V1, and Appendix.
Scope: strategy, positioning, product spec, and internal consistency. No code review —
the prototype lives on Rork, not in this repo.

Verdict up front: **the brand brief is strong and the app spec is a different product.**
The brief is sharp enough to build a business on. The build prompt drifts into a
different customer and a different emotional problem, and it commits the exact sin the
brief names as the enemy. Most of the fixes below are subtractive.

---

## 1. The biggest problem: two different customers in one document

**Brand brief PERSON:** a woman in midlife who built a full life around being needed and
feels disconnected from herself inside it. Her problem is *identity*.

**App prompt CORE CONCEPT:** "The user is currently trying to avoid defining their
wellbeing around one unavailable source of love, intimacy, validation, or connection.
The goal is NOT to replace that person."

That is not the same woman. That is someone decentering a specific unavailable person —
an *attachment* problem, closer to limerence or a stalled relationship than to role-loss.
The two overlap in the Venn diagram but they buy differently, they search differently,
they respond to different language, and they need different products.

This reads like a private situation leaked into the product spec. It matters because it
has already shaped the feature set (see §2), and because an AI builder took that CORE
CONCEPT paragraph as the governing frame for everything downstream.

**Fix:** delete the unavailable-person framing from the app spec entirely, or commit to
it and rewrite the brief. Don't ship both. My recommendation is to keep the brief — the
midlife identity market is larger, more defensible, less shameful to admit to, and the
"roles can coexist with a self" line at the end of Content Direction #1 is the most
commercially valuable sentence in the document.

---

## 2. "DESIRABLE" is the wrong fourth dimension

Three of your four dimensions are self-referenced: capable, alive, embodied. Those are
measured from the inside.

DESIRABLE is defined as *"attractive, magnetic, expressive, noticed, chosen, or
confident."* **Noticed** and **chosen** are other-referenced. They require an audience
issuing a verdict. You have built a metric whose score is set by other people, inside a
product whose entire thesis is that she stopped knowing herself because she organized
around other people's needs.

It's also the clearest residue of the unavailable-person concept from §1.

**Fix, in order of preference:**
1. Replace it. **EXPRESSIVE** ("I showed up as myself, visibly") or **FREE** ("I did what
   I wanted without asking") both fit the brief and stay self-referenced.
2. Or keep the word, strip the audience: "expressive, magnetic, confident, unhidden" —
   delete *noticed* and *chosen*.

If you keep "noticed/chosen," expect a predictable failure mode: users score high on
desirable after events where they got attention, and the app teaches her that aliveness
comes from being seen. That is the disease, sold back as the cure.

---

## 3. The app violates its own enemy

The enemy is **overthinking your way back to yourself**. The big idea is that you can't
think your way there. Then count the introspection the app demands:

| Surface | Reflective prompts |
|---|---|
| Home screen | 1 daily ("what made you feel most alive today?") |
| Daily check-in | 3 |
| Complete an experience | 4 sliders + "what surprised me?" |
| Weekly review | 3 |
| 30-day final review | 5 + a manifesto |

Over 30 days that is roughly **120 reflection inputs against maybe 8–12 actual
experiences**. Ten times more thinking than living. The ratio is inverted against the
thesis.

Worse, the home screen's default action after the primary button is a *text box*. On any
day she hasn't done anything, the app gives her a place to journal about it. That is
"months thinking about herself without experiencing herself differently," with a UI.

**Fix:** the daily check-in and the home reflection box are the same feature twice —
delete one. Cut the check-in to one question ("what am I craving right now?" is the only
one of the three that points at *future action*; the other two point backward). And make
the empty state of the home screen a scheduling prompt, not a writing prompt.

---

## 4. The instrumentation will produce noise, not evidence

Four 1–10 sliders, filled in immediately after an experience, at the moment her energy is
lowest and her willingness to fiddle with a UI is at its minimum.

Three problems:
- **No one has 10-point resolution** on "how embodied did I feel." The difference between
  a 6 and a 7 is mood, not signal. You will collect 40 numbers that all cluster between 6
  and 8 and then draw a map of them.
- **False precision feeds a false map.** Averaged 1–10 scores on n=9 experiences look
  quantitative and mean nothing.
- **Four sliders is four decisions** at the worst possible moment for decisions.

Meanwhile the doc contains the single best question in the whole product and then buries
it below the sliders:

> **"Would I do this again even if nobody knew I did it?"**

You even wrote "This question is extremely important." You're right, and it deserves to
be the spine, not the footnote. It's binary, it's fast, it's honest, it strips external
validation (which is exactly the correction §2 needs), and it's the only input here that
would survive contact with a tired user at 10pm.

**Fix:** lead the completion flow with that question. Then one forced choice — "which did
this give you most?" (pick one of four) — and an optional line of text. Two taps. Drop
the sliders to 1–5 if you keep them at all, and make them skippable. You will get *more*
usable data from less instrumentation, because the completion rate will be far higher.

---

## 5. Internal contradiction: the accountability target is impossible

The spec says: encourage **at least 1 experience per week in each of the four areas.**
That's 4 experiences per week, ~17 in a month, for a woman whose defining problem is that
she has no unclaimed time. Then two lines later: no shame, no streaks, no punishment.

You have set a target she will miss in week one and then told the UI to be nice about it.
That's not a no-shame product — that's a product that generates shame and then applies a
gentle voice to it. She'll notice.

**Fix:** one experience per week. That's it. 4–6 over the container. If she wants more,
she'll do more; the app should never ask for the fourth.

---

## 6. 30 days is probably the wrong container

At a realistic cadence of 1–2 experiences a week — these are dance classes, art openings,
dinners, swims, things that need scheduling around a family — 30 days yields 6–10 data
points. That is not enough to reveal a "pattern," populate a "map," or support a "final
review" titled THIS IS WHAT YOU LEARNED. The product will over-promise and under-deliver
at exactly the moment it's asking her to renew, recommend, or pay.

Also: a fixed 30-day container is a deadline, and a deadline is a thing you can fail. That
sits badly next to the no-shame principle.

**Fix — pick one:**
- **Extend to 90 days**, with the 30-day review demoted to a checkpoint. More honest data,
  but a much bigger commitment to ask for on day zero.
- **Keep 30 days but change what it promises.** Don't promise the answer. Promise the
  *proof that she can act*: "In 30 days you'll have done six things you'd been putting
  off, and you'll know which one you'd do again." That's deliverable at n=6. The pattern
  discovery is what the second container is for — which conveniently gives you a reason
  for her to continue.

I'd take the second. It's the honest version of the promise and it creates the retention
mechanism you currently don't have (§8).

---

## 7. The Map is the most expensive screen and the least informative

A 2D interactive visualization of nine items with four dimensions each reveals nothing a
sorted list wouldn't. It will look impressive in a screenshot and be useless in the hand.
It's also the single hardest thing in the spec to build well.

**Fix:** cut it from the MVP. Replace with a ranked list — "would do again" at the top,
sorted by which dimension it fed. Build the map only if a real user, at day 30, says the
list isn't telling them enough. Right now the map is a designed answer to a question no
one has asked yet.

---

## 8. There is no reason to open the app on a normal Tuesday

The core loop as specified is *record → reflect → discover*. But recording only happens
after an experience, and experiences are weekly at best. On the other six days, the app
offers journaling. Journaling apps have famously bad retention, and this user's stated
problem is that she already ruminates.

The missing loop is the one your own brief points at: **her bottleneck is not knowing what
would make her feel alive — it's giving herself permission to put it on the calendar.**
Screen 3 of onboarding proves you know this: she can already list what she suspects makes
her come alive. She just isn't doing it.

**Fix:** make the app's job "get one thing on the calendar this week," not "record how you
felt." That means: a scheduling nudge as the primary recurring interaction, a real date
with a real reminder, and the Experiments Library surfaced *when she's stuck picking*, not
as a browse-anytime tab. The reflection is the exhaust of the product, not the engine.

---

## 9. The best feature in the doc is unbuilt, nearly free, and you're one line from it

Onboarding Screen 3 collects: *"what do you already suspect makes you feel more alive?"*
Then that list is never mentioned again.

Close the loop at day 30:

> **You guessed:** deep conversations, travel, art.
> **The evidence says:** swimming, building things, dancing.
> **You were right about:** deep conversations.

That is the entire thesis of the brand — you can't think your way there, you have to live
your way there — delivered as a single screen of the user's own data. It's the emotional
payoff, it's the shareable moment, it's the proof the product worked. It costs almost
nothing to build because you already collect both halves.

If you implement one thing from this review, implement this.

---

## 10. Naming is fragmented

In one document: product **COME ALIVE**, app **ALIVENESS MAP**, URL `comealive.rork.app`,
plus three taglines and a separate one-liner:

- "Cure self-loss. Feel like yourself again."
- "Live your way back to yourself"
- "Stop waiting to feel alive. Collect evidence about what makes you come alive."
- One-liner: "A daily experiment to discover what makes you come alive."

**Recommendations:**
- **Name: Aliveness Map.** It's concrete, ownable, and searchable. "Come Alive" is generic,
  competes with a thousand wellness brands, and is unsearchable. (Caveat: if you cut the
  map screen per §7, the name needs to survive on metaphor alone — it can, "map" here
  means the thing she's drawing of herself.)
- **Tagline: "Live your way back to yourself."** It's the best line in the document. It
  contains the thesis, the enemy, and the promise in six words.
- **Kill "Cure self-loss."** Medicalized, clinical, and tonally at war with the warm,
  spacious design direction three sections later. It also frames her as sick.
- Also: "ONE LIGNER" → "ONE-LINER."

---

## 11. Missing sections the doc needs before more building

**Business model — entirely absent.** Nothing on price, or on whether COME ALIVE is an
app, a cohort, a coaching container, or a book. This matters structurally: a single-player
app that *ends after 30 days* has terminal churn designed into it. The likely shape is
that the app is the free wedge and the money is in a cohort or coaching — but the document
should say so, because it changes what the app needs to do (a cohort version needs shared
experiments and a group; a solo app doesn't).

**Distribution — asserted, not planned.** The Content Philosophy section correctly says
distribution comes from attaching to desires people already have, then never names the
desire, the format, the channel, or the face. Note also the channel mismatch: the cited
source is a tweet, and midlife women are not on X. Instagram, YouTube, newsletter, and
podcast are where this audience is. Who's on camera?

**Riskiest assumption + how you'd test it — absent.** Your brief argues the bottleneck is
*doing*, not *knowing*. So the riskiest assumption is that she'll actually run the
experiments. No app feature de-risks that. Run it manually: five women, one WhatsApp
group, 30 days, you as the prompt. If four of five schedule something in week one, build.
If two do, the product problem is permission and the app is the wrong shape.

**Privacy — under-specified for the data you're collecting.** Free-text emotional
journaling, photos, and a future "share with your therapist or partner" feature. Your user
may be a married woman writing honestly about feeling unseen. For her, "private,
exportable, deletable, and never used to train anything" is not compliance boilerplate —
it's a *feature*, and it belongs on the landing page. The tech requirements list
"Authentication / Private user accounts / Persistent data storage" and stop there.

---

## What I'd actually do next

1. Strike the unavailable-person paragraph from the spec. One customer. (§1)
2. Redefine or replace DESIRABLE so all four dimensions are self-referenced. (§2)
3. Rebuild the completion flow around "would I do this again if nobody knew?" — two taps,
   sliders optional. (§4)
4. Cut the daily check-in to one forward-looking question; delete the duplicate home-screen
   reflection box. (§3)
5. Drop the weekly target to one experience. (§5)
6. Cut the Map screen from the MVP; ship a ranked list. (§7)
7. Build the guess-vs-evidence reveal for day 30. (§9)
8. Re-point the home screen at scheduling, not recording. (§8)
9. Run the manual five-woman version before building further.

Items 1–8 make the prototype smaller. That's the point — the current spec is roughly
twice the product it needs to be, and the half you'd cut is the half that contradicts the
brief.

---

## What's genuinely good, and worth protecting

- **The enemy is well-chosen and rare.** "Overthinking your way back to yourself" is a
  real, specific, non-obvious antagonist, and most wellness brands sell the opposite of
  what you're attacking. That's a defensible position.
- **"Those roles can coexist with a self that still needs to be actively discovered."**
  This is the line that makes the brand sellable rather than divisive. It doesn't ask her
  to resent her family. Keep it central.
- **"Would I do this again even if nobody knew I did it?"** The best question in the
  document by a distance. It's a validation-stripping mechanism disguised as a survey
  question.
- **Evidence over insight as the core mechanic.** Correct, differentiated, and it gives the
  product a reason to exist as software rather than as a book.
- **No streaks, no badges, no trophies.** Right call for this audience, and unusual
  discipline for a prototype.
