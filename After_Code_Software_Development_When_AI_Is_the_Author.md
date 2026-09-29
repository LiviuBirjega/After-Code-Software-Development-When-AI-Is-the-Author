# After Code: Software Development When AI Is the Author

**Sep 29, 2026 · Liviu Birjega**

*Disclaimer: The ideas and opinions in this paper are solely the author's and do not necessarily represent the views of any organization with which the author is affiliated.*

*A note on method: For what it is worth, artificial intelligence was used in the research and writing of this paper. It may be the last time anyone can honestly say that as a disclosure rather than a given.*

## Abstract
Software engineering is entering a structural transition in which AI agents move from completion assistants to primary authors of implementation code, while human engineers move toward intent specification, system architecture and verification. When code generation becomes cheap and abundant, the binding constraint shifts from how fast code can be written to how reliably its correctness, security, extensibility and maintainability can be established.

This paper proposes a two-phase timeline with a speculative third: a transition over the next 3 to 5 years in which agents write most code in today's languages under human review; a possible AI-native phase over 7 to 10 years in which languages, frameworks and education are redesigned around machine authorship and human auditing; and, 15 to 20 years out, the prospect of custom operating systems and hardware built for individual systems. It argues that the specification becomes the primary engineering asset, that teams reorganize around single technical owners directing agents, that software creation splits into three tiers, and that the apprenticeship pipeline for senior engineers is the transition's most serious casualty. Each claim is tied to current evidence, and the paper states what would falsify it.

## Contents
* Abstract
* 1. Introduction
* 2. Why this time is different
* 3. Phase 1: The transition
* 4. The verification bottleneck
  * Verification debt
* 5. The specification becomes the source of truth
  * 5.1 Limits of the specification model
* 6. AI-native languages and frameworks
  * 6.1 Toward Phase 3: custom operating systems, private AI and modular hardware
* 7. Syntax becomes optional; computational understanding does not
* 8. The new developer
* 9. The new team
* 10. The three-tier software economy
* 11. Education and the apprenticeship paradox
* 12. Employment and the transitional generation
* 13. Risks and open questions
  * 13.1 The circular AI trust chain
  * 13.2 Other systemic risks
  * 13.3 Liability, licensure and intellectual property
* 14. What would falsify this thesis
* 15. Recommendations
* 16. Conclusion
* References

---

## 1. Introduction

When AI makes producing code cheap, the scarce skills in software development move upward: toward specifying intent, structuring systems, managing constraints and verifying behavior. The central question is no longer how quickly AI can write code, but how software engineering changes when implementation becomes abundant.

This paper argues that AI agents are becoming the primary authors of implementation while humans move toward the roles of designer, specifier, reviewer and verifier. The transition is already visible at the leading edge of the industry, but its eventual extent remains uncertain.

I propose two broad phases, and a speculative third:

*   **Phase 1 (next 3 to 5 years).** A transition in which AI agents write an increasing majority of implementation code in today's programming languages, while humans remain responsible for intent, architecture, review and verification.
*   **Phase 2 (next 7 to 10 years).** A possible AI-native phase in which languages, frameworks and development processes are increasingly designed around machine authorship and human auditing.
*   **Phase 3 (15 to 20 years).** An era in which complex systems ship with custom operating systems, private AI and modular custom hardware built for that system, running on private infrastructure that coexists with the public cloud, driven as much by security, sovereignty and intellectual property as by cost.

These horizons are forecasts, not established facts. They depend on continued progress in AI capability, improvements in verification, organizational adoption, economics and the ability of education to adapt. The timeline exists to make the thesis testable, not to claim certainty. Beyond roughly 25 years the paper makes no claims, because anything past that horizon is pure speculation.

The core claims are:
*   AI is already moving software development from code production toward specification and verification.
*   Writing code will become less important as a professional skill, while understanding computation remains essential.
*   Programming languages and frameworks will increasingly be optimized for machine generation and machine checking rather than human typing.
*   The specification, together with tests, contracts and other constraints, will become the primary expression of software intent.
*   Development teams will become substantially smaller, although complex systems will still require multiple human specialists.
*   People without traditional programming training will increasingly build small and medium-complexity applications.
*   Professional software engineers will concentrate on systems where complexity, scale, integration, security, safety or regulation make casual development insufficient.
*   The central constraint shifts from generating software to establishing that generated software is correct, secure and appropriate.

My vantage point is that of someone who was part of the history this paper describes and evolved with it. My first contact with the new information technologies came in the late 1980s, in high school and at university, at the beginning of the modern software development era we are now leaving. In early 1992, still a fourth-year student at a five-year Faculty of Automation, Electronics and Computer Science, I was hired as a systems engineer to run the university's newly acquired IBM PS/2 networks on Novell NetWare; it was the first time something of that complexity had entered the institution, and the senior staff could not efficiently take it on themselves, so the faculty turned to its students. That pattern, a new technology arriving faster than the established generation can absorb it, is the same one this paper is about. I graduated in 1993, taught labs and stood in for professors across several disciplines, and in 1996 founded a small company that helped businesses in accounting, publishing and printing, transportation and real estate make the transition from analog to digital. In early 2001 I joined MedcomSoft in Toronto to build a pioneering electronic medical records system when few physicians used anything digital, and in early 2002 I joined IBI Group, since acquired by Arcadis, where I still build transportation infrastructure software, data platforms and, most recently, AI agents.

I have watched several waves of tooling promise to change development. This one differs in one decisive respect: it changes not merely the tools used by the author, but the identity of the author itself.

I cannot claim to see the future, but I can see it with reasonable confidence, and the method matters as much as the experience. Intelligence analysts are trained to hold three to five possible scenarios for everything, to assign each a likelihood, and to raise or lower those likelihoods continuously as facts and verified feedback arrive. Almost nothing is certain; there are always trade-offs and compromises. But practiced permanently, that discipline produces about the best understanding a given context allows. The phases in this paper are scenarios of that kind, the evidence in each section is what moves their likelihoods, and Section 14 states what would move them downwards.

