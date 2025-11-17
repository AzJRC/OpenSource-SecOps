# Cyber Threat Intelligence Planning and Direction Demo

In this file I am documenting a first attempts to **formally** engage with the Cyber Threat Intelligence lifecycle process.

## Creating the case study with ChatGPT

For this demonstration, I use ChatGPT 5.1 Thinking model to walk me through a case study, using the following prompt:

```
I am currently studying the Cyber Threat Intelligence (CTI) lifecycle and focusing specifically on the **Planning and Direction** phase. Recently, I reviewed a SANS publication titled:
[*“Bridging the Gaps in CTI: A Practical Guide to Threat-Informed Security with PIRs”*](https://www.sans.org/blog/bridging-gaps-cti-practical-guide-threat-informed-security-pirs)

During this process, I identified two major Priority Intelligence Requirements (PIR) development frameworks relevant to formalizing this lifecycle phase:

1. **Red Hat PIR Development Framework**

   * Documentation: [FIRST Priority Intelligence Requirements](https://www.first.org/resources/papers/Berlin2023/Priority-Intelligence-Workshop-Requirements-Rojcik-and-Janout.pdf)
   * Repository: [Priority Intelligence Requirement's RedHat](https://github.com/redhat-infosec/priority-intelligence-requirements-dev/tree/main)

2. **Intel 471 Cybercrime Underground General Intelligence Requirements (CU-GIR) Framework**

   * Overview: [CU-GIR Intel471](https://www.intel471.com/blog/introducing-intel-471s-cybercrime-underground-general-intelligence-requirements-cu-gir-a-common-framework-to-address-a-common-challenge)
   * Model: [CU-GIR Document Intel471](https://hs-8813571.f.hubspotemail.net/hubfs/8813571/CU-GIRH%20v7.pdf)
   * Repository: [CU-GIR Intel471 Repository](https://github.com/intel471/CU-GIR/blob/main/README.md)

After PIRs are established, the subsequent activity is **Threat Actor Prioritization**, guided by the methodology found here:
[FIRST Threat Actor Prioritization with RedHat Methodology](https://www.first.org/resources/papers/Berlin2023/Threat-Quantification-Prioritization-Kraus-Small.pdf)

Finally, once actors are prioritized, PIRs must be operationalized into **priority TTPs** using tools such as:

* MITRE ATT&CK Navigator
* Red Hat PriorityTTPGen Tool: [PriorityTTPGen Tool](https://github.com/redhat-infosec/PriorityTTPGen/tree/main)

---

### **Task Request**

Please construct a realistic CTI scenario and guide me through the **Planning and Direction** phase from start to finish. The walkthrough must include the following steps:

1. Defining a plausible organization profile and threat context.
2. Developing PIRs using both:
   * The Red Hat PIR development methodology.
   * The Intel 471 CU-GIR framework.
3. Performing threat actor prioritization using:
   * Structured Analytical Techniques,
   * Example advanced search queries (e.g., OSINT sources),
   * And examples of effective AI analytical prompts.
4. Prioritize related TTPs using:
   * MITRE ATT&CK Navigator
   * Red Hat PriorityTTPGen Tool

For the purposes of this exercise, assume the following:

* I already understand the theory of the CTI lifecycle.
* No prior hands-on experience using **MITRE ATT&CK Navigator** or the **PriorityTTPGen tool**, so procedural guidance should be explicit.
* The objective is not only to explain the process but to simulate its execution and produce tangible outputs.
* Don't give the answers directly; attempt to guide me instead of giving me the answwers directly. Promote critical thinking.

By the end of the walkthrough, I should have:

* A defined organizational scenario.
* Completed PIRs in both frameworks.
* A ranked list of threat actors.
* A set of prioritized TTPs mapped to relevant frameworks and tools.

In this walkthrough, you should:

* Behave as the orchestrator of this CTI demonstration (when applicable)
* Behave as an stakeholder of the fictional company you will create (when applicable)
* Behave as a parner CTI specialist (when applicable)

Use the following scenario starting-point to build the case study.

_I am in a conference room with you for our first CTI planning meeting. I've just explained the idea of the CTI lifecycle to you, the stakeholder. Now it's your turn, as the CISO of Finetic, to give me the context of the organization. This is the context:_

> You know the entire company is betting on the LATAM expansion over the next six months. The board is watching it, our investors are watching it, and I'm supposed to make sure it doesn't all blow up.

> My problem is that I'm seeing all this chatter about other FinTechs getting hit. Every morning, it's a new report about a ransomware crew or some data breach. Then, last week, our own devs accidentally exposed an API key on a public GitHub repo. We caught it, thank God, but it proves we're vulnerable.

> I can't protect everything. I have a limited budget and a small team. I need you to tell me what to worry about. Don't give me a 50-page report on 'all the threats.' Give me something actionable. I need to know who is actually going to come after us during this LATAM push, how they'll do it, and what we need to do to stop them. That's the 'subject' of this. Make sense?"
```

The goal of this task is to practice in a realistic setting the application of the following theretical concepts:
- Priority Intelligence Requirements
- Threat Actor Prioritization
- Prioritization of TTPs

> [!IMPORTANT]
> I will revise this report with a comparison analysis once this demo workflow has been validated in a real engagement. The update will outline what remained consistent, what changed in practice, and what lessons emerged when applying this methodology in a live operational context.

## Demo

### Demo overview

This section will cover the whole Planning and Direction phase. Follow along and consider how I am formatting the text of this file:

- Normal text are my own thoughts, notes, or instructions
- _Italics are scenario descriptions to set the tone of the "theater" (the demo), manually rephrased from the AI generated response_
- **Bold text highlights important CTI concepts**
- > Quoted text is part of the "theater" experience, manually reprased from the AI generated response

> [!NOTE]
> Follow along and try to come up with your own ideas. My answers are hidden from the rendered Markdown. You can inspect them by looking at the raw file.

We will go through the following tasks:

1. Contextualization and first engagement
   * define Finetic in a way CTI can use
2. Develop PIRs
   * Red Hat–style decision-centric PIRs
   * Map them into Intel 471 CU-GIR structure
3. Threat actor prioritization
   * Use Structured Analytic Techniques (SATs)
   * OSINT queries + example AI prompts
   * End with a ranked actor list
4. TTP prioritization
   * Translate PIRs + actors → ATT&CK techniques
   * Build a Navigator layer and show how PriorityTTPGen would score them


### Task 1: Contextualization and first engagement

_I am in a conference room with you for our first CTI planning meeting. I've just explained the idea of the CTI lifecycle to you, the stakeholder. Now it's your turn, as the CISO of Finetic, to give me the context of the organization. This is the context:_

> You know the entire company is betting on the LATAM expansion over the next six months. The board is watching it, our investors are watching it, and I'm supposed to make sure it doesn't all blow up.

> My problem is that I'm seeing all this chatter about other FinTechs getting hit. Every morning, it's a new report about a ransomware crew or some data breach. Then, last week, our own devs accidentally exposed an API key on a public GitHub repo. We caught it, thank God, but it proves we're vulnerable.

> I can't protect everything. I have a limited budget and a small team. I need you to tell me what to worry about. Don't give me a 50-page report on 'all the threats.' Give me something actionable. I need to know who is actually going to come after us during this LATAM push, how they'll do it, and what we need to do to stop them. That's the 'subject' of this. Make sense?"

_The stakeholder takes a deep breath. Then he tells you..._

> I need you to tell me what to worry about during the LATAM push. Who is actually going to come after us, how they’ll do it, and what to do about it. Not all threats. The ones that matter

