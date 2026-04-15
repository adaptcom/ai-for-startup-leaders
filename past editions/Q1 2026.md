According to MIT's State of AI in Business 2025 report, 95% of AI deployments within a business fail. This guide gives leaders the tools to make it into the other 5%.

Get a clear view of the AI landscape and learn how to evaluate AI platforms and AI agents so they move your business forward faster without adding drag.

## Introduction

On April 7th, 2025, Shopify's CEO Tobias Lütke tweeted about his controversial, leaked memo on AI. The tweet went viral, generating 4 million views and thousands of responses on social media. Slack channels at startups lit up with internal debates about AI usage at work.

The memo's core message was that using AI was now a "baseline expectation" at Shopify. Before requesting more headcount, employees would need to prove they couldn't accomplish their goals using AI first.

At Coinbase, Brian Armstrong gave engineers a week to adopt AI coding assistants or face termination. "I jumped on this call on Saturday and there were a couple people that had not done it," Armstrong explained in an interview. "Some of them had a good reason, because they were just getting back from a trip or something, and some of them didn't. And they got fired."

At Amazon, CEO Andy Jassy encouraged employees to become proficient with AI, and warned that corporate roles would shrink as AI efficiency gains took hold. Airtable CEO Howie Liu grants employees time off to learn how to use AI for their jobs.

## The AI disconnect

CEOs are demanding AI adoption, but the results, for many, have been disappointing. MIT's [State of AI in Business 2025 report](https://mlq.ai/media/quarterly_decks/v0.1_State_of_AI_in_Business_2025_Report.pdf) found that despite $30 billion in enterprise spending on generative AI, 95% of organizations are seeing no measurable return.

While tools like ChatGPT and Claude have been piloted by over 80% of organizations, they primarily enhance individual productivity rather than driving business transformation.

Meanwhile, enterprise-grade AI systems are quietly failing. The MIT report says that 60% of organizations evaluated such tools, but only 20% reached pilot stage and just 5% made it to production.

The problem, according to the leaders building these systems, is that we're using AI wrong. At the 2025 Snowflake Summit, OpenAI's Sam Altman diagnosed the issue:

> "Using these models as databases is sort of ridiculous. It's a very slow, expensive, very broken database."
>
> — Sam Altman, CEO of OpenAI

Altman explained that business use of AI is failing because the current approach treats AI as a knowledge repository, asking it to recall facts and generate text. Altman laid out a vision for how AI will be used by companies in the near future:

> "The amazing thing is they can reason, and if you think of [AI] as this reasoning engine that we can then throw all of the possible context of a business into, and any tool that they need, that's quite amazing what people can do."
>
> — Sam Altman, CEO of OpenAI

Anthropic CEO Dario Amodei echoed this shift in thinking, pointing to context as the key to unlocking AI's potential:

> "Context windows are getting longer and models actually do learn during the context window. From a machine learning perspective, there's no reason we can't make the context length 100 million words, which is roughly what a human hears in their lifetime."
>
> — Dario Amodei, CEO of Anthropic

Amodei says the best way to use AI is to give the LLM your entire business context so that the model can "learn" and produce better answers.

Since 2024, the landscape has exploded with new tools to help you get AI done at work. OpenAI and Anthropic have leaned in to making ChatGPT and Claude fit for the enterprise through connectors and integrations to your business systems. A new standard for connecting to existing tools and data, MCP (Model Context Protocol), has emerged, and companies are quickly adopting it for its potential.

Amongst all of the innovation happening, many users themselves have run into broken promises and failed attempts to use AI to its full potential. In this guide, we'll explore the underlying technology needed for AI to do its best work. You'll learn how to apply the terms you're hearing to increase your own knowledge and discernment when considering how to make AI work best for you and your organization.

## The ARC Framework

Altman and Amodei's visions converge on three core capabilities that define the future of AI in business. You can call this the ARC of AI capability:

