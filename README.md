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
- [Basics](#basics)
- [Gotchas](#gotchas)

**Datadog Services**
- [Metrics](#metrics)
- [Logs](#logs)
- [Traces](#traces)

**Special Topics**
-	[Billing and Cost Management](#billing-and-cost-management)

Why an Open Guide?
------------------

There's not much documentation that dive deep into Datadog usage beyond the official docs. While these docs are a great starting point, they lack detail when you go off the golden path. 

This guide is by and for engineers who use Datadog. It aims to be a useful, living reference that consolidates links, tips, gotchas, and best practices. 

Before using the guide, please read the [**license**](#license) and [**disclaimer**](#disclaimer).


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
-	💸 Cost issues, discussion, and gotchas
-	❗ “Serious” gotcha (used where risks or time or resource costs are significant: critical security risks, mistakes with significant financial cost, or poor architectural choices that are fundamentally difficult to correct)

### Basics
- Datadog is the all in one observability platform that markets itself as the "single plane of glass" solution for observability related use cases. They are the dominant player in the commercial observability market.
- Datadog has [different sites](https://docs.datadoghq.com/getting_started/site/) around the world that store and process data locally to a particular region. You choose the site when creating an account. There is no automatic way of transferring data or configuration between datadog sites. 

## Tips
- If you care about vendor lock in, its a good idea to use the [OpenTelemetry libraries](https://docs.datadoghq.com/opentelemetry/) to instrument your applications. This makes it possible to migrate vendors in the future or use multiple vendors at the same time

### Gotchas
- Datadog offers FedRAMP Moderate Impact compliance in its `us1-fed` site - onboarding requires a manual account migration if you're already using a different site
- While datadog offers support for the OpenTelemetry collector, adopting it means you forego one of Datadog's strongest qualities - seamless integration with existing services. These integrations exist for the datadog agent but is not available if you use the open telemetry collector

**Datadog Services**

Metrics
---

### Metric Basics
- metrics is provided by Datadog's [Infrastructure](https://docs.datadoghq.com/infrastructure/) and [Metrics](https://docs.datadoghq.com/metrics/) offering

### Metric Tips
- Datadog offers rich integrations into many popular services like `nginx` and `kubernetes` which can automatically collect the right metrics and populate pre-built dashboards

### Metric Gotchas
- if you're using Datadog's integration to automatically collect metrics from your cloud provider, know that those metrics are [subject to delays](https://docs.datadoghq.com/integrations/guide/cloud-metric-delay/) of anywhere between 2min to 20min. Datadog provides provider specific (eg. [metric streams for AWS](https://docs.datadoghq.com/integrations/guide/aws-cloudwatch-metric-streams-with-kinesis-data-firehose/)) which can cut the delay but incur additional costs
- because Datadog charges per host, it can make certain workloads that involve short lived host (eg. running kubernetes or utilizing spot instances) prohibitively expensive  💸 

Logs
---

### Logs Basics
- logs are provided by Datadog's [Log Management](https://docs.datadoghq.com/logs/) offering

### Logs Tips
- Datadog charges predominantly based on indexed log events. If you have logs that you're not using, use the [exclusion filters](https://docs.datadoghq.com/logs/log_configuration/indexes#exclusion-filters) to avoid paying for indexing 💸 

### Logs Gotchas
- If you use services like [Cloud SIEM](https://www.datadoghq.com/pricing/?product=cloud-siem#products) that price based on per million logs scanned - note that excluding logs using an exclusion filter does not exclude it from scanning or the associated cost that come with that 💸


Billing and Cost Management
---------------------------

### Basics
- Datadog prices varies by each service which charge among multiple dimensions

### Tips
- You can make use of AWS Private Link to reduce egress fees from AWS by 90%. Be aware that this is only available in the `us1` and `ap1` site 💸❗ 

### Gotchas
- For metrics, logs, and traces, Datadog charges $0.10/GB for data ingress. Note that there is generally a corresponding charge from your cloud provider for egress fees. AWS for example [charges](https://aws.amazon.com/ec2/pricing/on-demand/) charges $0.09/GB of egress. This effectively doubles your data transfer fee when using Datadog 💸