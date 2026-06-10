# Drawing the Unseen: Technology Card Deck

**Scenario:** Meridian Mobility Group (MMG)
**Use:** Block 4 of the session. Groups select a subset of these cards under the point cap to answer the shareholder mandate "embed AI more deeply into the product," then draw the resulting solution architecture and AI data flow using the notation kit.

Accuracy note: cards describe architecture archetypes and where they sit, not feature GA status. Forward-looking productization claims are marked [Inference]. Verify the bleeding-edge ones (Voice, native MCP/A2A support) before fixing any dates with stakeholders.

---

## How the cards work

Each card is one technology approach. There is no single correct set. A strong answer matches ambition (Helena), risk and compliance (Marcus), and cost and operability (Priya) at the same time.

**The point model, all the rules.** Put these on screen for the whole block.

- **Cap.** You have 12 effort points per team. Spend more and Priya walks out.
- **Cost.** Each card shows a cost from 1 to 7. Higher cost means more to build, more to run, and more to govern.
- **Discounts.** Three cards carry a blue star with a minus one. Each lowers the cost of another card by 1: MCP discounts your custom actions and extra integrations, AI-Assisted Delivery discounts every build-heavy card, and the Model Gateway discounts extra model cards. A card never drops below 1 point, and at most one discount applies to any single card.
- **Defends.** Four cards carry a blue star that gives a head start in the review: Grounded RAG defends safety, Agent-Assist defends oversight, Observability and Evaluation defends operability, and the Model Gateway defends a vendor change. A defense is a head start, not immunity. You still have to draw the thing on the diagram for the executive to accept it.
- **The point.** Twelve points is not enough for everything. Choose what actually serves your domain and your three executives, and be ready to defend the trade-offs.

**Two axes that decide everything:** where the component lives (which plane of which diagram), and whether its behaviour is deterministic or probabilistic.

---

# Section A: The Cards

### 01. Prompt Templates (Prompt Builder)
- **Cost:** 1
- **What:** Generative prompts grounded in record and field data, embedded in Flows and Lightning pages. Produces drafts, summaries, and recommendations inside screens people already use.
- **Placement:** Runtime, inside the Salesforce platform. A probabilistic call that crosses the trust boundary and returns into a deterministic Flow or UI. No new system.
- **Appeals to:** Priya (cheap, contained). Helena in part (visible, not headline material).
- **Watch-out:** Output is only as good as the grounding context you pass in. Easy to ship something that reads well and is quietly wrong.

### 02. Einstein Standard Features (Sales and Service)
- **Cost:** 2
- **What:** Out-of-the-box generative features: work and call summaries, reply and knowledge recommendations, email drafting.
- **Placement:** Runtime, native. Vendor-managed probabilistic calls behind the trust boundary. Nothing to architect beyond enablement and data access.
- **Appeals to:** Priya (buy, not build). Marcus (vendor-governed, auditable).
- **Watch-out:** You inherit the vendor's model and behaviour, with limited control over tone, grounding, and edge cases. Satisfies "we use AI," not "we built something differentiated."

### 03. Grounded Retrieval / RAG (Data Cloud and Retrievers)
- **Cost:** 3
- **Bonus:** Defends safety in the review.
- **What:** Ground model answers in curated knowledge, vehicle history, and customer context retrieved at query time, instead of relying on the model's training.
- **Placement:** Runtime. A retrieval step (deterministic search over indexed data) feeding a probabilistic generation step. Leans heavily on Data Cloud. [Inference] The exact retriever and library constructs are evolving.
- **Appeals to:** Marcus (better grounding lowers hallucination risk). Helena (better answers). Priya (reuses the Data Cloud investment).
- **Watch-out:** Retrieval that silently returns nothing, or the wrong slice, degrades answers with no error. Grounding is an architecture problem, not a checkbox.

### 04. Conversational AI Voice
- **Cost:** 5
- **What:** A customer-facing voice agent on the telephony channel. Speech in, agent reasoning, speech out. [Inference] Productization and GA scope move quickly; verify before committing dates.
- **Placement:** Runtime, customer-facing. Sits on the CTI and voice channel in front of an agent or service logic. Adds a speech-to-text stage and a text-to-speech stage on either side of a probabilistic core.
- **Appeals to:** Helena (this is the headline she wants).
- **Watch-out:** The most visible channel is the least forgiving. A wrong or hallucinated spoken answer about a recall or safety item is a brand and liability event, not a UX bug.

