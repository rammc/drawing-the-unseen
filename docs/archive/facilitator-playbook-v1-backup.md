# Drawing the Unseen: Facilitator Playbook

How to Diagram AI in Your Salesforce Architecture
90 minutes · ~15 participants · 3 groups of 5 · Architect Dreamin

---

## The shape

Three blocks plus a short close. Each block is one act, not a list of steps.

| Block | Start | Min | What happens | Output |
|---|---|---|---|---|
| 1 · Setting the Scene | 0:00 | 10 | MMG landscape, the mandate, the three CxOs | Shared context and tension |
| 2 · AI into the Solution | 0:10 | 35 | Choose tech under a budget, hit the magic box, get the kit, redraw honestly | Solution architecture diagram |
| 3 · Distractors | 0:45 | 35 | Draw the data flow, absorb distractors, defend to the board | Data flow diagram and defended strategy |
| Close · Debrief | 1:20 | 10 | Where the notation ran out, the reveal, the takeaway | Notation vocabulary, community output |

What every group leaves with: a solution architecture diagram (Block 2), a data flow diagram (Block 3), and the reusable notation kit. These three are the Abstract.

---

## Materials checklist

Per table (one set per group): pre-drawn MMG landscape worksheet (A2 or A3, surrounding systems drawn, AI not drawn); one tech card deck (10 cards); one CxO acceptance rubric (also the pitch checklist); two marker colours, black plus one accent; blank flip-chart sheets for the data flow diagram and the pitch.

Per person: the notation kit handout.

Facilitator-held: the five distractor cards (dealt in two waves); a flip chart with five labelled columns for the debrief; a timer visible to the room.

Still to produce before the session: the landscape worksheet and the printed distractor cards. Content for both is in this playbook.

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

# Block 2 · AI into the Solution (0:10 to 0:45)

Goal: choose a defensible set of technologies, discover the magic-box problem when you try to present it, and learn to draw AI honestly. Output: the solution architecture diagram.

Two challenges run inside this block: not every technology fits, and however you choose, you have to present it to a board that will not accept a vague box.

### Beat 1: choose, then try to present it (0:10 to 0:25)

You do: hand out the tech card deck and announce the complexity budget.

You say:
> "Ten technologies, from configuration to cross-vendor orchestration. Pick the set that meets the mandate. There is a budget: Low costs 1 point, Moderate 2, High 3, Very High 4, and you have 7 points. Spend more and Priya walks out."

Groups (about 10 minutes): read the cards, debate the fit, commit to a set within the budget.

Then, with about five minutes left in the beat:
> "Now draw it for the board, on your landscape."

Groups attempt it. Their boxes carry real names, Agentforce, RAG, an agent, but show nothing about what those things do. Reasoning, grounding, and where data crosses are all invisible.

The hook (last two minutes, hold up the sheets):
> "You picked real technology. Your diagram still cannot show what any of it does, what it touches, or where the customer's data goes. That is the presentation problem, and it is the same vague box we draw in every real review."

### Beat 2: the notation kit (0:25 to 0:33)

You do: hand out the kit. Walk the five primitives fast, each tied to the box they just drew. Use the Einstein Trust Layer as the worked example for the boundary.

You say (compressed):
> "Black is for conventions you already use. The accent colour, your second marker, is for everything new and AI-specific."
> "Nodes: is the box deterministic, same in same out, or probabilistic, where the same input can vary? Mark the probabilistic ones."
> "The agent is not one call. It reasons and may loop. Draw the loop."
> "Grounding is not data flow. It shapes the answer without being passed through, and retrieval is a deterministic search that can quietly return nothing."
> "The trust boundary is the one that matters most for Marcus. The Einstein Trust Layer is the canonical example: the instant data touches a model, it is masked, ground-checked, kept out of retention, and logged. Draw it as a place, not a line you wave at."
> "Every component sits on exactly one plane: runtime, delivery, or operations."
> "This kit is version 0.1 and deliberately incomplete. Part of your job today is to notice where it runs out."

### Beat 3: redraw it honestly (0:33 to 0:45)

Groups redraw the solution on the landscape using the kit. Probabilistic nodes marked, the agent loop drawn, grounding shown, the trust boundary placed, every component on a plane. This is the solution architecture diagram.