## 2. Why this time is different

Every previous major shift in software development raised the level of abstraction, but a human still wrote the program. Assembly gave way to high-level languages; compilers took over machine code; libraries absorbed reusable functionality; frameworks absorbed boilerplate. Each step let developers express more with less effort, but the developer remained the person translating intent into executable instructions.

AI agents change that division of labor. The human increasingly specifies what should happen while an agent determines how to implement it. Anthropic's analysis of roughly 400,000 Claude Code sessions found that people make most of the planning decisions, what to do, while the agent makes most of the execution decisions, and how to do it. The same study found that greater domain expertise was associated with substantially more work completed per instruction, and that the share of sessions spent debugging fell by nearly half over seven months [1].

This does not mean AI has removed the constraints that limited earlier automation. AI systems remain imperfect, probabilistic and dependent on context. Their output requires evaluation, and generated software can contain functional, security and architectural defects. The decisive difference is that general-purpose agents generate ordinary software in existing languages and frameworks rather than being confined to the templates of a particular low-code environment.

Fourth-generation languages (4GL), computer-aided software engineering (CASE) tools and low-code platforms previously promised to reduce or eliminate conventional programming. Their limitation was expressiveness: when the desired behavior fell outside the abstractions they provided, conventional programming returned. AI agents attack the problem differently. They generate the implementation the specification requires rather than forcing the specification to fit a fixed template.

The open question is therefore not whether AI can write code. It clearly can. The harder question is whether verification, security and human understanding can keep pace with the volume of software that increasingly capable agents produce.

## 3. Phase 1: The transition

The first phase is already operating at scale. Google reported in April 2026 that 75% of its new code was AI-generated and approved by engineers, up from about a quarter in late 2024, with engineers increasingly orchestrating agents rather than typing implementation [2].

Anthropic reported that, as of May 2026, more than 80% of the code merged into its own codebase was authored by Claude, up from low single digits before Claude Code shipped in early 2025, and that the typical engineer merged roughly eight times as much code per day in the second quarter of 2026 as in 2024 [3]. The report itself calls the eightfold figure "almost certainly an overstatement of the true productivity gain," since lines merged are not the same as value delivered [3]. These are company-specific, self-reported measurements, not industry averages. Their significance is that the proposed workflow is already operational at substantial scale, not that every organization has adopted it.

Gartner forecast in 2024 that generative AI would require 80% of the engineering workforce to upskill through 2027 and described a medium-term shift to AI-native software engineering in which most code is AI-generated and engineers primarily steer agents by supplying context and constraints [4].

When implementation can be generated on demand, the marginal cost of producing another version of an application falls sharply. The bottleneck moves elsewhere. Six patterns define the phase:

*   **AI as the primary implementation author.** Agents generate features, tests, migrations, documentation and infrastructure configuration from specifications, issues and conversation. The human decides what the system should accomplish and whether the result is acceptable.
*   **The developer as reviewer and verifier.** Human time shifts from typing toward defining intent, examining generated behavior and designing mechanisms that detect errors. Automated tests, static analysis, contracts, security analysis and formal verification grow in importance because more code is not automatically more trustworthy code.
*   **Experienced developers carry disproportionate value.** Developers who understand conventional implementation know what kinds of mistakes software contains, because they have created, debugged and maintained those mistakes for decades. That knowledge becomes a specialized form of verification expertise. The paradox is that AI reduces the implementation experience needed to produce software while raising the value of people who have it.
*   **Teams begin to shrink.** If one developer can direct several agents in parallel, work that required several developers can be done by fewer. This does not make every complex system a one-person project: product, domain, security, operations and compliance knowledge remain human responsibilities. The defensible prediction is that the ratio of implementation authors to systems falls while the importance of system owners and specialist reviewers rises.
*   **Non-developers begin building software.** Business users, analysts and domain experts build small applications, reports, workflows and internal tools through natural-language interfaces. Professional developers do not disappear; work that once had to pass through a development department no longer needs to.
*   **Education begins to adapt, and lags.** In spring 2026, undergraduate enrollment in Computer and Information Sciences fell 8.4% at four-year institutions and 11.2% at two-year colleges, while overall undergraduate enrollment grew 1.3% [5]. Enrollment trends have many causes and should not be attributed solely to AI, but the direction matters for a profession whose training model is changing.

## 4. The verification bottleneck

The most important consequence of cheap code generation is that verification becomes the scarce resource.

A system can now generate thousands of lines of plausible implementation faster than a human can read them. This reverses an old economic relationship. Historically, implementation was expensive and verification was applied to a relatively small amount of human-written code. In an AI-native workflow, implementation is abundant while the capacity to establish correctness remains strictly bounded.

DORA's 2025 research describes AI as an amplifier of an organization's existing strengths and weaknesses: AI adoption now improves delivery throughput, but it still increases delivery instability, which suggests that teams have learned to move faster before their delivery systems have learned to absorb that speed safely [6]. The benefit depends on the surrounding organizational system rather than on the coding tool alone [6].

Security illustrates the gap between plausible output and trustworthy output. Veracode's evaluation of more than 100 language models on 80 curated tasks found that generated code introduced an OWASP Top 10 vulnerability in 45% of cases, and that security performance had not improved as functional correctness did [7]. This was a controlled evaluation, not a claim that 45% of production AI code is vulnerable. Its significance is that gains in syntactic or functional correctness do not automatically produce gains in security.

