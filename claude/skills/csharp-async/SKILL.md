---
name: csharp-async
description: Describe what this skill does and when to use it. Include keywords that help agents identify relevant tasks.
---
Define the functionality provided by this skill, including detailed instructions and examples

1) **Naming Conventions**
- Use clear and descriptive names for methods, variables, and classes to enhance readability.
- Follow C# naming conventions (e.g., PascalCase for methods and classes, camelCase for variables).
- Use the 'Async' suffix for all async methods
- Match method names with their synchronous counterparts when applicable (e.g., GetDataAsync() for GetData())

2) **Return Types**
- Return Task<T> when the method returns a value
- Return Task when the method doesn't return a value
- Consider ValueTask<T> for high-performance scenarios to reduce allocations
- Avoid returning void for async methods except for event handlers

3) **Exception Handling**
- Use try-catch blocks to handle exceptions in async methods  
- Use try/catch blocks around await expressions
- Avoid swallowing exceptions in async methods
- Use ConfigureAwait(false) when appropriate to prevent deadlocks in library code
- Propagate exceptions with Task.FromException() instead of throwing in async Task returning methods

4) **Performance**
- Use Task.WhenAll() for parallel execution of multiple tasks
- Use Task.WhenAny() for implementing timeouts or taking the first completed task
- Avoid unnecessary async/await when simply passing through task results
- Consider cancellation tokens for long-running operations

5) **Pitfalls**
- Never use .Wait(), .Result, or .GetAwaiter().GetResult() in async code
- Avoid mixing blocking and async code
- Don't create async void methods (except for event handlers)
- Always await Task-returning methods

6) **Best Practices**
- Use async/await for I/O-bound operations to improve responsiveness
- Use async/await for CPU-bound operations to offload work to background threads
- Use ConfigureAwait(false) in library code to avoid capturing the synchronization context
- Implement the async command pattern for long-running operations
- Use async streams (IAsyncEnumerable) for processing sequences asynchronously
- Consider the task-based asynchronous pattern (TAP) for public APIs