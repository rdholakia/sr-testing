# Hence / Finneas — Round 4 Research Guide
## Ask: understanding how pacing, visualization and interaction impact content comprehension and product value

**Format:** 60 minutes, remote. Two halves — current Finneas, re-run live by the participant, then a dumb-data Claude prototype pre-filled with data and content from their previous round question. The user receives a link to the prototype and clicks to move between beats; animations play on their own.

**Before the session:** participants are asked to join on a laptop and be ready to share their screen. They re-enter their original question in current Finneas themselves; only the prompt is prepared for them.
**Participants:** 5 returning from the Aug 5–7 round — Luke, Heather, Whitney, Josh, Chad
**Field dates:** Tue/Wed
**Moderator:** Melissa

---

## Overview

Round 1 established that Ask output is valuable and trustworthy, but length and ordering can make the information feel hard to digest.

> Chad: when things get long you start skimming.
> Heather: I get lost in the paragraphs.

This round tests changes to pacing, new modules that visualize trade-offs, and simple graphics like tables and charts to make information easier to understand and engage with. The analysis is identical; the only change is how it's delivered — paced into steps, with interactive modules replacing some of the prose, and two new beats inserted (a priority container created mid-conversation, and an options component the participant can open and adjust).

We know folks found the breadth highly valuable. This test is designed to see whether pacing impacts that value or makes the information feel less trustworthy.

The session runs in two halves. The first is current Finneas, re-run live by the participant, with real time spent in **Options and Compare** — the part almost nobody reached in August. The second is the paced prototype.

## What we are answering

1. Does pacing the analysis into steps preserve the sense of comprehensiveness, or dilute it — set against their own real answer, read fresh at the top of the session?
2. Do the modules do the work the prose was doing, or do people read past them?
3. Where do people want the numbers relative to the reframe?
4. Does the check-in before options read as attentive or as an obstacle?
5. Does a visualized option summary before the three options help or pre-empt?
6. What does the confidence signal do for people, what should it be called, and what has to be said about it?
7. Given the choice, do people pick from options or set the numbers themselves?

## What we will not cover

Foundations, value prop statement, money attitudes, tone.

---

## Stimulus

**Two artifacts per participant, in this order:**

1. **Current Finneas, run live.** They get their original prompt back — that's all we can prepare — and re-enter it themselves, then work through the response. The session is not saved, so this is a fresh run rather than a reopened conversation.
2. **The prototype** — a single path, no variants, pre-loaded with that participant's own question and numbers from Round 1.

**Because they re-run it live, the Finneas half takes longer and lands somewhere slightly different than it did in August.** Budget for that, and don't fight it — a second run of the same question is itself informative. What matters is that they reach **Options and Compare** and spend real time there; see section 2.

The prototype does not self-advance between beats — the participant holds the link and clicks to move forward. Animations within a beat do play on their own; nobody should be clicking through an animation frame by frame.

| | Question | Modules needed |
|---|---|---|
| Luke | Move up from the 2018 starter house, land outside Portland city limits | Cost curve, timeline options |
| Heather | Fund for Nolan's first car, few years' runway, invisible money | Savings-target projection, account comparison |
| Whitney | ~$45K truck, financing route | Payment math, three-lender comparison |
| Josh | Retire at 55 off FRS special-risk pension, 15-year runway | Income-gap projection, lever comparison |
| Chad | Get household debt under control, build a budget | Payoff/balance-transfer comparison, budget snapshot |

**Watch how they move through it.** Where they linger, where they click straight past, whether they scroll back, whether they touch the modules at all. We're not instrumenting anything or counting anything — but what someone does with a step usually tells you more than what they say about pacing when asked. Watch it, and don't fill the silence.

---

## Pre-session ask

Send the morning of:

> We'll start by putting your question from last time back into the tool and looking at what comes back, so please join on a laptop where you can share your screen. Nothing to prepare — I'll paste the question to you when we start.

---

## Prep work

**Owner:** Melissa, with Arjun where noted. The recreation step may need to run on Melissa's machine if Finneas retains data per browser.

### Step 1 — Confirm everyone can share a screen
They're driving both halves of the session, so a laptop and screen share is the one hard requirement. Confirm it in the pre-session note.

### Step 2 — Get each participant's original prompt ready

Their session won't persist, so there's nothing to reopen. Paste the prompt into the Zoom chat at the top of the session; they enter it themselves and share their screen.

**Josh — retiring at 55**
> I am looking for ways to retire within the next 15 years when I reach 55. I am a firefighter in the state of Florida and will "age out" in my department so I will not take a penalty on my FRS retirement. How should I start planning and saving so I can live comfortably and well within my means if I retire at 55?

**Luke — the acre outside Portland**
> My current home is 4130 North Russet, Portland Oregon. My wife and I have a combined income of about $220,000 annually. We would like to upgrade our home in the next 5 or so years…