The software supply chain adds another failure mode. A USENIX Security 2025 study of 576,000 code samples from 16 models found that recommended packages did not exist at average rates of at least 5.2% for commercial models and 21.7% for open-source models, with more than 205,000 unique hallucinated names, many of them recurring across runs [8]. Attackers can register those names in public registries, so a hallucination becomes a supply-chain attack [8].

### Verification debt

These findings describe the growth of verification debt: the gap between the volume of software an organization can generate and the volume it can reliably understand, test, secure and govern. In traditional engineering, generation and comprehension scale together because humans write the code line by line. AI-native development breaks that link through an extreme cost asymmetry:

*   **Generation cost approaches zero.** An agent synthesizes thousands of lines of syntactically valid code in seconds.
*   **Verification cost grows non-linearly.** Reading, mentally simulating, threat-modeling and integration-testing generated code requires human cognitive capacity, domain context and execution time, all of which remain expensive and bounded.

Verification debt compounds through three failure modes:

*   **Loss of mental models.** When code is approved on the strength of passing tests without deep comprehension, engineers stop understanding the system. During incidents, mean time to resolution rises because no human knows the execution paths.
*   **Self-confirming tests.** When agents write unit tests for their own generated code, the tests mirror the agent's assumptions. High coverage masks low robustness because tests validate what the model thought it wrote rather than probing real boundary conditions.
*   **Architectural decay.** Agents working within a local context window tend to add helper functions or duplicate logic rather than refactor abstractions, so structural complexity accumulates.

If generation becomes dramatically faster while verification capacity stays roughly constant, the organization looks more productive while becoming less certain about what it has built. The central engineering question changes from "Can we build it?" to "Can we establish that what we built is what we intended, and that it behaves safely under conditions we did not explicitly anticipate?"

## 5. The specification becomes the source of truth

If implementation becomes cheap enough, the specification becomes the primary asset.

In a conventional process, code is treated as the ultimate source of truth because it is the artifact that executes. Requirements documents go stale, architecture diagrams fall behind, and tests cover only part of the intended behavior.

An AI-native process reverses that relationship. The desired architecture, requirements, constraints, invariants, tests and acceptance criteria become the persistent expression of intent, and implementation becomes a generated artifact that is regenerated when intent changes. GitHub's Spec Kit is an early example: it places a structured specification, then a technical plan, then small testable tasks at the center of agentic execution, with the specification as the contract that agents generate, test and validate code against [9].

The pipeline becomes: intent, specification, verification criteria, generated implementation.

This does not imply that specifications will be written in unconstrained English. Natural language is ambiguous. The likely direction is disciplined articulation combined with structured constraints: schemas, types, executable tests, contracts and formal properties.

Nor does it imply that the specification collapses into code by another name. The specification evolves into a two-layer artifact. One layer is plain language: a description of the system that a domain expert, an auditor, a new team member or a regulator can read and understand without machine assistance. The other layer is formal: the schemas, contracts, tests and properties that agents generate against and verifiers check. The agent keeps the two consistent. That dual audience is the point. A specification that only instructs machines would be a programming language; one that also explains the system to humans is documentation, onboarding material, audit evidence and the record of intent, all in one maintained artifact.

### 5.1 Limits of the specification model

Two constraints bound pure specification-driven development.

**Hyrum's Law and non-deterministic regeneration.** Hyrum's Law states: "With a sufficient number of users of an API, it does not matter what you promise in the contract: all observable behaviors of your system will be depended on by somebody" [10]. In traditional development, code persists: its unstated quirks, such as execution timing, error formats, ordering of operations or resource usage, stay fixed until someone changes them, and downstream systems quietly come to depend on them. When implementation is regenerated from a specification, a functionally equivalent implementation that passes every explicit test can still alter those unstated behaviors:
*   Reordered internal operations or different concurrency primitives change timing and lock contention that callers assumed.
*   Changes in error payloads, JSON key order or enum-to-string mappings break downstream parsers.
*   Different allocation or query-batching strategies trigger rate limits or memory pressure in shared infrastructure.

Regeneration then breaks production not because the code violated its specification, but because it changed an implicit dependency. Specifications therefore cannot describe only the happy path; they need behavioral pinning, deterministic regression tests and explicit non-functional invariants.

**The specification complexity ceiling.** As system complexity rises, the effort required to write an unambiguous, complete specification approaches the effort of writing the implementation. Real systems are governed by distributed consensus failures, partial network partitions, security boundaries and regulatory constraints. This produces three tensions:
*   **Exhaustiveness versus readability.** A high-level specification forces the agent to make unguided assumptions about unspecified edge cases, introducing latent architectural risk.
*   **Specification bloat.** Eliminating ambiguity by specifying every failure mode, retry policy, validation schema and state transition produces thousands of lines of dense constraints, as complex and fragile as the codebase it replaces.
*   **Specification-level logic errors.** Specifications are written by humans and carry logic flaws, contradictory invariants and intent drift. An agent will faithfully implement a specification containing an unnoticed deadlock or security hole, producing a system that is provably correct against an incorrect specification.

The specification does not eliminate complexity; it relocates it. Moving from human authoring to AI generation changes how intent is executed, not the intellectual rigor required to define, bound and evaluate a complex system.

## 6. AI-native languages and frameworks

Current programming languages were designed around human authorship. Their syntax, naming conventions, module structures and abstraction mechanisms are shaped by human memory, typing effort and readability. An AI author operates under different constraints.

Verbosity costs a machine far less than it costs a human. Repetition that is undesirable in human-written code is harmless if it makes generation and automated verification more reliable. Explicit contracts become more valuable than concise syntax. Architectural constraints can be encoded directly into the development environment rather than expressed only through convention.

Likely directions include:
*   Explicitness over brevity.
*   Machine-checkable contracts and invariants built into the language.
*   Stronger, enforceable representations of architectural constraints.
*   Specifications capable of generating multiple implementation forms.
*   Human-readable views rendered on demand from machine-oriented representations.
*   Verification is integrated directly into the development environment.
*   Frameworks that constrain agents rather than merely assist human developers.

