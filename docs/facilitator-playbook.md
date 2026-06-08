# Drawing the Unseen: Facilitator Playbook

How to Diagram AI in Your Salesforce Architecture
90 minutes · about 15 participants · 3 groups of 5 · Architect Dreamin

Version 3. Restructured into six sections. The technology deck now runs on an effort-point model with a hard cap and bonus abilities, the notation is introduced before the build, and the review board has each team present to one executive with optional distractors rather than all three judges grilling everyone.

---

# 1 · Timeline

Five working blocks plus this overview. Each block is one act, not a checklist.

| Section | Start | Min | What happens | Output |
|---|---|---|---|---|
| 2 · Scenario and stakeholders | 0:00 | 10 | MMG, the mandate, the three CxOs | Shared context and tension |
| 3 · Intro to the AI notation | 0:10 | 10 | The vague box problem, the kit, where it runs out | A shared vocabulary |
| 4 · Cards and build | 0:20 | 30 | Assign domains, the point model and all its rules, pick under the cap, draw both diagrams | Solution architecture and data flow per team |
| 5 · Review board | 0:50 | 30 | Each team presents to one executive, optional distractors | A defended strategy |
| 6 · Closing | 1:20 | 10 | Where the notation ran out, the reveal, the takeaway | Notation vocabulary, community output |

