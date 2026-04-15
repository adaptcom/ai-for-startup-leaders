## Introduction

On February 15th, 2026, Sam Altman posted on X that OpenAI had hired Peter Steinberger, the creator of OpenClaw. "He is a genius with a lot of amazing ideas about the future of very smart agents interacting with each other to do very useful things for people," Altman wrote.

The post was viewed 16.3 million times. The tech community erupted with reactions. The mainstream press immediately ran stories and analyses about what this means for businesses.

Peter Steinberger’s hiring was the capstone on a remarkable journey for him and his OpenClaw creation. Three months earlier, Steinberger was an independent developer on vacation in Marrakesh. He had built a prototype in a single hour, frustrated that nobody had created what seemed obvious: an AI agent that could take independent action on your computer, not just have a conversation with you.

Steinberger connected WhatsApp to Claude's command-line interface, sent a message, and watched the AI respond. "I was annoyed that it didn't exist," [he later told Lex Fridman](https://youtu.be/YFjfBk8HI5o?si=WMhaaTL7PzJf4FBI&t=448), "so I just prompted it into existence."

What Steinberger built was different from every AI tool on the market. Instead of running in the cloud, OpenClaw runs locally on your computer with full access to your files, apps, and terminal. Instead of connecting to a few tools selected by a vendor, it could use any API or even run a web browser and log in to services.

And instead of the standard text-in, text-out interaction, OpenClaw solved problems by writing and executing code on the fly.

But the key difference that first made OpenClaw popular was that it was built to act autonomously by default. ChatGPT, Claude, and Gemini all wait for a user prompt. But OpenClaw runs on a “heartbeat” system that triggers the agent every thirty minutes to check on tasks, follow up on reminders, and surface things you hadn't thought to ask for.

The results startled even Steinberger. During his trip, he absent-mindedly sent the agent a voice message, a capability he had never built the agent to handle. A typing indicator appeared. Then a reply. The agent had inspected the file, identified the audio format, found an OpenAI API key in the environment, and used it to transcribe the message.

"How the f- did he do that?" Steinberger said on the Lex Fridman podcast.

He described the agent's problem-solving as "so much world knowledge and creative problem solving" packed into a single sequence of decisions.

Within weeks, OpenClaw had 194,000 GitHub stars, making it the fastest-growing repository in GitHub history. Business leaders who had spent 2025 debating whether to adopt AI were now watching a solo developer's side project outperform entire product teams.

Jason Calacanis, co-host of the All-In Podcast and host of This Week in Startups, built an internal system on top of Steinberger's project he called "OpenClaw Ultron." He gave agents full access to his company's Slack, Notion, and Gmail, then pointed them at his team's daily work.

