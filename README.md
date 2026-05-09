# Building AI Teams: Multi-Agent Systems with Gemini

> A 45-minute hands-on workshop for **[Build with AI by GDG Gurugram](https://www.linkedin.com/company/gdggurugram)** — May 9, 2026

Build a working **4-agent AI team** in Google Colab using Gemini 2.5 Flash. The agents plan, research the live web, draft, **and argue with each other until the work is good enough**. Wrap it in a public web app at the end. No frameworks, no magic — just Python and a real mental model for how multi-agent systems work.

## What you'll build

```
   topic
     │
     ▼
   Planner ──→ 3 questions
     │
     ▼
   Researcher (×3) ──→ research findings + sources
     │            (uses Gemini's Google Search grounding)
     ▼
   Writer ──→ draft v1
     │
     ▼
   Critic ──→ approved? ──→ YES → done
     │             │
     │             └── NO → feedback ──→ Writer rewrites
     │                                       │
     │                                       └─→ back to Critic (max 3 rounds)
     ▼
  final report → wrapped in Gradio → public URL you can share
```

- **Planner agent** — decomposes a topic into 3 specific research questions
- **Researcher agent** — uses Gemini's built-in Google Search grounding to answer each question with live web data
- **Writer agent** — drafts a structured report from the research
- **Critic agent** — reviews the draft, sends it back with feedback if not good enough (the **reflection loop** — the most important pattern in production agentic AI)
- **Orchestrator** — wires everything together with the loop logic
- **Gradio wrap-up** — turns the whole thing into a shareable web app with a public URL

By the end, you'll have a working AI tool with your own URL you can send to anyone.

## Quick start

1. Open the notebook: **[multi_agent_workshop.ipynb](./multi_agent_workshop.ipynb)** ([open in Colab](https://colab.research.google.com/github/YOUR_USERNAME/YOUR_REPO/blob/main/multi_agent_workshop.ipynb))
2. Click **File → Save a copy in Drive**
3. Get a free Gemini API key at [aistudio.google.com/apikey](https://aistudio.google.com/apikey)
4. Add it as a Colab secret named `GEMINI_API_KEY`
5. Run the cells top to bottom — **fill in the `# TODO` system prompts as you go**

The whole notebook works on the **free tier**. No credit card, no Cloud project required.

## What makes this workshop different

You're not copying code from slides. The boilerplate, the agent function bodies, and the orchestrator are all pre-written. **The system prompts are blank and you write them.** That means:

- your agents behave differently from the person sitting next to you
- you actually learn prompt design, which is the real agentic AI skill
- when something doesn't work, you debug *your* prompt — that's the actual learning

By the end you'll know not just what a multi-agent system *is*, but how to design and tune one.

## Stack

| Layer | Tool | Why |
|---|---|---|
| Model | `gemini-2.5-flash` | Fast, free tier, supports Google Search grounding |
| SDK | `google-genai` (v1.x) | The new unified Gemini SDK; pinned to v1 for Colab compatibility |
| Runtime | Google Colab | Zero local setup, same env for everyone |
| Web search | Built-in `google_search` tool | Native Gemini grounding, no scraping |
| Web app | Gradio | 3 lines of code → public URL |

## Why no framework?

The workshop deliberately uses **raw Python + the Gemini SDK**. No LangChain, CrewAI, or AutoGen.

This is a teaching choice. Once you understand that an agent is just **an LLM call with a focused system prompt and an input/output contract**, the frameworks become optional. You can read their source and know what they're doing.

If you want to graduate to a framework later, look at [Google's Agent Development Kit (ADK)](https://google.github.io/adk-docs/) or [LangGraph](https://langchain-ai.github.io/langgraph/) — both give you orchestration, state, and tracing on top of the same patterns you'll learn here.

## Workshop structure (45 min)

| Time | Section | What happens |
|---|---|---|
| 0–5 | Hook + finished demo | Trainer shows the full team running on a live topic |
| 5–12 | Setup | Everyone gets API key + hello-world working |
| 12–20 | Build Planner | Concept on slide → write your own system prompt → run |
| 20–28 | Build Researcher | Add Google Search grounding (the wow moment) |
| 28–34 | Build Writer | Draft generation with feedback support baked in |
| 34–42 | Build Critic + Orchestrator | The reflection loop — agents argue and improve |
| 42–47 | Wrap in Gradio | Get a public URL, share it with someone right now |
| 47–50 | Q&A | |

## After the workshop

- **Add a 5th agent** — e.g., a fact-checker that runs after the Critic approves
- **Add memory** — persist research to a JSON file or vector DB
- **Add more tools** — `types.Tool(url_context=types.UrlContext())` lets the Researcher read specific pages
- **Deploy permanently** — Hugging Face Spaces, Render, Cloud Run. All free tier.
- **Swap models** — try Gemini 2.5 Pro for the Writer and see how the output changes

## License

MIT. Take it, fork it, teach it, ship it.

## About

Built for **Build with AI by [GDG Gurugram](https://www.linkedin.com/company/gdggurugram)** by **Jatin**.

If you build something cool with this, tag me — I want to see it:
- Instagram: [@heyjatinnn](https://instagram.com/heyjatinnn)
- YouTube: [@heyjatinnn](https://youtube.com/@heyjatinnn)
- LinkedIn: [@heyjatinnn](https://linkedin.com/in/heyjatinnn)

Tag your build with **#BuildWithAI** and **@gdggurugram** so the community sees it.
