# Drawing the Unseen: Facilitator Playbook

How to Diagram AI in Your Salesforce Architecture
90 minutes · ~15 participants · 3 groups of 5 · Architect Dreamin

Version 2: live judging. The board throws distractors on the fly during the presentations rather than dealing them in waves, and each team builds for a different MMG domain so the three architectures and pitches stay distinct.

---

## The shape

Three blocks plus a short close. Each block is one act, not a list of steps.

| Block | Start | Min | What happens | Output |
|---|---|---|---|---|
| 1 · Setting the Scene | 0:00 | 10 | MMG landscape, the mandate, the three CxOs | Shared context and tension |
| 2 · Build | 0:10 | 40 | Assign domains, choose tech under a budget, hit the magic box, get the kit, draw the solution architecture and the data flow | Two diagrams per team: solution architecture and data flow |
| 3 · The Review Board | 0:50 | 30 | Teams present their domain in different formats, the board throws distractors live, the audience challenges | A defended strategy |
| Close · Debrief | 1:20 | 10 | Where the notation ran out, the reveal, the cross-team comparison, the takeaway | Notation vocabulary, community output |

What every group leaves with: a solution architecture diagram and a data flow diagram (both built in Block 2, both scoped to their domain), and the reusable notation kit. These three are the Abstract.

Budgets are tunable [Inference]. Version 2 deliberately moves time out of structured distractor waves and into building both diagrams and defending them live.

---

## Materials checklist