Watch-out: this is the tightest stretch for its value. Circulate and keep groups moving: pick, do not perfect. Let two failure modes happen rather than preventing them:
- over-engineering, a group that blew the budget on the shiniest cards
- the plane trap, a group that puts an AI-assisted delivery tool or an internal co-worker assistant in the customer runtime

Both surface in the close. Do not correct them now.

---

# Block 3 · Distractors (0:45 to 1:20)

Goal: stress the solution with constraints that hit exactly where the kit runs out, then defend the changed approach. Output: the data flow diagram and a defended strategy.

### Beat 1: draw the data flow (0:45 to 0:51)

You say:
> "Zoom into the box. On a fresh sheet, draw the data flow through your AI subsystem: the prompt going in, the trust boundary, grounding and retrieval, the model call, the response coming back, and what gets logged. This is the diagram Marcus reads line by line."

Groups (6 minutes): draw the AI subsystem data flow with the kit. This is the data flow diagram, and it gives the distractors something to bite.

Watch-out: subsystem only, not the whole landscape. Six minutes works only if they zoom in.

### Beat 2: the distractors (0:51 to 1:04)

Mechanic: two waves. Deal one card per group in wave 1. In wave 2, hand-pick the card that targets the specific weakness you have watched each group build. Read each card aloud with the CxO who escalates it.

You say (before dealing):
> "New information just arrived, the way it always does after the architecture is drawn. React on the diagram, not in conversation. If your notation cannot show it, invent something and tell us about it later."

Groups adapt both diagrams. The five cards are in the distractor deck below.

Suggested coverage so all five surface (tunable):
- Group 1: wave 1 Data Breach, wave 2 The Bill and the Lag
- Group 2: wave 1 The AI Act Knock, wave 2 The Vendor Moves
- Group 3: wave 1 The Confident Wrong Answer, wave 2 your choice based on their design

### Beat 3: defend to the board (1:04 to 1:20)

Build (5 minutes), three slides:
- Slide 1 for Helena: what you are building and why, with the solution diagram
- Slide 2 for Marcus: where the data goes and where a human stays in control, with the data flow diagram
- Slide 3 for Priya: the cost and operability posture, and how you absorbed the two curveballs

Pitches (11 minutes): three groups, about three and a half minutes each. Facilitators play the CxO board and ask one pointed question per persona from the rubric.

Watch-out: protect the pitches. If time is short, cut the close, not this. A pitch that wins one persona and ignores the other two has failed; say so kindly when it happens.

---

# Close · Debrief (1:20 to 1:30)

Goal: harvest where the notation ran out, reveal the design, and leave with a thesis.

Harvest (4 minutes): on a flip chart with five columns, ask each group to name the one place their notation ran out. Tally each answer under the matching gap.

The reveal (3 minutes):
> "The kit was deliberately incomplete. The distractors were built to hit exactly the gaps it does not cover: confidence, human oversight, data sensitivity, cost and latency, failure and fallback. You did not fail to draw these. The conventions do not exist yet. That is the finding: this is where AI architecture notation still has to evolve."

The traps (1 minute): ask whether anyone placed a delivery tool or an internal assistant in the customer runtime. Surface it without blame. The lesson: where a component goes is a real architecture decision.

Takeaway and collect (2 minutes):
> "Good AI notation is not decoration. It is risk management you can see. Every distractor today was a risk your first vague box hid. Take the kit, plus the gaps you discovered, as your starting vocabulary."

Collect the notation the room invented: a symbol for an agent that must defer, a human-approval gate, a PII-bearing arrow, a cost per call. This is the constructive feedback to Salesforce and the community output.

---

# The distractor deck

Read the participant side aloud. Keep the key.

### D1 · Data Breach (Marcus escalates)
Participant:
> "A journalist publishes a screenshot from your model provider's logs. It shows a named customer's full service history and home address. The provider retained it. The board meets in twenty minutes."
> Your diagram must now show: where customer data crosses into the model, what is masked before it does, what is retained or logged and by whom, and which arrows carry PII end to end.

Key: exploits the data sensitivity gap; weaponises the data flow diagram from Beat 1. Good response: PII masked at the trust boundary before the model call, zero retention with the provider, sensitive arrows marked distinctly, logging scoped to non-PII.

