# Meridian Mobility Group (MMG)

Workshop Scenario · Drawing the Unseen: How to Diagram AI in Your Salesforce Architecture
Architect Dreamin · 90 minutes · groups of 5

---

## Using this scenario

Your group has a realistic Salesforce landscape and a vague instruction from the top: put more AI into it. Over the session you will decide which AI technologies fit, draw the solution so a board can actually understand it, and defend that solution when reality intervenes.

This is a workshop, not an exam. Where a requirement is not stated, make a reasonable assumption and note it. You cannot ask the fictional stakeholders clarifying questions. You will not be judged on the tool you draw with, only on whether your diagrams represent the AI honestly and whether your approach survives the executive board.

---

## Project Overview

Meridian Mobility Group (MMG) is one of Europe's larger automotive retail and service groups. It sells and services vehicles across eight countries in Western, Central, and Northern Europe through roughly 600 dealership and service locations. MMG is a multi-marque group: it retails and services around eight vehicle brands on behalf of their manufacturers, but it does not manufacture vehicles itself. It is the retail and service layer between the carmakers and the customer.

In numbers, MMG has about 4 million active customers, sells close to 900,000 new and used vehicles per year, completes about 3 million service and repair visits per year, and handles roughly 8 million inbound customer contacts per year across phone, chat, email, and its customer portal.

Two years ago MMG consolidated a patchwork of regional CRM systems onto Salesforce Automotive Cloud (Sales and Service), which is now the operational core. There is no AI in production today. MMG has a strong Salesforce platform team but no in-house machine learning or data science function. The board has been clear that it intends to use platform-native AI and external model providers rather than build and train models itself.

The pressure to act is real. The manufacturers MMG represents are increasingly selling directly to customers through their own digital channels and agency models, which threatens the group's traditional position as the owner of the customer relationship. At the same time, customers now expect the same instant, self-service experience from a car group that they get from any consumer app. The board sees AI as the way to defend the customer relationship and to make the cost of serving it sustainable. That is the growth and the efficiency the shareholders are asking for, even if they have not put it in those words.

Two facts shape what is possible. The customer experience today is fragmented and slow. A customer who calls, then chats, then visits a location usually has to repeat themselves, and advisors spend much of their day on the same routine questions rather than selling or resolving complex cases. The consolidation, however, left MMG with something valuable: a single unified customer and vehicle profile in the enterprise data platform, bringing together contact details, ownership, service history, and telematics. The raw material for a better experience already exists. It has simply never been put to work in the moment a customer is waiting.

---

## The Constraints

None of this will be easy, and the constraints are exactly the kind that surface in an architecture review. Operating in eight countries means eight regulatory and language contexts: GDPR applies everywhere, but consent for marketing and for telematics data was captured differently in each market during the CRM consolidation, and the works councils in Germany and Austria must approve any tool that could be read as monitoring advisor performance. The EU AI Act is on every legal agenda, and any AI that gives safety-relevant guidance, such as recall advice, is expected to attract its higher-risk obligations. The manufacturer contracts add a second layer: each brand has its own rules on how its vehicle, telematics, and customer data may be used, several insist that the customer relationship is theirs, and at least one is piloting an agency model in which MMG legally sells on the manufacturer's behalf. The location network is a mix of fully owned dealerships and franchise partners, running three different dealer management systems on various versions, so no integration can assume one system of record at the retail edge. Data quality reflects the consolidation's age: duplicate customers across markets and stale vehicle ownership records still exist in the regions that migrated last. Demand is spiky, a single safety recall across one brand's model range can triple inbound contact volume within days and floods exactly the routine-question channels AI is meant to relieve. And while the Salesforce platform team is strong, it already carries the release calendar for eight markets, so anything new must fit an established governance cadence, a finite change budget, and a board that expects something visible within three quarters.

---

## The System Landscape

Salesforce Automotive Cloud sits at the centre. Eight systems surround it and will be retained. Your worksheet shows them already.

1. Dealer Management System (DMS): the transactional system of record for vehicle inventory, deals, service orders, and parts.
2. OEM connected-vehicle and telematics platforms: live vehicle data from the manufacturers, including location, mileage, diagnostic trouble codes, and driving behaviour.
3. ERP (SAP): finance, parts procurement, and invoicing.
4. Marketing automation: campaigns and customer consent.
5. Contact-centre telephony (CTI): inbound and outbound voice across the contact centres.
6. Service scheduling: bay and technician availability and booking.
7. Data Cloud and enterprise data platform: the unified customer and vehicle profile, and analytics.
8. Customer portal and identity provider: customer self-service and the single sign-on identity used across all of the above.

---

## The Mandate

The shareholders have given the board one instruction:

> "Embed AI more deeply into the product to drive growth and efficiency."

