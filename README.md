![An Open Guide](figures/signpost-crossroads.webp)

The Open Guide to Datadog
=====================================

> NOTE: This guide is a fork of the awesome [The Open Guide to Amazon Web Services](https://github.com/open-guides/og-aws?tab=readme-ov-file#alb-basics). Formatting, layout, and conduct is either directly used as is or heavily inspired from said guide.

Table of Contents
-----------------

**Purpose**
-	[Why an Open Guide?](#why-an-open-guide)
-	[Scope](#scope)
-	[Legend](#legend)

**Datadog in General**
* [Basics](#basics)
- [Gotchas](#gotchas)

**Datadog Services**
* [Metrics](#metrics)
* [Logs](#logs)
* [Traces](#traces)

Why an Open Guide?
------------------

There's not much documentation that dive deep into Datadog usage beyond the official docs. While these docs are a great starting point, they lack detail when you go off the golden path. 

This guide is by and for engineers who use Datadog. It aims to be a useful, living reference that consolidates links, tips, gotchas, and best practices. 

Before using the guide, please read the [**license**](#license) and [**disclaimer**](#disclaimer).

[Back to top :arrow_up:](#table-of-contents)

### Please help!
**This is an early in-progress draft!** It’s our first attempt at assembling this information, so is far from comprehensive still, and likely to have omissions or errors.

Please help by [**contributing to the guide**](CONTRIBUTING.md). This guide is *open to contributions*, so unlike a blog, it can keep improving. Like any open source effort, we combine efforts but also review to ensure high quality.


Scope
-----

-	Currently, this guide covers selected “core” signals, such as Infrastructure (Metrics), Log Management (logs), and APM (Traces). We expect it to expand.
-	It is not a tutorial, but rather a collection of information you can read and return to. It is for both beginners and the experienced.
-	The goal of this guide is to be:
	-	**Brief:** Keep it dense and use links
	-	**Practical:** Basic facts, concrete details, advice, gotchas, and other “folk knowledge”
	-	**Current:** We can keep updating it, and anyone can contribute improvements
	-	**Thoughtful:** The goal is to be helpful rather than present dry facts. Thoughtful opinion with rationale is welcome. Suggestions, notes, and opinions based on real experience can be extremely valuable. (We believe this is both possible with a guide of this format, unlike in some [other venues](http://meta.stackexchange.com/questions/201994/is-there-a-place-to-ask-opinion-based-questions).)
-	This guide is not sponsored by Datadog. It is written by and for engineers who use Datadog.

Legend
------
-	❗ “Serious” gotcha (used where risks or time or resource costs are significant: critical security risks, mistakes with significant financial cost, or poor architectural choices that are fundamentally difficult to correct)
-	💸 Cost issues, discussion, and gotchas

### Basics
- Datadog is the all in one observability platform that markets itself as the "single plane of glass" solution for observability related use cases. They are the dominant player in the commercial observability market.
- Datadog has [different sites](https://docs.datadoghq.com/getting_started/site/) arounds the world that store and process data locally to a particular region. You choose the site when creating an account. There is no automatic way of transferring data or configuration between datadog sites. 

### Gotchas
- If you want to make use of AWS Private Link (reduce egress fees from AWS to datadog by 90%), know that this is only supported in `us1` and `ap1` site 💸
- Datadog offers FedRAMP Moderate Impact compliance in its `us1-fed` site - onboarding requires a manual account migration if you're already using a different site

**Datadog Services**

Metrics
---

### Infrastructure Basics
- Datadog charges per hose 

### Infrastructure Tips
- Datadog offers rich integrations into many popular services like `nginx` and `kubernetes`. Use them ahead of building your own

### Infrastructure Gotchas
### Infrastructure Cost Optimization
