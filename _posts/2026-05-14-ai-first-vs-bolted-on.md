---
layout: post
title: "Born AI-First vs. Bolted-On Later: Which Codebase Actually Wins?"
date: 2026-05-14 00:09:00 -0400
background: '/img/posts/ai-first-vs-bolted.jpg'
---

> *The real cost of teaching old dogs new prompts — and why greenfield AI projects aren't the magic bullet you think they are.*

**Tags:** AI-Native · Legacy Modernization · Agentic SDLC · Retail Tech · Adtech  
**Read time:** 15 min · Opinion & Engineering

---

## Two systems walk into a sprint

Somewhere, an engineering team is at a whiteboard arguing about how to "integrate AI properly" into a ten-year-old monolith. Across town, another team just spun up a brand-new repo where the git history has more agent commits than human ones. Both think they're winning. One of them is lying to themselves. Possibly both.

The software world has quietly split into two camps. Camp One: greenfield projects built from day zero with AI agents doing the heavy lifting — writing code, running tests, opening PRs, closing issues, updating docs. Camp Two: the legacy systems that keep the lights on, the revenue flowing, and the SLAs met — now being asked to absorb AI workflows like a tired commuter being handed a jetpack.

These aren't just different architectures. They're different philosophies. Different cultures. And increasingly, different species of organization.

---

## Everyone has the files. Nobody agrees on what's in them.

Let's kill one myth immediately: the context problem, for what it's worth, is mostly solved. Knowledge graphs got smarter. Retrieval got cheaper. Every team has an `agent.md` now. Skills are defined somewhere. Rules live in markdown files, hierarchical context folders, prompt libraries. Someone gave a talk about it at an internal conference six months ago and got a lot of nodding heads.

But here is the thing nobody says out loud: having all the context in the world doesn't help if the agent can't tell what matters versus what's noise. A knowledge graph that contains everything is just an expensive way to be confused at scale.

A mid-size fashion retailer's recommendation engine has context files covering 600 product attributes, 14 discount rule sets, three loyalty tier schemas, and a section labeled "holiday overrides (ask someone)." When a new agent task arrives to optimize the product carousel for mobile, it faithfully reads all 600 attributes. Then it optimizes for the wrong metric — because the context says "engagement" and nobody updated it when the business switched to margin-focused ranking eight months ago. The agent was not wrong. The context was just stale and nobody noticed.

This is the new version of technical debt: **context debt**. And it compounds the same way. Nobody wants to audit 40 markdown files to figure out which rules still apply. So they don't. The agent works from a world model that is 70% accurate, which is great for a trivia night but genuinely dangerous for a pricing engine.

---

## The PR graveyard

Here is a dynamic playing out at legacy engineering teams right now that nobody puts in the case study.

An agent can generate 8 meaningful PRs in the time it takes a senior engineer to deeply review one. The backlog is not a scheduling problem. It's a structural one. The humans become the bottleneck — not because they're slow, but because they physically cannot hold the full context of a large AI-generated change in their heads while also doing everything else their job requires.

So they skim. They miss things. They approve. Six weeks later, something in production behaves in a way nobody expected. The agent didn't introduce a bug on purpose. The reviewer just didn't catch it because they were on their fourteenth PR review of the day and the description said "refactors checkout flow for performance" and the tests passed and honestly it looked fine.

> *Here lies the edge case. It was known to no one. It rose only to write the epitaph of a dying business.*

The fix is not more reviewers. It's automated eval layers that catch what humans are too tired to catch — so humans can save their judgment for the decisions that actually need it.

---

## The productivity paradox: more tools, somehow less shipped

This one hurts to say, but it needs saying. The promise of AI tooling was velocity. Instead, many teams are spending their velocity evaluating velocity tools.

Every new framework that drops means engineers form opinions on it, someone writes a spike, a meeting gets scheduled, and six weeks later the decision is "let's wait for it to mature." Meanwhile, the greenfield startup that launched five months ago already has it in production and has moved on to the next thing.

In adtech, this is spectacular to watch. A team rebuilding their bidding engine using AI assistance now has to manage: the agent's understanding of their auction mechanics, real-time signal freshness, privacy regulation constraints that change by jurisdiction, and brand safety rules that are different for every major client. Each of those is a context file. Each context file was last updated by someone who has since moved teams. The agent reads all of it and produces code that is technically correct and operationally risky.