### D2 · The AI Act Knock (Marcus and Legal escalate)
Participant:
> "Legal has reviewed the pilot. Because the agent gives recall and safety guidance, it may carry higher-risk obligations under the EU AI Act: transparency, human oversight, traceability. The board wants to see, on the diagram, where a human stays in control."
> Your diagram must now show: where the customer is told they are talking to AI, which agent actions need human approval before they commit, and how decisions are logged for traceability.

Key: exploits the human oversight gap. Good response: a human-in-the-loop checkpoint on high-stakes actions, an explicit AI-disclosure node, an audit trail. Forces oversight notation the kit lacks.

### D3 · The Confident Wrong Answer (Marcus and Helena both feel it)
Participant:
> "In the pilot, the agent told a customer with worn brake pads that everything looked fine and they could skip the inspection. It was wrong. No one was hurt. This time. And it sounded completely confident."
> Your diagram must now show: when the agent may answer versus when it must defer or escalate, what grounding it needs before giving safety guidance, and what happens when it is unsure.

Key: exploits the confidence gap (act vs defer). Good response: a confidence or grounding gate before high-stakes answers, a defer-and-escalate path below threshold, stricter grounding for safety topics.

### D4 · The Bill and the Lag (Priya escalates)
Participant:
> "Finance modelled it at projected volume. The design costs four times the contact-centre savings it was meant to deliver, and voice replies lag six seconds. Priya wants the number to work before this leaves the room."
> Your diagram must now show: where the expensive model calls are, what could use a cheaper model or none, where latency accumulates, and what you would cut or cache.

Key: exploits the cost and latency gap. Good response: model tiering (cheap model for triage, expensive only for hard cases), removing gratuitous LLM calls, caching, scoping voice to where it pays. Punishes the over-engineered design directly.

### D5 · The Vendor Moves (Priya and Procurement escalate)
Participant:
> "Your model provider announces a breaking API change and a thirty percent price rise, effective in ninety days. Procurement asks two questions: how locked in are we, and what happens if a model we depend on simply goes away?"
> Your diagram must now show: where you are coupled to one provider, what sits behind a stable interface, and the fallback path if a model becomes unavailable.

Key: exploits the failure and fallback gap. Good response: the model behind a stable interface or gateway (where MCP and standardisation pay off), a documented fallback model, graceful degradation. Rewards groups that picked MCP for the right reason.

---

# CxO acceptance rubric

Judges pitches and voices the board. Also given to groups as the pitch checklist.

| Persona | Says yes only if the pitch shows |
|---|---|
| Helena (CEO) | A visible, customer-facing capability that supports the growth story, with a credible timeline |
| Marcus (CISO and CDO) | PII handling, the trust boundary, grounding, and human oversight made explicit and auditable, and AI Act exposure acknowledged |
| Priya (CIO) | Run cost at scale, latency, operability (who runs this at 2 a.m.), and lock-in addressed, with complexity matched to value |

A pitch must move all three. Winning one and ignoring two is a fail.

---

# Facilitator design map

The kit gaps map one to one to the distractors:

| Kit gap (named on the handout) | Distractor that exploits it |
|---|---|
| Confidence: act vs defer | D3 Confident Wrong Answer |
| Human oversight: who approves | D2 AI Act Knock |
| Data sensitivity: which arrows carry PII | D1 Data Breach |
| Cost and latency | D4 Bill and the Lag |
| Failure and fallback paths | D5 Vendor Moves |

The two engineered traps live in the tech deck (cards 09 and 10: AI-assisted delivery, internal co-worker). Their placement clue is honest, but they are never labelled traps. A group that puts either in the customer runtime made a category error the planes primitive should have caught. Surface it in the close.

Two failure modes to provoke and then name: over-engineering, made costly by the budget, and under-ambition, made visible by the mandate.

The through-line: the first vague box hid five risks. The kit made the easy structure visible. The distractors proved that the hard, AI-specific risks are exactly the ones notation still struggles with. That is the session.

---

# Flex and contingency

If running long, in this order: shorten the close harvest to two groups reporting; drop the Beat 1 hold-up share in Block 2 to one minute; pull two minutes from the pitch build into Block 3 Beat 1 if a group is behind on the data flow.

Never cut: the pitches, and the reveal in the close.

If running short: extend the harvest and collect more invented notation. The richest output of this session is the vocabulary the room builds.