That is the whole brief. The board expects AI to play a central, visible role in how MMG serves and sells to customers. Beyond that, it has not said what to build, on which channels, or with what guardrails. Three executives are sponsoring the work, and each reads the instruction differently.

---

## The Stakeholders

You must satisfy all three. Not one. All three.

Dr. Helena Vance, Chief Executive Officer. She reads the mandate as a growth story: a customer-facing assistant that answers questions, books service, and sells, available everywhere, around the clock. She wants it live and she wants it in the announcement.
> "I want customers talking to our AI by Q3, and I want it in the announcement."
Red line: a timeline she can commit to publicly, and a capability customers will notice.

Marcus Reinhardt, Chief Information Security and Data Officer. He sees customer personal data, vehicle location and driving data, recall and safety information, and the reputational and regulatory exposure of an assistant that gets any of it wrong. He would rather move slowly and provably.
> "Where does the customer's data go the second it touches a model, and who can prove it?"
Red line: he must be able to show, on a diagram, what happens to personal data and where a human stays in control.

Priya Anand, Chief Information Officer. She owns delivery, run cost, and operations. She is sceptical of anything that sounds like magic and wants to know what it costs at full volume, how fast it responds, and who keeps it running.
> "Show me the cost at 10,000 conversations a day, and who operates this at 2 a.m."
Red line: the cost and latency have to work at scale, and the design must be operable and not locked to a single supplier.

---

## Business Process Requirements

The mandate touches three areas of how MMG works today. AI is expected to help across all three. How, and how much, is your decision.

### A. Customer service and engagement

Customers contact MMG with questions about their vehicle, their service, billing and financing, and open recall or safety campaigns. Today this runs through contact-centre agents and service advisors and is the single largest cost in the customer operation. The board sees this as the primary place for AI to create both growth and efficiency.

- Customers reach MMG by phone, web chat, the portal, and email.
- A customer interaction often requires looking up the vehicle, its service history, its current telematics state, and any open recalls, then giving the customer an accurate answer or taking an action on their behalf.
- Some questions concern vehicle safety, including whether a vehicle is affected by a recall and whether it is safe to keep driving. Today a trained advisor handles these.
- Volume is high and seasonal, and response time is visible to the customer, especially on voice.

### B. Sales and ordering

Customers configure and order new and used vehicles, arrange financing, and trade in their existing vehicle. Sales representatives assist them in person and remotely.

- A customer or representative configures a vehicle, checks availability against the DMS, and prepares a quote.
- Financing options and eligibility questions are common and currently require a representative.
- Trade-in valuations depend on the customer's vehicle data and current market conditions.

### C. Service operations and post-service

MMG schedules and delivers service and repair work and runs the manufacturers' recall campaigns.

- A customer books a service. The booking must respect bay and technician availability in the scheduling system and create a service order in the DMS.
- Telematics data can indicate that a vehicle is due for service or shows a fault, creating an opportunity to reach the customer proactively.
- When a manufacturer issues a recall, MMG must identify affected customers, contact them, and book the corrective work. Accuracy here is a safety and legal matter.

---

## Data Requirements

The AI will need access to customer and vehicle data, and some of that data is sensitive.

- Customer profile: contact details, home address, and marketing and data-use consent.
- Vehicle: identification number, ownership, full service history, and live telematics including location, mileage, and diagnostics.
- Financial: financing arrangements and payment information.
- Interaction history: records of calls, chats, and emails, including transcripts.

Under European data protection law, customer personal data and vehicle location and driving data are personal and in places sensitive. For legal and regulatory reasons, MMG must retain records of customer interactions and must be able to account for how customer-facing decisions were reached. Recall and safety information must be accurate and current, and much of it originates from the manufacturers rather than from MMG.

---

## Identity and Data Access Requirements

- Single sign-on already spans MMG's systems through the enterprise identity provider. Any customer-facing assistant must authenticate the customer and act only on their own data.
- Customers may see only their own vehicles, history, and orders.
- Service advisors and sales representatives may see the customers and vehicles they are responsible for. Managers may see their teams. Senior management may see roll-ups across regions.
- Marketing actions are governed by each customer's recorded consent.
- MMG must be able to log and, where required, explain automated decisions that affect a customer.

---

## Reporting and Analytics Requirements

MMG wants to:
- Forecast service demand and balance load across locations.
- Track customer satisfaction and identify upsell and retention opportunities.
- Measure recall campaign completion and customer response.

---

## What you will produce

Working in your group, you will:
1. Choose a set of AI technologies that meets the mandate. You will be given options across a wide range of complexity. Not all of them fit, and you cannot afford all of them.
2. Produce a solution architecture diagram showing where and how AI is applied across the landscape.
3. Produce a data flow diagram for the AI subsystem.
4. Defend your approach to the executive board.

Both diagrams must represent the AI components accurately enough that the board can see what they do, what they touch, and where customer data goes. A vague box will not survive the room.
