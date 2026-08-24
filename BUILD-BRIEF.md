# Finneas — Ask prototypes for Round 4 research

**Josh is the reference build.** Copy `josh-ask.html` and replace its content. All five are built: Josh, Luke, Heather, Whitney, Chad. `compare.html` shows them side by side, stepping through together.

Field is Tue/Wed. Each participant gets a link and clicks through their own prototype while sharing their screen.

---

## What these are

Dumb-data click-through prototypes, one per participant, pre-filled with **that participant's own question and numbers from the previous research round**. No backend, no model calls — every word is written in advance. One self-contained HTML file each. Open in a browser, no build step.

They exist to test one thing: whether pacing the Ask response into steps, with interactive modules replacing some of the prose, preserves the sense of comprehensiveness that made the original valuable. Round 1 established that people found the output valuable *and* too long to read.

---

## The strategy — this is the part that matters

The two built prototypes follow a specific sequence. It is not "the same thing, but paced." Getting this wrong produces something that looks right and tests nothing.

**1. Entry.** The participant's real question, verbatim, sitting typed in the composer.

**2. An open, voiced question that asks nothing about money.** "Tell me a bit more about why this one's on your mind." The participant answers in their own words. Use their actual words from the session transcript — not a summary of them.

**3. The reframe, named back from what they said.** This is the value moment. Finneas states the question under their question and confirms it: *does that land right?*

The reframe must be **earned, not asserted**. Finneas guessing a motive from collected data and handing over a theory is the failure mode — it was explicitly rejected in an earlier build review. The user says why first; Finneas names it second.

The reframe must come from what the person actually wants, which is usually not what they asked about. Luke asked how to afford a bigger house; he wants an acre outside the Portland city limits. Heather asked how to save for a car; she wants to know where the money comes from while she's still paying down debt.

Where the person has two goals, braid them. Heather's reframe names Nolan's fund *and* her debt-free date, because they run on the same money.

Where the person has a coping strategy, affirm it. Heather hides money from herself; the reframe says that's the right call, not a workaround.

**4. The motive routes the intake.** Finneas says outright that the reframe changes what it needs to ask, then asks fewer questions than the original did. **One block, numbered straight through** — if the original asked a second round of questions later, fold them into the same block rather than running a separate sharpening stage; it is the same process — five instead of ten for Luke, four for Heather. Each question carries a one-line rationale: *why I'm asking this.*

**5. A priority is created mid-conversation**, as a toast, right after the reframe is confirmed. "Started a priority for you — [name]. Nothing is saved until you say so."

**6. Work happens during intake.** Insights arrive between questions — "Working while you answer" — rather than the product going silent for six turns. This is switchable: see the laced/held toggle below.

**7. The answered set, editable.** A recap of everything they said, with Edit on each row, before any math runs.

**8. The analysis, paced.** Each beat advances on a click. Modules replace prose wherever the original was carrying numbers in a paragraph. Aim for five or six analysis beats, not thirteen — Josh went from eighteen beats to eleven and lost nothing.

**9. The Math.** Prose plus at most one reference table. No controls, no result card. **Same three moves for everyone: the answer, what is working in their favour, and the one thing that would change the order.** State the answer as a figure in the first line — do not open on mechanics or on how a thing works. The reference table below it carries the detail. It always ends on **See my options**.

**Refine — a collapsed block at the foot of the Math module, not a beat.** Closed by default, showing only a title and a count. The figures Finneas had to estimate, offered as things the person could go and find, each with an **+ Add** that puts it on the plan. Do not call this step sharpening — that is intake. Opening it is the participant's choice, which is the point: it measures whether anyone wants to give more data once they have already seen an answer. The framing is an offer, not a caveat: *none of it is required — the answer stands without it.* Chad named this himself in Round 1: a reminder that pinpoint data buys better detail.

**10. The options component.** One beat, three states, identical for every participant.

- **Closed** — a table of three named options with the selected column detailed beneath it. One CTA on the plum surface below the card: **Explore trade-offs**.
- **Open** — the trade-off card appears *below* the options table: an `EXPLORE TRADE-OFFS` eyebrow, bars against the target, the fixed rows the person can't change, then the controls, then confidence. Its footer carries the resulting figure on the left and **Set my target** on the right.
- **Committed** — *Set my target* saves and advances in one action. It is the beat's only way forward, so the beat's own CTA is suppressed entirely (`gate:true`). The trade-off card stays in the thread afterwards, tied to the commit flag rather than the open flag.