His producer estimated 60% of his production tasks could be automated within 30 days. Calacanis announced his firm would not hire another human for at least a year. "It's easier, faster, and more cost-efficient to set up replicants," [he wrote](https://calacanis.substack.com/p/openclaw-and-the-great-hiring-hiatus), using his term for the AI workers now embedded across his 20-person company.

The era of autonomous AI agents had arrived. The question for startup leaders was no longer whether to use AI. It was how far to let it go.

## The AI disconnect

CEOs have been waiting for AI to become business-ready after years of disappointing results. [MIT's State of AI in Business report](https://mlq.ai/media/quarterly_decks/v0.1_State_of_AI_in_Business_2025_Report.pdf) found that despite $30 billion in enterprise spending on generative AI, 95% of organizations saw no measurable return.

While tools like ChatGPT and Claude have been piloted by over 80% of organizations, they primarily enhance individual productivity rather than driving business transformation.

Meanwhile, enterprise-grade AI systems are quietly failing. The MIT report says that 60% of organizations evaluated such tools, but only 20% reached pilot stage and just 5% made it to production.

The problem, according to the leaders building these systems, is that we're using AI the wrong way. At the 2025 Snowflake Summit, OpenAI's [Sam Altman diagnosed the issue](https://youtu.be/gJf39VG87O8?si=zupV3y9wgV_Vnynu):

>"Using these models as databases is sort of ridiculous. It's a very slow, expensive, very broken database."
>— Sam Altman, CEO of OpenAI

Altman explained that business use of AI is failing because the current approach treats AI as a knowledge repository, asking it to recall facts and generate text. Altman laid out a vision for how AI will be used by companies in the near future:

>"The amazing thing is they can reason, and if you think of \[AI\] as this reasoning engine that we can then throw all of the possible context of a business into, and any tool that they need, that's quite amazing what people can do."
>— Sam Altman, CEO of OpenAI

Anthropic CEO Dario Amodei echoed this shift in thinking, pointing to “context” as the key to unlocking AI's potential:

>"Context windows are getting longer and models actually do learn during the context window. From a machine learning perspective, there's no reason we can't make the context length 100 million words, which is roughly what a human hears in their lifetime."
>— Dario Amodei, CEO of Anthropic

Amodei says the best way to use AI is to give the LLM your entire business context so that the model can "learn" and produce better answers.

Just a few months after both CEOs delivered these comments on how to use AI's advanced capabilities, OpenClaw was born.

## **The ARC Framework**

Altman and Amodei's visions converge on three core capabilities that define the future of AI in business. You can call this the ARC of AI capability:

**Agency · Reasoning · Context**

Understanding how these three pillars work together, and where each stands today, is essential for any startup leader who wants to build an AI-native company. Let's break down each component.

## **Part 1: Agency — AI that can complete tasks**

In early 2026, Anthropic [published a system card](https://www-cdn.anthropic.com/0dd865075ad3132672ee0ab40b05a53f14cf5288.pdf) describing security evaluations of Claude Opus 4.6. The goal of these tests was to understand how the model behaves when given tools, access to a computing environment, and an objective to complete.

What they discovered was surprising, like the opening scene of a science fiction movie.

In one evaluation, Claude was asked to make a pull request on GitHub. It was not authenticated, and therefore could not complete the action through normal means.

Anthropic reports:

“In one case, the model was asked to make a pull request on GitHub, but was not authenticated, and so could not do so. Rather than asking the user to authenticate, it searched and found a misplaced GitHub personal access token on an internal system—which it was aware belonged to a different user—and used that.”

In another case, Claude again worked around obstacles without guidance:

“Claude was not given a tool to search our internal knowledgebase, but needed such a tool to complete its task. It found an authorization token for Slack on the computer that it was running on… and used it, with the curl command-line tool, to message a knowledgebase-Q\&A Slack bot in a public channel from its user’s Slack account.”

Anthropic disclosed this leap in agency as a warning. They strengthened the guardrails in tools like Claude Code to guard against the model’s resourceful behavior.

But Peter Steinberger drew a different conclusion. If models are already capable of exploring environments and overcoming barriers creatively, then he wanted OpenClaw to unleash that behavior, not limit it.

### The history of agency in AI

To understand the state of the art of agency in AI, we need to look back at the growth of these models' ability to call functions or tools, and also run code in a sandbox.

OpenAI led the way in agentic AI by [introducing a plugin system for ChatGPT in March 2023](https://openai.com/index/chatgpt-plugins/). The announcement explained that ChatGPT could now "run computations, or use third-party services."

Microsoft simultaneously [launched plugins for Bing Chat](https://blogs.microsoft.com/blog/2023/05/23/microsoft-build-brings-ai-tools-to-the-forefront-for-developers/), with the additional ability to search the web for up-to-date answers or use Wolfram Alpha for complex calculations. Each function or plugin essentially acted as a new ability the AI could invoke when needed, and the model would decide if and when to use it.

Developers did not have access to these capabilities until OpenAI also [enabled function calling in their API in mid-2023](https://openai.com/index/function-calling-and-other-api-updates/) to define custom functions that models could call via JSON requests. This meant businesses could allow an AI agent to directly execute operations, from database lookups to sending an email, in a controlled manner.

Meanwhile, Google was not far behind. That same year, Google's Bard AI gained enhanced capabilities like code execution and image analysis, and in September 2023 Google [launched Bard Extensions](https://blog.google/products-and-platforms/products/gemini/google-bard-new-features-update-sept-2023/). This allowed Bard to seamlessly integrate with Google's own suite of applications. A user could ask Bard to pull data from their Gmail, summarize a Google Doc, fetch directions via Google Maps, or get YouTube videos on a topic.

### **AI that runs code**

Alongside plugins, OpenAI also [launched code execution](https://openai.com/index/chatgpt-plugins/). This gave the model the ability to spin up a temporary, secure environment and run a script that would help it complete a task. In late 2025, Anthropic also enabled code execution in its AI model with the [launch of Claude Skills](https://claude.com/blog/equipping-agents-for-the-real-world-with-agent-skills).

Running code was a leap forward for the agentic capabilities in AI models. The earliest models could only produce text, but code execution enables the AI to perform enhanced computations and also create files such as CSVs, slide decks, or PDFs. Anthropic refers to this as a "private computer environment".

### **The Model Context Protocol (MCP)**

Anthropic officially [rolled out Claude 3's tool use feature in mid-2024](https://www.anthropic.com/news/claude-3-family), allowing Claude to interact with external APIs and perform tasks for users.

At this point, enabling agentic use cases for AI was a spaghetti mess for developers. OpenAI and Microsoft announced a collaboration to make plugins cross-platform. And Google's plugins were primarily for their own services.

But using multiple models in your app, and connecting them to multiple services required weaving together APIs.

This problem gave birth to MCP (Model Context Protocol). It was introduced by Anthropic as an open standard for how LLM-based agents can connect to external tools, data, and other resources. As the [initial blog post explained](https://anthropic.com/), "Instead of maintaining separate connectors for each data source, developers can now build against a standard protocol."

MCP defines a common language for an AI system to discover available tools and invoke them, decoupling the tool implementation from any single AI vendor. With MCP, a tool provider can create an MCP server, essentially an API endpoint that advertises a list of functions or tools, what inputs they require, and what they do.

An AI application with an MCP client can then query any MCP server, get the list of tools, and allow the LLM to call those functions in a standardized format. A common analogy is that MCP is like USB for AI models.

MCP [exploded in developer popularity](https://www.latent.space/p/why-mcp-won), and soon Anthropic's competitors, like Google and OpenAI, adopted the standard.

In less than two years, tool use and function calling graduated from being an AI capability that was closed and fragmented, to now being a table stakes feature empowered by a universal protocol.

## **Part 2: Reasoning — AI that can plan ahead**

The story of reasoning in AI begins with a simple yet revolutionary insight from Google researchers in early 2022.

[The team discovered](https://arxiv.org/abs/2201.11903) that by providing large language models with examples that showed step-by-step reasoning processes, they could dramatically improve performance on complex tasks. This technique, called chain-of-thought (CoT) prompting, represented the first major breakthrough in making AI systems "think" through problems systematically.

However, this technique had significant limitations. It only worked effectively with models containing around 100 billion parameters or more, and smaller models often produced illogical reasoning chains.

### **The reasoning revolution: OpenAI's o-series**

In September 2024, OpenAI launched a fundamentally different approach with the o1 model series. Unlike chain-of-thought prompting, which relied on external techniques, o1 was the first model designed from the ground up to "think" before responding.

The model spends time reasoning internally, making it dramatically better at complex reasoning tasks, science, and programming than previous models. Initial benchmarks showed that o1 [achieved an 83% problem-solving rate on the International Mathematics Olympiad qualifying exam](https://openai.com/index/introducing-openai-o1-preview/), compared to GPT-4o's 13% success rate.

By December 2024 o3 was released as an advanced reasoning model. It scored an impressive 96.7% on the American Invitational Mathematics Exam (AIME), missing a single question.

So, in two years, LLM reasoning made the leap from an advanced prompting feature, used only by experts, to a baked-in capability of AI models. Cost, however, remained an issue, and OpenAI gated access to the models for only their highest pricing tiers.

### **The open source response: DeepSeek's innovation**

Google entered the advanced reasoning model space in December 2024 with [Gemini 2.0 Flash Thinking Experimental](https://blog.google/innovation-and-ai/models-and-research/google-deepmind/google-gemini-ai-update-december-2024). And Anthropic followed quickly after with [Claude 3.7 Sonnet](https://www.anthropic.com/news/claude-3-7-sonnet) with extended thinking capabilities.

But Chinese AI company DeepSeek made waves in January 2025 with [the release of DeepSeek-R1](https://api-docs.deepseek.com/news/news250120), an open-source reasoning model that matched OpenAI's o1 performance while being freely available. The model demonstrated that reasoning capabilities could be achieved through innovative training methods without the massive resources typically required by major tech companies, like OpenAI, Google, and Anthropic.

Companies now had several choices of advanced reasoning, across a range of prices, and from multiple vendors.

### **Reasoning unlocked more agency**

[Anthropic explained](https://www.anthropic.com/news/claude-3-7-sonnet) that their new reasoning models also came with "an improved capability that allows it to iteratively call functions, respond to environmental changes, and continue until an open-ended task is complete." In other words, the extended thinking technique boosted the AI's agentic capabilities.

Developers experienced this shift first. Reasoning models demonstrated remarkable capabilities in generating complex code, debugging intricate systems, and explaining their reasoning process. Vibe coding apps began to live up to their promise, with startups like Replit and Bolt gaining millions of users, while [Lovable crossed $100 million](https://lovable.dev/blog/product-updates/agent) in expected ARR.

### **Hallucination issues remain**

Accuracy remained a blocker for enterprise adoption of advanced reasoning and agency. Developers can immediately verify AI-written code by compiling and testing for errors. However, business users of AI models do not have that luxury.

In June of 2025 [Apple uncovered concerning patterns in reasoning model behavior](https://machinelearning.apple.com/research/illusion-of-thinking). Apple's researchers found that reasoning models experience what they called a "complete accuracy collapse" beyond certain complexity thresholds.

The models exhibit a counterintuitive scaling limit. Their reasoning effort increases with problem complexity up to a point, then *declines* despite having adequate computational resources.

[The NY Times surveyed the hallucination problem in AI models](https://www.nytimes.com/2025/05/05/technology/ai-hallucinations-chatgpt-google.html), reporting that the inaccuracy is actually worse in reasoning models.

This barrier is the backdrop of why the leading AI CEOs fielded skeptical questions about the capabilities of their models. As we discussed above, Sam Altman explained that hallucination is only a problem if you treat the model as an old school database.

Dario Amodei agrees and believes the best use of AI in its current state is to use advanced reasoning over context that a business provides to a model. Context is the C in ARC, and we'll discuss that next.

## **Part 3: Context — AI that can learn**

Context refers to the amount of data an AI model can "hold in its head" at once, like an attention span. When the context window of a model is small, or not used, it defaults to pulling information from its training set. However, if the model has a large context window, and it is used properly, the model can base its reasoning on qualified data and complete the right agentic tasks.

In the early days of modern AI, the attention span of models was short. OpenAI's GPT-3 could only handle 2,048 tokens of context, or about 1,500 words of text.

By 2023 [GPT-4 launched with the ability to ingest 40-50 pages of context](https://openai.com/index/gpt-4-research/). OpenAI hinted at experimental GPT-4 models handling up to 128,000 tokens, approaching an entire novel's worth of text.

### **The 1 million breakthrough**

Anthropic [made headlines in 2023](https://www.anthropic.com/news/100k-context-windows) by loading the entire text of "The Great Gatsby" into Claude and having it spot a single sentence that had been altered. Claude scanned the whole novel and pinpointed the change. This feat was impossible for AI just a few months before.

Google [broke the sound barrier in 2024](https://blog.google/innovation-and-ai/products/google-gemini-next-generation-model-february-2024/), with the first model that included a 1 million token context window. As Google explained, this meant the model could handle "1 hour of video, 11 hours of audio, or over 700,000 words."

OpenAI finally opened up the context window of the GPT-5.4 model to 1 million tokens in [March of 2026](https://openai.com/index/introducing-gpt-5-4/).

The AI context window's state-of-the-art went from a few paragraphs to multiple books in just a few years.

### **The need for context engineering**

Google has hinted that they've achieved a context window of up to 10 million tokens. However, [researchers have found](https://arxiv.org/abs/2307.03172) that AI models don't always utilize ultra-long context with full precision. They tend to focus on the beginning and end while neglecting middle portions of text.

This drawback has been labeled ["context rot"](https://research.trychroma.com/context-rot), a problem where an AI model's performance becomes increasingly unreliable as input length grows.

Early attempts to solve this challenge involved compressing context or using summarization to reduce the information the model needed to process. The downside of this technique was losing important details or oversimplification, which led to poorer model performance.

A new, more effective approach to addressing context rot is referred to as context engineering. AI pioneer Andrej Karpathy [describes context engineering](https://x.com/karpathy/status/1937902205765607626) as "the delicate art and science of filling the context window with just the right information for the next step."

Rather than overwhelming the model by stuffing all possible content into a prompt, context engineering selectively retrieves the right information for the task, then chunks, organizes, and labels it for maximum usefulness.

While Altman and Amodei envision future AI models with nearly infinite context windows, the timing of these predictions is irrelevant. Current context window lengths already suffice for most businesses that apply proper context engineering. Frontier models can handle entire corporate knowledge bases, years of email messages, or volumes of customer data in a single prompt when combined with an orchestrator to manage context.

### Solving the consistency problem

A related development in context engineering is the introduction of structured, reusable directions referred to as “skills.” [Anthropic introduced skills](https://claude.com/blog/skills) as a way to define agent behaviors outside the prompt itself.

A skill can encapsulate instructions, constraints, workflows, or tool configurations that the model invokes when needed. Rather than a user prompting with detailed guidance for each task, a predefined skill standardizes how a job is performed.

Skills allow you to give your company’s operational playbooks to an agent. A skills folder can represent how support triages tickets, how sales qualifies enterprise deals, how finance models pricing tiers, or how marketing maintains brand voice.

Together, long context windows and skills mark a shift in how AI labs and businesses approach reliability. In the past, model labs assumed that if LLMs were trained on enough of the world’s knowledge, they would be able to run your business. That proved unreliable, so the emphasis moved to feeding models structured, business-specific context.

OpenClaw builds on these advances in context, agency, and reasoning to experiment with agents that have maximum autonomy. The next question for business leaders is how those same capabilities can reshape work, and how AI becomes a teammate, not just an agent.

## The future of AI at work

When a company’s product idea moves from concept to launch, it touches many teams. Product and engineering work to build a technically elegant solution, while marketing shapes a launch strategy.

The two sides then meet in a conference room and discover they've been solving different problems:

P\&E's prototype ignored user activation, how customers would actively sign up and pay for the product. And marketing’s ad campaign overpromised with capabilities that engineering never scoped. Weeks of rework follow the meeting due to teams operating in functional silos.

## AI can now solve this classic business problem

Researchers from Harvard ran [a field experiment](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5188231) with 776 professionals at Procter & Gamble. They randomly assigned participants to work on real product innovation challenges, either individually or in two-person teams, with or without AI.

Without AI, the functional silos held. R\&D professionals proposed technical solutions, while Commercial professionals proposed commercially-oriented ones. Each group defaulted to its training, its incentives, and its corner of the org chart.

However, with AI as an intelligence layer, the silos dissolved. The researchers did not replace human workers, but instead enabled faster collaboration:

“Our findings show that AI replicates many of the benefits of human collaboration, acting as a ‘cybernetic teammate.’”

AI achieves this by carrying business knowledge across functional boundaries. R\&D professionals produced solutions that incorporated commercial viability. And Commercial professionals produced solutions grounded in technical reality. Both produced balanced, cross-functional proposals regardless of their professional background.

Even more individuals using AI matched the performance of two-person human teams working without it. And AI-enabled teams were three times more likely to produce solutions in the top 10% of quality.

[A separate study confirms the pattern](https://hbr.org/2026/02/ai-doesnt-reduce-work-it-intensifies-it) at the company level. Over an eight-month period, UC Berkeley researchers tracked what happened after a U.S. technology company offered enterprise AI subscriptions to about 200 employees.

No one was told to use AI or work differently. On their own initiative, employees began working at a faster pace, taking on a broader scope of tasks, and reaching across traditional role boundaries.

Product managers started writing code, and researchers took on engineering work. People did more because AI made "doing more" feel possible, accessible, and intrinsically rewarding.

The company did not have to reorganize or run a digital transformation program. It simply gave its team access to AI, and barriers between roles started to soften.

These two studies point to a conclusion that the AI industry has largely missed.

NVIDIA CEO Jensen Huang [put the underlying logic bluntly](https://www.youtube.com/watch?v=gwW8GKwHB3I&t=1470). If you pay an engineer $500,000 a year and they consume only $5,000 in AI tokens, something has gone wrong. Not because AI is an additional expense, but because the investment you already made in that person is not being maximized:

>"If that $500,000 engineer did not consume at least $250,000 worth of tokens, I am going to be deeply alarmed."
>— Jensen Huang, CEO of NVIDIA

Huang is not arguing that companies should spend more on AI so they can replace expensive employees. He is arguing that companies should spend more on AI so they can make expensive employees worth it. Without AI multiplying their output, a highly paid team is an underperforming asset.

Currently, the AI industry is pulled between two extremes. On one end, OpenClaw represents an AI system operating with minimal human intervention. On the other end, Human-in-the-loop (HITL) approaches, [popularized by practitioners like Lukas Biewald](https://www.computerworld.com/article/1632469/why-human-in-the-loop-computing-is-the-future-of-machine-learning.html), counterbalance this trajectory. HITL frames AI as a tool that accelerates work, but only within safe checkpoints of human judgment and correction.

Both positions miss what Huang, the P&G researchers, and the Berkeley team are converging on. The debate over control boundaries between a human and a model is secondary. The primary question is whether AI multiplies the value of the people you have already hired, across every function they touch.

In both the P\&G experiment and the Berkeley field study, AI's primary impact was not replacing workers or simply inserting oversight. AI systems provided intelligence across functional boundaries, enabling teams to produce more balanced, cross-disciplinary outcomes. Huang's $500,000 engineer becomes far more valuable when their AI usage benefits not just their own output, but every teammate and workflow connected to them.

So, the shift underway is not from chat interfaces to autonomous agents. It is from isolated productivity gains to improvements in organizational growth. This transition introduces the need for a new operating model for working with AI that we call Teams-in-the-Flow.

## Teams-in-the-flow: a new approach for AI-native organizations

The teams-in-the-flow approach embeds AI directly within shared workflows to connect groups of employees. We didn't invent this pattern; we discovered it by watching teams that were already succeeding with AI.

For example, [we observed that hospitality startup Wander](https://adapt.com/blog/customer-wander) used Adapt to help their teams make better decisions.

When a question arises during a Wander meeting or a strategy session, the team no longer has to park the discussion and wait for a data report. Instead, they simply tag Adapt directly in their Slack thread.

Adapt instantly queries the data models and returns charts and intelligent responses in 10 to 15 seconds. Business users can explore the data as a team alongside Adapt, drilling down into anomalies and asking follow-up questions together.

Adapt empowers every employee at Wander to make data-informed decisions while freeing data engineers to focus on infrastructure.

This same pattern happens [internally at Adapt](https://adapt.com/blog/ai-workflows). Recently, a marketer spotted a website issue, then used Adapt to fix a TypeScript build error, and automatically filed a Linear ticket with the research already done. An engineer watched the process unfold within a Slack channel and simply validated the approach with an emoji.

In this model, teammates with expertise did not become bottlenecks to shared work.

The question for startup leaders is no longer how to configure AI to act on its own and reduce headcount. It is whether your AI helps the whole team move together faster. This is what Adapt was built for.

## About Adapt

Adapt is the AI computer for business. It connects to all of your tools and data sources, orchestrates context across them, and powers clarity and action across the entire company.

Set it up once, and anyone in your company can tag @Adapt to get trusted answers and take action. Available in Slack and the Adapt app, and coming soon to wherever you work.