Formal verification is the most consequential of these. Martin Kleppmann argues that AI could reduce the cost of producing formal proofs by orders of magnitude, making formal verification economically viable for mainstream software: if the AI proves the code correct against a specification, the human need not review the code line by line, and a mechanical proof checker, unlike a human reviewer, cannot be talked into accepting a wrong argument [11]. AI does not remove the need for specifications; it moves the difficulty toward defining correctly what should be proved [11].

This produces a hierarchy of questions, each harder than the last:
1.  Is the implementation correct?
2.  Is it a correct implementation of the specified behavior?
3.  Is the specified behavior the desired behavior?

The higher the level of automation, the more the third question dominates.

One consequence of this shift is easy to overlook. Today's models learned to code from decades of human-written software. If humans stop writing it, the next generation of models learns from AI-generated code verified by humans, or from nothing new at all. That feedback loop will be resolved by humans, not by AI, and it is one of the reasons new languages and frameworks will be needed: deliberately designed representations that are unambiguous to generate, cheap to verify and rich enough to train on. It may also be resolved locally. A complex system in Phase 2 or Phase 3 may carry its own custom model, trained on that system's verified specification and implementation, so that the AI that maintains the system is itself part of the system.

### 6.1 Toward Phase 3: custom operating systems, private AI and modular hardware

If code generation becomes cheap enough, the logic that regenerates an application from its specification extends to the layers beneath it. A third phase, 15 to 20 years out, is one in which complex systems ship with custom operating systems, private AI, purpose-built runtimes and modular custom hardware, on private infrastructure that lives beside the public cloud rather than replacing it. Three current trends make this an extrapolation rather than a guess.

*   **The custom operating system already exists; what was missing was cheap specialization.** Unikernels, operating-system images tailored to a single application, have demonstrated for a decade what a custom OS delivers: boot times in milliseconds, runtime memory of about a megabyte, a minimal trusted computing base, and an image stripped of shells, unused system calls and idle services [12]. What blocked mass adoption was cost: every specialized image had to be developed and optimized by hand for its application [12]. That is precisely the cost AI generation removes. When an agent can produce and verify the operating-system slice a system needs from its specification, the custom OS becomes the default rather than the exception. The record also carries a warning: a 2019 security assessment found that some unikernels lacked basic mitigations such as address-space randomization and stack protection [13]. Custom means smaller, not automatically secure, and the verification discipline of Section 4 still applies.
*   **Private AI, and the private cloud it runs on, will live beside the public cloud.** Enterprise AI is pulling infrastructure back toward private environments. Broadcom's 2026 survey of 1,800 senior IT decision-makers found 56% of enterprises running or planning production AI inference on private cloud, and 83% considering or having already repatriated workloads from public cloud [14]. A February 2026 survey of 203 enterprise IT leaders found that 91% would choose on-premises, private-cloud or hybrid infrastructure over public cloud for AI involving sensitive data, citing data sovereignty, cost predictability and real-time performance [15]. Gartner defines AI sovereignty in terms of who holds decision authority over each layer of the AI stack within a given geography, and its analysts expect 65% of governments to impose technological sovereignty requirements by 2028 and 90% of organizations to run hybrid or multi-cloud architectures by 2027 [16]. The evidence is not one-sided: an IDC survey from December 2025 found AI applications split almost evenly between private and public cloud, and the analyst who ran it saw no massive repatriation push [17]. The consistent picture is hybrid. The public cloud keeps elastic and experimental workloads; sensitive, steady-state and regulated AI moves to private infrastructure. Once AI is embedded in the systems themselves, not only used to build them, the models, their data and the hardware they run on inherit the same sovereignty requirements. That is why private AI implies private, and eventually custom, infrastructure.
*   **Hardware is becoming modular, and AI is learning to design it.** The semiconductor industry is moving from monolithic chips to chiplets: pre-validated silicon building blocks combined in one package over the open Universal Chiplet Interconnect Express (UCIe) die-to-die standard. At the March 2026 Chiplet Summit, Intel and Cadence showed independently designed dies from two companies exchanging data over UCIe without custom adaptation logic, and Rebellions presented a quad-chiplet inference accelerator built entirely on UCIe interconnects [18]. Chiplet vendors now sell platforms that combine a customer's own logic with off-the-shelf connectivity, memory and compute dies, aimed explicitly at system developers as well as hyperscalers [19]. AI is entering the design loop at the same time: reinforcement learning has placed production chip floorplans since 2021 [20], the first fully AI-generated chip design was taped out in 2023 [21], and agent frameworks now generate register-transfer-level hardware from specifications with verification in the loop [22]. Modular hardware turns custom silicon into a composition problem; AI makes composition cheap. Together they make purpose-built hardware for a specific system economically conceivable, for the same reasons custom software is. Custom will usually mean composed and configured, from chiplets, programmable logic and firmware, rather than fabricated: mask sets at advanced nodes still cost tens of millions of dollars, so fully custom silicon will remain reserved for the highest-value systems. Phase 3 is a combination of custom and modular hardware with custom software, not a bespoke chip for every application.

The drivers are not only cost and convenience. A system that runs only the operating-system components it needs has a smaller attack surface and no exposure to vulnerabilities in code it never uses. A custom stack is also harder to copy, which matters where intellectual property is the product. Hardware is likely to evolve in two directions at once: to accelerate the models that write software, and to run the explicit, verifiable and often verbose code those models produce more economically than general-purpose processors designed around hand-written software.

This makes the future of the traditional software corporation hard to predict. Its moat has been the accumulated code of its operating systems, frameworks and applications. When the required parts of an operating system or framework can be reproduced on demand, that moat narrows, and the durable assets become specifications, verified components, data and trust. Whether incumbents adapt, are displaced, or become suppliers of verified building blocks is an open question this paper does not resolve.

