# Grant Ships Whitepaper

**Authors**: Matt Davis (ui369.eth), Chris Wylde (boilerrat.eth), Jordan Lesich (jord.eth)

**Date**: Feb 19th 2024

## Summary

### Vision

Grant Ships is a meritocratic, decentralized, capture-resistant grants framework that enables communities to deploy capital in an effective and accessible way.

### Mission

At the heart of Grant Ships' mission is a commitment to merit. We believe that the best way to distribute grants is to work within a game cycle where the best allocators receive progressively larger sums to allocate. 

With Grant Ships, the best grants programs aren't selected or even voted in through proposal. The best grant programs and the most talented allocators will be discovered through open and decentralized competition. With these core ideals in mind, we designed a grants framework called Grant Ships. 

Grant Ships strives to make full use of the distributed nature of its natural habitat, Arbitrum DAO. It aims to not only enhance the decentralized, onchain technical capabilities of Arbitrum but also to cultivate a vibrant, dynamic community where groundbreaking ideas are brought to fruition, setting new standards for ecosystem development. 

### Abstract

At its core, Grant Ships is a DAO game where a set number of "Ships" simultaneously operate their own onchain grants programs under a structured, codified ruleset. Over the course of a round, they are free to implement their own strategies and compete to provide the best results. When a round ends, the DAO is presented with each Ship's portfolio and votes in a Token Curated Registry (TCR) on the performance of each Grant Ship. In the following round, each ship receives funds in proportion to the votes they received. 


## Contents

[[toc]]

## Introduction

With DAOs, we usually only get 2 choices for how we distribute funds to contributors. We either make proposals and vote on every grant, or we delegate large portions of the treasury to centralized councils and hope that they are effective and remain honest. 

The benefit of voting for every grant proposal is the transparency that results. Provided that the DAO contract automatically executes transactions following a vote, we can say that the DAO truly gets to decide which grant it wants to fund. However, there are many drawbacks to this design, including governance fatigue, inactivity, and extremely high friction for contributors. 

Centralized councils and workstreams offer a more streamlined alternative. Contributors needn't spend weeks deliberating in forums and voters needn't be concerned with deciding on every grant. However, councils have little incentive to deliver great results or remain accountable to external contributors. Also, there is no incentive for voters to examine the results of a centralized grants program, and even if they were so inclined, the information is usually siloed across a constellation of Telegram chats, spreadsheets, and gated discord chats. 

Moreover, with both these models, we have no way of knowing *who* the talented actors are. We want the highest amount of capital to be stewarded by the best allocators who direct it to the most talented builders. To truly compare the results of one program versus another, we must have a controlled standardized system where programs compete under the same ruleset. 

In other words, we need a game.  

In the following sections, we will outline how Grant Ships leverages modular, onchain protocols to gain the focus and efficiency of centralized grants programs, while still maintaining a high degree of decentralization, voter signal, and most importantly: clear incentives to perform. 

## How It Works 

### Problem Statements and Solutions

This section aims to outline the problems we see with traditional grant programs and how Grant Ships provides solutions to each.

#### Problem: **Undiscovered Potential**
>  We are working in the dark. DAOs have no way of knowing who the best allocators and contributors are.  
   - Monolithic grant programs have no point of comparison to weigh efficacy per token spent. 
   - Voters are only ever presented with the choice of continuing a grant program or killing it. This low-definition signal provides little meaningful or nuanced feedback for program managers. 
   - Without a regular assessment of performance, we aren't determining who is doing a good job.

##### **Solution: *Experimentation and Adaptation***

- The first developed strategy, `GrantShipStrategy.sol`, is based on milestones and direct funding. Direct funding is flexible enough that multiple Ships can try out different strategies to find out what works best. 
- The GameManagerStrategy contract allows us to adapt other Allo strategies into GrantShips for additional experimentation (e.g. quadratic rounds, hackathon formats, etc).
- GameManagerStrategy contract provides an "A/B" test environment where we can more easily compare allocation practices.
- Transparency and feedback from the voting community create an evolutionary factor that should lead to the best allocation strategies thriving and propagating.


#### Problem: **Friction and Uncertainty for Talented Builders**
> Qualified builders often find too much friction and uncertainty to justify the pursuit of a web3 grant.

   - As a builder trying to get funded by a DAO, a lot of time and effort is spent identifying communities with funding opportunities, researching what they need, building reputation, networking, courting delegates, generating proposals, and if they are lucky enough to get feedback on a forum, fending off trolls in the comment section.
   - It's difficult to justify investing this time and effort, especially when outcomes are uncertain. Unless there is a clear path to getting a yes or no answer, most talent won't even enter the scene. 
   - With traditional grant programs, program managers are the central gatekeeper for prospective applicants. Since these programs are essentially monopolies, builders are completely at the mercy of a mostly unaccountable program manager. 
   - With direct DAO votes on grants, grantees are tasked with writing proposals to please the majority of the DAO (at the time of voting) and whoever is currently the loudest in the forum (at the time of discussion). Often this results in bland, omnibus proposals that are designed by committee. For contributors with a vision, this adds considerable friction as this process practically ensures their vision never comes to fruition.  