And then there's **vibe coding**. It starts innocently. "Refactor this function" becomes "improve the whole service" becomes "here's the ticket, do your thing." The human's prompt gets vaguer over time — partly from trust, partly from fatigue, partly because reading a 400-line diff at 4pm on a Friday is genuinely hard. The agent delivers. The human approves. Nobody quite knows what got shipped, but the tests pass and the demo looks great.

Vibe coding is not a workflow. It's a symptom. It shows up when humans get fatigued doing reviews at a scale their brains weren't designed for, when context retention across many large changes breaks down, and when the gap between "the agent worked fast" and "we understood what it built" gets quietly accepted as normal.

---

## The abstraction trap: what agents bury

Here is the part people don't like to hear. When you delegate the low-level details to an agent, the low-level problems go along for the ride.

Edge cases don't disappear. They go underground. The agent builds the happy path beautifully. Then a user does something slightly weird. Then slightly weirder. And you discover that the thing you shipped has a hole in it that only shows up at 1am when someone from a timezone your product manager didn't consider tries to process a refund on a leap day.

In adtech: a greenfield DSP launched with an agent-native bidding pipeline. Clean, fast, impressive CTRs in the demo. Three months after launch, a campaign started winning auctions for inventory that was on a brand safety exclusion list — defined in a context file, but never connected to the bidding guardrails. The two contexts existed. The relationship between them did not. The advertiser found out when their brand appeared next to content they had explicitly excluded.

In retail: an agent-built promotion engine handled standard discount stacking beautifully. It had never been told what to do when a loyalty reward, a referral credit, a clearance discount, and a birthday coupon all applied to the same item simultaneously. Not because nobody thought about it — because at the speed the system was built, nobody had the time to think through every combination. At normal human dev pace, that scenario would have come up in a review. At agent pace, it shipped.

KISS — Keep It Simple, Stupid — doesn't automatically happen because an AI wrote the code. AI systems make things complicated fast. They generate working solutions at speed, but "working under these test conditions" and "deterministic under all real conditions" are very different bars. Mission-critical systems don't get to miss edge cases. The edge case is always there. You find it either by spending time on it upfront, or by your users finding it for you, loudly.

---

## The greenfield advantage (and its dirty secret)

The new incumbents have one structural advantage that no amount of `agent.md` writing can replicate: they designed for agents from the start. Their acceptance criteria are machine-readable. Their folder structures, validation schemas, and task scopes were tuned for an AI to parse and execute — not for a human to hold in their head during a standup. There was no meeting about "how do we add AI to our checkout flow." The checkout flow was the AI.

A new retail personalization startup built their entire merchandising engine this way. Every feature ticket ships with three required fields: agent context, testable acceptance criteria ("increase click-through rate on mobile by 8% without degrading average order value, measured over a 14-day window"), and explicit guardrails ("never surface out-of-stock items, never rank by margin when the user's last three purchases were under $20"). Their CI pipeline runs eval suites that score the agent's output before anything touches staging. A team of twelve competing with a department of eighty.

But the dirty secret: their codebase is eight months old. It has never survived a Black Friday. It has never had a GDPR audit. It has never processed a refund from a user who bought something in one currency, returned it in another, and opened a dispute with their bank three weeks later during a promotional window that no longer exists. The edge cases are coming. They always come.

> *The greenfield team is fast. But fast without edge case modeling is just a way to fail quickly at scale.*

---

## Greenfield vs. legacy: no spin, no winners yet

| | AI-native greenfield | Legacy + AI integration |
|---|---|---|
| **What works** | Agents are first-class contributors from day one | Battle-tested business logic that has survived real users |
| | SDLC designed around machine-readable specs | Known edge cases already handled (in blood and Slack messages) |
| | No context debt inherited from past decisions | Deep domain expertise in the team |
| | Evals baked in, not retrofitted | Lower risk if changes are surgical and scoped |
| **What doesn't** | Edge cases abstracted away at agent speed | Context files exist but signal-to-noise is broken |
| | Requires clear product vision before the first prompt | PR review is a human bottleneck at scale |
| | Context relationships between rules not yet defined | Tool evaluation fatigue slows teams that should be shipping |
| | No earned wisdom from failure | Vibe coding creeps in as review fatigue sets in |

---

## So is anyone winning?

Yes. But not who you'd expect.

The teams winning aren't the ones who went fully autonomous, or the ones who resisted agents entirely. They're the ones who got boring about it. They defined their boundaries before writing their first prompt. They wrote acceptance criteria that were specific enough to be testable before asking an agent to build anything. They kept humans in the loop for decisions that matter — not as PR gatekeepers rubber-stamping diffs they can't fully process, but as product thinkers who set the objective and trust a well-scoped, well-evaluated agent to execute.

