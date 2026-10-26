name: xunit-test-writer
version: 1.0.0
description: >
  Write high-quality xUnit tests for .NET 8+ projects. Produces test classes using
  [Fact]/[Theory], AAA style, clear naming, and .NET-friendly patterns. Can scaffold
  a test project (xUnit v2 by default) or work within an existing solution.
author: You
tags: [dotnet, csharp, xunit, testing, tdd]
activation:
  hints:
    - "write xunit tests"
    - "create unit tests for .NET"
    - "convert requirements into xunit tests"
    - "add tests for this class/method"
  files:
    - "*.cs"
goals:
  - Generate or update xUnit tests targeting .NET 8+.
  - Use AAA pattern, meaningful test names, and small focused assertions.
  - Prefer [Theory]/[InlineData] when inputs vary; use [Fact] for single cases.
  - Provide clear instructions to run tests via `dotnet test`.
inputs:
  required:
    - Code under test (paste or path)
  optional:
    - Test framework version: "xunit-v2" (default) or "xunit-v3"
    - Project layout: paths to src and tests folders
    - Constraints: mocking library preference (e.g., Moq/NSubstitute), coverage goals, etc.
outputs:
  - One or more C# test files ready to compile.
  - If needed, `.csproj` snippet and CLI steps.
---

# Operating guide (for the model)

1) **Detect context**
- If the user supplies code or a repo path, identify public APIs to test.
- Confirm target: `.NET 8` (or higher). Use `net8.0` TFM unless told otherwise.
- If the user says "xunit-v3", generate tests compatible with xUnit v3 templates; otherwise use v2.

2) **If no test project exists (xUnit v2 default)**
- Propose creating a new test project with the CLI:
  - `dotnet new xunit -o <ProjectName>.Tests`
  - Add reference to the SUT project:
    `dotnet add <ProjectName>.Tests/<ProjectName>.Tests.csproj reference <ProjectName>/<ProjectName>.csproj`
- Mention that the template brings in:
  `Microsoft.NET.Test.Sdk`, `xunit`, `xunit.runner.visualstudio`, and `coverlet.collector`.
- Provide a minimal `.csproj` snippet with `<TargetFramework>net8.0</TargetFramework>`.

3) **If user prefers xUnit v3**
- Ask if templates are installed. If not, advise: `dotnet new install xunit.v3.templates`
- Mention `xunit3` test project template and that xUnit v3 supports .NET 8+.

4) **Authoring tests**
- Use AAA: Arrange, Act, Assert; keep one logical assertion per test.
- Naming: `MethodName_ShouldExpectedBehavior_WhenCondition`.
- Use `[Theory]` with `[InlineData]` for parameterized tests.

5) **Output**
- Provide complete test class code with necessary `using` directives. 
- If scaffolding a new project, include CLI commands and `.csproj` snippet.
- If working within an existing solution, just provide the test class code.
- Include instructions to run tests: `dotnet test` from the solution or test project directory

6) **Mocking and Isolation**
- Consider using Moq or NSubstitute alongside XUnit
- Mock dependencies to isolate units under test
- Use interfaces to facilitate mocking
- Consider using a DI container for complex test setups

7) **Test organisation**
- Group tests by feature or component
- Use [Trait("Category", "CategoryName")] for categorization
- Use collection fixtures to group tests with shared dependencies
- Consider output helpers (ITestOutputHelper) for test diagnostics
- Skip tests conditionally with Skip = "reason" in fact/theory attributes

8) **Standard tests**
- Keep tests focused on a single behavior
- Avoid testing multiple behaviors in one test method
- Use clear assertions that express intent
- Include only the assertions needed to verify the test case
- Make tests independent and idempotent (can run in any order)
- Avoid test interdependencies