**Agency · Reasoning · Context**

Understanding how these three pillars work together, and where each stands today, is essential for any startup leader trying to separate genuine AI capability from vendor hype. Let's break down each component.

## Part 1: Agency — AI that can complete tasks

There are many definitions of "agency" in LLMs, but for this report we will focus on the model's ability to call functions or tools, and also run code in a sandbox. This recent capability in AI models expanded its use case from just writing and delivering answers to accomplishing tasks on a user's behalf.

OpenAI led the way in agentic AI by [introducing a plugin system for ChatGPT in March 2023](https://openai.com). The announcement explained that ChatGPT could now "run computations, or use third-party services."

Microsoft simultaneously [launched plugins for Bing Chat](https://www.microsoft.com), with the additional ability to search the web for up-to-date answers or use Wolfram Alpha for complex calculations. Each function or plugin essentially acted as a new skill the AI could invoke when needed, and the model would decide if and when to use it.

Developers did not have access to these capabilities until OpenAI also [enabled function calling in their API in mid-2023](https://platform.openai.com) to define custom functions that models could call via JSON requests. This meant businesses could allow an AI agent to directly execute operations, from database lookups to sending an email, in a controlled manner.

Meanwhile, Google was not far behind. That same year, Google's Bard AI gained enhanced capabilities like code execution and image analysis, and in September 2023 Google [launched Bard Extensions](https://blog.google). This allowed Bard to seamlessly integrate with Google's own suite of applications. A user could ask Bard to pull data from their Gmail, summarize a Google Doc, fetch directions via Google Maps, or get YouTube videos on a topic.

### AI that runs code

Alongside plugins, OpenAI also [launched code execution](https://openai.com). This gave the model the ability to spin up a temporary, secure environment and run a script that would help it complete a task. In late 2025, Anthropic also enabled code execution in their AI model with the [launch of Claude Skills](https://anthropic.com).

Running code is a leap forward for the agentic capabilities in AI models. The earliest models could only produce text, but code execution enables the AI to perform enhanced computation, and also create files such as CSVs, slide decks, or PDFs. Anthropic refers to this as a "private computer environment".

### Open standards emerge: The Model Context Protocol (MCP)

Anthropic officially [rolled out Claude 3's tool use feature in mid-2024](https://anthropic.com), allowing Claude to interact with external APIs and perform tasks for users.

At this point, enabling agentic use cases for AI was a spaghetti mess for developers. OpenAI and Microsoft announced a collaboration to make plugins cross-platform. And Google's plugins were primarily for their own services. But using multiple models in your app, and connecting them to multiple services required weaving together APIs.

This problem gave birth to MCP (Model Context Protocol). It was introduced by Anthropic as an open standard for how LLM-based agents can connect to external tools, data, and other resources. As the [initial blog post explained](https://anthropic.com), "Instead of maintaining separate connectors for each data source, developers can now build against a standard protocol."

MCP defines a common language for an AI system to discover available tools and invoke them, decoupling the tool implementation from any single AI vendor. With MCP, a tool provider can create an MCP server, essentially an API endpoint that advertises a list of functions or tools, what inputs they require, and what they do.

An AI application with an MCP client can then query any MCP server, get the list of tools, and allow the LLM to call those functions in a standardized format. A common analogy is that MCP is like USB for AI models.

MCP [exploded in developer popularity](https://github.com), and soon Anthropic's competitors, like Google and OpenAI, adopted the standard.

In less than two years, tool use and function calling graduated from being an AI capability that was closed and fragmented, to now being a table stakes feature empowered by a universal protocol.

### MCP problems in production

MCP is a very new standard, and companies are still learning about its drawbacks as they ship internal and external products that rely on the protocol. The three key weaknesses of MCP include flaky performance, poor implementation, and security risks.

Poor performance is the most immediate issue. MCP depends on the model correctly calling structured tools, but LLMs are inconsistent at doing so. Cloudflare's AI team found that LLMs often fumble tool calls, leading to broken chains of reasoning. Their solution was [having the model write and run TypeScript to call APIs directly](https://blog.cloudflare.com), which proved faster and more reliable.

Compounding the instability issue is the problem of poor implementations of MCP. Database startup Neon [delivered a talk](https://neon.tech) highlighting how many MCP servers are often rushed, thin wrappers over existing APIs. They add overhead without adding intelligence, producing brittle integrations that fail under real-world load.

Finally, security gaps in MCP servers have raised red flags. Research by Backslash Security [uncovered over 15,000 exposed MCP servers](https://www.backslash.security), half of which were dangerously misconfigured, with some open to remote code execution.

MCP is a powerful promise as a universal standard, but the agentic capabilities of models may currently be better suited to write scripts to interact with APIs directly.

## Part 2: Reasoning — AI that can plan ahead

The story of reasoning in AI begins with a simple yet revolutionary insight from Google researchers in early 2022. [The team discovered](https://arxiv.org) that by providing large language models with examples that showed step-by-step reasoning processes, they could dramatically improve performance on complex tasks. This technique, called chain-of-thought (CoT) prompting, represented the first major breakthrough in making AI systems "think" through problems systematically.

However, this technique had significant limitations. It only worked effectively with models containing around 100 billion parameters or more, and smaller models often produced illogical reasoning chains.

### The reasoning revolution: OpenAI's o-series

In September 2024, OpenAI launched a fundamentally different approach with the o1 model series. Unlike chain-of-thought prompting, which relied on external techniques, o1 was the first model designed from the ground up to "think" before responding.

The model spends time reasoning internally, making it dramatically better at complex reasoning tasks, science, and programming than previous models. Initial benchmarks showed that o1 [achieved an 83% problem-solving rate on the International Mathematics Olympiad qualifying exam](https://openai.com), compared to GPT-4o's 13% success rate.

By December 2024 o3 was released as an advanced reasoning model. It scored an impressive 96.7% on the American Invitational Mathematics Exam (AIME), missing a single question.

So in two years LLM reasoning made the leap from being an advanced prompting feature, used only by experts, to being a baked-in capability of AI models. Cost however remained an issue, and OpenAI gated access to the models for only their highest pricing tiers.

### The open source response: DeepSeek's innovation

Google entered the advanced reasoning model space in December 2024 with [Gemini 2.0 Flash Thinking Experimental](https://blog.google). And Anthropic followed quickly after with Claude 3.7 Sonnet with extended thinking capabilities.

But Chinese AI company DeepSeek made waves in January 2025 with [the release of DeepSeek-R1](https://deepseek.com), an open-source reasoning model that matched OpenAI's o1 performance while being freely available. The model demonstrated that reasoning capabilities could be achieved through innovative training methods without the massive resources typically required by major tech companies, like OpenAI, Google, and Anthropic.

Companies now had several choices of advanced reasoning, across a range of prices, and from multiple vendors.

### Reasoning unlocked more agency

[Anthropic explained](https://anthropic.com) that their new reasoning models also came with "an improved capability that allows it to iteratively call functions, respond to environmental changes, and continue until an open-ended task is complete." In other words, the extended thinking technique boosted the AI's agentic capabilities.

Developers experienced this shift first. Reasoning models demonstrated remarkable capabilities in generating complex code, debugging intricate systems, and explaining their reasoning process. Vibe coding apps began to live up to their promise, with startups like Replit and Bolt gaining millions of users, while Lovable crossed $100 million in expected ARR.

### Hallucination issues remain

Accuracy remained a blocker for enterprise adoption of advanced reasoning and agency. Developers can immediately verify AI-written code by compiling and testing for errors. However, business users of AI models do not have that luxury.

In June of 2025 [Apple uncovered concerning patterns in reasoning model behavior](https://apple.com). Apple's researchers found that reasoning models experience what they called a "complete accuracy collapse" beyond certain complexity thresholds. The models exhibit a counter-intuitive scaling limit: their reasoning effort increases with problem complexity up to a point, then declines despite having adequate computational resources.

[The NY Times surveyed the hallucination problem in AI models](https://nytimes.com), reporting that the inaccuracy is actually worse in reasoning models.

This barrier is the backdrop of why the leading AI CEOs fielded skeptical questions about the capabilities of their models. As we discussed above, Sam Altman explained that hallucination is only a problem if you treat the model as an old school database.

Dario Amodei agrees, and believes the best use of AI in its current state is to use advanced reasoning over context that a business provides to a model. Context is the C in ARC, and we'll discuss that next.

## Part 3: Context — AI that can learn

Context refers to the amount of data an AI model can "hold in its head" at once, like an attention span. When the context window of a model is small, or not used, it defaults to pulling information from its training set. However, if the model has a large context window, and it is used properly, the model can base its reasoning on qualified data and complete the right agentic tasks.

In the early days of modern AI, the attention span of models was short. OpenAI's GPT-3 could only handle 2,048 tokens of context, or about 1,500 words of text.

By 2023 [GPT-4 launched with the ability to ingest 40-50 pages of context](https://openai.com). OpenAI hinted at experimental GPT-4 models handling up to 128,000 tokens, approaching an entire novel's worth of text.

### The 1 million breakthrough

Anthropic [made headlines in 2023](https://anthropic.com) by loading the entire text of "The Great Gatsby" into Claude and having it spot a single sentence that had been altered. Claude scanned the whole novel and pinpointed the change. This feat was impossible for AI just a few months before.

Google [broke the sound barrier in 2024](https://blog.google), with the first model that included a 1 million token context window. As Google explained, this meant the model could handle "1 hour of video, 11 hours of audio, or over 700,000 words."

The AI context window's state-of-the-art went from a few paragraphs to multiple books in just a few years.

### The need for context engineering

Google has hinted that they've achieved a context window of up to 10 million tokens. However, [researchers have found](https://arxiv.org) that AI models don't always utilize ultra-long context with full precision. They tend to focus on the beginning and end while neglecting middle portions of text.

This drawback has been labeled ["context rot"](https://arxiv.org), a problem where an AI model's performance becomes increasingly unreliable as input length grows.

Early attempts to solve this challenge involved compressing context or using summarization to reduce the information the model needed to process. The downside of this technique was losing important details or oversimplification, which led to poorer model performance.

A new, more effective approach to addressing context rot is referred to as context engineering. AI pioneer Andrej Karpathy [describes context engineering](https://karpathy.ai) as "the delicate art and science of filling the context window with just the right information for the next step."

Rather than overwhelming the model by stuffing all possible content into a prompt, context engineering selectively retrieves the right information for the task, then chunks, organizes, and labels it for maximum usefulness.

While Altman and Amodei envision future AI models with nearly infinite context windows, the timing of these predictions is irrelevant. Current context window lengths already suffice for most businesses that apply proper context engineering. Frontier models can handle entire corporate knowledge bases, years of email messages, or volumes of customer data in a single prompt when combined with an orchestrator to manage context.

### Challenges with context engineering in business

Despite context engineering being an effective way to handle large amounts of context, the struggle to assemble and orchestrate context efficiently across an organization's many systems and data sources remains. No simple, plug-and-play system exists. And companies who build this internally often turn to building an organizational knowledge graph or their own semantic context layer — a costly endeavor that can quickly leave them behind as the next new technology emerges.

However, without a solution in place for this, companies are unlikely to see the results they expect at scale.

## AI as an intelligence layer that can act and reason — with context

After years of false starts, AI is finally ready for business. [A quarter of startups in Y Combinator's current cohort](https://ycombinator.com) have codebases that are almost entirely AI-generated. The next generation of companies are not threatening or bribing employees to adopt AI, like Coinbase and Airtable. Young startups have AI usage as part of their company culture from day 1.

However, if your company evaluated AI in 2024 and came away disappointed, it's likely because some part of ARC in AI models was still immature or misused. Companies prompted LLMs to recall facts from training data, then wrote off the technology when it hallucinated. Also, vendors sold company leaders the wrong narrative. They positioned AI as a tool for reducing headcount instead of amplifying human potential.

The MIT "State of AI in Business" report found that while only 5% of organizations are seeing measurable success with AI, they share one defining trait:

> "Organizations are already experimenting with agentic systems that can learn, remember, and act autonomously within defined parameters."

In other words, the small group that's winning with AI is using its Agency, Reasoning, and Context capabilities.

The maturation of ARC in the latter half of 2025 finally enables AI to function as an intelligence layer for a business. AI can now learn from a business's unique context, reason through complex problems, and take action.

### What ARC looks like in business

Consider a sales leader asking: "Which Q1 customers mentioned integration concerns during onboarding but haven't opened support tickets?"

Previously, this required querying multiple systems, manually cross-referencing data, and spending hours synthesizing results. Now an AI system can ingest your entire data infrastructure and reason across customer records, sales notes, and support logs. It can then surface the answer with suggested next actions in seconds.

Or imagine a customer success manager's request: "Review at-risk accounts, check usage patterns against contract size, draft personalized emails highlighting underutilized features, and schedule follow-ups." An AI model with full ARC capabilities can execute the entire workflow, escalating only decisions requiring human judgment.

### The competitive advantage

Adopting an intelligence layer helps companies operate at a fundamentally different pace. Employees can focus on high-judgment work while routine processes are completed autonomously.

This is why startup CEOs like Lütke and Armstrong drew hard lines about AI adoption. They are betting that the velocity advantage of using AI for its ARC capabilities will compound over time and grow their companies.

### Your framework for evaluation

You now have a mental model for cutting through AI hype. When SaaS vendors or model providers announce "revolutionary" improvements, you'll recognize whether the feature is truly transformative or merely incremental.

Conversely, when you see genuine breakthroughs, like dramatically improved reasoning at lower costs, more reliable tool execution, or expanded usable context, you'll understand exactly how they impact operations.

The ARC framework helps you set internal priorities. You'll know whether your team needs better reasoning for complex decisions, expanded context for business data, or improved agency for automation.

You'll be able to evaluate pitches and identify solutions that help you maximize your business intelligence layer.

### Becoming an AI-native company

When evaluating AI solutions for business growth, the ultimate question is whether the tool serves the whole company or just one department.

Too often, companies adopt specialized AI tools that can enable one team's productivity, while ignoring the collaborative nature of the work. For example, a coding agent adopted by one team might speed up their velocity but create discrepancies in workflow and visibility with the rest of the development organization.

That's because the value of AI is not just in automation, but in providing an intelligence layer across the entire organization, producing compounding growth.

In an AI-native startup, your sales lead can ask, "Why did bookings drop last week?" The AI system should be able to pull relevant data from your CRM and support tools, and write a Python script that traces the decline to accounts that churned after a pricing change.

A product manager could then pick up the thread, asking the AI to review meeting notes on what the pricing change was originally meant to achieve. Finally, the leadership team might receive a proposal for a win-back campaign, complete with a deck co-created by staff and an AI model that generated the charts and slides.

AI should act like the nervous system of your company, connecting teams across functions, transmitting context instantly, and turning signals into coordinated action. This is what it means to be AI-native.

## About Adapt

Adapt is the AI computer for business. It connects to all of your tools and data sources, orchestrates context across them, and powers clarity and action across the entire company.

Set it up once, and anyone in your company can tag @Adapt to get trusted answers and take action. Available in Slack and the Adapt app, and coming soon to wherever you work.