## 7. Syntax becomes optional; computational understanding does not

Writing programming syntax will become less important. Understanding computation will not.

A professional developer may eventually deliver production systems without manually writing implementation code. That developer still needs to understand algorithms, data structures, state machines, concurrency, failure modes, security boundaries, performance and distributed systems. The distinction is between authoring implementation and understanding implementation.

Anthropic's randomized trial makes the risk concrete. Fifty-two mostly junior engineers learned an unfamiliar Python library; those using AI assistance scored 17% lower on a mastery quiz taken minutes later, with the largest gap in debugging, while their speed advantage was not statistically significant [23]. How people used AI mattered: participants who asked conceptual questions and requested explanations retained far more than those who delegated code generation outright [23].

This is the central educational paradox of AI-assisted development: the less code humans need to write, the more deliberate education is required to ensure they understand what the machines produce.

Debugging changes accordingly. Instead of stepping through lines written by oneself or a colleague, developers diagnose the gap between intended and observed behavior. The questions become:
*   Was the intent specified correctly?
*   Did the agent interpret the specification correctly?
*   Did the implementation satisfy all stated constraints?
*   Did the test suite cover the critical failure modes?
*   How did the system behave outside the conditions the specification anticipated?

## 8. The new developer

The developer of the AI-native era is valued less for typing speed and more for judgment. Five competencies become central.

*   **Architecture and system design.** Decomposing complex problems into components, establishing boundaries, evaluating trade-offs and anticipating how the system will evolve. AI will assist with design, but human architectural judgment remains essential because it integrates business goals, organizational context and long-term risk.
*   **Specification and articulation.** Expressing intent precisely enough that an agent produces an acceptable system. Clear writing becomes a core engineering discipline. Andrej Karpathy's framing of "Software 3.0" makes the point directly: prompts written in natural language are becoming programs, and English is becoming a programming interface [24].
*   **Verification engineering.** Designing tests, contracts, property checks and evaluation frameworks that establish whether a generated system behaves as intended. The critical skill is identifying failure modes and knowing what evidence separates a correct system from a plausible but flawed one.
*   **Understanding influence, human and machine.** Extracting clear requirements from stakeholders who may not know what they want and defending systems against manipulation of the machines that build them: prompt injection, poisoned dependencies and compromised context. Both draw on the same knowledge of how trust works and how it is exploited.
*   **Decision-making under speed.** When an agent can produce a working alternative in minutes, the developer makes more consequential decisions per day than before, often with incomplete information. Making fast, well-reasoned, near-optimal decisions, and recognizing which of them are reversible, becomes a core competency rather than a senior privilege.

## 9. The new team

Teams do not disappear, but their composition changes. The most plausible model is one primary technical owner per complex system, supported by a smaller network of specialists and directing AI agents. The technical owner directs the agents, maintains the architecture and specifications, controls verification and remains accountable for the system's integrity.



*[Figure 1. The new team: one developer, five specialist roles, AI agents]*

Around the technical owner remain the domain specialists, product managers, security engineers, site reliability engineers, compliance officers and business stakeholders. What changes is the number of people whose daily job is writing line-by-line implementation code.

Much of today's organizational structure exists to coordinate multiple human code authors: sprints, code review, merge conflicts and hand-offs. When one engineer directs several agents, that coordination overhead falls. Risk moves from peer coordination to system continuity: if a single owner holds primary oversight, their departure creates severe exposure unless specifications, decision records and verification suites are maintained as long-lived organizational assets.

Section 4 argued that verification is the scarce resource, which might seem to imply more people, not fewer. It does not, in most cases, because the verifier is not a passive reader. The people who verify generated systems must also be able to use AI to resolve what they find and to steer the agents toward the correct approach. That makes them the new professional developers, not an additional layer of reviewers, and they carry the same obligations the profession always had: to practice domain-driven design and to learn the domain deeply enough to judge whether the system is right. Authoring headcount falls sharply; verification headcount is the developer role, reshaped.

## 10. The three-tier software economy

Software creation is dividing into three operational tiers rather than a simple professional-versus-amateur split.

*   **Tier 1: Casual builders.** Non-technical individuals building small applications, reports and personal automations through natural-language interfaces.
*   **Tier 2: AI-assisted domain applications.** Technically capable domain experts building departmental tools, workflows and integrations with AI agents, structured specifications and organizational guardrails.
*   **Tier 3: Professional systems engineering.** Professional engineers concentrating on systems where complexity, scale, integration, security, safety, regulation or reliability make casual development insufficient.

The lower tiers are not hypothetical. Anthropic's session analysis found that people in non-software occupations reached verified success on code-producing tasks at about 29%, against about 34% for software engineers, and that every one of the ten largest occupation groups landed within seven points of engineers; domain knowledge predicted success more reliably than a coding background [1].

The critical operational challenge lies at the boundaries. A Tier 1 automation becomes a departmental workflow, which becomes mission-critical infrastructure, without anyone having decided that it should. Organizations need explicit policies and automated triggers defining when a casual tool must graduate to professional engineering ownership, and a professional responsibility for finding, hardening and governing what the lower tiers produce.

There are therefore two kinds of "new developers," and history explains why both persist. The industry once believed that subject-matter experts would learn enough software to build their own applications; fourth-generation languages and end-user computing were built on that belief, and it collapsed. In its place a profession was created in which software engineers learn the domain. That profession does not disappear now. What changes is that the subject-matter expert can, for the first time, build real applications with AI, and the two will work side by side and often together. The limit is mindset rather than tooling: domain experts are experts in their domain, and complex, non-linear, abstract software systems require a way of thinking that their expertise does not supply. They will build something, and it will be useful, but it will be bounded.