### 05. Agentforce Service Agent (autonomous)
- **Cost:** 4
- **What:** An autonomous agent that interprets a request, decides how to handle it, and acts, rather than following a fixed script. [Inference] Internal construct names (topics, sub-agents, actions) are shifting; describe behaviour, not a fixed mechanism.
- **Placement:** Runtime, the heart of the customer experience. A reasoning node (probabilistic, may loop) behind the trust boundary, grounded via retrieval, invoking actions outward.
- **Appeals to:** Helena (the growth story), provided Marcus and Priya are satisfied.
- **Watch-out:** This is the box most teams leave as "magic." It reasons, so its path is not fully predictable. That property has to be visible in the diagram, not hidden inside a cloud.

### 06. Agentforce Custom Actions (Apex / Flow / API)
- **Cost:** 4
- **What:** Custom actions that let the agent actually do things: check inventory in the DMS, book a service bay, raise an order in ERP.
- **Placement:** Runtime. The bridge from agent reasoning (probabilistic) to back-end systems of record (deterministic). Each action is a controlled, typed door out of the agent.
- **Appeals to:** Helena (real outcomes, not just chat). Priya (depends on integration effort). Marcus (each action is an error and attack surface).
- **Watch-out:** An agent with broad actions and weak validation can take real, wrong actions on systems of record. Draw the boundary and the permissions explicitly.

### 07. MCP (Model Context Protocol)
- **Cost:** 4
- **Bonus:** Discount, minus 1 to one custom-action or integration card.
- **What:** An open standard for connecting agents and models to external tools and data through a common interface, instead of bespoke glue per integration. [Inference] Native Salesforce support is evolving; confirm current state.
- **Placement:** Runtime integration layer. A standardized adapter between the agent and external systems and tools. Reduces N bespoke connectors to one protocol.
- **Appeals to:** Priya (less lock-in, less custom integration, future-proofing). Marcus (one governed surface to audit instead of many).
- **Watch-out:** A standard adopted for a single integration is premature. Justify it by breadth, not by novelty.

### 08. A2A (Agent-to-Agent)
- **Cost:** 6
- **What:** A protocol for agents from different systems or vendors to discover each other and collaborate, so MMG's agent can delegate to or negotiate with an external agent.
- **Placement:** Runtime, cross-boundary. Agent-to-agent calls crossing an organizational trust boundary. The most complex orchestration on the board.
- **Appeals to:** Helena (sounds visionary). Rarely the right first move.
- **Watch-out:** If there is no real external agent to talk to, A2A is a slide, not an architecture. Demand a concrete counterparty before drawing it.

### 09. AI-Assisted Delivery (e.g. Claude Code)
- **Cost:** 3
- **Bonus:** Discount, minus 1 to one build-heavy card.
- **What:** Agentic coding and delivery tooling that generates code, tests, and metadata, and reviews changes inside the software development lifecycle.
- **Placement:** Delivery and SDLC plane. IDE, version control, CI/CD, and pipelines. It accelerates how the team builds the product.
- **Appeals to:** Priya (delivery speed and quality). The architects doing the work.
- **Watch-out:** It speeds up build, which is rarely the real bottleneck. Be deliberate about where, and whether, it belongs on a runtime diagram.

### 10. AI Co-Worker (internal agentic assistant, e.g. Cowork)
- **Cost:** 3
- **What:** An agentic assistant for staff knowledge work: research, drafting, analysis, and multi-step internal tasks across documents and tools.
- **Placement:** Employee productivity and internal operations plane. Used by people inside MMG, not by customers.
- **Appeals to:** Priya and team leads (internal efficiency).
- **Watch-out:** Useful, but it is an internal tool, not part of the customer-facing product. Be clear about which diagram it belongs on.

### 11. Predictive Models (propensity, churn, demand)
- **Cost:** 2
- **What:** Non-generative models that score or forecast: likelihood to buy, churn risk, expected service demand, the next best offer. They produce a number or a class, not text.
- **Placement:** Runtime or batch, native via Data Cloud. A scoring node fed by structured data, writing a value back to a record rather than holding a conversation.
- **Appeals to:** Priya (cheap and well understood), Helena (drives upsell and retention), Marcus (a score is explainable and auditable in ways a generation is not).
- **Watch-out:** Not all AI is a language model. A prediction is a different thing from a generated answer and must be drawn as such. Treating a score like a chat reply hides what it actually is.

