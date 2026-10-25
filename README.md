# Unified AI Agent Skills

A curated library of plug-and-play AI agent skills, compiling multi-source references into single, installable `SKILL.md` files.

## Overview

When configuring AI agents, providing them with the right context often involves juggling multiple instruction files, reference documents, and rule sets. This repository solves that problem by **synthesizing scattered knowledge into unified, single-file deployments.** 

We take complex skill sets—along with their necessary guidelines, edge cases, and reference data—and merge them into a single `SKILL.md` file. This makes it incredibly easy to copy, paste, and install new capabilities directly into any AI agent's system prompt or knowledge base.

## Features

* **Plug-and-Play Integration:** No need to manage complex file structures. Every skill is self-contained.
* **Contextually Rich:** Each `SKILL.md` includes not just instructions, but all the necessary reference material merged into one place.
* **Agent Agnostic:** Designed to be universally understood by modern LLMs and agent frameworks (OpenAI, Anthropic, LangChain, AutoGen, etc.).
* **Modular Design:** Add or remove skills from your agent without worrying about breaking interdependent context.

## How It Works

Instead of feeding your agent a folder full of scattered text files (e.g., `coding_rules.txt`, `api_reference.md`, `examples.json`), this repository provides a compiled version. 

**The Anatomy of a `SKILL.md`:**
1. **System Role/Objective:** The core behavior the agent needs to adopt.
2. **Execution Rules:** Step-by-step logic for the skill.
3. **Reference Material:** Embedded documentation, API schemas, or examples required to execute the skill successfully.
4. **Constraints & Guardrails:** What the agent *should not* do.

## How to Use

1. **Browse the Library:** Navigate to the `/skills` directory to find the capability you want your agent to learn.
2. **Select a Skill:** Open the folder for your desired skill (e.g., `/skills/python-data-analyst`).
3. **Install:** Open the `SKILL.md` file, copy its entire contents, and paste it into your agent's system instructions, custom prompt, or designated knowledge file.

## Repository Structure

```text
├── skills/
│   ├── api-integrator/
│   │   └── SKILL.md       # The compiled, single-file skill
│   ├── creative-writer/
│   │   └── SKILL.md
│   └── code-reviewer/
│       └── SKILL.md
├── CONTRIBUTING.md
└── README.md
```

## Contributing

Have a custom skill you've built that requires multiple references? We'd love to see it synthesized! 

1. Fork the repository.
2. Create a new folder under `/skills/your-skill-name`.
3. Draft your unified `SKILL.md` following the standard format.
4. Submit a Pull Request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