Much of what the lower tiers produce will also be disposable software: applications built to serve one purpose, used, and regenerated from the specification when the need returns or changes, rather than maintained. Disposability is a legitimate design goal at Tier 1 and Tier 2 and a hazard at Tier 3, where the specification, not the generated artifact, is what must persist.

One specialization will persist across all three tiers: the legacy engineer. Mainframes, COBOL and Fortran still need people who understand them, decades after they stopped being current, and the same will be true of today's systems. The hand-written codebases, frameworks and languages of the 2010s and 2020s will be the legacy of the AI-native era, and maintaining, migrating and eventually retiring them will require engineers who can read and reason about code written for human authors. That skill may become scarce, and valuable, precisely because new engineers will not have learned to write such code.

## 11. Education and the apprenticeship paradox

Computer science curricula must adapt to this realignment. The fundamentals, mathematics, logic, data structures, operating systems, networking and distributed systems, remain essential for judging complex systems, but what is taught around them must change.

System design, decomposition and verification must move earlier in a student's training. Articulation and technical writing must be taught as primary engineering skills, not soft skills. Edsger Dijkstra, the sharpest critic of natural-language programming, also lamented a decline in people's mastery of their own language; in a world where the specification is the program, that mastery is an engineering competency [25].

*   **A new discipline: the history of computing.** An architect's judgment has traditionally been accumulated by living through the history of the field: the shifts from mainframes to client-server to cloud, the rise and fall of languages and frameworks, and the architectural mistakes each generation made and corrected. If students can no longer acquire that experience in real time, they must acquire it compressed. A rigorous discipline covering the history of hardware, software, systems architecture and design, taught as engineering case study rather than trivia, is the most direct way to accelerate the experience an architect needs.
*   **Critical thinking, from early childhood.** The new developer must make fast, sound decisions, and that ability rests on critical thinking that cannot be "installed" by a university course. It has to be taught from the earliest years of schooling, because a generation that grows up with AI producing fluent answers on demand will need, more than any time before, the habit of asking whether the answer is right. Starting in high school is too late.

The hardest problem is the apprenticeship paradox. Engineering judgment has historically developed through years of writing routine code, debugging failures, reviewing pull requests and maintaining legacy systems. If AI automates that routine work, how do junior engineers acquire equivalent judgment?

The answer cannot be to prohibit AI tools, and it cannot be unguided use, which measurably reduces skill mastery [23]. Education and onboarding must create deliberate, artificial experience:
*   Dissecting complex AI-generated systems.
*   Diagnosing intentionally introduced, subtle failures.
*   Conducting comparative architectural trade-off analyses.
*   Writing formal specifications and property-based test suites.
*   Red-teaming generated applications for security vulnerabilities.
*   Using AI as a tutor that explains, rather than a contractor that delivers, during skill formation [23].

## 12. Employment and the transitional generation

The labor-market impact of AI on software development is already showing structural signs. Stanford's analysis of ADP payroll records covering millions of U.S. workers finds no widespread displacement, but employment among workers aged 22 to 25 in highly AI-exposed occupations, including software development, is roughly 19% lower than it would be if it had tracked the employment of similarly aged workers in occupations less exposed to AI, a gap that stood at 15% a year earlier; experienced workers in the same occupations show no comparable shortfall [26]. The gap comes mainly from fewer hires, not more departures, and it shows up in employment rather than in pay [26].

This matters for software engineering because entry-level implementation work has been the training ground for senior talent. The chain runs: routine implementation is automated, so fewer junior engineers are hired, so the skill-formation pipeline is truncated, so the long-term supply of senior verifiers shrinks.

If organizations eliminate junior positions to capture short-term productivity gains, they deplete the future supply of senior architects capable of verifying complex AI-generated systems. Lisanne Bainbridge identified the same irony in industrial automation four decades ago: automating most of a job erodes the skills operators need for the rare interventions that still fall to them, so they need more training, not less [27]. Rebuilding the apprenticeship model is therefore an urgent industry requirement, not an educational nicety.

## 13. Risks and open questions

### 13.1 The circular AI trust chain

To handle high code volume, organizations increasingly deploy AI agents to review code and scan for security issues. This creates a closed loop in which probabilistic models evaluate the output of similar probabilistic models: human intent, AI generation, AI audit, human sign-off.

The circularity introduces three vulnerabilities:
*   **Shared blind spots.** Language models used as evaluators recognize and favor their own generations, and models trained on similar data share similar weaknesses, so an AI reviewer is least likely to catch exactly the errors an AI author is most likely to make [28]. The security and supply-chain failure rates in Section 4 show that those errors are common [7, 8].
*   **Prompt injection.** Adversarial content in a context window can compromise the author and the reviewer at the same time, since both read the same inputs.
*   **Automation bias.** People who supervise reliable automation become complacent and approve its output without scrutiny; the more often the system is right, the less able the human becomes to notice when it is wrong [29]. Bainbridge's ironies of automation describe the same dynamic: the operator left to catch the failures the designer could not automate is the one whose skills the automation has eroded [27].

Breaking the circle requires verification that is out of band and deterministic, so that no probabilistic component certifies another: sound compilers and strict type systems, property-based and boundary testing, and machine-checkable proofs. The AI may propose the proof; a proof kernel that cannot be persuaded checks it [11].

### 13.2 Other systemic risks

*   **The ambiguity of natural language.** Dijkstra argued that formal languages exist precisely because natural language permits the ambiguity that formal symbolism eliminates [25]. AI-native development must pair human language with schemas, contracts and formal constraints rather than unconstrained prose.
*   **Knowledge concentration.** One technical owner per system raises key-person risk. Specifications, decision records and verification suites must preserve knowledge that once lived across a team.
*   **Vendor dependency.** Development capability becomes tied to a small number of model providers, with exposure to lock-in, price changes, outages and data-sovereignty constraints, especially for public-sector and regulated clients.
*   **The transitional generation.** Phase 1 relies on engineers who learned to write code the traditional way. When they retire, the industry needs a replacement source of the judgment they carry, and Section 12 shows that source is already narrowing.