Per table (one set per group): pre-drawn MMG landscape worksheet (A2 or A3, surrounding systems drawn, AI not drawn); one tech card deck (the cards); one CxO acceptance rubric, which is also the pitch checklist; one domain card (the team's assigned slice of MMG); one format card (how this team must present in Block 3); two marker colours, black plus one accent; blank flip-chart sheets for the data flow diagram and the presentation.

Per person: the notation kit handout.

Judges-held (the three facilitators): one judge card each (Helena, Marcus, Priya); the distractor deck, to read aloud when a card is thrown; a five-column flip chart for the debrief; a timer visible to the room.

Audience: three perspective cards (Customer, Regulator, Operations) handed to the non-presenting teams during each review round.

Still to produce before the session: the landscape worksheet, the printed distractor cards, the three judge cards, the domain cards, the format cards, and the perspective cards. Content for all of these is in this playbook.

---

# Block 1 · Setting the Scene (0:00 to 0:10)

Goal: set the scenario and the tension fast. No drawing in this block.

You do: present MMG and its landscape, put the mandate on screen, introduce the three CxOs.

You say:
> "Meridian Mobility Group: a European automotive retail and service group. Salesforce Automotive Cloud is the centre. Around it sit the eight systems on your worksheet. The shareholders have given the board one instruction."

> "Embed AI more deeply into the product to drive growth and efficiency."

> "That is the whole brief. It is vague on purpose, because your three executives read it three different ways."

- Helena Vance, CEO, ambition: "I want customers talking to our AI by Q3, and I want it in the announcement."
- Marcus Reinhardt, CISO and CDO, risk: "Where does the customer's data go the second it touches a model, and who can prove it?"
- Priya Anand, CIO, feasibility and cost: "Show me the cost at 10,000 conversations a day, and who operates this at 2 a.m."

> "Your job today is to satisfy all three. Not one. All three."

Watch-out: hold this to ten minutes. The scenario earns its weight in Block 2, not here.

---

# Block 2 · Build (0:10 to 0:50)

Goal: choose a defensible set of technologies for your domain, discover the magic-box problem when you try to present it, learn to draw AI honestly, and produce both required diagrams. Output: the solution architecture diagram and the data flow diagram.

### Beat 0: assign domains (first 60 seconds of the block)

You do: give each team a domain card. Same MMG, same landscape, but each team builds the AI architecture for one slice. This is what keeps the three architectures, and later the three pitches, genuinely different.

| Team | Domain card | Whose problem it is most |
|---|---|---|
| A | Customer self-service: chat and voice, deflection at scale | Priya |
| B | Sales: financing and trade-in | Marcus |
| C | Service and recall | Helena |

You say:
> "You are all inside the same MMG, but each team owns one part of it. Build your AI architecture for your slice. At the board, you present your slice."

### Beat 1: choose, then try to present it (0:11 to 0:25)

You do: announce the complexity budget.

You say:
> "Pick the set of technologies that meets the mandate for your domain. There is a budget: Low costs 1 point, Moderate 2, High 3, Very High 4, and you have 7 points. Spend more and Priya walks out."

Groups (about 10 minutes): read the cards, debate the fit for their domain, commit to a set within the budget.

Then, with about four minutes left in the beat:
> "Now draw it for the board, on your landscape."

Groups attempt it. Their boxes carry real names, Agentforce, RAG, an agent, but show nothing about what those things do. Reasoning, grounding, and where data crosses are all invisible.

The hook (last two minutes, hold up the sheets):
> "You picked real technology. Your diagram still cannot show what any of it does, what it touches, or where the customer's data goes. That is the presentation problem, and it is the same vague box we draw in every real review."

### Beat 2: the notation kit (0:25 to 0:31)

You do: hand out the kit. Walk the five primitives fast, each tied to the box they just drew. Use the Einstein Trust Layer as the worked example for the boundary.

You say (compressed):
> "Black is for conventions you already use. The accent colour, your second marker, is for everything new and AI-specific."
> "Nodes: is the box deterministic, same in same out, or probabilistic, where the same input can vary? Mark the probabilistic ones."
> "The agent is not one call. It reasons and may loop. Draw the loop."
> "Grounding is not data flow. It shapes the answer without being passed through, and retrieval is a deterministic search that can quietly return nothing."
> "The trust boundary is the one that matters most for Marcus. The Einstein Trust Layer is the canonical example: the instant data touches a model, it is masked, ground-checked, kept out of retention, and logged. Draw it as a place, not a line you wave at."
> "Every component sits on exactly one plane: runtime, delivery, or operations."
> "This kit is version 0.1 and deliberately incomplete. Part of your job today is to notice where it runs out."

### Beat 3: draw the solution architecture (0:31 to 0:43)

Groups redraw the solution on the landscape using the kit. Probabilistic nodes marked, the agent loop drawn, grounding shown, the trust boundary placed, every component on a plane. This is the solution architecture diagram.

### Beat 4: draw the data flow (0:43 to 0:50)

You say:
> "Now zoom into the box. On a fresh sheet, draw the data flow through your AI subsystem: the prompt going in, the trust boundary, grounding and retrieval, the model call, the response coming back, and what gets logged. This is the diagram Marcus reads line by line, and the one the board will push on hardest."

Groups (about 7 minutes): draw the AI subsystem data flow with the kit. Subsystem only, not the whole landscape.

Watch-out: this whole block is the tightest stretch for its value, and it now carries two diagrams. Circulate and keep groups moving: pick, do not perfect. Let two failure modes happen rather than preventing them:
- over-engineering, a group that blew the budget on the shiniest cards
- the plane trap, a group that puts an AI-assisted delivery tool or an internal co-worker assistant in the customer runtime

Both surface in the close. Do not correct them now.

---

# Block 3 · The Review Board (0:50 to 1:20)

Goal: each team presents its domain architecture and defends it against curveballs the board throws live, aimed exactly where the notation is weakest. Output: a defended strategy. Both diagrams already exist from Block 2.

How the live judging works, and why it is disciplined rather than chaotic:
- Each persona owns a small set of distractors (see Judge Cards). A judge throws one only when the team's diagram invites it, that is, when the diagram cannot answer it. Throwing the curveball the notation cannot answer is the diagnostic moment, and it is the skill you are modelling.
- Cap: at most two distractors per team, plus the oversight wildcard (D2), which any judge may throw at any team at any time.
- When you throw a card, read its participant side aloud from the distractor deck, then make the team respond on the diagram, not in conversation.

### Beat 1: prep in your assigned format (0:50 to 0:55)

Each team assembles its presentation in the format on its format card. Five minutes, no new analysis, just shape what they already built.

### Beat 2: three review rounds (0:55 to 1:19)

About eight minutes per team: roughly four to present, four to be grilled. For each round:
1. The team presents its domain architecture in its assigned format.
2. The board grills. Each judge may throw an owned distractor if the diagram invites it, capped at two for the team, with the oversight wildcard always available.
3. One audience challenge. The two non-presenting teams hold perspective cards; one of them poses a single challenge from its role (Customer, Regulator, or Operations).
4. Rotate the signature opener. Each judge opens each round with a different one of their signature questions, so the three rounds feel distinct.

| Team | Domain | Primary judge | Sharpest live distractor | Presentation format | Audience lens most likely to bite |
|---|---|---|---|---|---|
| A | Customer self-service | Priya | D4, cost and latency at 8M contacts | Three-slide board pitch | Operations |
| B | Sales, financing, trade-in | Marcus | D1 PII, plus D5 model lock-in | Live whiteboard, no slides | Regulator |
| C | Service and recall | Helena | D3, a confident wrong answer on a safety question | Walk one journey end to end | Customer |

The formats are not arbitrary. The board pitch suits Team A's deflection-and-cost story for Priya. The live whiteboard suits Marcus interrogating Team B's data flow line by line. The single-journey walk for Team C is literally the recall question, "is my car safe to drive?", which is exactly where the D3 confidence distractor and Helena's announcement risk collide.

Watch-out: protect the rounds. If time is short, cut the close, not this. A presentation that wins one persona and ignores the other two has failed; say so kindly when it happens. Keep one eye on the two-distractor cap so a strong team does not get buried.

### The formats (one card per team)

- Team A, three-slide board pitch: slide for Helena (what and why, with the solution diagram), slide for Marcus (where the data goes and where a human stays in control, with the data flow), slide for Priya (cost and operability posture).
- Team B, live whiteboard: no slides. Present at the data flow sheet and redraw the changes as the board pushes. Rewards a team that can think in notation under pressure.
- Team C, one journey end to end: narrate the recall question from the customer's first message to the resolution, saying at each step what the customer experiences and what the architecture does, including the moment the agent must defer to a human.

---

# Close · Debrief (1:20 to 1:30)

Goal: harvest where the notation ran out, reveal the design, and leave with a thesis. The cross-team comparison is the new centrepiece.

Harvest (4 minutes): on a flip chart with five columns, ask each group to name the one place their notation ran out. Tally each answer under the matching gap.

The cross-comparison (the gold): because the teams had different domains, they hit different gaps. Name it out loud:
> "Team C had to invent a confidence symbol for a safety answer that Team A never needed. Team B needed a way to mark PII on an arrow that Team A's diagram never had. Team A needed a cost-per-call notation the others could ignore. Put together, your three boards just covered all five gaps. That was the design."

The reveal (2 minutes):
> "The kit was deliberately incomplete, and the distractors were aimed at exactly the gaps it does not cover: confidence, human oversight, data sensitivity, cost and latency, failure and fallback. You did not fail to draw these. The conventions do not exist yet. That is the finding: this is where AI architecture notation still has to evolve, from version 0.1 toward version 1.0."

The traps (1 minute): ask whether anyone placed a delivery tool or an internal assistant in the customer runtime. Surface it without blame. The lesson: where a component goes is a real architecture decision.

Takeaway and collect (3 minutes):
> "Good AI notation is not decoration. It is risk management you can see. Every distractor today was a risk your first vague box hid. Take the kit, plus the gaps you discovered, as your starting vocabulary."

Collect the notation the room invented: a symbol for an agent that must defer, a human-approval gate, a PII-bearing arrow, a cost per call. This is the constructive feedback to Salesforce and the community output.

---

# Judge cards (one per judge)

Print one card per judge. Each is self-contained: stance, the curveballs you own, when to throw them, your signature openers, and the single condition under which you say yes. The rule on every card: throw the curveball the team's diagram cannot answer, and stop at two per team.

---

### JUDGE CARD · Helena Vance, CEO

Stance: ambition and story. You already promised the board AI by Q3. You want a headline, and you do not want to hear "it depends."

You own:
- The Q3 Promise. "I told the board this ships in Q3. Show me on the diagram what is live by then and what is not." Throw when a team shows a big-bang design with no phasing. Forces a staged roadmap.
- The Simplify-or-Scale squeeze. To an over-built design: "This is a science project. Will a customer ever feel it?" To a thin one: "Is this all the shareholders get for the investment?" Throw the half that matches what you see.
- (Shared with Marcus) The story angle on D3. "If this gives a wrong safety answer in week one, my announcement becomes the story. What on this page stops that?" Throw at any safety-touching design, especially Team C.

Signature openers (rotate one per round): "Where is my headline on this page?" · "What can I announce, and when?" · "Put me on stage in Q3. What do I say?"

You say yes only if: a visible, customer-facing capability supports the growth story, with a credible, phased timeline.

---

### JUDGE CARD · Marcus Reinhardt, CISO and CDO

Stance: risk and proof. Nothing is safe until the diagram proves it. "Where does the data go the second it touches a model, and who can prove it?"

You own:
- D1 Data Breach. Throw when the data flow does not clearly mask PII before the model, when PII-carrying arrows are undifferentiated, or when retention and logging are unshown.
- D2 The AI Act Knock, your wildcard. You may throw this at ANY team at any time. Throw when human oversight, AI disclosure, or traceability is missing from a design that gives advice or takes action.
- (Shared with Helena) D3 the risk angle. Throw on any safety or recall guidance with no confidence or grounding gate before the answer.

Signature openers (rotate): "Walk me to the exact line where a customer's data crosses into a model." · "Who is accountable when this is wrong, and where is that on the page?" · "Show me where a human can still say no."

You say yes only if: PII handling, the trust boundary, grounding, and human oversight are explicit and auditable, and AI Act exposure is acknowledged.

---

### JUDGE CARD · Priya Anand, CIO

Stance: feasibility and cost. You operate this at 2 a.m. "Show me the cost at 10,000 conversations a day, and who runs it."

You own:
- D4 The Bill and the Lag. Throw when the design routes everything through the expensive model, adds gratuitous model calls, or puts voice everywhere without justifying the latency and the cost.
- D5 The Vendor Moves. Throw when the design is coupled to one provider with no stable interface or gateway, and no fallback if a model disappears.

Signature openers (rotate): "What does this cost me per conversation, and where on the diagram is the expensive call?" · "Your model vendor doubles the price in ninety days. What changes on this page?" · "It is 2 a.m. and the model is down. What does the customer get?"

You say yes only if: run cost at scale, latency, operability, and lock-in are addressed, with complexity matched to value.

---

# The distractor deck

Version 2: these are no longer dealt in waves. Each card is owned by a judge (see Judge Cards) and thrown live, read aloud, when the team's diagram invites it. Cap two per team, plus the D2 oversight wildcard.

### D1 · Data Breach (owned by Marcus)
Participant:
> "A journalist publishes a screenshot from your model provider's logs. It shows a named customer's full service history and home address. The provider retained it. The board meets in twenty minutes."
> Your diagram must now show: where customer data crosses into the model, what is masked before it does, what is retained or logged and by whom, and which arrows carry PII end to end.

Throw when: the data flow does not mask PII before the model, or PII arrows are undifferentiated. Good response: PII masked at the trust boundary before the model call, zero retention with the provider, sensitive arrows marked distinctly, logging scoped to non-PII.

### D2 · The AI Act Knock (owned by Marcus, the wildcard, any team)
Participant:
> "Legal has reviewed the pilot. Because the agent gives recall and safety guidance, it may carry higher-risk obligations under the EU AI Act: transparency, human oversight, traceability. The board wants to see, on the diagram, where a human stays in control."
> Your diagram must now show: where the customer is told they are talking to AI, which agent actions need human approval before they commit, and how decisions are logged for traceability.

Throw when: any team's design gives advice or takes action without visible oversight, disclosure, or an audit trail. Good response: a human-in-the-loop checkpoint on high-stakes actions, an explicit AI-disclosure node, an audit trail.

### D3 · The Confident Wrong Answer (shared by Marcus and Helena)
Participant:
> "In the pilot, the agent told a customer with worn brake pads that everything looked fine and they could skip the inspection. It was wrong. No one was hurt. This time. And it sounded completely confident."
> Your diagram must now show: when the agent may answer versus when it must defer or escalate, what grounding it needs before giving safety guidance, and what happens when it is unsure.

Throw when: a design gives safety or recall guidance with no confidence or grounding gate. Good response: a confidence or grounding gate before high-stakes answers, a defer-and-escalate path below threshold, stricter grounding for safety topics.

### D4 · The Bill and the Lag (owned by Priya)
Participant:
> "Finance modelled it at projected volume. The design costs four times the contact-centre savings it was meant to deliver, and voice replies lag six seconds. Priya wants the number to work before this leaves the room."
> Your diagram must now show: where the expensive model calls are, what could use a cheaper model or none, where latency accumulates, and what you would cut or cache.

Throw when: everything routes through the expensive model, or voice is everywhere without justification. Good response: model tiering, removing gratuitous model calls, caching, scoping voice to where it pays.

### D5 · The Vendor Moves (owned by Priya)
Participant:
> "Your model provider announces a breaking API change and a thirty percent price rise, effective in ninety days. Procurement asks two questions: how locked in are we, and what happens if a model we depend on simply goes away?"
> Your diagram must now show: where you are coupled to one provider, what sits behind a stable interface, and the fallback path if a model becomes unavailable.

Throw when: the design couples directly to one provider with no gateway and no fallback. Good response: the model behind a stable interface or gateway, a documented fallback model, graceful degradation.

---

# CxO acceptance rubric

Judges the presentations and voices the board. Also given to groups as the pitch checklist.

| Persona | Says yes only if the presentation shows |
|---|---|
| Helena (CEO) | A visible, customer-facing capability that supports the growth story, with a credible, phased timeline |
| Marcus (CISO and CDO) | PII handling, the trust boundary, grounding, and human oversight made explicit and auditable, and AI Act exposure acknowledged |
| Priya (CIO) | Run cost at scale, latency, operability (who runs this at 2 a.m.), and lock-in addressed, with complexity matched to value |

A presentation must move all three. Winning one and ignoring two is a fail.

Fairness note: with different domains, "who wins" is no longer apples to apples. Since the goal is learning rather than competition, that is fine. If you want a competitive element, score against this shared rubric on two things only: did the notation make the risk visible, and did they parry the live distractor with notation rather than hand-waving.

---

# Facilitator design map

The kit gaps map one to one to the distractors:

| Kit gap (named on the handout) | Distractor that exploits it |
|---|---|
| Confidence: act vs defer | D3 Confident Wrong Answer |
| Human oversight: who approves | D2 AI Act Knock (the wildcard) |
| Data sensitivity: which arrows carry PII | D1 Data Breach |
| Cost and latency | D4 Bill and the Lag |
| Failure and fallback paths | D5 Vendor Moves |

And in Version 2, domains, judges, and distractors line up so the union of three grillings covers all five gaps:

| Team | Domain | Primary judge | Distractors most likely thrown |
|---|---|---|---|
| A | Customer self-service | Priya | D4, then D2 wildcard |
| B | Sales, financing, trade-in | Marcus | D1 and D5, then D2 wildcard |
| C | Service and recall | Helena (with Marcus) | D3, then D2 wildcard |

D2 is shared on purpose: oversight should be askable of everyone, and it guarantees the human-control gap surfaces no matter which way a team built.

The two engineered traps live in the tech deck (the AI-assisted delivery card and the internal co-worker card). Their placement clue is honest, but they are never labelled traps. A group that puts either in the customer runtime made a category error the planes primitive should have caught. Surface it in the close.

Two failure modes to provoke and then name: over-engineering, made costly by the budget and punished live by D4, and under-ambition, made visible by the mandate and by Helena's simplify-or-scale squeeze.

The through-line: the first vague box hid five risks. The kit made the easy structure visible. The live distractors proved that the hard, AI-specific risks are exactly the ones notation still struggles with, and the cross-team comparison shows the gaps were placed on purpose. That is the session.

---

# Flex and contingency

If running long, in this order: drop the audience challenge in one or two rounds; shorten the close harvest to two groups reporting; trim the Block 3 prep to four minutes; hold each judge to one distractor plus the wildcard instead of two.

Never cut: the three review rounds, and the reveal in the close.

If running short: let the board throw the second distractor it was holding, extend the cross-comparison, and collect more invented notation. The richest output of this session is the vocabulary the room builds.
