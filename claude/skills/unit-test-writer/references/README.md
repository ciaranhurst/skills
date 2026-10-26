# References — xunit-test-writer

Curated, authoritative links the skill can cite when scaffolding or explaining xUnit tests for .NET 8+.

---

## Core Docs

- **Microsoft Learn — Unit testing C# in .NET using `dotnet test` and xUnit**  
  Official end‑to‑end tutorial that shows the CLI workflow, the `dotnet new xunit` template, included packages, and how to run tests.  
  https://learn.microsoft.com/en-us/dotnet/core/testing/unit-testing-csharp-with-xunit

- **xUnit.net — Home (v3 supports .NET 8+)**  
  Project homepage with release notes, platform support, runners, and quick start for the .NET SDK.  
  https://xunit.net/

- **xUnit.net — Getting Started with xUnit v3**  
  How to install the v3 project templates (`xunit.v3.templates`) and create a test project with `dotnet new xunit3`.  
  https://xunit.net/docs/getting-started/v3/getting-started

---

## Quick CLI Snippets (for copy/paste)

> **xUnit v2 (default .NET template)** — creates a test project targeting `net8.0`, adds SUT reference, runs tests:
```bash
dotnet new xunit -o MyProject.Tests
dotnet add MyProject.Tests/MyProject.Tests.csproj reference src/MyProject/MyProject.csproj
dotnet test
```
These commands and the default package set (`Microsoft.NET.Test.Sdk`, `xunit`, `xunit.runner.visualstudio`, `coverlet.collector`) mirror Microsoft’s official tutorial.

> **xUnit v3 (optional)** — install templates, create project, run tests:
```bash
dotnet new install xunit.v3.templates
dotnet new xunit3 -o MyProject.Tests
dotnet test
```
xUnit v3 explicitly supports .NET 8+ and ships its own templates.

---

## Anthropic Skills (for Claude Code)

- **Public Skills repo (spec + examples)** — folder structure with `SKILL.md` plus optional `references/`, `assets/`, and `scripts/`.  
  https://github.com/anthropics/skills

- **Skill Creator plugin** — create/evaluate/iterate skills directly in Claude Code.  
  https://claude.com/plugins/skill-creator

---

## Notes

- Prefer **`net8.0`** as the target framework unless your solution dictates otherwise; both xUnit v2 and v3 run fine on .NET 8.
- If you need the v3 project experience (new templates, in‑process runner, etc.), install the **xUnit v3 templates** first.
