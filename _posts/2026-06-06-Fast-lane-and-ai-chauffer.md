---
layout: post
title: "The Fast Lane and the AI Chauffeur"
date: 2026-06-06 00:09:00 -0400
background: '/img/posts/ai-drive.png'
---

Everyone is talking about Agentic SDLC.

Every conference talk, company all-hands, startup pitch deck, and LinkedIn post seems to have discovered the same three words:

**AI First. AI Native. Agentic.**

Nobody wants to be the company that admits they are still reading pull requests written by humans.

The race is on.

Not necessarily toward a destination.

Just... on.

## The Great Rush

Businesses want faster growth cycles.

The dream is simple:

* Idea in the morning
* Feature by lunch
* User feedback by evening
* Revenue by tomorrow

And honestly, that part makes sense.

Getting real user feedback quickly is one of the most valuable things a company can do. Nobody wants to spend six months building something nobody asked for.

Engineering, however, has slightly different dreams.

Engineers want systems that are:

* Robust
* Scalable
* Generalizable
* Secure
* Reliable enough to not require constant babysitting

The business wants speed.

Engineering wants sustainability.

The challenge is that both are right.

## The Success Pillars Nobody Likes Talking About

A system is not successful because it shipped quickly.

A system is successful when it continues working six months later.

The boring pillars still matter:

* Verifiability
* Reliability
* Completeness
* Accuracy
* Scalability
* Security

None of these show up in marketing announcements.

Nobody posts:

> "We are thrilled to announce our highly verifiable and reasonably secure architecture."

But those are exactly the things that determine whether the next quarter is productive or spent in incident calls.

## AI Theater is Becoming a Competitive Sport

Right now, there is no universally agreed direction.

What we do have is a lot of companies trying very hard to demonstrate that they are participating.

Every product suddenly has:

* AI summaries
* AI assistants
* AI copilots
* AI agents
* AI workflows
* AI-native experiences

Sometimes all on the same screen.

It feels a bit like the early cloud era where everything became "cloud-powered."

Today everything is becoming "agentic."

The question isn't whether AI belongs in software development.

It absolutely does.

The question is whether we're solving real problems or simply trying to avoid looking old-fashioned.

## The Ownership Problem Nobody Has Solved

Suppose an analyst opens a pull request for a dbt model.

The AI generated a recursive CTE.

The analyst does not fully understand the recursive CTE.

You review it.

It gets merged.

A downstream dashboard breaks.

Who owns it?

The analyst?

The reviewer?

The AI?

The team?

Now imagine your product manager raises a PR changing Spark entrypoint configurations.

Or your manager updates global Spark settings.

Or an agent creates the PR entirely.

Ownership suddenly becomes very fuzzy.

We have spent decades creating clear accountability structures.

Agentic workflows are currently very good at creating unclear accountability structures.

And unclear accountability structures have an impressive ability to create very clear incidents.

## The Permission Paradox

Every AI tool eventually reaches the same question:

**How much permission should it have?**

If it only has read access, people complain it is too limited.

Then we add:

* Ticket creation
* Ticket updates
* Comments
* PR creation

Then somebody says:

"Why not let it run the tests?"

Reasonable.

Then:

"Why not let it update files?"

Also reasonable.

Then:

"Why not let it create entire implementations?"

Still reasonable.

Then suddenly we're discussing whether it should be allowed to modify deployment pipelines.

The slope is not slippery.

It is practically frictionless.

## The Most Realistic Disaster Scenario

Cursor notices a bug from Linear.

It creates a fix.

It opens a PR.

You glance at it.

Looks reasonable.

Then life happens.

An emergency comes up.

You disappear for a few hours.

Meanwhile:

* Manager approves
* PR merges
* Deployment runs
* Pipelines fail
* Alerts fire
* Slack explodes

Technically, the AI didn't deploy anything.

Technically, humans approved everything.

Technically, everyone followed the process.

Yet somehow everyone is still staring at the same burning dashboard.

The problem was never the AI.

The problem was the confidence everyone borrowed from each other.

## The Cost Nobody Mentions

The funny thing about AI coding tools is that they often save time on expensive tasks while spending money on cheap tasks.

I sometimes ask an AI to perform things that historically cost me nothing.

Simple shell commands.

Small file searches.

Basic transformations.

The irony is that before AI, many of those actions were a Google search away.

I searched.

I learned.

I repeated them enough times that they became muscle memory.

Now I ask the assistant.

It works.

But my dependency grows.

One day I realize I can design a distributed system but need assistance writing a grep command with jq.

That is both impressive and slightly concerning.

## The Boring Workflow That Actually Works

Ironically, the most effective AI workflow is often the least exciting one.

Create a feature branch.

Write a detailed prompt.

Something like:

> Create a new class with these public and private methods. Define inputs, outputs, return types, and usage examples.

Or:

> Use this ETL as a template. Implement transformation X. Add two new tests. Update one existing test. Run tests until everything passes.

Then:

* Review the code
* Understand the code
* Commit the code
* Push the code
* Generate the PR description
* Open the PR
* Review AI review comments
* Understand those comments before addressing them

Nothing magical.

Nothing autonomous.

Just faster execution with human control.

Boring is underrated.

## The Sandbox Fantasy

Many discussions eventually arrive at:

"Just put the AI in a sandbox."

That sounds great.

Until reality arrives.

Your source systems are external.

Your destinations are external.

Your repositories are external.

Your ticketing systems are external.

Your deployments are external.

At some point, useful work requires interaction with the real world.

And the real world contains secrets.

API keys.

Credentials.

Access tokens.

Configuration files.

Terminal history.

The AI is not malicious.

It is goal-oriented.

If the objective is "fix the issue," it may explore paths you never intended.

That is why guardrails matter.

Not because the model is evil.

Because the model is eager.

And eager systems require boundaries.

## Build Harnesses, Not Trust

A surprising amount of AI safety in software engineering comes down to old-fashioned engineering.

Build harnesses.

Build guardrails.

Build approval flows.

Build permission boundaries.

Build auditing.

Build visibility.

If you need a transcript to understand what happened after the fact, you already lost some control.

The goal is not preventing AI from helping.

The goal is ensuring help arrives through mechanisms you can reason about.

## Agentic SDLC vs AI Assisted Coding

I suspect there is no universal winner.

For some teams, highly agentic workflows will work beautifully.

For others, explicit instruction and controlled execution will produce better outcomes.

Neither side is wrong.

The real question is:

**Do you want to be the trigger, control, and approval layer?**

Or do you want to delegate first and inspect later?

Both choices are valid.

They simply come with different tradeoffs.

What matters is making that choice consciously.

Not because everyone else is doing it.

Not because every company suddenly added "AI" to its mission statement.

Not because the tooling can do it.

But because you intentionally decided where the human belongs in the loop.

Some thoughts are meant to be difficult.

Not because they have complicated answers.

But because they force us to think harder.

And sometimes that discomfort is the actual gain.

The future probably belongs neither to humans doing everything nor to agents doing everything. It belongs to people who know exactly when to hand over the wheel and when to keep both hands firmly on it.

After all, just because there's an AI chauffeur doesn't mean you should fall asleep in **the fast lane**.

Everyone is talking about Agentic SDLC.

Every conference talk, company all-hands, startup pitch deck, and LinkedIn post seems to have discovered the same three words:

**AI First. AI Native. Agentic.**

Nobody wants to be the company that admits they are still reading pull requests written by humans.

The race is on.

Not necessarily toward a destination.

Just... on.

## The Great Rush

Businesses want faster growth cycles.

The dream is simple:

* Idea in the morning
* Feature by lunch
* User feedback by evening
* Revenue by tomorrow

And honestly, that part makes sense.

Getting real user feedback quickly is one of the most valuable things a company can do. Nobody wants to spend six months building something nobody asked for.

Engineering, however, has slightly different dreams.

Engineers want systems that are:

* Robust
* Scalable
* Generalizable
* Secure
* Reliable enough to not require constant babysitting

The business wants speed.

Engineering wants sustainability.

The challenge is that both are right.

## The Success Pillars Nobody Likes Talking About

A system is not successful because it shipped quickly.

A system is successful when it continues working six months later.

The boring pillars still matter:

* Verifiability
* Reliability
* Completeness
* Accuracy
* Scalability
* Security

None of these show up in marketing announcements.

Nobody posts:

> "We are thrilled to announce our highly verifiable and reasonably secure architecture."

But those are exactly the things that determine whether the next quarter is productive or spent in incident calls.

## AI Theater is Becoming a Competitive Sport

Right now, there is no universally agreed direction.

What we do have is a lot of companies trying very hard to demonstrate that they are participating.

Every product suddenly has:

* AI summaries
* AI assistants
* AI copilots
* AI agents
* AI workflows
* AI-native experiences

Sometimes all on the same screen.

It feels a bit like the early cloud era where everything became "cloud-powered."

Today everything is becoming "agentic."

The question isn't whether AI belongs in software development.

It absolutely does.

The question is whether we're solving real problems or simply trying to avoid looking old-fashioned.

## The Ownership Problem Nobody Has Solved

Suppose an analyst opens a pull request for a dbt model.

The AI generated a recursive CTE.

The analyst does not fully understand the recursive CTE.

You review it.

It gets merged.

A downstream dashboard breaks.

Who owns it?

The analyst?

The reviewer?

The AI?

The team?

