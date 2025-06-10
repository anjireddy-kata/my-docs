### Call Routing & ACD
Definition: Automatic Call Distributor (ACD) intelligently routes calls to the right agent/team.
Analogy: Like traffic navigation apps—routes calls based on rules, wait time, or skill set.

#### Routing Engine
This is the core decision-making logic that determines where to send the call. It considers multiple inputs and applies business rules.

##### Capabilities:
- Skill-based routing
- Priority-based routing
- Time-of-day and location-based routing
- Language or region-specific routing
- Business hours and holiday routing
- AI/ML-based predictive routing (advanced)

##### Skills Matrix
A configurable mapping of agent skills used by the routing engine to match customers with the best-suited agents.

Example:
Language (English, Hindi, Spanish)
Product expertise (Loans, Credit Cards)
Customer tier (VIP, Retail)

##### Queue Management
Handles calls waiting to be answered, assigning them to the right queue based on routing rules.

Capabilities:
Multiple queues (by department, product, etc.)
Queue overflow management
Estimated wait time announcements
Virtual hold (callback) options

##### Priority & SLA Management
Assigns priority levels to different interactions to meet Service Level Agreements (SLAs).

Example:
VIP customers get higher queue priority.
Calls older than 2 minutes escalate in priority.

##### Load Balancer / Resource Optimizer
Ensures even distribution of calls across available agents, avoiding overloads.

Techniques:
Round-robin
Least occupied agent
Longest idle agent

##### Real-time and Historical Analytics
Monitors and analyzes routing efficiency, queue wait times, agent performance, and more.

Tools:
Dashboards for supervisors
Alerts for SLA breaches
Historical reports for tuning routing logic

##### Multichannel Routing (in Omnichannel ACDs)
Routes non-voice channels like chat, SMS, email, or social media using the same intelligent logic.

Benefits:
Unified agent experience
Consistent prioritization across channels

##### Business Rules Engine 
A configurable rules layer enabling non-technical staff to tweak routing logic without code changes.

Example Rules:
“Route all platinum customers to Tier 2 agents.”
“After 8 PM, send all calls to the night-shift queue.”

##### Integration with CTI and CRM
ACD pulls context from CTI (Computer Telephony Integration) and CRM systems to make smarter routing decisions.

Example:
If CRM shows Sofia had an open complaint, route her to a resolution specialist.

### IVR (Interactive Voice Response)
Definition: Automated menus that help customers self-serve or reach the right team.
Analogy: Like ATM menus for customer support.
Example: “Press 1 for billing, 2 for tech support...

### CTI (Computer Telephony Integration)
Definition: Connects phone systems with computers to give agents real-time info.

Analogy: Like caller ID + CRM on steroids.

Example: When a customer calls, their profile pops up with their past orders or issues

### Agent Desktop & Experience
Definition: The unified interface agents use to handle interactions.

Analogy: Like a cockpit dashboard for agents—everything they need in one place.

Features: Customer history, notes, knowledge base, call controls

Story: “Sarah’s call lands with Alex, the agent. Let’s see what Alex sees.”

### Reporting & Analytics
Definition: Tools that track performance, customer satisfaction, and trends.

Analogy: Like a fitness tracker for your contact center.

Key Metrics: Call volumes, wait times, first contact resolution (FCR), CSAT

Visual: Example dashboard
### Workforce Management (WFM)
Definition: Forecasts and schedules agents to meet demand.

Analogy: Like air traffic control for agent shifts—ensuring the right number of agents at the right time.

Visual: Forecasting chart and schedule planner

Example: Handling Monday morning spikes after a weekend sale

### Quality Monitoring & Feedback Loops
Definition: Evaluates interactions to improve quality and agent coaching.

Analogy: Like a coach reviewing game footage to improve performance.

Methods: Call scoring, sentiment analysis, post-call surveys

Visual: Quality evaluation form



Analogy: Imagine a contact center as the “mission control” for customer service—just like air traffic control ensures planes land safely, 
contact centers ensure customers reach the right help at the right time.

In the telephony world, a carrier (also called a telecom carrier or service provider) is the company or organization that owns and operates the infrastructure 
needed to carry voice and data communications over long distances.

A carrier is like the highway system for phone calls—they move your call from your phone to its destination across networks they control.