Context hierarchy is not enough. You need context with priority signals. You need rules that reference each other. In retail: is the system optimizing for conversion, margin, inventory clearance, or brand positioning? All four probably live in context files somewhere. None of them say which one wins when they conflict. The agent guesses. Often wrong in ways that look right until they don't.

In adtech: the agent knows the campaign goal, the budget pacing rules, the frequency caps, the audience segments, and the creative performance data. What it doesn't know is that the client verbally told the account team to slow spend down because of an upcoming earnings announcement. That lives in a Slack DM. This class of knowledge cannot be in any file unless someone builds a deliberate process to capture and structure it.

The teams winning are building that process. The teams losing are still deciding which AI tool to evaluate next.

---

## How to actually make this work

### For legacy teams competing with greenfield newcomers

1. **Stop evaluating every tool that drops.** Pick a quarterly review cadence. New tool releases are not emergencies. The FOMO is real; the urgency is manufactured.

2. **Stop treating context files as write-once artifacts.** Assign ownership. Require a "last validated" date. Stale context is not neutral — it's actively misleading, and the agent will trust it anyway.

3. **Stop letting humans be the only quality gate on AI-generated code.** Build eval pipelines. Not as a project with an end date — as a product with an owner. Humans should review what the evals can't catch, not everything.

4. **Stop writing vague specs.** "Improve the recommendation carousel" is not acceptance criteria. "Increase click-through rate on mobile by 8% without degrading average order value, measured over 14 days, not applicable to clearance items" is acceptance criteria.

5. **Add priority signals to existing context, don't just add more context.** Which rule wins when rules conflict? Answer that before the agent has to guess. The answer should be in the file, not implied.

6. **Run a quarterly chaos scenario.** Pick three realistic but ugly user behaviors. Trace what the system does with them. Write down what it should do instead. Update the guardrails.

### For greenfield teams who think they've figured it out

1. **Write your product vision, user flows, and failure scenarios before the first prompt.** Agents need intent, not just instructions. "Build a recommendation engine" is not intent. "Surface products that increase basket size without increasing return rate for users who have bought from us before" is intent.

2. **Model edge cases before users find them.** In retail: what happens when a loyalty reward, referral credit, clearance discount, and birthday coupon all stack on the same item? In adtech: what happens when two active campaigns have conflicting brand safety exclusion lists competing for the same inventory?

3. **Define context relationships, not just context.** Rules that can conflict need a tiebreaker baked in, not assumed.

4. **Keep one human close to the "why" layer at all times.** Agents own the "how." If nobody on the team can explain why a feature exists in plain language, the agent is executing without a conscience.

5. **Challenge complex solutions.** If what the agent built is hard to reason about, the problem was probably under-specified. Don't ship the complexity. Rewrite the spec.

---

## Is refactoring futile? Should you just start over?

Mostly no. Rarely yes.

The businesses that have built real revenue, real users, and real trust should not blow that up chasing an architectural fantasy. The greenfield startup does not have your hard-won knowledge of how your users actually behave at 11pm on a Sunday when the promo code doesn't work and they've already entered their card details.

What is futile is continuing to add AI tools to a legacy system without making the underlying context legible and prioritized. A knowledge graph that knows everything but ranks nothing is a beautiful, expensive mess. A rules file that lists every constraint but says nothing about which one takes precedence when they conflict is a liability dressed as documentation.

The real question is not "greenfield or legacy?" The question is: can you define what success looks like before you write the prompt? Can you write acceptance criteria specific enough that an agent could fail them? Can you name the top three edge cases your system would encounter at 10x the current load?

If yes: great. Add the agent. Give it tight scope. Measure the output.

If no: fix that first. No agent makes a vague requirement precise. It just executes the vagueness faster.

---

## The honest verdict

Nobody is fully winning yet. The greenfield teams are shipping fast and will hit their edge-case wall soon. The legacy teams have the knowledge and are drowning in the process of making it useful to agents.

The teams losing the least are the ones who realized early that "adding AI" was never the task. The task was always the same: build something predictable, that solves a real problem, that doesn't surprise your users in ways they didn't agree to.

AI does not change that objective. It just changes how fast you can fail to meet it.

And occasionally, if you do the boring work first — the context audits, the eval pipelines, the precise acceptance criteria, the edge case modeling — how fast you can get it gloriously, verifiably right.

---

*Ship It (or Ship Out) — engineering opinions, served hot. May 2026.*
