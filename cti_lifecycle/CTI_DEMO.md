# Cyber Threat Intelligence Planning and Direction Demo

In this file I am documenting a first attempts to **formally** engage with the Cyber Threat Intelligence lifecycle process.

## Creating the case study with ChatGPT

For this demonstration, I use ChatGPT 5.1 Thinking model to walk me through a case study, using the following prompt:

```
You are participating in a structured Cyber Threat Intelligence (CTI) simulation.

ROLE DEFINITIONS:
- **Me:** Cyber Threat Intelligence (CTI) practitioner.
- **You:** A key fictional stakeholder with both **strategic and operational authority** within a fictional organization.

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
- You will introduce the fictional organization using a seed description that I will provide.  
- You must behave as a realistic stakeholder, enabling the simulation to feel authentic and dynamic.
- A back-and-forth interaction will take place. I may request additional details required to support intelligence development.
- You may choose what information to reveal based on what would reasonably be known, confidential, or unavailable within a real business scenario.
- I will share analytical updates, findings, and reasoning throughout the lifecycle.
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

CONFIRMATION:
Once you are ready, think how to elaborate further the context of your organization using the provided _seed, then acknowledge your role as the stakeholder so we may begin.
```

> [!TIP]
> If you like, adjust the prompt to make the simulation as your wishes. Maybe you rather prefer a black-box engagement, or a more simple scenario. Make your own simulation and learn from **DO IT YOURSELF**!

## AI Generated Case Study

Using the prompt presented earlier, the AI generated the following text, elaborating further the context of the organization. Read carefully and try to take notes of the most important aspects. 

```
The company is a mid-size FinTech, about six years old. We started in Europe, and our core business is an API-driven payments and digital wallet platform for other companies. Our customers are mainly online marketplaces, neobanks, and subscription platforms that plug into our APIs to issue virtual cards, move money between users, do FX (foreign currency exchange) conversions, and handle payout flows. Up to now, most of our volume has been in the EU and a bit in the US, but the board has decided that our next big growth bet is LATAM. That expansion is already in motion, and I’m being measured on whether we keep the platform stable, trustworthy, and out of the headlines while we do it.

On the tech side, we’re heavily cloud-native. We run on a single hyperscaler (I won’t name it for now, but think one of the big three), with most of our stack built around microservices, Kubernetes, and a very API-first mentality. Engineering moves fast; we use CI/CD everywhere, feature flags, all that modern DevOps culture. That’s great for speed, but it’s also how things like that exposed API key on GitHub happen. We already integrate with several LATAM banks and local payment rails via APIs and VPNs, and we’re starting to deal with more regional providers for KYC, fraud scoring, and SMS/notification services. So our attack surface in the region is not just “our” systems, but also all of these third parties and partners we depend on to make the product work in local markets.

From a security and compliance standpoint, we’re not a disaster, but we’re not a bank either. We’re PCI-DSS compliant, we have a basic SOC function that operates mostly during business hours with some on-call coverage, and we do vulnerability scanning and occasional red teaming. However, our CTI capability is almost non-existent beyond “we read vendor reports and some feeds.” The security team is small relative to the pace of change: I have a handful of engineers focused on product security, a small SOC, and SREs who help with reliability and incident response. Budget is tight, and anything I do in one area means I’m not doing something else. That’s why I can’t afford a broad, theoretical view of “all threats”; I need focus.

In terms of business stakes, for LATAM specifically, we’re pushing three main offerings: a white-label digital wallet for partners who want to launch quickly in Mexico and Brazil, cross-border payouts for gig and creator platforms, and a card-issuing API that lets companies issue physical and virtual cards in multiple currencies. The success metrics that my CEO and the board care about are transaction growth, uptime, and “zero major incidents” during the first eighteen months. We’ve promised 99.9999% availability to a couple of flagship partners in the region. If we fail on that or if we suffer a big breach that exposes customer PII or payment data, it will have a direct impact on churn, regulatory scrutiny, and our next funding round.

Risk-wise, we’ve already had a few warning shots. That exposed API key I mentioned never led to a confirmed breach, but it was a wake-up call about our engineering hygiene. We’ve seen some low-level credential stuffing and bot traffic against our login flows, a few DDoS attempts that our provider mostly absorbed, and a growing amount of phishing using our brand in Spanish and Portuguese. Nothing catastrophic yet, but enough to tell me that we’re on the radar. As we enter LATAM, I’m specifically worried about financially motivated criminal groups who specialize in banking and payment fraud in the region, ransomware crews that might go after us or our critical partners, and any threat actor who would want to disrupt our platform as a way to blackmail us or damage our reputation.

So yes, your mandate makes sense to me. I don’t want a giant encyclopedic view of the threat landscape. I want you to tell me, for this LATAM push, who is realistically likely to target us, how they are most likely to do it given our technology and business model, and what we should prioritize so that with my limited budget and small team, I can reduce the risk of something blowing up.
```