## Step-by-Step Call Flow: From Customer to ACD
#### Customer Initiates a Call
Device: Sofia uses a mobile or landline phone.
Network: Her call enters the Public Switched Telephone Network (PSTN) or VoIP network.
##### SS7 (Signaling System 7) – PSTN signaling
##### SIP (Session Initiation Protocol) – for VoIP-based calls

#### Carrier-Level Routing
The carrier (e.g., Airtel, AT&T) resolves the destination number (e.g., bank's toll-free or DID number).

If it’s a toll-free number (e.g., 1800):
It's resolved via Intelligent Network (IN) services.
The call is routed to the enterprise’s telephony ingress point.

Key Components:
- Toll-Free Routing Database
- Carrier Gateway (e.g., SIP trunking, PRI)

#### Entry to Enterprise Telephony Infrastructure
The call lands at the contact center’s edge telephony system, typically hosted on-premise or in the cloud.
##### Key Components:
- SBC (Session Border Controller): Secures and normalizes VoIP calls.
- IP-PBX or Voice Gateway: Converts analog/digital to IP (for VoIP) or routes SIP directly.
- IVR Platform: Plays the welcome prompt and gathers input.
- Call Control Platform: Initiates a session for the call.

##### Protocols:
- SIP: Session setup, modification, and teardown
- RTP: Real-Time Protocol for transmitting the actual voice
- DTMF: For keypress tones during IVR interaction

#### CTI (Computer Telephony Integration) Activation
A CTI Server listens for incoming call events from the PBX or telephony platform.
It triggers screen-pop actions in the agent desktop, even before call routing completes.

##### Key CTI Protocols:
- CSTA (Computer Supported Telecommunications Applications)
- TSAPI (Telephony Services API)
- JTAPI (Java Telephony API)
- Proprietary APIs from Avaya, Cisco, Genesys, etc.

#### IVR Interaction Begins
The IVR plays messages and may ask Sofia to:
- Press keys (DTMF)
- Speak (Voice Recognition/ASR)
- Inputs are used to:

Authenticate the customer
Capture intent (e.g., “lost card”, “account balance”)
Pass context to ACD

Key Technologies:

- ASR (Automatic Speech Recognition)
- TTS (Text-to-Speech)
- VoiceXML for IVR logic

#### Routing Decision Made by ACD
Once the IVR completes its job:

It invokes the ACD engine, passing:

Caller ID

Collected DTMF input

CRM context (via CTI)

Language preference, customer tier, etc.

ACD evaluates:
- Agent availability
- Skill match
- Queues
- Routing rules

✅ Protocols & Mechanisms:

- SIP REFER / SIP RE-INVITE: To transfer to another endpoint
- Routing APIs (e.g., REST-based if cloud ACD is used)
- Queue Frameworks (with Redis/Kafka in modern ACD engines)

Call Routed to Agent or Queue
The ACD sends the call to:
- A live agent via their softphone/deskphone
- A queue if no one is available
- Simultaneously, CTI updates the agent desktop with screen pop.

✅ Voice Path:
Call is bridged using SIP/RTP directly between customer and agent
Or via media proxy (e.g., Genesys Media Server, Avaya Media Processor)

![image](https://github.com/user-attachments/assets/3a8a2d34-96c4-4aeb-a021-461bd6df02ae)

![image](https://github.com/user-attachments/assets/c54a10b4-cdcd-4f42-8482-7459dc359335)

## Step-by-Step Breakdown: What Happens When You Call a Toll-Free Number (TFN)

### Step 1: Call Initiation (From Mobile)
You dial a TFN (e.g., 1800-123-4567) on your mobile.
Your mobile phone converts the keypresses into outbound call signaling using protocols like ISUP (ISDN User Part) or SIP (if you're using VoLTE).
📡 Your phone sends a "call setup" request to your Mobile Network Operator (MNO) (e.g., Jio, Airtel).

### Step 2: Toll-Free Resolution (Carrier-Level)
The TFN isn’t tied to a fixed location—it must be resolved. The carrier consults a Toll-Free Number Database (TFN Registry or IN - Intelligent Network) to determine the routing translation:
Which enterprise owns the number?
What is the destination number or SIP trunk?
Are there time-of-day or geographic routing rules?

🧠 Example:
TFN 1800-123-4567 → Resolved to SIP Trunk IP: sip:bank@xyz.sbc.com

### Step 3: Routing to Enterprise Entry Point
Once the TFN is resolved:
The call is routed through:
PSTN (Public Switched Telephone Network), or
VoIP SIP Trunks (if enterprise supports SIP)
The call lands at the enterprise Session Border Controller (SBC).

 Protocols Involved:

- SS7 / ISUP if via traditional TDM circuits
- SIP (Session Initiation Protocol) if over IP
- RTP (Real-Time Protocol) for audio transmission

### Step 4: Security & Media Negotiation (SBC)
The SBC (e.g., Oracle, Ribbon, AudioCodes):
- Verifies the call is legitimate (authentication, encryption)
- Converts and normalizes the SIP signaling
- Initiates NAT traversal and media codec negotiation

🔐 SBCs also guard against DoS, fraud, malformed SIP, and codec mismatches.
### Step 5: Entry to Voice Gateway or IP-PBX
The SBC passes the call to an internal voice gateway (e.g., Cisco CUBE, Avaya Media Gateway) or IP-PBX (if legacy infra exists).

It’s here that the call legs are bridged into the contact center environment.

🔁 In hybrid setups, TDM calls may convert to SIP and vice versa.

### Step 6: Contact Center IVR Engagement
The call reaches the IVR platform (e.g., Genesys GVP, Cisco CVP, Avaya Experience Portal).

The IVR plays welcome prompts like:

"Welcome to XYZ Bank. Press 1 for account info, 2 for credit card services..."

The system may:
- Use ASR (Automatic Speech Recognition) for speech input
- Capture DTMF tones from your keypad
- Use TTS (Text to Speech) to dynamically respond

🤖 The IVR is powered by VoiceXML logic, integrated with backend systems (e.g., for account lookup).

### Step 7: CTI Integration Begins
As soon as the call hits IVR, CTI (Computer Telephony Integration) kicks in:

The IVR shares call metadata (caller ID, inputs, ANI) with the CTI server (e.g., Genesys T-Server).

The CTI server fetches context from CRM systems (customer profile, past issues).

🖥️ This allows screen pop to be ready for the agent even before the call lands.

### Step 8: Call Routing via ACD
The IVR sends a routing request to the ACD (Automatic Call Distributor):

Includes metadata like intent, language, priority, CRM ID

The ACD uses routing strategies to determine:
- Which queue the call should go to
- Which agent has the right skills and availability

🧠 Routing logic may use: Skill-based routing, priority queuing, predictive algorithms

### Step 9: Call Connected to Agent
The ACD directs the call:

To a live agent’s softphone

Or into a queue if no agent is available

The RTP stream now connects Sofia (you) to the agent.

The agent desktop receives a screen pop with relevant info.

🔹 Step 10: Post-Call Processing
Once the call ends:

The contact center updates:

Interaction history in CRM

Call metadata in reporting systems

Recordings and transcripts (if enabled)

The session flows into:

Analytics platforms

Quality Monitoring

WFM (Workforce Management) for adherence metrics

![image](https://github.com/user-attachments/assets/bb17b788-69c7-44a5-8022-782f7ff29cca)

SIP/RTP protocols are used for voice call setup and audio delivery.

CTI enables context sharing, screen pop, and routing intelligence.

ACD decides routing based on skills, business rules, agent availability.

SBC provides security, normalization, NAT traversal, and interop.

CRM holds customer history, which is fetched in real-time for agent assistance.
![image](https://github.com/user-attachments/assets/65c4e4c3-8d4c-41af-8d5d-4c3a572dd79d)

In the telephony world, a carrier (also called a telecom carrier or service provider) is the company or organization that owns and operates the infrastructure needed to carry voice and data communications over long distances.

✅ In Simple Terms:
A carrier is like the highway system for phone calls—they move your call from your phone to its destination across networks they control.

🔧 What Carriers Do:
Provide phone numbers (including toll-free and mobile numbers)

Route and connect calls over PSTN, VoIP, or mobile networks

Manage protocols like SS7, SIP, and RTP

Handle interconnects with other carriers globally

Offer services like SIP trunking, PRI lines, SMS, and data plans

🧱 Examples of Carriers:
In the U.S.: AT&T, Verizon, T-Mobile

In India: Airtel, Jio, BSNL

Global / Enterprise Carriers: Tata Communications, Twilio, Bandwidth, BT, Orange, NTT

🔄 In a Contact Center Scenario:
When a customer dials a toll-free number:

The call goes to the carrier network.

The carrier routes it to the business’s contact center over SIP trunks or PSTN lines.

The carrier may perform TFN translation, load balancing, or failover routing.

In the context of telephony, a Session Border Controller (SBC) is a specialized network device that manages and secures SIP-based voice and video communications between different networks—most commonly between a telecom carrier and an enterprise (like a contact center).

📌 Simple Definition:
An SBC acts like a smart firewall for VoIP calls, protecting and managing voice traffic as it crosses network boundaries.

![image](https://github.com/user-attachments/assets/846dca75-fc08-4f11-a7fd-80cbe8e9fd3e)

What is PSTN?
PSTN (Public Switched Telephone Network) is the traditional, circuit-switched network used for landline telephone calls.

✅ Key Points:
Analog/digital voice network used globally for decades.

Relies on TDM (Time Division Multiplexing) and SS7 signaling.

Very reliable, but not IP-based.

Commonly used for:

Landline phones

Toll-free numbers

Emergency numbers (like 911)

An SBC (Session Border Controller) is a smart, secure gateway that controls VoIP (Voice over IP) traffic—especially SIP calls—at the boundary between networks (e.g., between a telecom carrier and a contact center).

✅ Key Points:
Works with SIP/RTP, not TDM.

Ensures security, interoperability, and quality for IP voice/video traffic.

Used in modern, IP-based telephony systems like:

VoIP phone systems

SIP trunking

Cloud contact centers

🧠 Think of SBC as:
A border control checkpoint for internet-based phone calls—it checks, secures, and manages every "traveler" (call session) crossing into your network.

How PSTN and SBC Work Together
In modern systems, many calls start on the PSTN (especially toll-free or mobile calls) but end in an IP-based system like a contact center.

🧱 Call Flow Example:
text
Copy
Edit
Customer dials a TFN ➝ PSTN routes the call ➝ Carrier converts it to SIP ➝ SBC ➝ IVR ➝ Agent
Call enters via PSTN

Carrier receives the call via traditional network.

Carrier converts TDM to SIP

If the contact center is IP-based, the call is converted into SIP format.

SBC receives SIP call

Validates and secures the call before passing it into the enterprise network.

What is PSTN?
PSTN (Public Switched Telephone Network) is the traditional telephone network—the global infrastructure of landlines, cell towers, fiber optics, and switches that carry voice calls.

Uses circuit-switched technology.

Supports mobile and landline calls.

Still the default backbone for regular phone calls worldwide.

Protocols: SS7, ISUP, TDM (for voice).

What is a SIP Trunk?
A SIP Trunk is the modern, IP-based replacement for traditional telephone lines, using the SIP (Session Initiation Protocol) to carry voice calls over the internet.

Used by contact centers, IP-PBXs, and VoIP systems.

Delivers voice via SIP + RTP (media).

Highly scalable and cost-effective.

Terminates on an SBC (Session Border Controller) or VoIP gateway.

nd-to-End Flow: Sofia Calls the Bank's TFN
Let’s say Sofia dials a bank’s TFN (1800-111-2222) from her mobile phone:

🧭 Step-by-Step Flow
📱 Sofia (Mobile Phone)

Dials the TFN from her mobile.

📡 Mobile Network → PSTN

Her call goes through her Mobile Network Operator (MNO), which routes the call into the PSTN.

🗺 TFN Database Lookup

The PSTN consults a TFN database (Intelligent Network - IN) to determine where the TFN should be routed (e.g., which SIP endpoint or number).

🚪 PSTN → SIP Trunk

The call is converted to SIP by the carrier (if the contact center is IP-based).

Now the voice call travels over a SIP trunk from the carrier to the bank's SBC.

🛡 SBC (Session Border Controller)

The SBC receives the SIP call, performs security checks, normalization, and routes it internally.

🎛 Voice Platform / IVR

The call is sent to the IVR to gather inputs (e.g., account number, intent).

👩‍💼 ACD → Agent Desktop

The call is routed using ACD logic (based on skills, availability, etc.).

The agent picks up the call, and media flows directly between Sofia and the agent.

![image](https://github.com/user-attachments/assets/2a660e88-8607-4f60-8aaf-c8a137a922b7)

![image](https://github.com/user-attachments/assets/6e45fc12-61d3-42f8-b490-cd8c06c481ef)


