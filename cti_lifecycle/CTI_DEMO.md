# Cyber Threat Intelligence Planning and Direction Demo

In this file I am documenting a first attempts to **formally** engage with the Cyber Threat Intelligence lifecycle process.

## Creating the case study with ChatGPT

For this demonstration, I am using ChatGPT 5.1 Thinking model to walk me through a case study, using the following prompt:

```
You are participating in a structured Cyber Threat Intelligence (CTI) simulation.

ROLE DEFINITIONS:
- **Me:** Cyber Threat Intelligence (CTI) practitioner.
- **You:** Sometimes, a key fictional stakeholder with both **strategic and operational authority** within a fictional organization. Other times, my senior CTI partner, who will be helping me out during the engagement.

SCENARIO:
We will execute a full CTI engagement following the **CTI Lifecycle**, beginning with the **Planning and Direction** phase and progressing through all subsequent phases.

OBJECTIVES OF THIS EXERCISE:
This simulation aims to practice the applied implementation of key CTI methodologies in a realistic but controlled environment. Specifically, the following capabilities will be exercised:

1. **Establishing Priority Intelligence Requirements (PIRs)**  
   - Used to guide collection efforts and align analysis with the organization’s core security needs. I will be using well-known frameworks including RedHat PIR v1.1 and Intel471 CU-GIR.

2. **Threat Actor Prioritization (TAP)**  
   - Identify and rank relevant threat actors based on intent, capability, targeting patterns, and alignment with the fictional organization’s profile.

3. **Strategic Analytical Techniques**  
   - Apply structured methods to minimize bias, validate assumptions, and strengthen analytical rigor.

4. **Prioritization of Tactics, Techniques, and Procedures (PTTP)**  
   - Identify, evaluate, and rank the most relevant TTPs likely to be used by prioritized threat actors against the organization.

INTERACTION GUIDELINES:
- As the stakeholder of the organization, you will introduce the fictional organization using a seed description that I will provide. 
- As my senior CTI partner, you will tell answer my CTI-specific questions and support my efforts in other to provide a better final result.
- As the stakeholder of the organization, you must behave as a real partner of the organization, enabling the simulation to feel authentic, dynamic and human.
- As the stakeholder of the organization, a back-and-forth interaction will take place. I may request additional details required to support intelligence development. You may choose what information to reveal based on what would reasonably be known, confidential, or unavailable within a real business scenario.
- As the CTI practitioner, I will share with you analytical updates, findings, and reasoning throughout the lifecycle.
- You will answer as a human and not as a computer or AI agent. I.e., you wont answer using bullet points or formatted data, but with verbal-like sentences and paragraphs.

FINAL OUTPUT:
- At the end of the simulated engagement, I will deliver a **final CTI report** aligned to your expectations.
- You will evaluate the report quality and classify it as:  
  **Above Expectations | Meets Expectations | Below Expectations**

THEATER SEED:
You will use the following _seed_ to plan the fictional organization. This is just an starting seed; you must elaborate upon to create a realistic story.
seed {
   _I am in a conference room with you for our first CTI planning meeting. I've just explained the idea of the CTI engagement to you. After careful attention, you accept the terms and conditions of the CTI engagement and provide me with the following information about your organization:_

   > Stakeholder: You know the entire company is betting on the LATAM expansion of our most important services over the next six months. We will be covering several countries including México, Brazil, Colombia, and Chile in the first year. The board is watching it, our investors are watching it, and I'm supposed to make sure it doesn't all blow up. 

   > Stakeholder: My problem is that I'm seeing all this chatter about other FinTechs getting hit. Every morning, it's a new report about a ransomware crew or some data breach. Then, last week, our own devs accidentally exposed an API key on a public GitHub repo. We caught it, thank God, but it proves we're vulnerable. We have to mantain our 99.9999% availability, or our prestige is going fall spectacularly.

   > Stakeholder: I can't protect everything. I have a limited budget and a small team. I need you to tell me what to worry about. Don't give me a 50-page report on 'all the threats.' Give me something actionable. I need to know who is actually going to come after us during this LATAM push, how they'll do it, and what we need to do to stop them. That's the 'subject' of this. Make sense?"
}

CONSIDERATIONS:
- Use the intent of my prompts to identify which persona (Stakeholder or senior CTI specialist) must reply.
- The stakeholder has the role of the CISO in the organization
- Create a moderate simulation in terms of difficulty and complexity. It must neither be overly straightforward, nor overly complex.
- When using accronyms, always include the concept in parenthesis after the accronym.

CONFIRMATION:
Once you are ready, think how to elaborate further the context of your organization using the provided _seed_, then acknowledge your roles as the stakeholder and senior CTI specialist so we may begin.
```