### 12. Proactive, Event-Triggered Outreach
- **Cost:** 4
- **What:** AI started by a signal rather than a customer question. A telematics fault code or a service-due event triggers an outbound message, offer, or booking.
- **Placement:** Runtime, but the entry point is an event from outside (the telematics platform or a lifecycle rule), not a prompt. The trigger flows in, the AI decides, and it acts outward.
- **Appeals to:** Helena (reaching the customer first), Priya (fewer inbound calls), Marcus (proactive contact on vehicle data raises consent and privacy questions).
- **Watch-out:** The input is not a customer prompt, and most diagrams only draw the prompt-in case. Show where the trigger comes from and what the AI is allowed to do unattended.

### 13. Agent-Assist (advisor copilot)
- **Cost:** 3
- **Bonus:** Defends oversight in the review.
- **What:** AI beside the human advisor in real time: surfacing the answer, drafting the reply, suggesting the next action, while the human stays in control and sends.
- **Placement:** Runtime, internal-facing within the service or sales console. The AI suggests; the human remains the actor of record toward the customer.
- **Appeals to:** Marcus (a human stays in the loop by design), Priya (faster handling without full autonomy risk), Helena in part (efficiency, less of a headline than a customer-facing agent).
- **Watch-out:** Assist versus autonomous is a real architecture fork, not a phase to skip. A human in the loop changes the diagram, the risk, and the timeline. Often the wiser first step.

### 14. Real-Time Translation and Multilingual AI
- **Cost:** 3
- **What:** Serving customers across MMG's eight countries in their own language, including translating into and out of the model and grounding content that may exist in only one language.
- **Placement:** Runtime. A translation step on either side of the AI core, or a multilingual-capable model. Either way it adds stages and calls to the flow.
- **Appeals to:** Helena (one capability across every market), Priya (watch the added cost and latency).
- **Watch-out:** Translation is rarely free or instant, and answers can degrade across languages. Show where it happens and what it costs, instead of assuming the model speaks every language equally well.

### 15. Vision AI (damage and trade-in assessment)
- **Cost:** 4
- **What:** Models that read images: assessing vehicle damage for a trade-in or service intake, reading a VIN or plate, identifying parts.
- **Placement:** Runtime. A vision model node with image data flowing in, distinct from the text path and often a different provider.
- **Appeals to:** Helena (a slick trade-in or intake experience), Priya (faster, more consistent assessment), Marcus (images of vehicles and locations are personal data too).
- **Watch-out:** Images are data with their own sensitivity and their own flow. A vision model is not the same node as a chat model, and the diagram should not blur them into one AI box.

### 16. Model Gateway and Multi-Model Abstraction
- **Cost:** 4
- **Bonus:** Discount, minus 1 to one extra model card. Defends a vendor change in the review.
- **What:** A layer between MMG and the model providers, so the choice of model is a configuration rather than a hard dependency, with routing and fallback across models.
- **Placement:** Runtime infrastructure, between the agent or app and the external models. Behind it, models are interchangeable. Distinct from MCP, which standardises access to tools and data, not the model itself.
- **Appeals to:** Priya (less lock-in, a fallback if a model changes or disappears), Marcus (one place to govern model use).
- **Watch-out:** Without it, the design is welded to one provider. With it drawn, the model becomes a swappable box behind a stable interface. That is the difference between surviving a vendor change and rebuilding.

### 17. AI Observability and Evaluation
- **Cost:** 3
- **Bonus:** Defends operability in the review.
- **What:** The layer that watches the AI in production: grounding and quality checks, hallucination and toxicity detection, cost and latency monitoring, and an evaluation harness for changes before they ship.
- **Placement:** A cross-cutting plane observing the runtime, not in the customer's path. It reads what the AI does and raises alarms.
- **Appeals to:** Priya (knowing it works, and who is paged at 2am), Marcus (evidence the AI behaves and a record when it does not), Helena (fewer public failures).
- **Watch-out:** Most teams draw the happy path and no way to see when it breaks. If the diagram cannot show how you would notice a bad answer, you cannot operate this.

### 18. Custom Model Fine-Tuning
- **Cost:** 7
- **What:** Training or fine-tuning a model on MMG's own data to specialise it for automotive and for MMG's tone and knowledge.
- **Placement:** A data-science and delivery effort upstream of runtime. It produces a model artefact that then has to be hosted, governed, and kept current.
- **Appeals to:** The instinct to build something uniquely MMG. Helena likes the differentiation.
- **Watch-out:** It needs a capable data-science function and sustained investment. Grounding usually delivers the specialisation you actually need without training anything.

