---
layout: post
title: "The Definition Dilemma"
date: 2026-04-09 00:09:00 -0400
background: '/img/posts/definition-dilemma.jpg'
---

You built a solid retail media platform.

Think something in the league of Amazon Ads or Walmart Connect:

* blazing fast dashboards powered by Druid or ClickHouse
* a warehouse like BigQuery or Snowflake holding the real, messy truth
* APIs neatly serving metrics to UI

Life was good. Numbers showed up fast. Stakeholders nodded confidently.

Then someone said:

> “Can we add AI to generate insights, not just show numbers?”

Of course. How hard could that be?

---

## The Moment Things Start Getting Weird

Your shiny new AI agent gets its first question:

> “What’s driving performance last week?”

Seems straightforward.

Except… your system doesn’t have *one* definition of anything.

Take something as basic as money:

* Ads platform calls it **Spend**
* Finance calls it **Cost**
* Attribution layer might call it **Revenue**

Same campaign. Same timeline. Slightly different logic behind each.

Now the AI has to decide:

> Are these the same thing? Should I combine them? Compare them?

Good luck.

---

## Then Comes the Real Trap

Let’s get into a more “this actually happens” scenario.

You have two datasets:

**deterministic_ad_logs**

* impressions from actual ad delivery events

**synthetic_event_logs**

* impressions reconstructed from modeled journeys
* conversions (only available here)

Now someone asks:

> “Give me CTR and conversion rate.”

To answer correctly:

* CTR → needs **deterministic impressions**
* Conversion rate → needs **modeled conversions ÷ deterministic impressions**

But here’s the catch:

Both tables have a column called **impressions**.

Same name. Different meaning. Equal confidence.

Now imagine an AI agent trying to pick the right one without context.

It’s like giving someone two identical-looking doors and saying,
“One leads to the right answer, the other leads to a slightly wrong answer that looks completely right.”

---

## Why This Breaks in Practice

At this point, your architecture quietly starts sweating.

Because semantics are scattered:

* AI service has a dictionary baked into code
* API layer has its own mappings for UI
* Warehouse has dbt models defining actual logic

None of these are guaranteed to agree tomorrow.

So:

* AI might use modeled impressions
* Dashboard uses deterministic
* Analyst exports something in between

No errors. Just different truths.

---

## And Then You Add AI on Top

Here’s what your AI actually does behind the scenes:

1. First, it tries to understand

   * what “CTR” means
   * which tables to use
   * how metrics are defined

2. Then it runs the query

That’s already two steps.

Now layer in your serving system.

Druid is fantastic at aggregations.
It is… less enthusiastic about joins across datasets.

So what happens?

* Query runs on deterministic logs → impressions
* Another runs on synthetic logs → conversions

And then:

> The final “join” happens in your **application layer**

Not in a database. Not optimized.

But in code that:

* aligns dimensions
* merges aggregates
* hopes time buckets match perfectly

It works most of the time.

And then one day:

* a dimension is missing
* a grouping changes
* a metric silently shifts

Now your AI confidently explains a number that doesn’t quite exist.

---

## “Let’s Just Flatten Everything” (Famous Last Words)

At some point, someone suggests:

> “Why don’t we just create one big table with everything?”

And yes, you do build wide, pre-joined tables for common queries:

* impressions
* conversions
* campaign metadata
* product attributes

These help. A lot.

But they don’t solve everything.

Because:

* New questions keep coming
* Business logic evolves
* AI asks things you didn’t precompute

So now you have two paths:

* Fast path → pre-aggregated tables
* Flexible path → multi-source queries + application joins

And if semantics aren’t consistent across both?

> The same question gives different answers depending on how it was asked.

That’s not a bug. That’s a trust crisis.

---

## “But We Have Governance” Yes, and That’s Not the Issue

Let’s be clear.

You’re not exposing raw sensitive data:

* PII is masked at source
* Access is controlled
* Queries are templated and guarded

The problem isn’t leakage.

The problem is **interpretation within allowed data**.

For example:

* Combining two “safe” datasets that shouldn’t be mixed for that metric
* Using modeled data where only deterministic should be used
* Applying a metric outside its intended context

Everything is technically allowed.

But not everything is **correct**.

Governance answers:

> “Can you access this data?”

Semantics answers:

> “Are you using it the right way?”

Right now, every system answers that second question differently.

---

## So What Do People Actually Try?

Some teams hardcode definitions in services. Fast to build, guaranteed to drift.

Some go heavy on pre-aggregations. Fast queries, painful to evolve.

Some rely on AI to infer everything. Flexible, but unpredictable and slower.

Some juggle all three and hope for the best.

Spoiler: hope is not an architecture.

---

## What Actually Starts Working

The shift is subtle but powerful:

> Stop redefining metrics everywhere. Define them once.

A proper semantic layer does a few unglamorous but critical things:

* Clearly distinguishes

  * deterministic vs modeled impressions
  * spend vs cost vs revenue
* Encodes how metrics are computed
* Knows which system to query for what
* Plans queries instead of letting AI guess

So when the AI gets:

> “Top campaigns by conversion rate”

It doesn’t improvise.

It follows a defined path:

* impressions → correct source
* conversions → correct source
* combine → using known logic

Even if multiple systems are involved, the stitching is:

> intentional, not accidental

---

## The Quiet Wins

Once this is in place:

* AI doesn’t need a “figure it out” query before the real query
* Application-layer joins don’t disappear, but they become standardized
* Pre-aggregations are driven by definitions, not guesswork
* Metrics mean the same thing in UI, API, and AI

And most importantly:

> The same question stops producing multiple believable answers.

---

## The Real Lesson

Adding AI didn’t break your system.

It exposed what was already fragile.

Because dashboards can get away with inconsistency.
AI cannot. It has to explain things.

And the moment it explains:

> Any ambiguity in your data model becomes painfully obvious.

---

## Final Thought

You can build the fastest queries.
You can design elegant pipelines.
You can add the smartest AI.

But if:

* “impressions” can mean two different things
* “spend” depends on who you ask
* and combining datasets requires guesswork

Then your platform isn’t delivering insights.

It’s generating very convincing confusion.

And now, thanks to AI…

It does it in full sentences.