##### **Solution: *Transparency and Clarity***

- By leveraging Allo Protocol, we can provide a structured, predictable, and transparent step-by-step process. There is never any ambiguity about what to do next. 
- The Grant Ships UI allows candidates to fully understand the opportunities in front of them. They can quickly assess which program suits their talents. 
- Clearly defined roles and simple rules dispel uncertainty by providing transparent insight into the process as a whole.    

##### **Solution: *Competitive, Merit-based Allocations***

- Talented contributors have many programs to apply to. If they are displeased with the performance of one ship, they can apply to another. 
- In the voting round, ship operators are judged by the performance of their portfolio. The ships that seek great contributors will outcompete those who simply wait around for applications. 
- Ships will compete based on contributor experience. The ship that can provide the fastest response times, the best support, and even promotion will ultimately win the best contributors.  
- Because Grant Ships splits the funding between smaller, more focused grants programs, Contributors never have to undergo the lengthy proposal process. 
- Contributions are judged once the round is complete. This allows contributors to build according to their own vision. 
   

#### Problem: **No Way to Win: Opacity vs Transparency** 
> Grant administrators can either invest a lot of time and energy in broadcasting their activities to the community, creating an overhead burden or they can stay more opaque and risk losing trust.

- It's hard for program managers to make everyone happy. They can choose to focus on allocation at the expense of record-keeping to reduce overhead, but this creates opacity that may lead to suspicion and mistrust among stakeholders.
- On the other hand, radical transparency is great for voters, but the program manager spends more time publishing funding decisions, outcomes, communications, timelines, updating records, and tracking transactions that are scattered through many walled gardens, among many organizations.
- Even worse, all this work results in off-chain records that can be easily altered, deleted, or corrupted.

##### **Solution: *Passive Record Keeping***

- Grant Ships solves this problem by using the chain as the central source of truth. Records are automatically generated, and fully transparent to all 
- Record-keeping is a _passive side effect_ of giving grants. Onchain transactions which are linked to immutable offchain data create a mesh of rich, indisputable records that help illustrate any user's intentions and reasoning. 
- In the app, onchain events are aggregated into easy-to-consume feeds that provide full context and insight into grants program operations. 
- Additional content can be posted onchain by any actor within the system by publishing an *UpdatePosted* event.

#### Problem: **Overhead, Waste & Redundancy**
> Repeated actions that are performed among many circles could be delegated to discrete roles.
   - Grant allocators are often overly focused on creating systems for recipient applications and tracking distributions in spreadsheets. They could instead be exclusively focused on scouting for and allocating to great teams and projects.
   - Every grants program has administrative overhead for reporting, KYC/KYB, securing funding, and more. All of this could be delegated to a well-designed governance and contract system and done just once per community. 

##### **Solution: *Meritocratic Funding***
- TCR voting at the end of each round lets an allocator's performance *at allocation* serve as its best bet to secure additional funding. This frees grants programs from the overhead of constantly applying for additional funding when they should be focused on effectively allocating the funds they have. 

##### **Solution: *Role Delegation***
- We integrated Hats Protocol with Allo in GameManagerStrategy and GrantShipStrategy to provide clear role distinctions and appropriate division of responsibility.
- Roles allow us to divide labor among different function calls. We now know, through immutable code, which role is responsible for which steps in the grant-giving process.
- Roles can be revoked and reassigned as needed.

#### Problem: **Voter Fatigue and Context Overhead** 
> Using a yes or no Vote for each Grant has way too much context overhead for the voting community and leads to voter fatigue.

   - It's not practical to expect every voter to gain context and make informed votes on every grant.
   - Grant recipients each have massive overhead to educate the community on why their proposal is worthwhile and also on the outcomes after funding.
   - The high overhead cost inhibits the provision of numerous voter decision points, making more granular decisions impractical.

##### **Solution: *Clear Decisions***

- Grant Ships provides simple decision paths for the voter without the need for extensive study. 
- We replace massive context proposal voting with a series of smaller, targeted contextual votes.
- Many granular decisions are delegated to representatives once, and the community only has to vote on their performance over time. 

##### **Solution: *Structure***

- Rhythmic governance cycles create predictable, palatable demand for voter attention.
- Responsibilities are divided across multiple roles (provided via Hats Protocol) with periodic review and associated voting periods available to provide accountability.
- Hats Protocol roles span multiple contracts, allowing a greater degree of specialization; people can focus on what they're good at without duplicating work, absolving the voting community from making many small decisions.


##### **Solution: *Isolation of Variables***

- The A/B test environment provided by Grant Ships allows clean comparisons to be made between allocation strategies. The voting signal then determines the relative funding levels of these allocators rather than only allowing a binary "yes or no" on each issue.
- All Ships start at the same time. All Ships operate within the same rules and produce comparable, documented results by the game end.
- This provides a cleaner way to compare DAO allocation mechanisms and the efficacy of allocators.

