---
CIP: 1
Title: Cardano Improvement Proposals
Status: Active
Category: Meta
Authors:
    - Matthias Benkort <matthias.benkort@cardanofoundation.org>
    - Michael Peyton Jones <michael.peyton-jones@iohk.io>
Implementors: N/A
Discussions:
    - https://github.com/cardano-foundation/cips/pulls/365
Created: 2022-10-14
License: CC-BY-4.0
---

# CIP-0001: Cardano Improvement Proposals

## Abstract

A Cardano Improvement Proposal (CIP) is a formalised design document for the Cardano community and the name of the process by which such documents are produced and listed. A CIP  provides information or describes a change to the Cardano ecosystem, processes, or environment concisely and in sufficient technical detail. In this CIP, we explain what a CIP is; how the CIP process functions; the role of the CIP Editors; and how users should go about proposing, discussing and structuring a CIP.

The Cardano Foundation intends CIPs to be the primary mechanisms for proposing new features, collecting community input on an issue, and documenting design decisions that have gone into Cardano. Plus, because CIPs are text files in a versioned repository, their revision history is the historical record of significant changes affecting Cardano.

## Motivation

CIPs aim to address two challenges mainly:

1. The need for various parties to agree on a common approach to ease the interoperability of tools or interfaces.

2. The need to propose and discuss changes to the protocol or established practice of the ecosystem.

The CIP process does not _by itself_ offer any form of governance. For example, it does not govern the process by which proposed changes to the Cardano protocol are implemented and deployed. Yet, it is a crucial, community-driven component of the governance decision pipeline as it helps to collect thoughts and proposals in an organised fashion. Additionally, specific projects may choose to actively engage with the CIP process for some or all changes to their project.

## Specification

### CIPs

#### Structure

A CIP is, first and foremost, a document which proposes a solution to a well-defined problem. Documents are [Markdown][] files with a front matter _Preamble_ and a set of pre-defined sections. CIPs authors must abide by the general structure, though they are free to organise each section as they see fit.

The structure of a CIP file is summarised in the table below:

Name           | Description
---            | ---
Preamble       | Headers containing metadata about the CIP ([see below](#header-preamble)).
Abstract       | A short (\~200 word) description of the proposed solution and the technical issue being addressed.
Motivation     | A clear explanation that introduces a proposal's purpose, use cases, and stakeholders. If the CIP changes an established design, it must outline design issues that motivate a rework. For complex proposals, authors must write a [Cardano Problem Statement (CPS) as defined in CIP-9999][CPS] and link to it as the `Motivation`.
Specification  | The technical specification should describe the proposed improvement in sufficient technical detail. In particular, it should provide enough information that an implementation can be performed solely based on the design outlined in the CIP. A complete and unambiguous design is necessary to facilitate multiple interoperable implementations.
Rationale      | The rationale fleshes out the specification by describing what motivated the design and what led to particular design decisions. It should describe alternate designs considered and related work. The rationale should provide evidence of consensus within the community and discuss significant objections or concerns raised during the discussion. <br/><br/>It must also explain how the proposal affects the backward compatibility of existing solutions when applicable. If the proposal responds to a [CPS][], the 'Rationale' section should explain how it addresses the CPS and answer any questions that the CPS poses for potential solutions.
Path to Active | Organised in two sub-sections:<br/><h5>Acceptance Criteria</h5>Describes what are the acceptance criteria whereby a proposal becomes _'Active'_.<br/><h5>Implementation Plan</h5>A plan to meet those criteria. Or `N/A` if not applicable.
Copyright      | The CIP must be explicitly licensed under acceptable copyright terms ([see below](#licensing)).

<details>
  <summary><span id="header-preamble"><strong>Header preamble</strong></span></summary>

Each CIP must begin with a YAML key:value style header preamble (also known as 'front matter data'), preceded and followed by three hyphens (`---`).

Field          | Description
---            | ---
`CIP`          | The CIP number (without leading 0), or "\?" before being assigned
`Title`        | A succinct and descriptive title
`Status`       | Proposed \| Active \| Inactive (.._reason_..)
`Category`     | One of the registered categories covering one area of the ecosystem.
`Authors`      | A list of authors' real names and email addresses (e.g. John Doe <john.doe@email.domain>)
`Implementors` | A list of implementors committed to delivering an implementation of the proposal, when applicable. `N/A` when not applicable and `[]` when there's currently no implementor.
`Discussions`  | A list of links where major technical discussions regarding this CIP happened. Links should include any discussion before submission, and _must_ include a link to the pull request that created the CIP and any pull request that modifies it.
`Solution-To`  | A list of [CPS][] that this CIP addresses, if any. Omitted when not applicable.
`Created`      | Date created on, in ISO 8601 (YYYY-MM-DD) format
`License`      | Abbreviation of an approved license(s)

For example:

```yaml
---
CIP: 1
Title: Cardano Improvement Proposals
Status: Active
Category: Meta
Authors:
    - Frederic Johnson <frederic.johnson@cardanofoundation.org>
    - Sebastien Guillemot <sebastien@dcspark.io>
    - Matthias Benkort <matthias.benkort@cardanofoundation.org>
    - Duncan Coutts <duncan.coutts@iohk.io>
Implementors: N/A
Discussions:
    - https://github.com/cardano-foundation/cips/pulls/1
Created: 2020-03-21
License: CC-BY-4.0
---
```

</details>

<details>
  <summary><span id="repository-organization"><strong>Repository Organization</strong><span></summary>

A CIP must be stored in a specific folder named after its number (4-digit, left-padded with `0`) and in a file called `README.md`. Before a number is assigned, use `????` as a placeholder name.

Additional supporting files (such as diagrams, binary specifications, dialect grammars, JSON schemas etc.) may be added to the CIP's folder under freely chosen names.

For example:

```
CIP-0010
├── README.md
├── registry.json
└── registry.schema.json

```
</details>

<details>
  <summary><span id="licensing"><strong>Licensing</strong></span></summary>

CIPs are licensed in the public domain. Moreso, they must be licensed under one of the following licenses. Each new CIP must identify at least one acceptable license in its preamble. In addition, each license must be referenced by its respective abbreviation below in the _"Copyright"_ section.

#### Recommended licenses

- for software / code: Apache-2.0 - [Apache License, version 2.0][Apache-2.0]
- for documentation: CC-BY-4.0 - [Creative Commons Attribution 4.0 International Public License][CC-BY-4.0]

#### Unacceptable licenses

All licenses not explicitly included in the above lists are not acceptable terms for a Cardano Improvement Proposal unless a later CIP extends this one to add them.

</details>

> **Note** A reference template is available in [.github/CIP-TEMPLATE.md][CIP-TEMPLATE.md]

#### Statuses

CIPs can have three statuses: `Proposed`, `Active` or `Inactive`. [The CIP Process section](#the-cip-process) highlights how CIPs move through these statuses; no CIP should be given one of these statuses without satisfying the criteria described here below.

> **Note** There is no "draft" status: a proposal which has not been merged (and hence exists in a PR) is a draft CIP. Draft CIPs should include the status they are aiming for on acceptance. Typically, but not always, this will be _'Proposed'_.

##### Status: Proposed

A _'Proposed'_ CIP is any CIP that meets the essential CIP criteria but is not yet _'Active'_. The criteria that must meet a CIP to be merged as _'Proposed'_ are:

- It must contain all the sections described in [Structure](#structure).
- The quality of the content must be to the Editors’ satisfaction. That means it must be grammatically sound, well-articulated and demonstrates noticeable efforts in terms of completeness and level of detail.
- Its technical soundness should have been established. Where necessary, this may require review by particular experts and addressing their concerns. Note that the requirement is that the proposal makes sense (i.e. be technically sound), yet no consulted experts need to think it is a good idea.
- It must have a valid _'Path to Active'_. This particular section must be subdivided into two sub-sections:

  - _'Acceptance Criteria'_

    This sub-section must define a list of criteria by which the proposal can become active. Criteria must relate to observable metrics or deliverables and be reviewed by editors and project owners when applicable.

  - _'Implementation Plan'_

    This sub-section should define the plan by which a proposal will meet its acceptance criteria, when applicable. More, proposals that require implementation work in a specific project may indicate one or more implementors. Implementors must sign off on the plan and be referenced in the document's preamble.

    In particular, an implementation that leads to a hard-fork should explicitly mention it in its _'Implementation Plan'_.

##### Status: Active

An _'Active'_ CIP has taken effect according to the criteria defined in its _'Path to Active'_ section. What that means depends on the nature of the CIP, typically:

- For CIPs that relate to particular projects or pieces of technology, it becomes _'Active'_ by being implemented and released;
- For changes to the Cardano protocol, a CIP will become _'Active'_ by being live on the Cardano mainnet;
- For ecosystem standards, it means gaining sufficient and visible adoption in the community.

##### Status: Inactive

An _'Inactive'_ CIP describes any proposal that does not fit into the other types. A CIP can therefore be _'Inactive'_ for various reasons (e.g. obsolete, superseded, abandoned). Hence the status must indicate a justification between parentheses; for example:

```
Status: Inactive (superseded by CIP-0001)
```

#### Categories

CIPs are classified into distinct categories that help organise (and thus, find) them. Categories are meant to be flexible and evolve as new application domains emerge. Authors may leave the category as `?` should they not be sure under which category their proposal falls; editors will eventually assign one or reject the proposal altogether should it relate to an area where the CIP process does not apply.

At present, we consider the following list of initial categories:

Category   | Description
---        | ---
Meta       | Designates meta-CIP, such as this one, which typically serves another category or group of categories.
Wallets    | For standardisation across wallets (hardware, full-node or light).
Catalyst   | For proposals affecting Project Catalyst or the Jörmungandr project.
Tokens     | About tokens (fungible or non-fungible) and minting policies in general.
Metadata   | For proposals around metadata (on-chain or off-chain).
Tools      | A broad category for ecosystem tools not falling into any other category.

Additionally, projects of the ecosystem may explicitly enlist as new categories. The following section describes how projects can engage with the CIP process.

Explicitly registered categories are otherwise listed below.

Category   | Description
---        | ---
Plutus     | Changes or additions to Plutus, following the process described in [CIP-0035][]


#### Project Engagement With The CIP Process

In this context, we define _a project_ as a git repository owned by a team of maintainers. Besides, projects of the Cardano ecosystem that intend to follow the CIP process must explicitly enlist themselves and commit to the following:

- a) allocating time to **review** proposals from actors of the community when solicited by editors (i.e. after one first round of reviews);
- b) defining additional rules and processes whereby external actors can engage with their project;
- c) defining boundaries within their project for which the CIP process does apply;
- d) writing CIPs for significant changes introduced in their projects when it applies.

Enlisting for the CIP process happens by creating a CIP. That CIP must encapsulate the information listed above, as well as any other pieces of information deemed helpful to future authors. Of course, only team members of a target project can author such a proposal.

> **Warning** A reviewed and merged CIP does not automatically turn it into a work item for the team of maintainers.

Projects' maintainers define how a proposal can move from the state of idea (i.e. CIP) to actual implementation work. For example, some maintainers may volunteer to implement ideas as they see fit, and some may accept code changes in the form of pull requests. We, however, expect each team that enlists in the CIP process to provide clarity on these elements when registering their category.

Editors occasionally invite project owners to speak during review meetings and solicit them for ultimate approvals of proposals affecting a project under their authority. Said differently, CIPs that concern (part of) an enlisted project will only be merged after explicit acceptance of the enlisted reviewers.

> **Note** Optionally, projects may show their engagement using the following badge on their introductory README: ![](../.github/badge.svg) <svg xmlns="http://www.w3.org/2000/svg" width="211.97" height="35" viewBox="0 0 211.97 35"><rect class="svg__rect" x="0" y="0" width="160.07000000000002" height="35" fill="#487FFF"/><rect class="svg__rect" x="158.07000000000002" y="0" width="53.89999999999998" height="35" fill="#005384"/><path class="svg__text" d="M13.95 18.19L13.95 18.19L13.95 17.39Q13.95 16.19 14.38 15.27Q14.80 14.35 15.60 13.85Q16.40 13.35 17.45 13.35L17.45 13.35Q18.86 13.35 19.73 14.12Q20.59 14.89 20.73 16.29L20.73 16.29L19.25 16.29Q19.14 15.37 18.71 14.96Q18.28 14.55 17.45 14.55L17.45 14.55Q16.48 14.55 15.97 15.26Q15.45 15.96 15.44 17.33L15.44 17.33L15.44 18.09Q15.44 19.47 15.93 20.20Q16.43 20.92 17.38 20.92L17.38 20.92Q18.25 20.92 18.69 20.53Q19.13 20.14 19.25 19.22L19.25 19.22L20.73 19.22Q20.60 20.59 19.72 21.35Q18.84 22.12 17.38 22.12L17.38 22.12Q16.36 22.12 15.59 21.63Q14.81 21.15 14.39 20.26Q13.97 19.37 13.95 18.19ZM24.77 18.00L24.77 18.00L24.77 17.52Q24.77 16.28 25.21 15.32Q25.65 14.37 26.46 13.86Q27.27 13.35 28.31 13.35Q29.35 13.35 30.16 13.85Q30.96 14.35 31.40 15.29Q31.84 16.23 31.85 17.48L31.85 17.48L31.85 17.96Q31.85 19.21 31.41 20.16Q30.98 21.10 30.18 21.61Q29.37 22.12 28.32 22.12L28.32 22.12Q27.28 22.12 26.47 21.61Q25.66 21.10 25.22 20.17Q24.78 19.23 24.77 18.00ZM26.25 17.46L26.25 17.96Q26.25 19.36 26.80 20.13Q27.35 20.90 28.32 20.90L28.32 20.90Q29.31 20.90 29.84 20.15Q30.37 19.40 30.37 17.96L30.37 17.96L30.37 17.51Q30.37 16.09 29.83 15.34Q29.29 14.58 28.31 14.58L28.31 14.58Q27.35 14.58 26.81 15.33Q26.26 16.09 26.25 17.46L26.25 17.46ZM37.80 22L36.31 22L36.31 13.47L37.80 13.47L41.61 19.54L41.61 13.47L43.08 13.47L43.08 22L41.60 22L37.80 15.95L37.80 22ZM49.50 14.66L46.87 14.66L46.87 13.47L53.63 13.47L53.63 14.66L50.97 14.66L50.97 22L49.50 22L49.50 14.66ZM58.87 22L57.39 22L57.39 13.47L60.39 13.47Q61.87 13.47 62.67 14.13Q63.47 14.79 63.47 16.05L63.47 16.05Q63.47 16.90 63.06 17.48Q62.64 18.06 61.91 18.37L61.91 18.37L63.82 21.92L63.82 22L62.23 22L60.52 18.71L58.87 18.71L58.87 22ZM58.87 14.66L58.87 17.52L60.39 17.52Q61.14 17.52 61.57 17.15Q61.99 16.77 61.99 16.11L61.99 16.11Q61.99 15.43 61.60 15.05Q61.21 14.68 60.44 14.66L60.44 14.66L58.87 14.66ZM69.43 22L67.95 22L67.95 13.47L69.43 13.47L69.43 22ZM77.35 22L74.24 22L74.24 13.47L77.16 13.47Q78.61 13.47 79.37 14.05Q80.12 14.63 80.12 15.78L80.12 15.78Q80.12 16.36 79.81 16.83Q79.49 17.30 78.88 17.56L78.88 17.56Q79.57 17.75 79.95 18.26Q80.33 18.78 80.33 19.51L80.33 19.51Q80.33 20.71 79.56 21.36Q78.79 22 77.35 22L77.35 22ZM75.72 18.15L75.72 20.82L77.37 20.82Q78.07 20.82 78.46 20.47Q78.85 20.13 78.85 19.51L78.85 19.51Q78.85 18.18 77.49 18.15L77.49 18.15L75.72 18.15ZM75.72 14.66L75.72 17.06L77.18 17.06Q77.87 17.06 78.26 16.75Q78.65 16.43 78.65 15.86L78.65 15.86Q78.65 15.23 78.29 14.95Q77.93 14.66 77.16 14.66L77.16 14.66L75.72 14.66ZM84.66 19.16L84.66 19.16L84.66 13.47L86.14 13.47L86.14 19.18Q86.14 20.03 86.57 20.48Q87.01 20.93 87.85 20.93L87.85 20.93Q89.56 20.93 89.56 19.13L89.56 19.13L89.56 13.47L91.04 13.47L91.04 19.17Q91.04 20.53 90.17 21.32Q89.30 22.12 87.85 22.12L87.85 22.12Q86.39 22.12 85.53 21.33Q84.66 20.55 84.66 19.16ZM97.29 14.66L94.65 14.66L94.65 13.47L101.42 13.47L101.42 14.66L98.76 14.66L98.76 22L97.29 22L97.29 14.66ZM110.76 22L105.18 22L105.18 13.47L110.72 13.47L110.72 14.66L106.66 14.66L106.66 17.02L110.16 17.02L110.16 18.19L106.66 18.19L106.66 20.82L110.76 20.82L110.76 22ZM117.58 18.95L114.50 18.95L114.50 17.80L117.58 17.80L117.58 18.95ZM124.17 22L121.12 13.47L122.74 13.47L124.88 20.14L127.05 13.47L128.68 13.47L125.61 22L124.17 22ZM134.19 22L132.72 22L132.72 13.47L134.19 13.47L134.19 22ZM139.78 22L138.24 22L141.47 13.47L142.80 13.47L146.02 22L144.48 22L143.78 20.01L140.47 20.01L139.78 22ZM142.13 15.28L140.89 18.82L143.36 18.82L142.13 15.28Z" fill="#FFFFFF"/><path class="svg__text" d="M171.83 17.80L171.83 17.80Q171.83 16.54 172.43 15.54Q173.03 14.55 174.08 13.99Q175.13 13.43 176.45 13.43L176.45 13.43Q177.60 13.43 178.52 13.84Q179.45 14.25 180.06 15.02L180.06 15.02L178.55 16.39Q177.74 15.40 176.57 15.40L176.57 15.40Q175.88 15.40 175.35 15.70Q174.82 16 174.52 16.54Q174.23 17.09 174.23 17.80L174.23 17.80Q174.23 18.51 174.52 19.05Q174.82 19.60 175.35 19.90Q175.88 20.20 176.57 20.20L176.57 20.20Q177.74 20.20 178.55 19.22L178.55 19.22L180.06 20.58Q179.45 21.35 178.53 21.76Q177.60 22.17 176.45 22.17L176.45 22.17Q175.13 22.17 174.08 21.61Q173.03 21.05 172.43 20.05Q171.83 19.06 171.83 17.80ZM186.98 22L184.60 22L184.60 13.60L186.98 13.60L186.98 22ZM194.53 22L192.15 22L192.15 13.60L195.99 13.60Q197.13 13.60 197.97 13.98Q198.81 14.35 199.27 15.06Q199.73 15.76 199.73 16.71L199.73 16.71Q199.73 17.66 199.27 18.35Q198.81 19.05 197.97 19.42Q197.13 19.80 195.99 19.80L195.99 19.80L194.53 19.80L194.53 22ZM194.53 15.47L194.53 17.93L195.85 17.93Q196.58 17.93 196.95 17.61Q197.32 17.29 197.32 16.71L197.32 16.71Q197.32 16.12 196.95 15.80Q196.58 15.47 195.85 15.47L195.85 15.47L194.53 15.47Z" fill="#FFFFFF" x="171.07000000000002"/></svg>
>
> ```md
> ![https://github.com/cardano-foundation/CIPs](https://raw.githubusercontent.com/cardano-foundation/CIPs/master/.github/badge.svg)
> ```

### The CIP Process

#### 1. Early stages

##### 1.a. Authors open a pull request

Proposals must be submitted to the [cardano-foundation/CIPs][Repository] repository as a pull request named after the proposal's title. The pull request title should _not_ include a CIP number; the editors will assign one. Discussions may precede a proposal. Early reviews and discussions streamline the process down the line.

> **Note** Proposals addressing a specific CPS should also be listed in the corresponding CPS header, in _'Proposed Solutions'_, to keep track of ongoing work.


##### 1.b. Authors seek feedback

Authors shall champion their proposals. The CIP process is a collaborative effort, which implies discussions between different groups of individuals. While editors may provide specific inputs and help reach out to experts, authors shall actively seek feedback from the community to help move their proposal forward.

Discussions and comments shall mainly happen on Github in pull requests. When discussed on other mediums, we expect authors or participants to report back a summary of their discussions to the original pull request to keep track of the most critical conversations in a written form and all in one place.

A dedicated Discord channel may also be created for some long-running discussions to support quick chats and progress on particular topics (while still being regularly summarised on the repository).

As much as possible, commenters/reviewers shall remain unbiased in their judgement and assess proposals in good faith. Authors have the right to reject comments or feedback but are strongly encouraged to address concerns in their 'Rationale' section. Ultimately, CIP editors shall make the last call concerning the various statements made on a proposal and their treatment by the author(s).

By opening pull requests or posting comments, commenters and authors agree to our [Code of Conduct][CoC]. Any comment infringing this code of conduct shall be removed or altered without prior notice.

#### 2. Editors' role

##### 2.a. Triage in bi-weekly meetings

CIP editors meet regularly in [a public Discord server][Discord] to go through newly proposed ideas in a triage phase. As a result of a triage, editors acknowledge new CIPs, and briefly review their preamble. Proposers should not pick a CIP number and instead use `?` when first opening a proposal. Editors will allocate a temporary number as part of the triage phase. The triage also allows new CIPs to get visibility for potential reviews.

##### 2.b. Reviews

In every meeting, editors will also review in more depth some chosen CIPs (based on their readiness and the stability of the discussions) and assess if they meet the criteria to be merged in their aimed status.

During review sessions, editors will regularly invite project owners or actors from the ecosystem who are deemed relevant to the meeting's agenda. However, meetings are open and held in public to encourage anyone interested in participating.

#### 3. Merging CIPs in the repository

Once a proposal has met its necessary acceptance criteria (as explained in [Statuses](#Statuses)) and has been sufficiently and faithfully discussed by community members, it is merged with its target status.

> **Warning** Ideas deemed unsound shall be rejected with justifications or withdrawn by the authors. Similarly, proposals that appear abandoned by their authors shall be rejected until resurrected by their authors or another community member.

CIPs are generally merged with the status _'Proposed'_ until they meet their _'Path to Active'_ requirements. In some rare cases (mainly when written after the facts and resulting in a broad consensus), proposals may be merged as _'Active'_ immediately.

Each proposal is unique and has a bespoke _'Path to Active'_, which must be reviewed case-by-case. There must be sufficient time between the first appearance of a proposal and its merge into the repository to ensure enough opportunity for community members to review it.

#### 4. Implementors work towards completeness following their 'Implementation Plan'

Once merged, implementors shall execute the CIP's _'Implementation Plan'_, if any. If a proposal has no implementors or no _'Implementation Plan'_, it may simply remain as _'Proposed'_ in the repository.

> **Warning** It is perfectly fine to submit ideas in the repository with no concrete implementation plan, yet they should be treated as such: ideas.

Besides, once all of the _'Path to Active'_ requirements have been met, authors shall make another pull request to change their CIP's status to _'Active'_. Editors may also do this on occasion.

### Editors

#### 1. Missions

CIP Editors safeguard the CIP process: they form a group enforcing the process described in this document and facilitating conversations between community actors. CIP editors should strive to keep up to date with general technical discussions and Cardano proposals. For each new draft proposal submitted on [cardano-foundation/CIPs][PullRequest] an editor might review it as follows:

- Read the proposal to check if it is ready, sound, and complete.
- Check if it has been [properly formatted](#structure).
- Check if sufficient time has been allowed for proper discussion amongst the community.
- Ensure the motivation behind the CIP is valid and that design choices have relevant justifications or rationale.
- Confirm licensing terms are acceptable.
- Assign a CIP number
- Assign a given category to help with searching
- Request wording/grammar adjustments

CIPs that do not meet a sufficient level of quality or don't abide by the process described in this document will be rejected until their authors address review comments.

#### 2. Reviews

Note that editors **may** provide technical feedback on proposals in some cases, although they aren't expected to be the sole technical reviewers of proposals. CIPs are, before anything, a community-driven effort. While editors are here to facilitate the discussion and mediate debates, they aren't necessarily technical experts on all subjects covered by CIPs.

Therefore, CIPs authors are encouraged to reach out to known experts to demonstrate their good faith and openness when they champion a proposal. Editors may help with such efforts but cannot be expected to do this alone.

#### 3. Nomination

Existing editors or the community may nominate new editors, provided they have proven to be already existing and active contributors to the CIP process and are ready to commit some of their time to the CIP process regularly.

The missions of an editor include, but aren't exclusively limited to, any of the tasks listed above. Active members that seek to become listed editors may also come forth and let it be known. Any application will take the form of a pull request updating this document with a justification as the pull request's description.

Current editors are listed here below:

| Matthias Benkort <br/> [@KtorZ][] | Sebastien Guillemot <br/> [@SebastienGllmt][] | Robert Phair <br/> [@rphair][] | Frederic Johnson <br/> [@crptmppt][] |
| ---                               | ---                                           | ---                            | --- |

[@KtorZ]: https://github.com/KtorZ
[@SebastienGllmt]: https://github.com/SebastienGllmt
[@rphair]: https://github.com/rphair
[@crptmppt]: https://github.com/crptmppt

## Rationale

### Key changes from CIP-0001 (version 1)

#### Explicit enlisting

A recurring pain point with the previous CIP process was the lack of clear ownership/accountability of some proposals affecting remote parts of the ecosystem. On several occasions, proposals from community members have concerned, for example, core components of the Cardano architecture. However, those proposals have been hard to move forward with and to either reject or turn into concrete action steps. Authors usually do not have the technical proficiency required to implement them and rely on the core engineering team in charge of projects to do so. Thus, explicit compliance and collaboration of those engineering teams are necessary to propose changes affecting their work.

By asking teams to explicitly state their compliance with the CIP process with clear, accountable owners (as individuals), it becomes plausible to now establish a dialogue between community members and technical leadership responsible for specific ecosystem projects. Furthermore, projects that, on the contrary, do not seek to participate in CIP or receive contributions in the form of CIP/CPS are automatically taken out of this process, saving time and energy for both reviewers and authors.

#### Introduction of Cardano Problem Statements

A significant friction point regarding complex CIPs is often how the main problem is stated. The _'Motivation'_ is often insufficient (or simply underused) to describe various aspects of a problem, its scope, and its constraints. This lack of clarity leads, in the end, to poorly defined issues and debates over solutions that feel unclear amongst different participants.

The introduction of [CIP-9999: Cardano Problem Statements][CIP-9999] addresses this gap by introducing a formal template and structure around problem statements. However, requiring any CIP to be preceded by a CPS would likely be overkill and become an obstacle to the overall adoption of the CIP process for more straightforward problems. At this stage, it is reasonable to think either (a) that CIP authors would foresee the complexity and state their problem as a CPS beforehand or (b) that editors or reviewers will require authors to write a CPS to clarify a perhaps ambiguous motivation on complex CIPs.

We also anticipate project owners or community actors will write standalone CPS to document well-known issues for which the design space is still to be explored.

#### Nomination of new editors

The _'Editors'_ section now details how to become a CIP editor. The process aims to be simple and define those involved the most with editorship tasks as editors. Thus, being an active contributor to the CIP process as a prerequisite only makes sense. We want to leave the room open for either existing editors to refer an existing community as an editor or for community members to formulate that request explicitly.

There are no delays or number of contributions necessary to pretend to become an editor. Those criteria are often less relevant than others and more subjective, such as the quality of one's participation or their relevance. Since editors also need to work with one another in the end, it seems logical that existing editors have their final say about whom they intend to work with.

#### Removal of `type` in the preamble

The `type` field in the header has shown to be:

- confusing (often authors are getting it wrong);
- not-too-useful (as a `type` tells you very little about the nature of the CIP).

An ad-hoc classification by non-rigid categories, which may evolve over time to reflect ecosystem areas, seems better suited. Therefore, we do not require authors to categorise their CIPs; instead, categories will be added and maintained by editors as a side task atop the CIP process.

#### Simplification of the statuses

Over time we've learnt that the valuable information a status should convey is really about the readiness of a CIP, especially regarding standards. For a long time, many CIPs have lived as `Draft` despite some being used in dozens of systems. Consequently, the `status` has lost a bit of its meaning. The frontier between `Draft` and `Proposed` hasn't always been clear, and it has proven challenging to come up with good statuses to describe all possible rejections. So instead, the current division of statuses is as simple-as-it-can-be and remains flexible regarding rejections.

### Choice of CoC

The choice of a code of conduct follows other popular open source initiatives. It serves as a good, unilaterally accepted foundation which can be later revisited if necessary.

## Path to Active

- [ ] Rework existing draft CIPs to adopt this new format and process. In particular, CIPs affecting enlisted projects should be brought to the attention of the respective code owners.
- [ ] Possibly, edit / align old CIPs preambles and sections to at least reflect also this new format.

## Copyright

This CIP is licensed under [CC-BY-4.0][].

[Apache-2.0]: http://www.apache.org/licenses/LICENSE-2.0
[CC-BY-4.0]: https://creativecommons.org/licenses/by/4.0/legalcode
[CIP-0035]: https://github.com/cardano-foundation/CIPs/tree/master/CIP-0035
[CIP-9999]: https://github.com/cardano-foundation/CIPs/tree/master/CIP-9999
[CIP-TEMPLATE.md]: https://github.com/cardano-foundation/CIPs/tree/master/.github/CIP-TEMPLATE.md
[CODE_OWNERS]: https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners
[CPS]: https://github.com/cardano-foundation/CIPs/tree/master/CIP-9999
[Discussions:editors]: https://github.com/cardano-foundation/CIPs/discussions/new?category=editors
[Markdown]: https://en.wikipedia.org/wiki/Markdown
[PullRequest]: https://github.com/cardano-foundation/CIPs/pulls
[RFC 822]: https://www.ietf.org/rfc/rfc822.txt
[Repository]: https://github.com/cardano-foundation/CIPs/pulls
[CoC]: https://github.com/cardano-foundation/CIPs/tree/master/CODE_OF_CONDUCT.md
[Discord]: https://discord.gg/Jy9YM69Ezf
