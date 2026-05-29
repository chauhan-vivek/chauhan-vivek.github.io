---
layout: post
title: "AI Literacy or AI Theatre?"
date: 2026-05-29 00:09:00 -0400
background: '/img/posts/ai-literacy.jpg'
---

Somewhere in a meeting room right now, a dashboard probably exists that says:

- AI lines accepted: 18,420
- AI suggestions used: 63%
- Claude usage: high
- ChatGPT usage: medium
- Cursor activity: suspiciously enthusiastic

And somewhere beside that dashboard, a leadership team is nodding seriously while discussing "organizational AI maturity."

I know because I have helped build this exact thing.

Not theoretically. Properly.

Pull usage data from Cursor, Claude, Claude Code, Codex, ChatGPT, Granola, Atlassian Rovo. Join it with employee metadata. Standardize schemas across seven different APIs. Push it into a warehouse. Build three tiers of dashboards, one for employees, one for managers, one for executives.

A beautiful little observability platform for AI adoption.

The intent sounds genuinely noble. Find who is struggling. See which teams are comfortable. Measure literacy. Start conversations. Become an AI-first company.

On paper, incredibly reasonable.

Then you keep thinking about it.

And slowly the whole thing starts feeling like counting keyboard clicks to measure engineering quality.

---

## The Metrics Start Lying Very Quickly

The problem with AI usage metrics is they look meaningful from far away.

Get closer and they get weird.

Here is a simple example. I can intentionally use AI less and be more effective.

Ask AI once to generate a reusable script, save it, call it forever.

Meanwhile someone else asks:

> "Can you sort this file?"

> "Can you fix this JSON?"

> "Can you rename these columns?"

Who looks more AI-literate on the dashboard? The second person. By a lot.

The first person quietly automated themselves out of needing repeated prompts. The dashboard reads this as low adoption. The metric punishes the thing it was supposed to encourage.

---

## Token Consumption Is Not Innovation

A lot of AI usage today looks like organizational snacking.

Tiny prompt after tiny prompt.

Write a shell command. Explain a git diff. Summarize a Slack thread. Rewrite a comment. Rewrite the rewritten comment. Simplify the simplification.

At some point you are not accelerating work anymore. You are running expensive autocomplete in a loop.

The pattern that really gets me is the agent review cycle. An agent reviews code. Another prompt simplifies the review. A new direction emerges. Everything gets regenerated. Half the previous output becomes throwaway work.

Tokens are flowing. Dashboards are glowing. But zoom out and a lot of energy just produced disposable iterations.

The dashboard cannot see any of that. It just sees activity and calls it progress.

---

## The Quiet Skill Nobody Tracks

Nobody measures this because it is less flashy.

Good AI use often means using AI less over time.

Someone who really knows what they are doing writes a detailed system prompt once, structures their context with clear role, constraints, and output format before the first message, and gets what they need in two turns. Someone still learning fires off eight casual follow-ups trying to nudge the output into shape, gets frustrated, and starts over.

The first person finishes in ten minutes. The second person spent forty minutes and has a messy context window that is quietly degrading the quality of every subsequent response in the session.

Or take tool use. A sharp user spots that they are solving the same class of problem repeatedly, writes a script once, and calls it from the terminal forever. Done. Another user opens a chat window every single time, describes the problem fresh, waits for output, copies it out, and repeats this tomorrow. Same task. Forty tokens vs four thousand.

The experienced user also knows when to stop. A bloated 40-message session where the original goal has drifted three times is not deep work. It is compounding confusion. Recognizing that moment, compacting the context or restarting clean, is a real skill. It just looks like low activity on a dashboard.

Beginners generate lots of prompts because they are exploring. That is fine. But advanced users start compressing. They front-load structure, manage context deliberately, and build reusable tools instead of regenerating the same output in a sandbox every time.

The dashboard sees both of them and has no idea which is which. It just sees one person with higher numbers and calls that literacy.

---

## When "AI First" Quietly Becomes "AI Always"

This is the part that feels slightly uncomfortable to say out loud.

The intention behind AI-first is good. Build faster. Think bigger. Remove friction. Give people leverage.

But somewhere in execution, "AI first" can drift into "use AI everywhere possible." Even where it does not make sense.

A grep command becomes a chatbot interaction. A reusable script becomes a repeated generation task. A simple decision becomes a prompt, a response, a follow-up, a refinement, and somehow forty minutes of conversation that could have been a sticky note.

And company conversations about AI keep collapsing into one question: how much productivity did we gain? Not "did we build better systems" or "did we reduce technical debt" or even "did customers notice." Just "did token usage go up."

To be fair, productivity gains are real and worth measuring. AI does genuinely compress work that used to take days. That matters.

But when the measurement becomes the goal, you get measurement-shaped behavior. More prompts. Noisier workflows. Lightweight tasks becoming AI-assisted tasks not because it helps but because engagement is being tracked. People are not being malicious. They are just optimizing for what gets measured. If commits were counted by line length, engineers would write longer code.

---

## What Would Actually Help

Financial guardrails make total sense. Without spend limits, AI costs can leak quietly at scale. Set quotas. Monitor token burn. Build sensible access policies. That is just responsible infrastructure.

The harder question is whether individual usage metrics can tell you anything meaningful beyond that.

The most effective person on the team might have the lowest usage count. The strongest thinker might need the fewest prompts. And the person with 40,000 lines generated through agents might be sitting on 39,000 lines of future cleanup work.

None of that shows up in the dashboard.

If the actual goal is AI literacy, the conversations worth having are harder to automate. Why did this take ten prompts when it could have been two? What does good context structure actually look like? When does it make more sense to write the tool once and call it forever? These are judgment calls, not numbers.

---

## The Conversation Nobody Is Having

Here is the thing that bothers me more than the dashboards.

All the internal AI conversation is about productivity. Faster code. Shorter meetings. Better PRDs. Quicker emails.

Almost none of it is about using LLMs to actually improve the models we build.

Feature engineering with LLMs. Synthetic data generation for underrepresented classes. Using fast language models to clean and label messy training data at scale. Embedding-based retrieval to augment classical pipelines. Anomaly detection where the "anomaly" is semantically weird, not just statistically weird.

These are genuinely interesting problems. They are also where the leverage could be enormous.

But those conversations keep getting crowded out by "how do we get the team to use Copilot more."

Why? A few honest guesses.

One is that the ROI is murkier. Productivity gains are fast and visible. A developer ships a feature in two days instead of five. Done, measurable, easy to present upward. Improving a model's precision by four points through better training data is real, but it takes months, requires a proper experiment, and the story is harder to tell in a slide.

Another is that classical models still do a lot of jobs just fine. A well-tuned gradient boosted tree on good features beats a bloated LLM pipeline on bad ones, is cheaper to run, faster to explain, and easier to debug. LLMs are genuinely not the right tool for every data science problem. The hype does not always survive contact with a confusion matrix.

And honestly, some of it is capability. Using LLMs well inside a data science workflow requires knowing both worlds. Most conversations happen in one world or the other.

The result is that "AI first" ends up meaning: AI for the people writing the product, not AI improving the product itself.

Which is useful. But it is probably not what anyone meant when they said it.

---

## The Better Question

Instead of asking "how much AI are employees using," maybe ask "are people solving meaningful problems better?"

Because AI was supposed to help us think bigger.

Not create enterprise dashboards ranking who opened the chatbot most often.

The irony is not lost on me that building that observability platform would itself have been a classic case of using AI-adjacent tooling to produce something that looked useful without being particularly useful.

At least it would have had great charts.