#### Problem: **The Risk of Capture & Incompetence** 
> Choosing to delegate large amounts of capital to Grants Councils does not guarantee that the Grants Council will be effective or trustworthy.
   - Grants councils are entrusted with a lot of power and authority over funding decisions and are often also responsible for reporting on their outcomes. Capture is possible, incompetence is possible, and oversight is difficult.


##### **Solution: *Revokable Privileges***

- Delegation of certain authorities is an effective and necessary pattern within a DAO, but there needs to be a meaningful way to revoke that authority when needed. 
- Grant Ships' integration with Hats Protocol provides revokable privileges, reducing the risk of capture and "loyalty through sunk cost" - see Spencer Graham's ['Anticapture'](https://spengrah.mirror.xyz/f6bZ6cPxJpP-4K_NB7JcjbU0XblJcaf7kVLD75dOYRQ)
- Game Facilitators and Grant Ships can all be suspended or replaced by a DAO vote as needed.

##### **Solution: *Accountability through Transparency***

- Transparent allocation through automated reporting provides an incentive to be effective and trustworthy.
- Broadcasting all meaningful events within the grant-giving process provides signal to the DAO for accountability purposes.


##### **Solution: *Reasonable Safeguards***

- Game Facilitators screen and approve allocator Grant Ships and, once approved, allow Grant Ships to initiate Recipient funding allocations.
  - This can ensure DAO KYC/KYB standards are met for every recipient in a standardized manner, without relying on each allocator to do it right.
- Checks and balances are provided because Game Facilitators approve grant recipient _allocations_, but Grant Ships handle _distributions_ at their discretion.
  - With Allo, allocation and distribution are distinct actions and provide a 'two key' security mechanism.
    - Allocation earmarks the funds for a particular recipient.
    - Distribution disburses them only to that recipient.
- Game Facilitators can apply Yellow or Red Flags to a Grant Ship in instances of rules violation or acts of bad faith.
  - Yellow Flags are like a verbal warning, creating an attestation of the event with context for voter review.
  - Red Flags also create an attestation of the event with context but additionally lock down the ship's ability to distribute funds.
  - Both Yellow and Red Flags remain active on a Ship's profile until *resolved* by a Game Facilitator, but remain in the event feed as context for voters. 

#### Problem: **No budgets** 
> Voting for every issuance of Grant funds, whether to a group of Allocators or an individual project assures that setting a regular budget in DAOs is nearly impossible.
   - Without a governance framework or SubDAO that manages grant funds, only 'emergent' grant budgets are possible. i.e. Let's see what the DAO decides to spend and say that's what the budget was.
   - Bulky grant proposals to the DAO create uncertainty and irregularity in funding rhythms. This makes budgeting difficult or impossible, as the DAO at any time could decide to fund a larger or smaller grants program, and that could change at any time with a newly passed proposal.


##### **Solution: *Rhythm and Cadence***

- The GameManagerStrategy contract can enforce a regular cadence of grant giving - a defined start time and end time for each round - that could be tied to different funding cycles (i.e. monthly, quarterly)
- This creates a system where you could allocate a portion of sequencer fees to grants creating a reliable grants funding stream.

##### **Solution: *Budgets and Funding Faucets***

- Grant Ships functions like a funding faucet that can be filled by the DAO for eventual distribution.
- Once the pool is funded, as many Grant Ships in whatever variety required can be spun up to handle distribution to individual recipients.
  - With full adoption of the Grant Ships system it's reasonable to predict that fewer and fewer Yes or No grant proposals will need to go to Arbitrum DAO. Instead, funding streams could be designated for the Grant Ships funding pool. Grants programs could apply to be a Grant Ship and receive funding from the pool.
  - Grant recipients can then apply to these Grant Ships to receive funds.
  - Voters maintain influence and control through the regular voting and revokable privilege systems.
  - This allows the DAO to create a budget for grants, that can be increased or decreased as needed.


### What is a Grant Ship?

A Grant Ship is an entity with permission to approve grant applicants and make allocations within the Grant Ships game. Ideally, these entities will be a Sub DAO of Arbitrum DAO. During each funding round, ships are allocated funds to be distributed to successful Grant applicants.

Each active Ship can design and implement its own grants system, with the goal of providing grants to people or projects that support the known priorities of Arbitrum DAO.

Ship operators must follow the rules of the game, such as alignment with our [compliance policy](https://rules.grantships.fun/misc/compliance.html) and providing a high level of ethical standards. Other than that, operators are free to run their ships as they please. They may set up their own communications channels and create their own rules that they will follow.

### Participant Roles


Participants within Grant Ships w/Allo are divided into 4 main roles: Game Facilitators, Grant Ship Operators, Grant Recipients, and Delegated Voters. 

For the beta round, the Hat for Delegated Voters will be held by a designated Game Administrator responsible for setting up the game and translating votes into game parameters. 

Future versions will be automated and have the hat held by a DAO contract managed by voters or a delegated security council. 

![Group 45](https://hackmd.io/_uploads/BJsPug-hp.png)

### Role Permissions and Responsibilities

> This section details at a high level each role's permissions and responsibilities. These permissions each correlate to onchain events (i.e. contract function calls).

#### Delegated Arbitrum Voters

* Distributing initial allocation of funds to the game contract
* Periodically voting on ship performance to determine future funding levels
* Revoking and reassigning roles as needed

#### Game Facilitator

* Approving fund allocations (after due diligence, such as KYC and deny list accounting), allowing Grant Ships to distribute at their discretion.
* Activating or Deactivating the Grant Ship funding pools
* Withdrawing funds from deactivated Grant Ship Funding pools
* Flagging Grant Ships that are not operating in good faith, (e.g. Ships that have failed to make allocations, that make repeated attempts to fund bad actors, etc)
* Resolving Grant Ship flags that no longer apply
* Posting updates as needed

#### Grant Ship Operators

* Distributing funds to Grant Recipients
* Capturing Grant Recipient details and including them in the disclosure
* Reviewing Milestones declared by the recipient
* Rejecting invalid Milestones
* Declaring Milestones for recipients (or recipient can do it)
* Posting updates as needed

#### Grant Recipients

* Registering as a potential Grant Recipient for grants
* Declaring Milestones (or Grant Ship operator can do it)
* Submitting milestone completion
* Posting updates as needed


![GrantShips-SwimLanes(2)](https://hackmd.io/_uploads/Hy7XmWEnT.png)

> This diagram shows the major actions available to each role within the game for a single funding round. It does not include the TCR vote that informs funding levels, or the optional updates posted by each role. 


## Executive Summary

### Landscape

We recognize the accomplishments and breakthroughs of existing grant-giving organizations, frameworks, and systems. 

Grant Ships is a "meta-framework" within which grant-giving systems that *are* specific about allocation strategies can operate. Any existing grant-giving model could operate and thrive within the Grant Ships metaframework. Grant Ships itself is silent on specific strategies for grantee selection and allocation and we hope the current rich grant allocation ecosystem sees the opportunity provided by Grant Ships to share and evolve their approaches over time. 

### Grant Game Theory Dynamics

In Grant Ships, we harness the power of competition to enhance performance. At the end of each funding round, Ships receiving high ratings from the voting community receive increased funding, while those with lower ratings receive reduced allocations.

The community also determines overall funding levels divided among ships, creating an incentive for the Ships to perform well as a whole.

This mechanic creates rewards and consequences for the Ships and hopefully leads to an interesting balance of cooperation and competition, motivating Ships to strive for excellence and driving the overall success of the network.

The main goal of Grant Ships is to enhance the effectiveness of grant allocation by encouraging the evolution of high-impact strategies over time. 

We anticipate established game theory dynamics such as the Nash Equilibrium principle to emerge over time, where observing and learning from the success of other programs leads to continuous improvement across all programs. This ensures that no single participant or program can gain an advantage without others also adapting and improving, promoting a competitive and collaborative improvement environment where high standards emerge collectively.

### Reputation and Impact

Grant Ships doesn't directly measure the impact of each ship operator. Instead, it measures votes from the governing community to determine funding levels for each ship. However, it is likely that community voters will factor impact (and many other factors) into their voting decisions.

All grant cycle events that occur within Grant Ships are published as events onchain. These events are aggregated and displayed in a feed within the app to provide always-up-to-date context for voters. 

Grant Ships will have the capacity to integrate with external assessment and reputation protocols to provide relevant context for voters making decisions on a particular Grant Ship.

By providing this performance and reputation data in an open format, we anticipate a community reporting ecosystem emerging around Grant Ships to inform voters on performance trends among Grant Ships and give Ships real-time feedback on their performance.

### Contractual Governance

Grant Ships can be seen as a smart contract-backed Governance OS for a grant-giving sub-DAO. Structure is enforced by the contracts and individuals take up roles within that structure. Where a typical DAO might have rules and operational flows written on paper and enforced through social convention, most of the rules of the Grant Ships game are enforced by code.  We see this pattern as one of the most important aspects of Grant Ships and a step toward delivering on the promise of smart contract-based governance.

Grant Ships is designed to be a progressively decentralized game. While the beta and alpha rounds will maintain some centralization as the game mechanics are being tested, future rounds will have free and fair elections for all positions within the game, including administrators and ship operators. All governance decisions will be handed over to Arbitrum DAO. 

This is made possible through the integration with [Hats Protocol](https://www.hatsprotocol.xyz/) which provides a revokable role and permissions framework. Game Facilitators, Grant Ships, and Delegated Voters are all holders of a Hats Protocol NFT, which is owned by the governing community (e.g. Arbitrum DAO) and can be revoked and reassigned through a vote. 

![GrantShips-SwimLanes(4)](https://hackmd.io/_uploads/SkEON-V26.png)

> This diagram shows the high level relationship between GameManagerStrategy and GrantShipStrategy and the various roles. Major actions taken within the game broadcast events that are compiled into real-time feeds. 

### The Ruleset

We have developed an initial set of rules for how the game is organized and played. As mentioned in the previous section, most of the operational flow is enforced by the backing smart contracts. The rest of the rules will be enforced by game facilitators through their ability to assign yellow or red flags when violations occur. Yellow and red flags are a contract mechanism that allows Game Facilitators to signal violations for voter consideration or revoke a ship's distribution permissions respectively. 

These rules are subject to change as the game is tested and becomes more decentralized. They will ultimately be decided by the governing DAO. This paper gives a brief overview of the rules and what you will find in the current version of the [rule book](https://rules.grantships.fun).


### Compliance

Grant Ships has developed a [compliance policy](https://rules.grantships.fun/misc/compliance.html) which all participants are expected to sign off on and follow. Failure to stay in compliance could result in the immediate revocation of a player's permission to play the game through the red flag mechanism. 

The mechanics of this revocation will be further explained in our technical overview.

### Delegated Voters

Within the regular flow of the game, Delegated Arbitrum Voters vote to elect Grant Ships when the game begins. After each funding round, Voters have an opportunity to vote for their favorite Grant Ships. Funds are then allocated proportional to voting totals in the subsequent round.

Outside of the regular flow of the game, the community may initiate a vote to revoke or reassign roles within the game. For example, if Game Facilitators are abusing power or not acting by their mandate, the DAO can revoke their role and assign new Game Facilitators.

In this way, the Arbitrum DAO community retains control of the Grant Ships program and can hold votes as needed to revoke permissions or withdraw funding from the program. 

### Rules of the Game

The public-facing rulebook for Grant Ships is at  [rules.grantships.fun](https://rules.grantships.fun).

This will be updated with user guides, screenshots, and tutorials as the game develops. 

## Technical Overview

### Key Integrations

####  Hats Protocol

Grant Ships incorporate Hats protocol to represent the roles as hats NFTs, so roles can be assigned to and revoked by the holder of the ‘top hat’ (e.g. a grants council or community DAO contract). This reduces capture risk by allowing the replacement of actors from any role as needed.

#### Allo Protocol 

Grant Ships uses Allo protocol and two custom Allo strategies to:
* Define and enforce the actions available to each role
* Track participants using the Allo registry
* Divide the act of funding into a multi-step process that includes allocation, distribution, and documentation.

Grant Ships has two separate Allo strategy contracts that work together to create the game structure: *GameManagerStrategy* and *GrantShipStrategy*.



### The Grant Ships Contracts

More detailed documentation on the Grant Ships solidity contracts can be found in the [Github repo](https://github.com/DAOmasons/allo-v2/blob/readme-review-notes/contracts/strategies/_poc/grant-ships/Spec.md).

#### GameManagerStrategy.sol (The Metastrategy)

* Holds the common funding pool
* Creates and initializes each Grant Ship sub-pool (which are created by *GrantShipStrategy.sol*)
* `allocate` and `distribute` funds from the common funding pool into sub-pools for each Grant Ship
* Enforces round start and stop times, and allows initiation of new game rounds.

The *GameManagerStrategy.sol* contract serves as the foundation for the Grant Ships game. It allows Game Facilitators to set the initial parameters, review Grant Ship applicants, and initiate the game when Grant Ship Operators have been selected. It has permission to make calls into the GrantShipStrategy and distribute funds.

#### GrantShipStrategy.sol (The Funding Strategy)

* Allows potential grant Recipients to apply
* Allows Recipients or Grant Ship Operators to specify milestones for distributions
* Allows Recipients to signal that a milestone is complete
* Allows Game Facilitators to `allocate` funding to Operator selected Recipients.
* Allows Grant Ship Operators to `distribute` funds for a completed milestone
* Allows Game Facilitators to issue a Yellow or Red Flag to a Grant Ship
* Locks down Grant Ship Operator permissions when a Red Flag is active
* Allows funds to be withdrawn back into the GameManager pool if needed

The GrantShipStrategy contract is also an Allo Strategy with an associated funding pool. Multiple instances are initialized by GameManagerStrategy - one for each Grant Ship. Once the game is started the contract handles applications from potential Grant Recipients and the submission of milestones.

Game Facilitators can make calls into this contract to flag a Grant Ship with Yellow or Red Flags. Yellow Flags are like notes or warnings that go into the public feeds. Red Flags lock down Ship operations until the flag is resolved.

##### Event Broadcasting

Every major action in both GameManagerStrategy and GrantShipStrategy emits an event, creating records that can be aggregated into feeds. In each function where the caller is making a decision, an optional parameter `Metadata _reason` is included to provide additional context. 

The `UpdatePosted` event allows Game Facilitators, Grant Ship Operators, and Grant Recipients to make posts directly to their feeds as needed. 

### Key Contract Features

GrantShipStrategy is a modified version of Allo’s Direct Grants Strategy with changes to integrate with Hats and to allow integration with the GameManagerStrategy meta-strategy.

##### Milestone Management

When a Grantee is selected by a Grant Ship Operator for a grant, the Operator can request Milestones from the Grantee or supply them themselves. Under the hood, distribution is tied to milestones. If an Operator doesn't want to use milestones and prefers to use bulk distribution, the Operator could submit a single milestone for the full grant amount and use that to distribute the funds all at once. 

This Milestone functionality is provided by `GrantShipStrategy.sol`.  

##### Allocation & Distribution (Facilitator Pre-check)

In Allo strategies, funding events are split across 2 functions: `_allocate` and `_distribute`.  Once funds are *allocated* for a particular recipient, they can then be *distributed* to send the funds. 

Ship Operators approve Grantee applications and an update is posted to signal Game Facilitators to *allocate* funds distribution. Game Facilitators call the `_allocate` function, which clears the Grant Ship Operator to call the `_distribute` function to make the actual distribution.

##### Open Application Process

The contracts each include `_registerRecipient` functions that allow anybody to submit an application to these contracts.  `GameManagerStrategy.sol` receives Grant Ship applications which can be approved or rejected. and once a `GrantShipStrategy.sol` instance is spun up for an approved Grant Ship, it receives applications for grants to that Grant Ship. 

##### Event Feeds
Every Recipient, Grant Ship, and Game Facilitator will have a feed of game lifecycle events and UpdatePosted events. Beginning with the Game Start event, every major event within the game (i.e. every contract function call) generates an event. These events are aggregated into a feed within the app. 

Each role can post an UpdatePosted event whenever they like. These events are added to the relevant feeds and are intended to allow actors to provide additional context to voters.

##### Game Start and Game End events

Game Start is triggered by Game Facilitators through the `startGame` function in GameManagerStrategy after initial funds distribution to sub-pools. The Game End event occurs by a call to `stopGame` after a specified amount of time and locks all Grant Ship activity until a new round begins.

##### Ship Flagging and LockDown

Facilitators can flag ships with a yellow or red flag. Flags can be marked as *resolved* by Game Facilitators. 

A yellow flag is like a community note or warning that goes into a Grant Ships event feed for voter review. When a yellow flag is *resolved* this goes into the ship's feed with Game Facilitator notes about the resolution. 

A red flag immediately locks down a Grant Ship preventing them from making further distributions.  When a red flag is *resolved* it unlocks the corresponding ship and adds that context to the ship's feed.


##### Composable Distribution Strategies

GrantShipStrategy.sol is a modified version of Allo's default DirectGrantStrategy based on milestone funding. Due to the composable nature of Allo protocol's strategy pattern, it will be possible to create additional strategies (e.g. quadratic funding, streaming, hackathons, etc) and use them within the Grant Ships game. 


##### Revokable and Reassignable Permissioning

All permissions are administered through the Hats protocol. This means that to have a particular permission within the game, you must hold a particular Hat. Internally, Hats represents the role of an NFT. If this NFT is reassigned, the corresponding permissions are reassigned. 

Hats provides revokable roles to provide capture resistance and lets a DAO or council assign and revoke game roles as needed.

More detailed information on contract specifics can be found in the [contract repo documentation](https://github.com/DAOmasons/allo-v2/blob/readme-review-notes/contracts/strategies/_poc/grant-ships/Spec.md).




## Current Development, MVP and Future Plans
As of February 2024, we are in our first development cycle creating an MVP and planning a beta test. This document provides a holistic view of the whole Grant Ships framework including the vision for a fully decentralized future, and refers to some features that will not be included in the beta release.

These features are: 
- *Integrated Community Voting*: The community voting features that allow delegated voters to signal on Grant Ship efficacy, automatically translating to funding levels in subsequent rounds. 
- *Reputation and Impact Assessment*: Integration with external impact assessment protocols.

Instead of a direct implementation of these features in the MVP, we use the following workarounds:
- *Integrated Community Voting*: We intend to set up a community vote between rounds using Jokerace, Snapshot, or a similar TCR tool and have Game Facilitators manually translate the voting signal into the contract by setting funding levels for ships in subsequent rounds. 
- *Reputation and Impact Assessment:* We include project profiles and a real-time event feed within the app that will provide an easy integration point for external reputation and impact assessment tools. Our event feeds can be consumed by external tools to provide assessment data to users. We provide links to relevant tools within our documentation, especially those consuming our feeds, and encourage their use.

A future version of Grant Ships will include:
- *Integrated Community Voting*: an integrated TCR voting mechanism that is used to determine and allocate funding levels in subsequent rounds. 
- *Reputation and Impact Assessment:* integrations with external assessment protocols to pull relevant reputation and performance context to help voters make informed decisions.



## Appendix 1: Game Theory in Grant Ships

### Overview of Game Theory Application

Game theory, a study of strategic decision-making, plays a critical role in shaping the dynamics of Grant Ships. By leveraging game theory principles, Grant Ships aims to create a competitive yet collaborative environment, driving participants toward optimal performance and contribution. This section explores the key game theories utilized in Grant Ships and how they influence behavior and outcomes within the ecosystem.

### Nash Equilibrium in the Context of Grant Ships

#### Strategic Decision-Making:
- In Grant Ships, each Ship (or player) makes strategic decisions regarding the allocation of grants, the selection of projects, and the adoption of various approaches to maximize their impact within the Arbitrum ecosystem.
- These decisions are based not only on their own goals and objectives but also on an understanding of the strategies and actions of other Ships.

#### Mutual Interdependence:
- The strategic interdependence among Ships is a crucial aspect. Each Ship's decision potentially influences the choices of others. For example, if one Ship adopts a particularly effective grant allocation strategy, others might be inclined to adopt similar strategies, leading to a form of strategic alignment.
- However, the goal is not to have a homogenous set of strategies but rather a diverse yet stable ecosystem where each Ship's approach is respected and valued. The goal is for all ships to perform effectively with the highest degree of impact for Arbitrum.

#### Achieving Nash Equilibrium:
- Nash Equilibrium in Grant Ships is achieved when all Ships, after considering the strategies of others, find that they cannot improve their position by unilaterally changing their strategy to gain an advantage over other Ships.
- This doesn’t mean that all Ships follow the same strategy. Instead, it indicates that each Ship has found a strategy that works best for them within the context of the overall game environment and the actions of other Ships.
- Improved performance at this point would require improvement of the overall performance of the grant-giving collective. 

#### Stability and Dynamism:
- The equilibrium brings a certain level of stability to the ecosystem. Ships are less likely to make frequent, drastic changes to their strategies, leading to a more predictable and reliable grant allocation process.
- However, this stability does not imply stagnation. Ships can still innovate and adapt within their strategic framework, contributing to the dynamism and evolution of the Grant Ships ecosystem.

#### Encouraging Collaboration and Competition:
- By striving for Nash Equilibrium, Grant Ships encourages a balance between collaboration and competition. Ships are motivated to compete by improving their strategies but also to collaborate, as the success of the ecosystem depends on the collective contributions of all participants.

### Why Achieve Nash Equilibrium?

#### For the Arbitrum Ecosystem:

1. **Stability and Predictability:** When Grant Ships reach a Nash Equilibrium, it creates a stable and predictable environment within the Arbitrum ecosystem. This stability attracts more developers and projects, as they can rely on consistent and rational funding patterns.
2. **Optimized Resource Allocation:** Nash Equilibrium leads to more efficient allocation of resources. Ships, understanding each other's strategies, are less likely to waste resources on ineffective or duplicated efforts.
3. **Enhanced Reputation:** A balanced and well-functioning grant system enhances the reputation of the Arbitrum ecosystem, positioning it as a leading platform for innovation and community-driven development.
4. **Impact Incentives:** Players who are playing the game and want to continue to play the game must constantly strive to provide maximum impact.

![nashbar](https://hackmd.io/_uploads/HkFjlTDwT.png)

*In this hypothetical scenario the maximum total impact that can be obtained would be a score of 6. According to Nash's Equilibrium, if both ships were working towards the same goal, that is the score that would be achieved. If one ship was working toward that goal and the other doing something else, the total score that can be achieved is 1. If they are both working towards low-impact grants, the highest score achievable is 2.*

#### For Grant Recipients:

1. **Fair and Transparent Funding:** A Nash Equilibrium scenario ensures that grant allocation is fair, transparent, and based on the merit of the projects, as Ships would have optimized their strategies to support the most impactful projects.
2. **Diverse Funding Opportunities:** With each Ship adopting a strategy that works best within the equilibrium, grant recipients benefit from a diversity of funding avenues and criteria, catering to a wider range of projects and needs.
3. **Consistent Support:** Recipients can expect consistent support and guidelines from the Ships, which helps in better planning and execution of their projects.

#### For an Individual Grant Ship:

1. **Strategic Efficiency:** Achieving Nash Equilibrium allows a Grant Ship to operate with a strategy that is most efficient and effective given the context of other Ships’ strategies. This reduces wasted efforts and increases the impact of their funding.
2. **Competitive Edge:** While the equilibrium ensures stability, it also encourages Ships to innovate within their strategic framework to maintain or enhance their effectiveness, thus fostering a healthy competitive environment.
3. **Community Alignment:** A Grant Ship operating at equilibrium is well-aligned with the community’s needs and expectations, leading to better relationships with project creators and increased trust within the ecosystem.
4.  **Program Success:** The project simply is not a success if only one ship ends up providing impact. In this scenario, the program itself would be in danger of folding. Likewise, if all ships were only providing low-impact grants, while the system would technically be in balance, the program could not be considered a success as the maximum impact is not being achieved.


The achievement of Nash Equilibrium within Grant Ships is beneficial across multiple levels. For the Arbitrum ecosystem, it brings stability and efficiency; for grant recipients, it ensures fairness, diversity, and consistency; and for individual Grant Ships, it results in strategic efficiency, competitive advantage, and stronger community alignment. This equilibrium is not about uniformity but about finding the most effective role each player can have in a complex, dynamic system, leading to collective growth and innovation.

## Appendix 2: Elinor Ostrom's Principles and Grant Ships

Elinor Ostrom's groundbreaking work on managing commons offers eight principles for the effective governance of shared resources. These principles are represented with the decentralized, community-driven nature of Grant Ships:

1.  **Clearly Defined Boundaries:** Grant Ships delineates the roles and responsibilities of participants (Governing Community, Game Facilitators, Grant Ship Operators, and Grant Recipients), ensuring that all actors understand the scope of their involvement and the rules of engagement.
2.  **Congruence with Local Conditions:** By allowing individual Grant Ship Operators to design their grant allocation systems within the meta-framework, Grant Ships ensures that strategies can be tailored to fit the specific needs and conditions of the Arbitrum ecosystem.
3.  **Collective Choice Arrangements:** The decentralized voting mechanism to assess and signal on Grant Ship Operators' efficacy embodies the principle of allowing most resource appropriators to participate in the decision-making process.
4.  **Monitoring:** The integration of external reputation and attestation systems ensures that the actions of Grant Ship Operators are transparent and accountable to the community, aligning with Ostrom's emphasis on monitoring compliance.
5.  **Graduated Sanctions:** The Grant Ships framework includes mechanisms for flagging violations for further review, temporarily locking down permissions, revoking or reassigning permissions based on performance, and funding level decreases in subsequent rounds. This provides a system of sanctions for non-compliance or underperformance that is responsive and adaptable.
6.  **Conflict Resolution Mechanisms:** Game Facilitators and the community voting system act as de-facto arbiters when there is a conflict. A spelled-out conflict resolution practice would be a great addition to the rulebook for an implementing community. 
7.  **Minimal Recognition of Rights to Organize:** The decentralized and autonomous nature of Grant Ships respects the right of the community to organize and govern itself without external authoritative interference. Grant Ships are given free reign to organize how they like internally. 
8.  **Nested Enterprises:** Grant Ships operates as a nested structure within the broader Arbitrum DAO, illustrating Ostrom's principle of multiple layers of nested enterprises managing the commons.

## Appendix 3: Team

- [DAO Masons](https://daomasons.com)
    - [Chris Wylde](https://x.com/boilerrat) (Boilerrat.eth)
        - Project Manager
        - Community Lead
        - Protocol Integrations
        - Marketing
        - Game Theory

    - [Jordan Lesich](https://x.com/JordanLesich) (Jord.eth)
        - Product Manager
        - Lead Engineer
        - Wireframes/Design
        - Game Design

    - [Matt Davis](https://x.com/ui_369) (UI369.eth)
        - Game Co-Ordinator Lead
        - Game Design
        - UX/UI Development
        - Marketing

## Index
### Grant Ships Links

- [Rule Book](https://rules.grantships.fun)
- [Sign Up Form](https://forms.grantsships.fun)
- [Telegram](https://t.me/grantships)
- [Welcome Page](https://grantships.fun)
- [X](https://twitter.com/daomasons)
- [DAO Masons Website](https://daomasons.com)

### Additional Documentation
- Grant Ships was made possible via a builders grant from [Plurality Labs](https://www.pluralitylabs.com/). See the [original grant proposal](https://hackmd.io/@DAOMasons/HkC4Hib-6).
- The [Grant Ships compliance policy](https://rules.grantships.fun/misc/compliance.html) is available as part of the [rulebook](https://rules.grantships.fun/)
- A [Weekly Dev Log](https://forum.arbitrum.foundation/t/grant-ships-weekly-dev-log/20191/1) have been posted on Arbitrum Forums during development.
- [Comparitive Analysis (Draft)](https://hackmd.io/xKL9ALxnRuGXHyBY1emsDA)

### References
- [Grants Framework Design Contest Announcement](https://forum.arbitrum.foundation/t/grants-framework-voting-is-live-for-the-top-100-delegates/14560)
- [Grants Framework Contest Voting Announcement](https://forum.arbitrum.foundation/t/grants-framework-voting-is-live-for-the-top-100-delegates/14560)
- [GovMonth Report](https://www.canva.com/design/DAFxnxARPYQ/-V_4RrRGcHJAphTjROakcw/view?utm_content=DAFxnxARPYQ&utm_campaign=designshare&utm_medium=link&utm_source=editor)

### Integrations Links
- [Allo Protocol](https://allo.gitcoin.co/)
- [Hats Protocol](https://www.hatsprotocol.xyz/)
- [Karma GAP](https://gap.karmahq.xyz/)

### Citations

Nash, John (1950) _Equilibrium points in n-person games: Proceedings of the National Academy of Sciences_ 36(1):48-49.

Ostrom, E. (1990). _Governing the Commons: The evolution of institutions for collective action_. Cambridge University Press.
