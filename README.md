# LLM Cookbook

An interactive reference of end-to-end LLM recipes — prompting techniques, fine-tuning
methods, agent patterns, evaluation strategies, and deployment/inference tricks — in the
same browsable "cookbook" format as the RAG cookbook this was based on.

Each recipe includes:
- A clickable pipeline of steps with expandable detail
- A runnable code sample (JS/TS using the Anthropic SDK, or Python for training/inference recipes)
- Difficulty rating, estimated time, and tags
- Search and category filtering in the sidebar

## Categories

- **Prompting** — zero-shot, few-shot, chain-of-thought, tree-of-thought, ReAct, self-consistency, prompt chaining, least-to-most
- **Fine-Tuning** — SFT, LoRA, QLoRA, RLHF, DPO, instruction tuning
- **Agents** — tool-calling agents, plan-and-execute, reflexion, multi-agent orchestration
- **Evaluation** — LLM-as-a-judge, perplexity, human preference (Elo), red-teaming
- **Deployment** — KV-cache, speculative decoding, quantization, prompt caching, streaming

## Getting started

```bash
npm install
npm run dev
```

Then open the printed local URL (usually `http://localhost:5173`).

## Build for production

```bash
npm run build
npm run preview
```

## Project structure

```
llm-cookbook/
├── index.html
├── package.json
├── vite.config.js
├── src/
│   ├── main.jsx       # React entry point
│   ├── App.jsx         # All recipe data + UI components
│   └── index.css       # Design tokens (colors, fonts) + global styles
└── README.md
```

## Customizing

All recipe content lives in the `RECIPES` array at the top of `src/App.jsx`. Each entry
follows this shape:

```js
{
  id: "unique-id",
  category: "Prompting", // must match an entry in CATEGORIES
  title: "Recipe Title",
  difficulty: "Beginner" | "Intermediate" | "Advanced" | "Expert",
  time: "~20 min",
  description: "One or two sentence summary.",
  tags: ["tag1", "tag2"],
  steps: [
    { label: "Step Name", icon: "🎯", detail: "What happens in this step." },
    // ...
  ],
  code: `// runnable example`,
  concept: "optional markdown string for a deeper-dive tab",
}
```

Add a new category by appending it to the `CATEGORIES` array near the bottom of `App.jsx`.
