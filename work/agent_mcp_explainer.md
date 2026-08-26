# What Is an Agent? What Is MCP?

## Workflow vs Agent: The Core Difference

A workflow is a fixed sequence of steps. You design the path, and the AI follows it. You control every decision: first do this, then do that, then stop. No deviation. The AI is a tool that executes your plan.

An agent is different. The AI decides what to do next based on what it sees. It can use tools, change course, and keep going until it decides the task is done. The AI is in the driver's seat — it reasons, acts, and adapts.

**Simple analogy:** A workflow is like a recipe. You follow the steps in order, and you get the same result every time. An agent is like a chef. They know how to cook, but they decide what to make, what ingredients to use, and how to adjust based on what's available.

| Workflow | Agent |
|----------|-------|
| You write the script | The AI figures out the steps |
| Same steps every time | Adapts based on results |
| Predictable output | Flexible output |
| You're in the driver's seat | The AI is in the driver's seat |

## My FL-04 Pipeline: A Workflow

My FL-04 pipeline (Job Application Workflow) is clearly a **workflow**. I defined every step:

- **STEP 1: GATHER** — Extract job requirements from a job description
- **STEP 2: SYNTHESIZE** — Match my FlyRank experience to the requirements
- **STEP 3: DRAFT** — Write a cover letter using the matched skills
- **STEP 4: REVIEW** — Cross-check tone, specificity, and voice

The AI does exactly what I tell it, in the order I told it. It doesn't decide to skip the review step or go back and gather more data. It doesn't choose to research the company independently or look for additional sources. Those are decisions I made upfront.

This is fine — for a job application workflow, you want predictability. You don't want the AI deciding to write a poem instead of a cover letter. Workflows are useful when you know exactly what you want and the path is clear.

## What Is MCP?

MCP stands for **Model Context Protocol**. It's a standard way for AI systems to connect to external tools — like reading files, querying databases, or searching the web.

Think of it like a **USB-C port for AI apps**. One standard connector that works with many tools. Before MCP, every AI tool required custom integrations. You'd have to write separate code for Claude to read a file, and different code for ChatGPT to do the same. MCP solves this by creating one standard that everyone can use.

## The Three Primitives of MCP

MCP has three main building blocks:

**1. Tools**
Tools are actions the AI can perform. Examples:
- `read_file()` — read the contents of a file
- `write_file()` — write to a file
- `search_web()` — search the internet
- `query_database()` — run a SQL query

Tools are how an agent actually changes the world. Without tools, an agent can only think. With tools, it can act.

**2. Resources**
Resources are data the AI can access. Examples:
- Documents (PDFs, Word files, Markdown)
- Database records
- API responses
- Local files

Resources are like a library the AI can read from. They provide context that the AI wouldn't otherwise have.

**3. Prompts**
Prompts are reusable instructions you write once and use many times. Examples:
- "Write a cover letter using this structure..."
- "Review this document for tone and clarity..."
- "Extract key information from this job description..."

Prompts are like templates that save you from rewriting the same instructions over and over.

## How They Work Together

An agent uses **tools** to take actions, reads **resources** for context, and follows **prompts** for guidance. The agent decides when to use each primitive based on what it's trying to achieve.

For example:
1. The agent reads a job description (**resource**)
2. It matches the requirements to my experience (**prompt**)
3. It writes a cover letter (**tool** — writing to a file)
4. It reviews the letter and suggests changes (**tool** — reading and comparing)

## What My FL-04 Pipeline Would Need to Become an Agent

To turn my Job Application Workflow into a true agent, I would need:

**1. Autonomy**
The AI would decide which companies to research based on my preferences. It would choose when to stop gathering data and when to start writing.

**2. Tool Use (via MCP)**
The AI would:
- Read job descriptions from local files using `read_file()`
- Search the web for company info using `search_web()`
- Write cover letters directly to files using `write_file()`

**3. Feedback Loops**
The agent would check if the cover letter is complete, ask if I want changes, and revise based on my feedback. It would learn from my preferences over time.

**4. Decision Points**
The agent would decide:
- Is this job description complete enough to proceed?
- Should I gather more company info before writing?
- Is the cover letter good enough to save, or should I revise?

## What I Learned

The biggest lesson is that workflows are useful when you know exactly what you want. Agents are useful when you don't — when the path is unclear and you need the AI to explore and adapt.

Most people should start with workflows. They're predictable, controllable, and easy to debug. Only move to agents when you truly need autonomy — when the task is complex enough that you can't predefine every step.

MCP is the key that makes agents practical. Without MCP, an agent is just a chat with opinions. With MCP, it can actually do things.

---

## Summary

| Concept | Definition | My FL-04 Pipeline |
|---------|------------|-------------------|
| **Workflow** | Fixed sequence of steps, predefined by the user | ✅ Yes — GATHER → SYNTHESIZE → DRAFT → REVIEW |
| **Agent** | AI decides steps, uses tools, adapts based on results | ❌ No — I control every step |
| **MCP** | Standard protocol for AI to connect to external tools | ⬜ Would need tools like `read_file()` and `search_web()` |

**Concrete agent upgrade for my pipeline:** Add MCP tools so the agent can read job descriptions from my local files, search the web for company information, and write cover letters directly to my folder — all without me manually pasting text.