## Cyber Threat Intelligence Simulation

In the following sections, we will go through the CTI lifecycle. Keep in mind the formatting of the text; it has meaning:

1. Normal text is generally my own thoughs or comments.
2. _italics instructions of what you should do next_
3. **bold text highlights important CTI concepts or keywords**
4. > Quoted text is AI generated information
5. > _Italics quoted text highlights comments made by others_
6. `<!--Hidden text is used to ocult my answers. You can see them by inspecting the raw file-->`

> [!IMPORTANT]
> This file documents a simulation engagement. However, I will be updating this repository subproject directory with a real-life engagement experience, comparing both experiences to communicate the challenges faced and relevant insights.

### Task 1: Developing PIR leveraging well-known PIR development frameworks

In this section of the activity I will be guiding through the process of creating **Priority Intelligence Requirements** using well-known frameworks including [RedHat PIR Framework v1.1](https://github.com/redhat-infosec/priority-intelligence-requirements-dev/tree/main) and [Intel 471 CU-GIR Handbook Framework](https://hs-8813571.f.hubspotemail.net/hubfs/8813571/CU-GIRH%20v7.pdf).

PIRs are

> _prioritized set of topics that your stakeholders need intelligence on in order to make better decisions_ (Josh Darby MacLellan at FIRSTCTI24)

Usually, we MUST go through every relevant stakeholder in the organization that will use or receive the intelligence, and ask them what kind of intel they need, their concerns, and needs. 

This interviewing process is very fruitful because stakeholder can provide experience-based information that minimizes the possibility of missing details or plugging gaps in the investigation.

> [!TIP]
> In a real engagement it is recommended to track the time invested in the interviewing process using tools such as Google Calendar. Also, you should use the concentric-circle (must, should, could) approach to identify the most important stakeholders you should interact with first.

#### Step 1: Identifying core ELEMENTS of the organization using Red Hat's Approach

Before mocking up any PIR, we need to identify the ELEMENTS of the organization, defined in [RedHat PIR Framework v1.1](https://github.com/redhat-infosec/priority-intelligence-requirements-dev/tree/main).

The **ELEMENTS** are **keywords** that represents

- The organization **identity**
- The organization **strategy**
- The organization **mission** and **vision**

> [!INFO]
> Even though Red Hat approch is mostly used for internal CTI engagements, it can still be an effective framework when working with stakeholders, who know the details of the organization.

Usually we find these keywords within internal documents or, in this scenario, by interviewing stakeholders. You can also request information that includes these ELEMENTS by asking relevant questions, such as:

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

_Using the information provided by the stakeholder (AI generated), what could be the ELEMENTS of the organization? My answer is below this line_
<!--
- Features that define the org
   - API-driven with microservices architecture
   - Cloud-native organization
   - Mid-size tech company with 6 years in the European market

- Special attention to particular products/services
   - GitHub for exposed API credentials

- How, what, and where does your organization makes revenue?

The organization makes the most to the least revenue today in the EU, US, and LATAM regions (Where), by providing digital wallet services (How) to marketplaces, platforms, and neobanks. The organization uses a cloud-first API-driven approach, kubernetes and microservices environments to run their workloads (what) to all their customers with 99.99% uptime. 

- Important products or services
   - Digital Wallet for partners launching in México and Brazil

- Ahead of competitors
   - High uptime rate (99.9999%)

- Internal security strategy
   - PCI-DSS compliant
   - Internal, mostly reactive SOC
   - Ocassional vulnerability scanning and red teamming operations
-->