Committing fires a toast on the *next* beat, rendered at the top of the turn: *Target added to [priority] — [what they set]*, with a View link into the priority page.

**11. The handoff.** One beat carrying the pack, what Finneas will watch, and the save decision. The pack is grouped by when (Week 1 / Week 2 / Month 2–3), each step numbered with a who-does-what pill. Monitoring items are a separate group at the end, marked with a ring rather than a number and carrying no pill — they aren't the person's to do. Three save options, each going somewhere different: save → signup, change → back to the options beat, decline → reveals the consequence inline in the same beat.

**12. Signup, loader, home.** The account ask lands here and nowhere earlier. Apple/Google/email, then a dark full-bleed loader — wordmark, "Welcome to Finneas", "Setting up your plan…", a lilac bar that fills over ~1.6s — then home: fanned card stack on top, MY FINNEAS plan sheet underneath.

---

## Rules learned the hard way

- **The product is Finneas.** These are a new design for Finneas, not a different product. Never reference the participant's earlier session inside the product — no "you told Finneas", no "Finneas said". It's the same product speaking, so it just knows.
- **Match the actual financial advice.** The recommendations in a prototype are the ones from that participant's real session. Pacing, sequence, framing and presentation are what we're changing — not what the person is told to do. If your version reaches a different conclusion, that isn't a better prototype, it's a different study: the participant is then reacting to new advice rather than to a new way of receiving the same advice. Check your verdict, your action list and your ordering rules against the extraction before you build. Adding something Finneas never covered is fine if it doesn't contradict; reversing a recommendation is not.

- **Anything opened stays open in the thread.** A module that expands on demand must keep its expanded state once the conversation moves on — if the open/closed flag resets on advance, the past turn silently re-renders collapsed and the participant's own work disappears from the scrollback. Tie the past state to what they committed, not to a transient UI flag.
- **One CTA per state.** If a module owns the way forward, gate the beat's own CTA off entirely rather than showing both. Two white pills stacked is the tell.
- **Modules stay when you continue.** Earlier turns keep their live artifacts. Do not collapse them to a summary line — the study is about whether a paced version still feels comprehensive, and deleting the analysis behind the participant guarantees it doesn't.
- **Sliders must survive the drag.** Re-rendering the module on every `input` event destroys the element under the user's thumb, so the drag stops after one step and the control feels stuck. Update state and the label live on `input`; do the full recompute and re-render on `change`, when they let go. A control with only a handful of values (a retirement age, a term in years) should be discrete buttons rather than a slider.
- **The options component, in three states.** This is the shape for every participant. **Closed:** the options table with the selected column detailed beneath it, and one CTA on the plum surface — *Explore trade-offs*. **Open:** the trade-off card appears below the table — headline figure, bars against the target, the fixed rows, then the controls — and the CTA becomes *Make this the goal*. **Committed:** *Set my target* both saves the settings and advances the conversation — it is the beat's only way forward, so the beat's own CTA is suppressed entirely. One CTA visible at every stage, and committing to a target is what moves things on.
- **One module pattern: a table of options, plus controls that move within them.** Every participant gets the same shape — the options laid out side by side so they can be compared, and sliders or a selector underneath so the comparison responds. The axis differs by question (Luke compares distances, Josh compares what he sets, Heather compares accounts) and that is fine; the interaction is what stays constant. This matters for the round: if the modules differ in kind, the pacing findings are confounded by module design.
- **Only make something interactive if the person can actually control it.** Sale price and transaction costs are the market's; they're static. Purchase price, contribution amount, timeline — those move.
- **No gradient section banners.** Those are Finneas's; they were removed deliberately.
- **Animations play; beats don't.** Nothing advances on a timer. Every beat waits for a click. Animation *inside* a beat runs on its own — nobody should be clicking through an animation frame by frame.
- **Say the thing, not a gesture at it.** If a number is available, use the number. "Three places, and the difference is smaller than it looks" became "Three places to put it. They land within $65 of each other." Watch for headlines whose rhythm does the work instead of their content, parallel constructions that sound resolved but state nothing, and any sentence that would survive being about a different person.
- **Hence can only use what it actually has.** A module may only reason from what the participant said in this conversation, what the product asked them, or public data it looked up. It cannot categorise their spending, name their subscriptions, or point at money it has no way to see. Where more is needed, the module asks for access — connect an account, send a statement — rather than presenting plausible categories as if they were findings. A slider does not fix this: the categories are an assertion even when the amounts are blank.
- **Never invent an answer the participant didn't give** without flagging it. Where a figure had to be made up to make a module work, say so in the handoff notes.
- **Mark what doesn't exist.** The check-in before options, the options summary, and anything else not yet designed appear as dashed "Not designed yet" boxes, not as invented screens.