What every team leaves with: a solution architecture diagram, a data flow diagram (both drawn in section 4, both scoped to the team's domain), and the reusable notation kit. These three are the Abstract.

Times and the point cap are tunable [Inference]. The version 3 split puts the notation before the build and moves defending time into a single focused review per team.

---

# 2 · Scenario and stakeholder intro (0:00 to 0:10)

Goal: set the scenario and the tension fast. No drawing in this block.

You do: present MMG and its landscape, put the mandate on screen, introduce the three CxOs.

The company, in one breath: Meridian Mobility Group is a European automotive retail and service group, not a manufacturer. About 8 countries, roughly 600 locations, around 4 million customers, and on the order of 8 million inbound contacts a year. Salesforce Automotive Cloud is the centre. Around it sit the systems on the worksheet: the dealer management system, OEM telematics, the SAP ERP, marketing automation, the call-centre CTI, service scheduling, Data Cloud, and the customer portal with its identity provider. There is no AI in production today. The platform team is strong, but there is no in-house machine-learning or data-science function.

You say:
> "Meridian Mobility Group, a European automotive retail and service group. Automotive Cloud is the centre, and the eight systems on your worksheet sit around it. The shareholders have given the board one instruction."

> "Embed AI more deeply into the product to drive growth and efficiency."

> "That is the whole brief. It is vague on purpose, because your three executives read it three different ways."

- Helena Vance, CEO, ambition: "I want customers talking to our AI by Q3, and I want it in the announcement."
- Marcus Reinhardt, CISO and CDO, risk: "Where does the customer's data go the second it touches a model, and who can prove it?"
- Priya Anand, CIO, feasibility and cost: "Show me the cost at 10,000 conversations a day, and who operates this at 2 a.m."

> "Your job today is to satisfy all three. Not one. All three."

Watch-out: hold this to ten minutes. The scenario earns its weight in section 4, not here.

---

# 3 · Intro to the AI notation (0:10 to 0:20)

Goal: give the room one honest way to draw AI before they build anything. Output: a shared vocabulary.

### The motivation, the vague box (about 3 minutes)

You do: show the magic-box example, the before and after.

You say:
> "Here is the box almost everyone draws today: a rectangle labelled Agentforce, or Einstein, or just AI. It looks finished. It hides every decision that matters: does it loop, can it refuse, where does the customer's data go, what grounds it. Here is the same thing drawn honestly."

> "That gap, between the box that looks done and the box that tells the truth, is what this kit is for."

### The kit, five primitives (about 6 minutes)

You do: hand out the kit, one per person. Walk the five primitives fast, each tied to a real question. Use the Einstein Trust Layer as the worked example for the boundary.

You say, compressed:
> "Black is for conventions you already use. The accent colour, your second marker, is for everything new and AI-specific."
> "Nodes: is the box deterministic, same in same out, or probabilistic, where the same input can vary? Mark the probabilistic ones."
> "The agent is not one call. It reasons and may loop. Draw the loop."
> "Grounding is not data flow. It shapes the answer without being passed through, and retrieval is a deterministic search that can quietly return nothing."
> "The trust boundary matters most for Marcus. The Einstein Trust Layer is the canonical example: the instant data touches a model, it is masked, ground-checked, kept out of retention, and logged. Draw it as a place, not a line you wave at."
> "Every component sits on exactly one plane: runtime, delivery, or operations."

The rule of thumb, say it and leave it on screen:
> "If a box hides a decision, will it loop, can it refuse, where does the data go, it is wrong."

### Where it runs out (about 1 minute)

You say:
> "This kit is version 0.1 and deliberately incomplete. It draws the easy structure well. It cannot yet express five things: confidence and when to defer, human oversight and who approves, data sensitivity and which arrows carry PII, cost and latency, and failure and fallback paths. Part of your job today is to notice where it runs out."

Facilitator variation [optional]: if you prefer the discovery version, run a draw-first hook instead. Let teams pick their technology and try to draw it before you hand out the kit, so they hit the vague-box wall themselves, then introduce the kit as the answer. It costs about five extra minutes and lands harder, but it reorders sections 3 and 4.

---

# 4 · Cards and purpose, build a solution on the point model (0:20 to 0:50)

Goal: choose a defensible AI architecture for your domain under a constraint that forces trade-offs, then draw it honestly with the kit. Output: the solution architecture diagram and the data flow diagram.

### Beat 0: assign domains (first 60 seconds)

You do: give each team a domain card. Same MMG, same landscape, but each team builds the AI architecture for one slice. This is what keeps the three architectures, and later the three pitches, genuinely different.

| Team | Domain | Whose concern it most touches |
|---|---|---|
| A | Customer self-service: chat and voice, deflection at scale | Priya |
| B | Sales: financing and trade-in | Marcus |
| C | Service and recall | Helena |

You say:
> "You are all inside the same MMG, but each team owns one part of it. Build your AI architecture for your slice. At the board, you present your slice to the executive who cares about it most."

### The cards and their purpose

You say:
> "This deck is your menu of AI building blocks. Each card tells you what the technology actually is, what it costs you in effort, and the honest catch you take on with it. Some carry a bonus ability. The names at the bottom show which executives it appeals to. Picking cards is how you choose your architecture, and the cost is what forces you to choose."

### The point model, all the rules

Put these on screen and keep them up for the whole block.

- Cap. You have 12 effort points per team. Spend more and Priya walks out.
- Cost. Each card shows a cost from 1 to 7. Higher cost means more to build, more to run, and more to govern.
- Discounts. Three cards carry a blue star with a minus one. Each lowers the cost of another card by 1: MCP discounts your custom actions and extra integrations, AI-Assisted Delivery discounts every build-heavy card, and the Model Gateway discounts extra model cards. A card never drops below 1 point, and at most one discount applies to any single card.
- Defends. Four cards carry a blue star that gives a head start in the review: Grounded RAG defends safety, Agent-Assist defends oversight, Observability and Evaluation defends operability, and the Model Gateway defends a vendor change. A defense is a head start, not immunity. You still have to draw the thing on the diagram for the executive to accept it.
- Traps. Some cards cost points but do not move the mandate, or sit off the customer runtime. No card is labelled a trap. The honest catch on each card, and the plane it belongs on, are the clues. Reading them is part of the game.
- The point. Twelve points is not enough for everything. Choose what actually serves your domain and your three executives, and be ready to defend the trade-offs.

Facilitator note, not announced to the room: the traps are A2A, which needs a real counterparty MMG does not have; AI-Assisted Delivery and AI Co-Worker, which live off the customer runtime; and Custom Fine-Tuning, which needs a data-science function MMG cannot staff. A team that spends points here has made a real mistake worth surfacing in the close, not blocking now.

### Beat 1: pick under the cap (0:21 to 0:31)

Groups, about 10 minutes: read the cards, debate the fit for their domain, commit to a set within 12 points, applying discounts where they help.

### Beat 2: draw the solution architecture (0:31 to 0:43)

Groups draw the solution on the landscape using the kit. Probabilistic nodes marked, the agent loop drawn, grounding shown, the trust boundary placed as a region, every component on a plane. This is the solution architecture diagram.

### Beat 3: draw the data flow (0:43 to 0:50)

You say:
> "Now zoom into the box. On a fresh sheet, draw the data flow through your AI subsystem: the prompt going in, the trust boundary, grounding and retrieval, the model call, the response coming back, and what gets logged. This is the diagram Marcus reads line by line, and the one the board will push on hardest."

Groups, about 7 minutes: draw the AI subsystem data flow with the kit. Subsystem only, not the whole landscape.

Watch-out: this block is the tightest stretch for its value, and it carries two diagrams. Circulate and keep groups moving: pick, do not perfect. Let two failure modes happen rather than preventing them: over-engineering, a team that spends the cap on the shiniest cards, and the plane error, a team that puts a delivery tool or an internal assistant in the customer runtime. Both surface in the close. Do not correct them now.

---

# 5 · Review board, present to one stakeholder with optional distractors (0:50 to 1:20)

Goal: each team presents its architecture to the one executive whose concern its domain most touches, and defends it. The executive may throw optional distractors, aimed exactly where the notation is weakest. Output: a defended strategy. Both diagrams already exist from section 4.

### Who presents to whom

| Team | Domain | Presents to | Format |
|---|---|---|---|
| A | Customer self-service | Priya, CIO | Three-slide board pitch |
| B | Sales, financing, trade-in | Marcus, CISO and CDO | Live whiteboard, no slides |
| C | Service and recall | Helena, CEO | Walk one journey end to end |

The build had to satisfy all three executives. The review is a focused defense to one. The other two may optionally throw a distractor, and the oversight wildcard is open to any team, but the assigned executive leads the round and gives the verdict.

The formats are not arbitrary. The board pitch suits Team A's deflection and cost story for Priya. The live whiteboard lets Marcus interrogate Team B's data flow line by line. The single-journey walk for Team C is literally the recall question, "is my car safe to drive?", which is exactly where a confident wrong answer and Helena's announcement risk collide.

### How a round runs (about 8 minutes per team)

1. The team presents its domain architecture in its assigned format, roughly four minutes.
2. The assigned executive leads the review and decides, using the single accept condition below.
3. Optional distractors, the discipline: the executive throws an owned curveball only when the team's diagram leaves that gap open, that is, when the diagram cannot answer it. Throwing the curveball the notation cannot answer is the diagnostic moment, and it is the skill you are modelling. If the diagram already answers it, skip it.
4. The defends tie-in: if the team took and drew the matching defends card, the distractor is already answered, so accept it. If they took the card but did not draw it, the executive may still throw it. A defense is a head start, not immunity.
5. Cap: at most two distractors per team. The oversight wildcard, D2 the AI Act knock, is open to any team and does not count toward the two.
6. When you throw a curveball, read its participant side aloud from your judge card, then make the team respond on the diagram, not in conversation.

Optional audience challenge [drop if short on time]: the two non-presenting teams hold perspective cards, Customer, Regulator, and Operations. After the executive is done, one of them poses a single challenge from its role.

### The accept conditions (the single yes)

| Executive | Says yes only if the presentation shows |
|---|---|
| Helena, CEO | A visible, customer-facing capability that supports the growth story, with a credible, phased timeline |
| Marcus, CISO and CDO | PII handling, the trust boundary, grounding, and human oversight made explicit and auditable, and AI Act exposure acknowledged |
| Priya, CIO | Run cost at scale, latency, operability, who runs this at 2 a.m., and lock-in addressed, with complexity matched to value |

A design that wins its own executive but would clearly fail the other two has not met the mandate. Say so kindly when it happens. Keep one eye on the two-distractor cap so a strong team does not get buried.

The full judge cards, with every distractor and its read-aloud, are in Appendix B. The five distractors map one to one onto the five kit gaps, which is the engine of the close.

---

# 6 · Closing (1:20 to 1:30)

Goal: harvest where the notation ran out, reveal the design, and leave with a thesis. The cross-team comparison is the centrepiece.

Harvest, 4 minutes: on a flip chart with five columns, one per gap, ask each team to name the one place their notation ran out. Tally each answer under the matching gap.

The cross-comparison, the gold: because the teams had different domains, they hit different gaps. Name it out loud.
> "Team C had to invent a confidence symbol for a safety answer that Team A never needed. Team B needed a way to mark PII on an arrow that Team A's diagram never had. Team A needed a cost-per-call notation the others could ignore. Put together, your three boards just covered all five gaps. That was the design."

The reveal, 2 minutes:
> "The kit was deliberately incomplete, and the distractors were aimed at exactly the gaps it does not cover: confidence, human oversight, data sensitivity, cost and latency, failure and fallback. You did not fail to draw these. The conventions do not exist yet. That is the finding: this is where AI architecture notation still has to evolve, from version 0.1 toward version 1.0."

The traps, 1 minute: ask whether anyone placed a delivery tool or an internal assistant in the customer runtime, or built on A2A or fine-tuning that MMG cannot staff. Surface it without blame. The lesson: where a component sits, and what it needs to exist, are real architecture decisions.

Takeaway and collect, 3 minutes:
> "Good AI notation is not decoration. It is risk management you can see. Every distractor today was a risk your first vague box hid. Take the kit, plus the gaps you discovered, as your starting vocabulary."

Collect the notation the room invented: a symbol for an agent that must defer, a human-approval gate, a PII-bearing arrow, a cost per call. This is the constructive feedback to Salesforce and the community output.

---
---

# Appendices (supporting material)

The six sections above are the session. Everything below is reference for preparing and running it.

## Appendix A · Materials checklist

Per table, one set per group: a pre-drawn MMG landscape worksheet (A2 or A3, the surrounding systems drawn, AI not drawn); one technology card deck; one domain card; one format card; the CxO acceptance rubric, which doubles as the pitch checklist; two marker colours, black plus one accent; blank flip-chart sheets for the data flow and the presentation.

Per person: the notation kit handout.

Held by the three facilitators: one judge card each, Helena, Marcus, Priya, carrying their optional distractors and read-alouds; a five-column flip chart for the close; a timer visible to the room.

Audience: three perspective cards, Customer, Regulator, Operations, handed to the non-presenting teams during each review round if you run the optional audience challenge.

Still to produce before the session: the landscape worksheet, the three judge cards, the domain cards, the format cards, and the perspective cards. Content for all of these is in this playbook.

## Appendix B · Judge cards (one per executive)

Print one card per executive. Each is self-contained: stance, the optional curveballs you own, when to throw them, your signature openers, and the single condition under which you say yes.

How the curveballs work: they are optional. Throw one only when the team's diagram leaves the gap open. If they have already answered it, or the team took and drew the matching defends card, leave it out. Stop at two per team across all judges. The oversight wildcard, D2, does not count toward the two. Each curveball carries its full read-aloud, so you throw it straight from the card.

### JUDGE CARD · Helena Vance, CEO

Stance: ambition and story. You already promised the board AI by Q3. You want a headline, and you do not want to hear "it depends."

**The Q3 Promise** [optional]. Throw at a big-bang design with no phasing.
> "I told the board this ships in Q3. Show me on the diagram what is live by then, and what is not."

Accept when: a staged roadmap with a credible Phase 1.

**The Simplify-or-Scale squeeze** [optional]. Throw the half that matches what you see.
> Over-built: "This is a science project. Will a customer ever feel it?"
>
> Too thin: "Is this all the shareholders get for the investment?"

Accept when: the scope visibly matches customer value.

**D3 The Confident Wrong Answer, story angle** [optional, shared with Marcus]. Throw at any safety-touching design, especially Team C. Pre-empted if the team drew Grounded RAG as a grounding and defer gate.
> "In the pilot, the agent told a customer with worn brake pads that everything looked fine and they could skip the inspection. It was wrong. No one was hurt. This time. If that lands in week one, my announcement becomes the story, so what on this page stops it?"
>
> The diagram must now show: when the agent may answer versus defer, what grounding it needs before safety guidance, and what happens when it is unsure.

Accept when: a confidence or grounding gate before high-stakes answers, a defer-and-escalate path, stricter grounding for safety.

Signature openers (rotate one per round): "Where is my headline on this page?" · "What can I announce, and when?" · "Put me on stage in Q3. What do I say?"

You say yes only if: a visible, customer-facing capability supports the growth story, with a credible, phased timeline.

### JUDGE CARD · Marcus Reinhardt, CISO and CDO

Stance: risk and proof. Nothing is safe until the diagram proves it. "Where does the data go the second it touches a model, and who can prove it?"

**D1 Data Breach** [optional]. Throw if the data flow does not mask PII before the model, PII arrows are undifferentiated, or retention and logging are unshown.
> "A journalist publishes a screenshot from your model provider's logs. It shows a named customer's full service history and home address. The provider retained it. The board meets in twenty minutes."
>
> The diagram must now show: where customer data crosses into the model, what is masked before it does, what is retained or logged and by whom, and which arrows carry PII end to end.

Accept when: PII masked at the trust boundary before the model call, zero retention with the provider, sensitive arrows marked distinctly, logging scoped to non-PII.

**D2 The AI Act Knock** [optional, your wildcard, any team, does not count toward the two]. Throw at a design that advises or acts but is missing oversight, AI disclosure, or traceability. Pre-empted if the team drew Agent-Assist as a human-in-the-loop checkpoint.
> "Legal has reviewed the pilot. Because the agent gives recall and safety guidance, it may carry higher-risk obligations under the EU AI Act: transparency, human oversight, traceability. Show me, on the diagram, where a human stays in control."
>
> The diagram must now show: where the customer is told they are talking to AI, which agent actions need human approval before they commit, and how decisions are logged for traceability.

Accept when: a human-in-the-loop checkpoint on high-stakes actions, an explicit AI-disclosure node, an audit trail.

**D3 The Confident Wrong Answer, risk angle** [optional, shared with Helena]. Throw on any safety or recall guidance with no confidence or grounding gate. Pre-empted by Grounded RAG drawn as a grounding and defer gate.
> "In the pilot, the agent told a customer with worn brake pads that everything looked fine and they could skip the inspection. It was wrong, and it sounded completely confident."
>
> The diagram must now show: when the agent may answer versus defer, what grounding it needs before safety guidance, and what happens when it is unsure.

Accept when: a confidence or grounding gate before high-stakes answers, a defer-and-escalate path, stricter grounding for safety.

Signature openers (rotate): "Walk me to the exact line where a customer's data crosses into a model." · "Who is accountable when this is wrong, and where is that on the page?" · "Show me where a human can still say no."

You say yes only if: PII handling, the trust boundary, grounding, and human oversight are explicit and auditable, and AI Act exposure is acknowledged.

### JUDGE CARD · Priya Anand, CIO

Stance: feasibility and cost. You operate this at 2 a.m. "Show me the cost at 10,000 conversations a day, and who runs it."

**D4 The Bill and the Lag** [optional]. Throw if everything routes through the expensive model, there are gratuitous model calls, or voice is everywhere without justifying latency and cost. Partly pre-empted if the team drew Observability and Evaluation as live cost and quality monitoring.
> "Finance modelled it at projected volume. The design costs four times the contact-centre savings it was meant to deliver, and voice replies lag six seconds. Make the number work before this leaves the room."
>
> The diagram must now show: where the expensive model calls are, what could use a cheaper model or none, where latency accumulates, and what you would cut or cache.

Accept when: model tiering, gratuitous model calls removed, caching, voice scoped to where it pays.

**D5 The Vendor Moves** [optional]. Throw if the design couples to one provider with no stable interface or gateway, and no fallback. Pre-empted if the team drew the Model Gateway as a stable interface with a fallback.
> "Your model provider announces a breaking API change and a thirty percent price rise, effective in ninety days. How locked in are we, and what happens if a model we depend on simply goes away?"
>
> The diagram must now show: where you are coupled to one provider, what sits behind a stable interface, and the fallback path if a model becomes unavailable.

Accept when: a stable interface or gateway, a documented fallback model, graceful degradation.

Signature openers (rotate): "What does this cost me per conversation, and where on the diagram is the expensive call?" · "Your model vendor doubles the price in ninety days. What changes on this page?" · "It is 2 a.m. and the model is down. What does the customer get?"

You say yes only if: run cost at scale, latency, operability, and lock-in are addressed, with complexity matched to value.

## Appendix C · CxO acceptance rubric

Judges the presentations and voices the board. Also given to groups as the pitch checklist.

| Persona | Says yes only if the presentation shows |
|---|---|
| Helena, CEO | A visible, customer-facing capability that supports the growth story, with a credible, phased timeline |
| Marcus, CISO and CDO | PII handling, the trust boundary, grounding, and human oversight made explicit and auditable, and AI Act exposure acknowledged |
| Priya, CIO | Run cost at scale, latency, operability (who runs this at 2 a.m.), and lock-in addressed, with complexity matched to value |

A design must move all three to meet the mandate. Winning one and ignoring two is a fail. Since the goal is learning rather than competition, "who wins" across different domains is not apples to apples. If you want a competitive element, score against this rubric on two things only: did the notation make the risk visible, and did they parry the live distractor with notation rather than hand-waving.

## Appendix D · Facilitator design map

The kit gaps, the distractors, and the defending cards line up on purpose.

| Kit gap (named on the handout) | Distractor that exploits it | Card that pre-empts it if drawn |
|---|---|---|
| Confidence, act vs defer | D3 Confident Wrong Answer | Grounded RAG, defends safety |
| Human oversight, who approves | D2 AI Act Knock, the wildcard | Agent-Assist, defends oversight |
| Data sensitivity, which arrows carry PII | D1 Data Breach | (no defend card, must be drawn from scratch) |
| Cost and latency | D4 Bill and the Lag | Observability and Evaluation, defends operability |
| Failure and fallback paths | D5 Vendor Moves | Model Gateway, defends vendor change |

Domains, executives, and distractors line up so the union of three reviews covers all five gaps:

| Team | Domain | Presents to | Distractors most likely thrown |
|---|---|---|---|
| A | Customer self-service | Priya | D4, then the D2 wildcard |
| B | Sales, financing, trade-in | Marcus | D1 and D5, then the D2 wildcard |
| C | Service and recall | Helena, with Marcus on D3 | D3, then the D2 wildcard |

D2 is the shared wildcard on purpose: oversight should be askable of everyone, and it guarantees the human-control gap surfaces no matter which way a team built. Data sensitivity has no defend card on purpose, so at least one team has to invent PII notation live.

The traps live in the deck and are never labelled: A2A needs a real counterparty MMG lacks, AI-Assisted Delivery and AI Co-Worker live off the customer runtime, and Custom Fine-Tuning needs a data-science function MMG cannot staff. A team that spends points on these made a category or feasibility error the planes primitive and the honest catch should have caught. Surface it in the close.

Two failure modes to provoke and then name: over-engineering, made costly by the 12-point cap and punished live by D4, and under-ambition, made visible by the mandate and by Helena's simplify-or-scale squeeze.

The through-line: the first vague box hid five risks. The kit made the easy structure visible. The point model forced real trade-offs. The optional distractors proved that the hard, AI-specific risks are exactly the ones notation still struggles with, and the cross-team comparison shows the gaps were placed on purpose. That is the session.

## Appendix E · Flex and contingency

If running long, in this order: drop the optional audience challenge; shorten the close harvest to two teams reporting; trim section 4 drawing by giving the data flow five minutes instead of seven; hold each executive to one distractor plus the wildcard instead of two.

Never cut: the three review rounds, and the reveal in the close.

If running short: let each executive throw a second distractor, extend the cross-comparison, and collect more invented notation. The richest output of this session is the vocabulary the room builds.