*Truncated in the prototype's entry field — his full prompt has not been recovered. Check the session recording before Tuesday, or paste from his Round 1 screenshot.*

**Heather — Nolan's first car**
> I am looking to save for my sons future car I have a few years to work with and I want something safe and nice. I don't have a whole LOT to set aside but some and I want to make it feel like it doesn't exist the savings toward it

**Whitney — financing the truck**
> How would a payment for a new truck look at 45,000?

**Chad — the card debt**
> I am in roughly $50,000 in credit card debt due to some recent major purchases. My wife and I currently bring home roughly $11,000 per month. Our family consists of myself, my wife, and our two children. We What questions do I need to answer for you to help me begin a plan to get out of that debt?

*The "We What" is in his original — he began a sentence and typed over it. Paste it as-is.*

### Step 2b — The prototypes

One link per participant. Open theirs before their session; nobody sees anyone else's.

| Participant | Link | Their question |
|---|---|---|
| Josh | `_____________________` | Retiring at 55 on the FRS pension |
| Luke | `_____________________` | An acre outside the Portland city limits |
| Heather | `_____________________` | Saving for Nolan's first car |
| Whitney | `_____________________` | Financing the truck without taking the dealer's word |
| Chad | `_____________________` | Getting $50,000 of card debt under control |

**Fill these in once they're deployed.** Suggested slugs, so the pattern is guessable under pressure: `finneas-r4-josh`, `-luke`, `-heather`, `-whitney`, `-chad`. Files in this package: `josh-ask.html`, `luke-ask.html`, `heather-ask.html`, `whitney-ask.html`, `chad-ask.html`.

**Three things to settle before deploying.**

Each prototype carries one real person's financial detail — balances, income, address in Luke's case. If the URLs are public and guessable, one participant can reach another's. Worth either a random slug per participant, or Vercel's password protection on the project.

`compare.html` should not be deployed at all. It embeds all five, so a single link exposes every participant's numbers. Keep it local, for your prep.

Have the links open in a tab before each session starts. If a deploy is still building at the top of the hour you lose the half of the session that matters most, and there is no offline fallback unless you also keep the local files to hand — which is worth doing regardless.

### Step 3 — Where each person actually stopped

Worth knowing before you sit down, because it tells you how much of Options and Compare is new to them.

### Step 4 — Click through their prototype before the session

All five are built. Open the participant's file, walk it end to end, and open the trade-off card at least once so nothing surprises you live. Check the numbers still read the way you expect after any last edits.

### Step 5 — Decide the confidence label

The signal is built into all the prototypes and reads **Moderate · 45%** for Josh, **Moderate · 60%** for Heather. Two open questions to settle before field, both of which the session can inform rather than answer: whether "confidence" is the right word, and whether a percentage is the right form.

Worth knowing going in: Finneas showed Josh **Strong · 92%** and Heather **Strong · 92%**. Our prototypes deliberately read lower, because they name the estimates behind the answer. Josh in particular went looking for this signal unprompted last round, so he may notice the change and say why he thinks it moved — which is the most useful thing he could tell us.

---

## 1. Recall, and their question re-run in current Finneas (16 min)

*Do not re-run the warm-up.*

Good to see you again. Last time you asked Finneas about [their question]. I'd like you to put that same question in again, and we'll look at what comes back.

*Paste their original prompt into the Zoom chat. They enter it and share their screen.*

- While it's working: what do you remember about the answer you got last time?
- Anything you've done since, or thought about differently? *(Genuinely open — several had live decisions running.)*

*As the response comes in:*

- Take a minute with this. What are you looking at?
- What's useful in here?
- Anything you'd forgotten was in it, or are skipping now?

**Then get them into Options and Compare, and stay there.** This is the part of current Finneas we most need time on, and in August almost nobody reached it before the clock ran out.

- *(When the options appear)* What are these?
- Open one. What did that give you that the summary didn't?
- Now try Compare. Walk me through what you're looking at.
- Is this enough to choose on? What's missing?
- Which of these would you pick, and what decided it?

*Moderator note: keep this on comprehension, not preference. Watch how they read: where they stop, where their eyes jump, whether they scroll past anything. Let them find Compare rather than pointing at it — but if they haven't reached it by the ten-minute mark, point them at it, because we need the time in there more than we need the discovery finding.*

Then play back one line of their own:

- **Luke** — you said the thing that beat ChatGPT was that it named the low-mortgage problem before it ran any numbers.
- **Heather** — you said the eight-step plan with the weekly split was where you started to feel guided.
- **Whitney** — you said several times you were waiting to see the numbers.
- **Josh** — you said you liked that the options on the side changed as you answered more questions.
- **Chad** — you said when things get long you start skimming.

Does that still sound right to you?

*Moderator note: this is the only place we mine Round 1. Don't return to it later; we want reactions to what's on screen, not comparisons to memory.*

---

## 2. The paced analysis (17 min)