---

## Tips

A **Tip** is content attached to an instruction that is not itself a step — a warning, a script, a tool, a reference. The test is that it is **never completed**: it governs how a step is done rather than being part of doing it. See `hence-system-decisions.md`.

Render as the taxonomy does: **sand (#f6efe0) with a 3px amber left rule (#c9843c)**, a diamond and a small uppercase label naming the kind, then the content. Do not invent a treatment.

Whitney has the first one: **◆ YOUR SCRIPT**, carrying the sentence she says at the dealership, with "Say it once, then stop talking" and a Copy button. The figure inside recomputes with her settings.

## Checking a build

Before saying it's done, run all four:

1. **Duplicate declarations.** `grep` for repeated `function X` and `var X` names. JavaScript takes the last definition silently, and `node --check` passes happily — this is the failure that gets through everything else.
2. **Walk every step** with the console captured, including the object pages.
3. **Walk it as a participant would** — entry, then only the forward controls — and list what's in each turn. Nothing should collapse or disappear behind you.
4. **Phone width.** 392px, not desktop.

Snapshot the file before any structural edit. Editing by `index("function A")` to `index("function B")` deletes whatever happens to sit between them; edit by line index with assertions instead.

## The files

`josh-ask.html` — **the reference build.** Retiring at 55 on an FRS pension. Copy this one.

`luke-ask.html` — home upgrade, Portland. Map with a distance slider, stay-vs-move comparison table, now-vs-new carrying cost, confidence signal.

`heather-ask.html` — saving for her son's first car. Step-up plan against her debt payoff, sourcing table, savings-vs-CD comparison, multi-goal module.

Both are one file: CSS, data, and render code inline. Open directly in a browser.

---

## Anatomy of the file

Top to bottom:

1. **CSS.** Two systems. The plum conversation (`.said`, `.sub`, `.opt`, `.mod` cream artifacts) and the light object pages (`.body.page`, `.pcard`, `.eyebrow`, `.stepc`). Don't cross them — a class defined for the plum context inherits white text and will disappear on a cream card. Both files already carry the fix for that.
2. **`var S`** — all state. Current beat, laced/held mode, and every number a slider can move.
3. **Artifact functions** — `modX()`, each returning an HTML string. Read from `S`, so they re-render live.
4. **`var D`** — the dialogue array. One object per beat. This is where nearly all the content lives.
5. **`var PACK`, `ACTIONS`, `ACT_STEPS`, `RATES`** — handoff pack, priority page actions, action page steps, monitoring chart data.
6. **`ROWS`, `STEPS`, `NOTES`** — the answered-set recap, the step switcher above the phone, and the caption under it.
7. **Render + wire.** Generic. You shouldn't need to touch it.

### The beat object

```js
{ says:   "Serif headline.",
  sub:    "Body under it.",
  after:  "More body, after any module.",
  math:   "Section head, e.g. The Math",       // optional
  mod:    modSomething,                         // optional artifact
  lace:   ["Working while you answer","..."],   // laced-mode insight
  toast:  "Started a priority for you — <b>…</b>",
  ask:    "A question",
  why:    "Why I'm asking",
  meta:   "1 of 4",
  opts:   ["Option","Option"],
  banded: true,                                 // adds "Or enter a specific answer / Skip"
  answered:"What they picked",                  // becomes their chat bubble
  answer: "Free text they typed",               // sends from the dock instead
  bare:   true,                                 // no avatar; continues the previous turn
  more:   true, cta:"Continue",                 // analysis beat, advances on a pill
  handoff:true, authorise:true, recapRows:true, end:true }
```

---

## Building a third one

1. **Copy `heather-ask.html`.** It's the cleaner of the two.
2. **Read that participant's de-duplicated content extraction** — the verbatim record of what Finneas actually showed them — *and* their session transcript. The extraction gives you the product's words; the transcript gives you theirs. You need both, and the transcript matters more.
3. **Find the reframe.** Read the warm-up, before the product appears. What they say when asked what's on their mind is usually the real answer; the question they type into the product is a narrower version of it. Find their words for it and use those.
4. **Replace, in order:** the title and header name; the entry composer text; beat 0's `answer` (their words); beat 1 (the reframe); the intake questions; `ROWS`; the artifacts; `PACK`; `ACTIONS` / `ACT_STEPS`; the priority and action pages; `STEPS` and `NOTES`.
5. **Check the step switcher indices still match** the `D` array after adding or removing beats. This is the most common breakage.
6. **Verify in a browser.** Click through every beat, move every slider, open both object pages, and toggle laced/held.

---

## The checklist for a new build

Every prototype must have all of these. Luke, Heather and Josh all do.

1. **Branding.** The product is Finneas. Wordmark, avatar letter, MY FINNEAS bar, "Send to Finneas" CTAs. Never reference the participant's earlier session inside the product.
2. **Intake as one block**, numbered straight through, each question with a one-line rationale. A priority toast fires after the reframe is confirmed.
3. **The Math beat**: the answer as a figure in the first line, then what is working in their favour, then the one thing that would change the order. One reference table. A collapsed **Refine this answer** block at the foot. Ends on **See my options**.
4. **The options component** in its three states, with **Set my target** committing and advancing, and the toast on the following beat.
5. **One or two "rest" beats** for whatever the original advice carried that the component doesn't. Not six.
6. **The handoff**: pack grouped by when, a **What I'll watch** group at the end marked with rings and no who-pill, and the save decision — three options, each going somewhere different, decline revealed inline.
7. **Signup → loader → home.** The account ask lands here and nowhere earlier.
8. **Home, priority and action pages**, with `HOME`, `HOME_CARDS`, `WEEK_STEPS`, `CAL`, `PRI`, `REC`, `PAST`, `NOTSTARTED`, `FOUND`, `ASKS` populated for that participant.
9. **No "Not designed yet" blocks.** Those gaps are closed.
10. **Five or six analysis beats, not thirteen.**

Both were built before the options component settled. Each needs:

- the options component in its three states, replacing whatever module currently carries the choice
- **Set my target** committing and advancing, with the toast on the following beat
- handoff and authorise merged into one beat, with monitoring as a watching group in the pack
- the signup → loader → home wrap-up
- the "Not designed yet" blocks removed — those gaps are closed
- beat count cut. Luke has fourteen analysis beats and Heather thirteen; the target is five or six.

## Open — conditional refinement

Chad's build originally opened with an inventory beat: *nine figures I have, two I don't, one that doesn't agree.* It has been folded into his Math, because it duplicated what the Refine block does and gave him a beat nobody else had.

It is worth keeping as an idea. A **conditional refinement** — surfaced only when confidence falls below a threshold — would let the product say "I can answer this, but not well, and here is exactly why" before it commits to a plan. Chad is the case that argues for it: at 45% confidence with the per-card APRs missing, ranking his three methods would be a guess presented as an answer.

Not built. Flagged here so it does not get lost.

## Notes on the five

**Whitney** — financing a ~$45,000 truck. Wanted the math and didn't get it: she said four separate times she was waiting for the numbers, and the payment and rate arrived buried under "what would change this." Lead with the payment figure. Options as leverage — she said the comparison gives her something in her back pocket rather than taking the dealer's word for it, and the online lender was new to her.

**Josh** — built. Retiring at 55 off a Florida firefighter pension, fifteen-year runway. Liked that the options panel updated live as he answered. Distrusted invented time estimates — "I also guarantee that calling my HR is going to be way more than 15 minutes" — so durations need to be honest or absent. He found the confidence signal on his own and asked how it fact-checks itself; he wants both the method and the list.

**Chad** — household debt and building a budget, running a restaurant and a new production brewery. The strongest voice for chunking: bold colours and separate cards made it legible, and when things get long he starts skimming. Wants emotion-neutral tone, against Luke and Heather who want warmth. A 55% confidence score raised his trust, and he wanted a line explaining what it measured because it would change whether he stopped to correct his own bad income figure.

---

## Still not designed by anyone

The check-in before options, the visualized options summary, and the confidence signal are all absent from Figma. In these prototypes the first two appear as "Not designed yet" boxes; confidence is built in Luke's and Heather's as a collapsible block at the foot of the options module. If the designs land before field, they replace the placeholders.