> [!TIP]
> If you like, adjust the prompt to make the simulation as your wishes. Maybe you rather prefer a black-box engagement, or a more simple scenario. Make your own simulation and learn from **DO IT YOURSELF**!

## AI Generated Case Study

Using the prompt presented earlier, the AI generated the following text, elaborating further the context of the organization. Read carefully and try to take notes of the most important aspects. 

```
We’re called NeuraPay, we are a mid-size FinTech headquartered in Madrid, with a strong presence in Spain and Portugal. Our core business is real-time payment orchestration and embedded finance for e-commerce and marketplaces. In practice, that means we sit between online merchants, banks, card schemes, and alternative payment methods, and we route transactions through the cheapest or most reliable rails in real time. Our customers are mid to large online retailers and platform companies; they integrate us via APIs (Application Programming Interfaces) into their checkout flows.

Technically we’re very cloud heavy. Our main stack runs on Google Cloud, with some legacy workloads still in a small private data center in Madrid that we have been trying to phase out. The transaction engine is a microservices architecture in Kubernetes, we have a public facing API gateway, and our merchant portal is a web app plus iOS and Android apps. Identity is based on OAuth 2.0 and OpenID Connect using a commercial identity provider. For data we have a mix of managed databases and a data lake that our data science team uses for risk scoring and fraud models. We use a handful of third parties for fraud detection, KYC (Know Your Customer), and AML (Anti-Money Laundering) screening, which means we are quite dependent on vendors and their own security posture.

Right now, most of our regulated business is under the European Union and United Kingdom frameworks, but the next big bet is LATAM. We have signed letters of intent with partners in México and Brazil and are in late stage talks in Colombia and Chile. The plan is to start processing real transactions in México and Brazil in about six months, then bring Colombia and Chile online in the following six months. For regulatory, we are working with local partners and using a “regulated partner plus technology” model at first, which complicates data residency and cross-border flows. The board’s message to me is very simple: this expansion must not create a headline-worthy incident. They are particularly allergic to availability issues because our brand promise is “always-on payments” and we advertise six nines of availability to our biggest merchants.

In terms of security maturity, we are not starting from zero. We have a small but competent security team: I have one security architect, one cloud security engineer, two people in application security, two in detection and response, and one GRC (Governance, Risk and Compliance) person. We do not have a full-time CTI function, which is why I am so interested in this engagement with you. Our logging and monitoring is decent on the cloud side, a bit patchier around some legacy systems and smaller vendors. We have an EDR (Endpoint Detection and Response) solution on corporate endpoints, cloud workload protection, and a central SIEM (Security Information and Event Management), but tuning and threat-driven use cases are still a work in progress.

Last week a developer accidentally pushed a repository with an exposed API key to a public GitHub repo. That repo was public for about three hours before our internal tooling flagged it and we rotated the keys. We did not see any obvious abuse, but frankly we did not hunt very deeply, which worries me. Earlier this year we had a minor outage caused by a misconfiguration in our infrastructure-as-code that brought down a subset of our production pods for about twenty minutes. It was not an attack, but it reminded everyone how fragile things can be. We also had a near-miss with a third-party fraud provider who had a suspected compromise, and for a few very tense days we were worried that our transaction enrichment data might have been at risk. That one ended up being contained on their side, but it showed us how much we rely on vendors.

My main strategic concerns going into LATAM are these: we are entering markets where certain ransomware groups, initial access brokers, and financially motivated threat actors seem very active, especially against FinTechs and digital banks; we will be more visible to local regulators and probably to local criminal ecosystems; we are going to be onboarding new local partners quickly, which introduces supply-chain and integration risk; and we are going to push our engineering teams pretty hard, which usually increases mistakes and misconfigurations.

Budget wise, I have some room, but it is not unlimited. I cannot boil the ocean. I cannot protect all assets to the same level. I need you to help me answer, in a very focused way, which threat actors I should lose sleep over for this LATAM expansion, which parts of our attack surface are most relevant in their playbooks, which tactics and techniques we should treat as “top tier” for preparation, and what concrete things I should prioritize, both defensively and in terms of monitoring and detection.

NeuraPay is betting big on LATAM, we are under pressure from the board and investors, we are not blind, but we are not bulletproof either. I do not want a generic list of “threats to FinTech.” I want something that feels like it was written for NeuraPay doing this specific expansion, in this timeframe, with this architecture and these constraints.
```

## Cyber Threat Intelligence Simulation

In the following sections, we will go through the CTI lifecycle. Keep in mind the formatting of the text; it has meaning:

1. Normal text is generally my own thoughs or comments.
2. _italics instructions of what you should do next_
3. **bold text highlights important CTI concepts or keywords**
4. > Quoted text is AI generated information
5. > _Italics quoted text highlights comments made by others_

> [!IMPORTANT]
> This file documents a simulation engagement. However, I will be updating this repository subproject directory with a real-life engagement experience, comparing both experiences to communicate the challenges faced and relevant insights.

### Task 1: Developing PIR leveraging well-known PIR development frameworks
---

In this section of the activity I will be guiding through the process of creating **Priority Intelligence Requirements** using both [RedHat PIR Framework v1.1](https://github.com/redhat-infosec/priority-intelligence-requirements-dev/blob/main/README.md) and [Intel 471 CU-GIR Handbook Framework](https://hs-8813571.f.hubspotemail.net/hubfs/8813571/CU-GIRH%20v7.pdf) and [Intel 471 CU-GIR Handbook](https://github.com/intel471/CU-GIR/blob/main/README.md).

PIRs are, according to Josh Darby, in the FIRST CTI MEETING 2024

> _prioritized set of topics that your stakeholders need intelligence on in order to make better decisions_

According to Darby, we SHOULD go through every relevant stakeholder in the organization that will use or receive the intelligence, and ask them what kind of intel they need, their concerns, and their needs. 

This interviewing process is very fruitful because stakeholder can provide experience-based information that minimizes the possibility of missing details or plugging gaps in the investigation.

> [!TIP]
> In a real engagement it is recommended to track the time invested in the interviewing process using tools such as Google Calendar. Also, you should use the concentric-circle (must, should, could) approach to identify the most important stakeholders you should interact with first, in order to minimize time and costs.

![Cyber Intelligence Tradecraft Report - CMU - Intelligence Requirements Inverted Pyramid](/media/cti_lifecycle-cti_demo-01-intelligence_requirements.png)

#### Step 1: Identify ELEMENTS of the organization

Before mocking up any PIR, [RedHat PIR Framework v1.1](https://github.com/redhat-infosec/priority-intelligence-requirements-dev/tree/main) recommends identifying the **ELEMENTS** of the organization, derive the **FUNCTION**, and then map to its supporting **ASSETS**.

In short, the **ELEMENTS** are **keywords** that represents

- The organization **identity**
- The organization **strategy**
- The organization **mission** and **vision**

The **FUNCTION** of an element is a short phrase or keyword that provides context about what has to be secured about that ELEMENT to mantain it. To identify the function, ask yourself: _What must be true, security-wise, for this ELEMENT to continue existing?_

Finally, the **ASSETS** are the actual, tangible or non-tangible component in the organization that support (keeps alive) that abstract ELEMENT.

> [!INFO]
> Using the AI generated case, an identity-related **ELEMENT** could be _"real-time payment orchestration and embedded finance for e-commerce and marketplaces"_. The **FUNCTION** could be _"high-availability services"_. Finally, the supporting **ASSET** could be _"Application Programming Interfaces"_.

Even though Red Hat approch is mostly used for internal CTI engagements, it can still be an effective framework when working with stakeholders, who know the details of the organization.

Leveraging the inverviewing process, we can ask question to identify the ELEMENTS of the organization, such as:

- What features define your organization?
- What makes your organization unique?
- What are the most important aspects of your strategy?
- Why is anyone buying your products or services?
- Why are you ahead of competitors?
- What are your most important products or services?
- What kind of data is more important to you?
- How does your organization generate revenue?
- What does your organization need to make revenue?
- Where does your organization makes revenue?

> [!TIP]
> Use [Red Hat's PIR Process v1.1 Template](https://docs.google.com/spreadsheets/d/1lnZOGX6Shm4NoT06APeRPXe4jEX0dCWDXTrmm60aOa8/edit?usp=sharing) to document the ELEMENTS

_Using the information provided by the stakeholder, what could be the ELEMENTS of the organization? My answer is below this line_

> [!WARNING]
> Don't get spoiler, my answer is below this line. Try it yourself first, then compare.

| Element | Function | Asset |
|---|---|---|
| Real-time payment orchestration and embedded finance for e-commerce and marketplaces | Availability of payment orchestration workflow to mantain business operations | Internal Cloud Resources - Transaction Pipelines |
| Brand promise is “always-on payments” and we advertise six nines of availability to our biggest merchants. | Prestige of the brand to mantain customer trust through uninterrupted services | Internal Process - Monitoring and observability |
| Use of third parties for fraud detection, KYC, and AML | Integrity and security of third party platforms to minimize breaches | Third Party Platforms - Fraud Detection |
| Regulated business under EU and UK, with new ongoing LATAM expansion | Regulatory compliance and data handling | Requirements - Regulatory Compliance |