Now I'm going to send you the same conversation but with a different design. I'll put the link here in the Zoom chat, and once you have it be sure to share your screen so I can see what you see. This is a prototype, so the answers are prefilled but they reflect what you asked about last time. Click through at whatever speed you want, and put your brain on speakerphone as you go.

**Observe, don't ask:**
- Which steps they hold on and which they clear fast
- Whether they scroll back
- Whether they engage the interactive modules, read past them, or don't notice them
- Whether they ask a question the next step is about to answer
- Whether they ever try to skip ahead

**After the third step:**
- What's happening here? Talk me through what you've got so far.
- Tell me how you feel about the amount of information you've seen so far.

**At the end of the analysis:**
- How does this compare with what you just did in the other one? *(Only ask once, here.)*
- To you personally, which of the two is more trustworthy?
- Did any step feel like it was holding something back from you?
- If you could collapse any of that into one screen, which?
- Is there anything missing? It's ok to say no.

**On the modules specifically:**
- *(For any module they engaged)* What did that tell you that the writing didn't?
- *(For any module they skipped)* Tell me about this one — did you look at it? What did you take it to be?
- How did that compare to reading it?

**On the pace:**
- How did the pace of it feel to you?
- Tell me about how it was broken up into steps.

---

## 3. Where the numbers belong (5 min)

- Think back through what you just went through. When did you first see a number that mattered to you?
- Tell me about where that landed for you.
- What do you remember about what came before it?
- If you were laying this out yourself, what's on the first screen?

**Probes:**
- Is that about this question specifically, or is that how you'd always want it?
- *(Follow whatever they say about ordering)* What would change for you if it were the other way round?

---

## 4. The options and the trade-offs (8 min)

*They reach the options beat. Do not point at anything — watch what they do first.*

- What are you looking at here?
- What's the difference between these?
- Which one would you take, and what decided it?

**Then, only if they haven't found it:** there's a button under that. What do you think it does?

*They open the trade-offs.*

- What changed when you opened this?
- Try moving something. What happened?
- Does this change which column you'd pick?

**Probes:**
- Would you rather be handed three options, or build it yourself like this? *(The core question. Frank's position is that people want to choose from options; the alternative is that they'd rather set it themselves. Do not signal which is which.)*
- What does "Set my target" mean to you? What would you expect to happen after you press it?

*Moderator note: the thing to watch is the order. Do they pick a column and stop, or open the trade-offs first and treat the columns as a summary? Whether they touch the sliders at all is the finding, more than what they say about them afterwards. Silence here is the instrument — let them sit with it.*

---

## 5. The confidence signal (5 min)

*It's inside the trade-off module, collapsed. Let them find it if they will; surface it if they don't.*

- What do you think this is telling you?
- What would you expect to happen if this were higher, or lower?
- How does seeing this impact your confidence in the answer?
- Is that the right word for what you think it's doing? What would you call it?

**Probes:**
- Would you want to know how it arrived at this? What would you want it to say?
- If this told you it wasn't complete, what would you do — keep going, or go get the missing information?

*Moderator note: this section exists because three of five went looking for this on their own last round. Chad said a moderate score raised his trust, and that not knowing what it measured affected whether he'd stop and correct his own bad number. Josh asked for both the method and the list, and said the mere presence of it mattered even to people who never open it. Test whether one sentence is enough or whether they want the detail.*

*On the name: the prototype calls it confidence, following today's Finneas. Dawn has flagged that the word collides with confidence intervals in retirement planning, where it means something specific and statistical, and is separately uneasy about expressing it as a percentage. That's why the "what would you call it" question is in here — the label is genuinely open.*

---

## 6. Priority creation (5 min)

*Almost nobody saw this last time. Treat it as first exposure.*

*The priority created, and the actions attached to it.*

- What just happened? What is this thing?
- Is this something you asked for, or something it did for you? How do you feel about that?
- What would you expect to find in here if you came back next week?

**Probes:**
- Is this the thing that makes you come back, or not?
- What would you want it to have done in the meantime, without you?

---

## 7. If there's time — first reactions to something new (5 min)

*Only if you're ahead. Cut without hesitation.*

Show **one** of these, not both — pick whichever the session has left room for:

**The marketing page** (Ritik's mock-up). Show it cold, no framing.
- What is this? What do they do?
- Who's it for?
- Would you click anything here?

**The Hence home screen** (in their prototype, the last beat).
- What are you looking at?
- What would you expect to find here if you came back next week?
- Is this the thing that brings you back?

*Moderator note: this is a first-impressions read, nothing more. Two minutes of reaction is the whole value — don't walk them through it, and don't defend it.*

---

## 8. Close (4 min)

- If you were describing the difference between today's version and the one you saw two weeks ago, what would you say?
- Which one would you rather use?
- Anything you want to go back to before we stop?

Thank you — and confirm they're open to a further session.