### 13.3 Liability, licensure and intellectual property

Civil engineering settled long ago how to hold someone accountable for a structure its designer did not personally build: a licensed engineer of record reviews and stamps the design and carries the liability. Software has never had an equivalent, and AI authorship makes the absence harder to ignore. When a system whose code no human wrote fails in the field, the question of who signed for it will be asked in court and in legislature.

This paper does not expect licensure in Phase 1. If it comes, it will most likely follow failures, as it did in civil, aviation and medical engineering, where regulation arrived after the discipline had shown what happens without it; Phase 2 is the period in which that pressure is likeliest to build. Defining and implementing such a regime will require political will and this will take a long time, but the outline is predictable: a professional accountable for Tier 3 systems, the specification and verification record as the stamped drawings, and deterministic verification evidence as the basis for sign-off. Phase 3 will almost certainly operate under something of that shape.

Intellectual property will evolve in parallel. Purely AI-generated output currently has uncertain copyright protection in major jurisdictions, which weakens copyright as a moat for generated stacks and strengthens the case for private infrastructure and trade-secret protection. In practice the legal argument will turn on the fact that this is human-directed work using AI as a tool, with human intent, specification and verification throughout. Too many industries and too much of daily life will depend on such software for the law to leave the question open indefinitely.

## 14. What would falsify this thesis

A technology thesis should name the evidence that would prove it wrong. This one would be weakened or falsified if:
*   **Manual coding keeps its economic value.** Human-written implementation remains superior and preferred for mainstream applications despite advancing AI capability. The METR randomized trial, in which experienced open-source developers were 19% slower with early-2025 AI tools while believing they were 20% faster, shows this is not a hypothetical [30]; METR's 2026 follow-up found developers likely faster with later tools but could not measure by how much, because many refused to work without AI [31].
*   **Verification fails to scale.** AI-assisted verification proves unreliable, forcing engineers back to line-by-line review and choking throughput.
*   **Demand expands faster than efficiency.** Productivity gains do not shrink team ratios because software demand grows faster than development efficiency, the Jevons paradox applied to code. Jevons observed in 1865 that more efficient steam engines had increased Britain's consumption of coal rather than reduced it, because a cheaper unit of work found more uses [32]; cheaper code may do the same to demand for developers.
*   **Specifications prove unmaintainable.** Structured specifications turn out to be too ambiguous, complex or expensive to serve as the source of truth, as Section 5.1 warns they might.
*   **Apprenticeship turns out to be seamless.** Junior developers acquire senior-level judgment through AI-mediated workflows without the skill-formation deficits measured so far [23].
*   **Custom stacks stay uneconomic.** General-purpose hardware, operating systems and public cloud keep winning on cost and ecosystem, the current move toward private AI reverses, and custom operating systems and silicon remain confined to hyperscalers and niches, so Phase 3 never arrives.

## 15. Recommendations

**For current developers**
*   Shift effort from syntax speed toward system architecture, specification design and verification strategy.
*   Treat AI agents as collaborators to be directed, not autocomplete to be accepted.
*   Build expertise in spotting plausible but incorrect output, static analysis, property-based testing and security boundary review.
*   Keep deep foundational knowledge of computation current; it is what makes auditing generated systems possible.

**For universities**
*   Move system architecture, decomposition and verification to the core of the curriculum, early.
*   Teach precise technical articulation and specification writing as core engineering disciplines.
*   Integrate adversarial security, formal methods and supply-chain risk into standard coursework.
*   Build labs around failure analysis, system dissection and debugging generated codebases, and teach students to use AI as a tutor rather than a substitute during skill formation [23].

**For organizations**
*   Replace lines-of-code and feature-throughput metrics with verification capacity, defect density, security compliance and mean time to resolution.
*   Restructure around one technical owner per complex system, supported by domain, product, operations, security and compliance roles.
*   Define explicit graduation policies for when departmental AI applications move to professional engineering ownership.
*   Treat specifications, architectural decision records and test suites as primary, long-lived assets.
*   Put deterministic, out-of-band verification in the CI/CD pipeline so that no AI reviewer is the last line of defense against an AI author.
*   Protect the junior pipeline deliberately: hire and train early-career engineers on verification and system dissection, because the market will not do it by default [26].

## 16. Conclusion

The developer does not disappear. The developer changes.

For decades, software engineering was constrained by the cost of translating human intent into executable code. AI attacks that constraint directly. As implementation becomes cheap, the market value of code authoring falls, and the scarce human contributions move to higher ground: what should be built, what constraints it must satisfy, how we establish that the generated system is correct and secure, and how we ensure the specification itself reflects real operational intent.

This does not make computational knowledge obsolete. It makes computational understanding more critical than mechanical typing. The future belongs to engineers who can translate complex human goals into precise specifications, direct networks of autonomous agents, and build the deterministic evidence required to trust the result.

Two principles should anchor how the profession prepares. First, AI is a tool, and it will remain a tool used by humans; responsibility for what is built, and for whether it is right, does not transfer to the machine. Second, the pace of this change is itself a hazard. Alvin Toffler described in 1970 the disorientation that follows when technological change outruns a society's ability to absorb it, and called it future shock [33]. The compression of decades of software practice into a few years is exactly that condition, and preparing people for it is part of the engineering task.

Human history offers one more lesson. Plans drift, and events arrive in their own order, rarely the one that was planned. What has consistently carried people through such transitions is language: the capacity to articulate, negotiate and pass on what was learned. Language is now acquiring a new dimension. Large language models make it, for the first time, a direct instrument for building machines. Whether we welcome that or not, we will need to be ready for it, as humans and as professionals.

