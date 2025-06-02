# 🧠 `guardian-open`

*A minimal, open-source starter brain for local-first autonomous software systems.*

## Qdrant Memory
🧙🏼‍♂️ Use this 👉
```bash
curl -X PUT http://localhost:6333/collections/memories \
  -H "Content-Type: application/json" \
  -d '{
    "vectors": {
      "size": 1024,
      "distance": "Cosine"
    }
  }'
```

### Guardian CLI
🧙🏼‍♂️ Use this 👉
```bash
bun install -g ./services/guardian-cli
```

---

### 🚀 What is This?

`guardian-open` is the open-source foundation of my agentic infrastructure system — a **self-hosted AI automation engine** built with LLMs, memory, pipelines, and real-time tooling. It’s designed to help developers:

* Automate reasoning and task handling with `runLLM`
* Store and retrieve memory with Qdrant + Supabase
* Trigger actions via code, CLI, or agents
* Build upon real infrastructure — not toy examples

---

### 🛠️ What’s Included

| Feature             | Description                                                                                  |
| ------------------- | -------------------------------------------------------------------------------------------- |
| `runLLM.ts`         | Flexible LLM interface (local or API) using Ollama or Gemini                                 |
| `addMemory.ts`      | Semantic memory logging via Qdrant + Supabase                                                |
| `embed.ts`          | Embedding utility for text/vector conversion                                                 |
| `logSystemEvent.ts` | Event logging and trace utility                                                              |
| `clients.ts`        | Pre-wired HTTP clients for Notion, Slack, n8n, Supabase, WordPress, Home Assistant, and more |
| `guardian-cli`      | WIP CLI for local automation                                                                 |
| `ollama-proxy`      | Optional inference layer for model + memory injection                                        |
| `codegen-worker`    | Experimental microservice for code generation pipelines                                      |

---

### 📦 Install Dependencies

Run this to get started:

```bash
pnpm add axios ollama @qdrant/js-client-rest js-base64 @google/genai @notionhq/client postgres @supabase/supabase-js drizzle-orm
```

> Or use `npm` instead of `pnpm` if needed.

---

### 📁 Project Structure

```
guardian-open/
├── config/              # Shared client configs (LLMs, APIs, DB)
├── services/            # Optional local tools (CLI, codegen, LLM proxy)
├── src/
│   └── lib/             # Core memory and automation utilities
│       ├── addMemory.ts
│       ├── embed.ts
│       ├── runLLM.ts
│       ├── logSystemEvent.ts
│       └── withHandler.ts
├── scripts/             # Bash scripts for setup, seeding, testing (coming soon)
├── .env.example         # Reference for your environment variables
├── README.md            # You're here
```

---

### 🧪 Example Usage

```ts
import { runLLM, addMemory } from "./src/lib";
import { qdrantClient } from "./config/clients";

await addMemory({
  content: "Shipped Guardian Open v1.0",
  type: "Reflection",
  tags: ["release", "guardian"],
});

const result = await runLLM("Summarize the core memory system design");
console.log(result);
```

---

### 🔐 Required `.env` Keys

Create a `.env` file using `.env.example` and include:

```env
NOTION_API_KEY=
GOOGLE_GENAI_KEY=
N8N_API_KEY=
N8N_BASE_URL=http://localhost:5678/api/v1
SLACK_BOT_TOKEN=
WORDPRESS_BASIC=base64encoded
WORDPRESS_HOSTNAME=https://yourwordpress.com/wp-json/wp/v2
HOME_ASSISTANT_ACCESS_TOKEN=
SUPABASE_URL=
SUPABASE_SERVICE_ROLE=
DATABASE_URL=postgres://...
```

---

### 📚 Tutorials & Documentation

All tutorials for this repo live on my blog:
👉 [The Guardian Tutorial Series](https://blog.woodwardwebdev.com/the-guardian-tutorial-series)

You’ll find step-by-step guides for:

* Setting up Supabase, Qdrant, and Ollama
* Building the MemoryManager
* Running BlogGen, CodeGen, and TestGen pipelines
* Hooking into Notion, Slack, WordPress, and more

---

### 🔧 Scripts (Coming Soon)

Inside `/scripts/`:

* `dev.sh` → Starts local services (Qdrant, Supabase, etc.)
* `seed.ts` → Populates sample memory + test data
* `bootstrap.sh` → One-liner to install, run, and test everything

---
Absolutely — here’s a polished `Included Services` section you can paste directly into your root `README.md`:

---

### 🧱 Included Services

This project is a bundled OSS release of the core Guardian system — a modular, local-first AI infrastructure stack. It includes four key services, each designed to run independently or as part of a unified agentic automation engine.

| Service                                          | Description                                                                                                                                                                                 |
| ------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 🧠 [`guardian-open`](./src)                      | The main backend server. Handles memory creation, LLM routing, metadata storage, and API orchestration using Bun + Hono + Supabase + Qdrant.                                                |
| ✍️ [`codegen-worker`](./services/codegen-worker) | A task-triggered microservice that receives input (like feature prompts or TDD test plans), generates production-ready code using LLMs, and returns structured output.                      |
| 🔁 [`ollama-proxy`](./services/ollama-proxy)     | A smart router for LLM requests. Wraps Ollama calls with memory context, schema formats, and model selection logic. Designed to give your system LLM superpowers with centralized control.  |
| 🛠️ [`guardian-cli`](./services/guardian-cli)    | A local-first CLI to interact with the Guardian server and trigger workflows like ingesting files, running blog or codegen pipelines, and managing memory. Lightweight and script-friendly. |

> Each service runs independently and can be used standalone or together as a foundation for agentic automation workflows.

---

### 🧩 Coming Soon

* [ ] Guardian CLI installable via `pnpm dlx`
* [ ] Memory ingestion loop
* [ ] UI walkthrough via blog
* [ ] Minimal `AgentFlow` support
* [ ] Full tutorial map

---

### 💬 Need Help?

* Reach out via [X / Twitter](https://x.com/LoveLiiiveLaugh)
* Open an issue or feature request
* Want to hire me to set this up for your business? [Work with me](https://blog.woodwardwebdev.com/services)

---

### 🧙‍♂️ Author

Built by [Michael Woodward](https://blog.woodwardwebdev.com)
I build sovereign AI infrastructure using local-first tools and agentic pipelines.
This repo is part of the Guardian AI ecosystem.

---

Let me know if you'd like a `logo.svg`, social banner, or deployment badge added next!
