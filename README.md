# Prompt-Sourced Development (PSD)

**A paradigm where prompts replace source code as the primary artifact.**

We've spent decades writing source code. Now we can prompt-source software instead.

## The idea

What if the prompt *is* the product?

Prompt-Sourced Development (PSD) is a software development paradigm where the prompt — not the generated code — is the primary artifact that is maintained, versioned, shared, and customized.

Generated code becomes disposable output. It can be regenerated at any time from the prompt and its context.

Instead of distributing applications, you distribute intent. Instead of modifying code, you modify the prompt and regenerate.

## Origin

I built a QA agent using a few prompts. The output was a folder structure, text files, and a Python file.

When I needed to deploy it to a different project, I realized something:

Modifying the prompt and regenerating the entire agent was faster, safer, and more consistent than modifying the generated code.

The prompt had become the source.

That's when it clicked: the prompt is not an ephemeral input. It is the durable artifact you carry forward, version, and share.

## Why this matters

When customization is extensive — when a large portion of an implementation needs to change for a new context — regenerating from a modified prompt beats modifying generated code:

- **Prompt modification scales linearly.** Changing a few sentences to retarget an agent from Python to TypeScript takes minutes.
- **Code modification scales unpredictably.** Making equivalent changes across generated files takes hours and risks inconsistency.
- **The prompt is a more accessible modification surface.** A tech lead who knows their project can modify a prompt. Reverse-engineering someone else's generated code requires implementation expertise.

## Key concepts

### SpecPrompt

The core artifact in PSD: a structured prompt, optionally accompanied by supporting context, designed to generate a complete and customized implementation when processed by an AI coding agent.

A SpecPrompt package has a layered structure:

| Layer | Contents | Required |
|-------|----------|----------|
| **Core prompt** | Purpose, user stories, key behaviors | Yes |
| **Context documents** | APIs, schemas, data models, business rules, design references | Optional |
| **Validation layer** | Acceptance criteria, tests for generated output | Optional |
| **Generation guide** | Architecture hints, tech stack preferences, constraints | Optional |

For simple tools, only the core prompt is needed. For complex systems, additional layers increase reliability and control.

These layers are swappable. The same core intent can be reused across different stacks, domains, or environments.

### The PSD stack

```
Prompt-Sourced Development (paradigm)
    SpecPrompt (artifact)
        Context Documents (knowledge layer)
            LLM / AI Agent (runtime)
```

## How PSD differs from Specification-Driven Development

PSD builds on ideas from SDD but makes a fundamentally different claim:

| | SDD | PSD |
|---|---|---|
| **Primary artifact** | Specification governs code | Prompt *replaces* code as what you carry forward |
| **Modification approach** | Edit spec, then update code | Edit prompt, regenerate code |
| **Scope** | Internal project alignment | Portable across projects and teams |
| **Distribution** | Share the codebase | Share the SpecPrompt |

SDD says: the spec is the source of truth.
PSD says: the prompt is the source.

## Feasibility

PSD already works across a meaningful range of applications, and its ceiling is rising quickly.

**Works well today:**

- Single-purpose tools
- CLI utilities
- CRUD apps
- Dashboards
- Data transformers
- Static sites

**Works with iteration:**

- Multi-page apps with authentication
- Simple API backends
- Multi-feature tools

**Emerging:**

- Complex multi-component applications. Improving rapidly as context windows grow, tool use matures, and multi-agent orchestration develops.

PSD does not require perfect one-shot generation. A SpecPrompt can include validation criteria and tests, enabling an iterative loop:

generate → validate → refine → regenerate

## The discipline

Every regeneration discards manual improvements made to generated code.

Those improvements must be fed back into the SpecPrompt.

This is intentional.

The SpecPrompt becomes a living artifact that accumulates operational knowledge and improves over time.

## When to prompt-source

PSD is not for everything. The decision point is the **customization ratio**:

- **Low customization** (minor changes) — just modify the code directly.
- **High customization** (large portions of the implementation change for a different context) — modify the prompt and regenerate. This is where PSD wins.

The sweet spot is tools and agents that are structurally transferable but deeply context-specific: the *shape* of the solution is reusable, but the *details* change with every deployment.

## Contributing

This is an evolving concept. If you're experimenting with prompt-sourced approaches, open an issue or start a discussion.

## Author

**Pekka Martikainen** — March 2026

## License

This work is licensed under [CC BY 4.0](LICENSE).