---

# Section B: Facilitator Key

*Do not hand this section to participants. No card is labelled a trap on its face; the honest watch-out text and the placement line are the only clues.*

## The traps: cards 08, 09, 10, and 18

Four cards are traps, of three kinds.

Cards 09 (AI-Assisted Delivery) and 10 (AI Co-Worker) are wrong-plane traps: legitimate technologies that belong in the delivery or operations plane, not the customer-facing runtime. Their placement line says so plainly. Groups under time pressure grab them for the current, impressive names and try to place them in the runtime diagram. Card 09 also carries a real discount bonus, which is the right reason to take it; the wrong reason is to draw it inside the customer runtime.

Card 08 (A2A) is a counterparty trap. The protocol is real, but the scenario gives MMG no concrete external agent to talk to. A team that spends 6 points here has bought an integration with nobody.

Card 18 (Custom Fine-Tuning) is a constraint-violation trap. Nothing on the card flags it. The scenario does: MMG has no in-house machine learning function and has decided not to train models. A group that picks it did not reread the brief, and Grounded RAG (03) usually delivers the specialisation they wanted without any of it.

This is a central teaching moment of Block 4 and the debrief. Where a component goes is a real architecture decision, not a formatting afterthought. The constraints are written in the brief, and reading them is part of the job. Do not correct any of these during the build. Let them surface in the pitch or the debrief.

## The shape of a strong answer

There is no single correct set, but a defensible north star for MMG looks like a staged path, not a big-bang:

1. Quick value, low risk: cards 01 and 02, with 03 for grounding (and its safety defense).
2. Keep a human in control first: card 13 (Agent-Assist) is often the wiser opening move before any autonomous customer-facing agent. It satisfies Marcus and defuses the hallucination problem by design, and its oversight defense pays for itself in the review.
3. A real differentiator: card 05 (autonomous agent), grounded by 03, governed by the trust boundary, made useful by 06 (Custom Actions) into the DMS and scheduling. Stage it after Assist has proven the grounding.
4. Use the data you already have: card 11 (Predictive) for the forecasting and upsell the reporting requirements ask for, and card 12 (Proactive) to act on telematics. These meet the mandate with non-generative AI that is cheaper and more explainable than a chat agent.
5. Staged ambition: card 04 (Voice) as a later channel, not day one.
6. Protect yourself: card 16 (Model Gateway) as the lock-in hedge with its vendor-change defense, and card 17 (Observability) so the thing can actually be operated and defended for operability. Neither is glamorous; both are what Priya needs.
7. Strategic, only if justified: card 07 (MCP) for integration breadth (and its action discount), card 08 (A2A) only with a concrete counterparty.

Cards 08, 09, 10, and 18 do not belong in the customer runtime when picked for the wrong reason: 08 has no counterparty, 09 and 10 are delivery and internal tools, and 18 contradicts a stated constraint.

## The two failure modes to provoke and then name

- **Over-engineering:** A2A plus Voice plus a full autonomous agent on day one, ignoring Priya's cost and operability reality and Marcus's risk. Glamorous, undeliverable, and almost always over the cap.
- **Under-ambition:** Only the cheapest cards. Safe, cheap, well under the cap, but it does not meet Helena's growth mandate. "We added summaries" is not a strategy.

The sweet spot is the staged middle. Reward groups that can say no to a shiny card and justify it, and groups that read a bonus star correctly: a discount is a real saving, a defense is a real head start, neither is a free pass.

## Per-CxO acceptance rubric

This doubles as the judging criteria for the pitch in the review board. The facilitators voice these when they play the board.

- **Helena (CEO), says yes if:** there is a visible, customer-facing capability that supports the growth narrative, with a credible timeline.
- **Marcus (CISO/CDO), says yes if:** PII handling, the trust boundary, grounding, and human oversight are explicit and auditable, and AI Act exposure is acknowledged rather than ignored.
- **Priya (CIO), says yes if:** run cost at scale, latency, operability (who runs this at 2am), and lock-in are addressed, and complexity matches value. The team stayed under 12 points or argued credibly for the over-spend.

A pitch that wins one persona and ignores the other two has failed the exercise. The diagrams are the evidence that earns all three.