Now imagine your product manager raises a PR changing Spark entrypoint configurations.

Or your manager updates global Spark settings.

Or an agent creates the PR entirely.

Ownership suddenly becomes very fuzzy.

We have spent decades creating clear accountability structures.

Agentic workflows are currently very good at creating unclear accountability structures.

And unclear accountability structures have an impressive ability to create very clear incidents.

## The Permission Paradox

Every AI tool eventually reaches the same question:

**How much permission should it have?**

If it only has read access, people complain it is too limited.

Then we add:

* Ticket creation
* Ticket updates
* Comments
* PR creation

Then somebody says:

"Why not let it run the tests?"

Reasonable.

Then:

"Why not let it update files?"

Also reasonable.

Then:

"Why not let it create entire implementations?"

Still reasonable.

Then suddenly we're discussing whether it should be allowed to modify deployment pipelines.

The slope is not slippery.

It is practically frictionless.

## The Most Realistic Disaster Scenario

Cursor notices a bug from Linear.

It creates a fix.

It opens a PR.

You glance at it.

Looks reasonable.

Then life happens.

An emergency comes up.

You disappear for a few hours.

Meanwhile:

* Manager approves
* PR merges
* Deployment runs
* Pipelines fail
* Alerts fire
* Slack explodes

Technically, the AI didn't deploy anything.

Technically, humans approved everything.

Technically, everyone followed the process.

Yet somehow everyone is still staring at the same burning dashboard.

The problem was never the AI.

The problem was the confidence everyone borrowed from each other.

## The Cost Nobody Mentions

The funny thing about AI coding tools is that they often save time on expensive tasks while spending money on cheap tasks.

I sometimes ask an AI to perform things that historically cost me nothing.

Simple shell commands.

Small file searches.

Basic transformations.

The irony is that before AI, many of those actions were a Google search away.

I searched.

I learned.

I repeated them enough times that they became muscle memory.

Now I ask the assistant.

It works.

But my dependency grows.

One day I realize I can design a distributed system but need assistance writing a grep command with jq.

That is both impressive and slightly concerning.

## The Boring Workflow That Actually Works

Ironically, the most effective AI workflow is often the least exciting one.

Create a feature branch.

Write a detailed prompt.

Something like:

> Create a new class with these public and private methods. Define inputs, outputs, return types, and usage examples.

Or:

> Use this ETL as a template. Implement transformation X. Add two new tests. Update one existing test. Run tests until everything passes.

Then:

* Review the code
* Understand the code
* Commit the code
* Push the code
* Generate the PR description
* Open the PR
* Review AI review comments
* Understand those comments before addressing them

Nothing magical.

Nothing autonomous.

Just faster execution with human control.

Boring is underrated.

## The Sandbox Fantasy

Many discussions eventually arrive at:

"Just put the AI in a sandbox."

That sounds great.

Until reality arrives.

Your source systems are external.

Your destinations are external.

Your repositories are external.

Your ticketing systems are external.

Your deployments are external.

At some point, useful work requires interaction with the real world.

And the real world contains secrets.

API keys.

Credentials.

Access tokens.

Configuration files.

Terminal history.

The AI is not malicious.

It is goal-oriented.

If the objective is "fix the issue," it may explore paths you never intended.

That is why guardrails matter.

Not because the model is evil.

Because the model is eager.

And eager systems require boundaries.

## Build Harnesses, Not Trust

A surprising amount of AI safety in software engineering comes down to old-fashioned engineering.

Build harnesses.

Build guardrails.

Build approval flows.

Build permission boundaries.

Build auditing.

Build visibility.

If you need a transcript to understand what happened after the fact, you already lost some control.

The goal is not preventing AI from helping.

The goal is ensuring help arrives through mechanisms you can reason about.

## Agentic SDLC vs AI Assisted Coding

I suspect there is no universal winner.

For some teams, highly agentic workflows will work beautifully.

For others, explicit instruction and controlled execution will produce better outcomes.

Neither side is wrong.

The real question is:

**Do you want to be the trigger, control, and approval layer?**

Or do you want to delegate first and inspect later?

Both choices are valid.

They simply come with different tradeoffs.

What matters is making that choice consciously.

Not because everyone else is doing it.

Not because every company suddenly added "AI" to its mission statement.

Not because the tooling can do it.

But because you intentionally decided where the human belongs in the loop.

Some thoughts are meant to be difficult.

Not because they have complicated answers.

But because they force us to think harder.

And sometimes that discomfort is the actual gain.

The future probably belongs neither to humans doing everything nor to agents doing everything. It belongs to people who know exactly when to hand over the wheel and when to keep both hands firmly on it.

After all, just because there's an AI chauffeur doesn't mean you should fall asleep in **the fast lane**.