Code becomes cheap. Specification becomes valuable. Verification becomes critical. Judgment remains the scarce human resource.

## References

1. Hitzig, Z., Massenkoff, M., Lyubich, E., Heller, R., and McCrory, P. Agentic coding and persistent returns to expertise. Anthropic, June 16, 2026. Analysis of about 400,000 Claude Code sessions from about 235,000 users, October 2025 to April 2026.
2. Pichai, S. Remarks at Google Cloud Next 2026, April 22, 2026. Reported 75% of new code at Google AI-generated and approved by engineers. Coverage.
3. Anthropic Institute (Clark, J., et al.). When AI builds itself. June 4, 2026. Reports more than 80% of merged code authored by Claude as of May 2026 and an eightfold rise in code merged per engineer, with the authors' own caveat on the latter. Coverage.
4. Gartner. Generative AI Will Require 80% of Engineering Workforce to Upskill Through 2027. Press release, October 3, 2024.
5. National Student Clearinghouse Research Center. Computer Science Enrollment Is Cooling, August 11, 2026, summarizing the Final Spring 2026 Enrollment Trends report of June 4, 2026.
6. DORA. State of AI-assisted Software Development 2025. Google, 2025.
7. Veracode. 2025 GenAI Code Security Report. July 30, 2025.
8. Spracklen, J., Wijewickrama, R., Sakib, A. H. M. N., Maiti, A., Viswanath, B., and Jadliwala, M. We Have a Package for You! A Comprehensive Analysis of Package Hallucinations by Code Generating LLMs. 34th USENIX Security Symposium, 2025. Summary.
9. GitHub. Spec-driven development with AI: Get started with a new open source toolkit. GitHub Blog, September 2025. Coverage.
10. Wright, H. Hyrum's Law, hyrumslaw.com; also Winters, T., Manshreck, T., and Wright, H. Software Engineering at Google. O'Reilly, 2020.
11. Kleppmann, M. Prediction: AI will make formal verification go mainstream. December 8, 2025.
12. Kuenzer, S., et al. Unikraft: Fast, Specialized Unikernels the Easy Way. EuroSys 2021; and Unikraft security documentation.
13. Michaels, S., and Dileo, J. Assessing Unikernel Security. NCC Group, 2019. Summary.
14. Broadcom. Private Cloud Outlook 2026: The AI Tipping Point. Survey of 1,800 senior IT decision-makers, June 2026. Coverage.
15. Cloudian. Enterprise AI Infrastructure Survey 2026. Survey of 203 enterprise IT decision-makers, February 2026; released March 3, 2026. Coverage.
16. Gartner. Predicts 2026: AI Sovereignty. October 16, 2025. Government-sovereignty and hybrid-adoption figures as reported by Spectro Cloud and Digital Chiefs.
17. TechTarget. Enterprises make strides with private AI on-premises. September 2, 2026, citing IDC's December 2025 survey of 304 application-platform decision makers.
18. The Machine Herald. Chiplets Enter the Production Era as UCIe 3.0, Massive Packaging Expansions, and Multi-Die AI Accelerators Converge. March 23, 2026.
19. Electronics For You. Chiplets Aim to Accelerate AI Design. July 16, 2026.
20. Mirhoseini, A., et al. A graph placement methodology for fast chip design. Nature, Vol. 594, 2021, pp. 207–212.
21. Blocklove, J., Garg, S., Karri, R., and Pearce, H. Chip-Chat: Challenges and Opportunities in Conversational Hardware Design. ACM/IEEE Workshop on Machine Learning for CAD, 2023. arXiv:2305.13243.
22. Spec2RTL-Agent: Automated Hardware Code Generation from Complex Specifications Using LLM Agent Systems. 2025. arXiv:2506.13905.
23. Anthropic. How AI assistance impacts the formation of coding skills. January 2026. Randomized controlled trial with 52 engineers.
24. Karpathy, A. Software Is Changing (Again). Keynote, Y Combinator AI Startup School, June 2025. Transcript and slides.
25. Dijkstra, E. W. On the foolishness of "natural language programming". EWD 667, 1978; published in Program Construction, Lecture Notes in Computer Science, Vol. 69, Springer, 1979.
26. Brynjolfsson, E., Chandar, B., and Chen, R. Canaries in the Coal Mine? Six Facts about the Recent Employment Effects of Artificial Intelligence. Stanford Digital Economy Lab, August 2025; revised August 12, 2026, with data through June 2026.
27. Bainbridge, L. Ironies of Automation. Automatica, Vol. 19, No. 6, 1983, pp. 775–779.
28. Panickssery, A., Bowman, S. R., and Feng, S. LLM Evaluators Recognize and Favor Their Own Generations. NeurIPS 2024. arXiv:2404.13076.
29. Parasuraman, R., and Manzey, D. H. Complacency and Bias in Human Use of Automation: An Attentional Integration. Human Factors, Vol. 52, No. 3, 2010, pp. 381–410.
30. Becker, J., Rush, N., Barnes, E., and Rein, D. Measuring the Impact of Early-2025 AI on Experienced Open-Source Developer Productivity. METR, July 10, 2025. Coverage.
31. Becker, J., Rush, N., Cunningham, T., Rein, D., and Mahamud, K. We Are Changing Our Developer Productivity Experiment Design. METR, February 24, 2026.
32. Jevons, W. S. The Coal Question; An Inquiry Concerning the Progress of the Nation, and the Probable Exhaustion of Our Coal-Mines. London: Macmillan and Co., 1865 (2nd ed., revised, 1866). The paradox is set out in Chapter VII, "Of the Economy of Fuel."
33. Toffler, A. Future Shock. Random House, 1970.