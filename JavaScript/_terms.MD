| Short Form | Long Form | Definition |
| --- | --- | --- |
| SPR | Single Responsibility Principle | The single-responsibility principle (SRP) is a computer programming principle that states that "A module should be responsible to one, and only one, actor." |
| DI | Granular Dependency Injection | Why Granular Dependency Injection is Good: <ul><li> Explicitness: Each function clearly states what it depends on.</li> <li> Reduced Coupling: Modules don't become overly dependent on each other.</li> <li> Testability: As we've seen, testing is greatly improved.</li> <li> Maintainability: Code is easier to change and refactor.</li> </ul> The principle of granular dependency injection says, "Only pass what's explicitly needed."|
| --- | Reduced API Surface Area | <ul><li> A module's API surface area is the set of things it exposes to the outside world (the exported functions, constants, etc.).</li> <li>A smaller API surface area is generally better because it:<ul><li>Makes the module easier to understand (less to learn about).</li><li>Reduces the risk of accidental misuse (fewer things to call incorrectly).</li><li>Makes it easier to refactor the module's internals (you have fewer external dependencies to worry about).</li></ul></li> </ul> |
| --- | Mock Dependency | <ul><li>A mock dependency is a stand-in for a real dependency that you use during testing.</li><li>It's a fake or simulated version of the real thing.</li><li>It's designed to:<ul><li>Isolate the module you're testing. </li><li>Make tests more predictable.</li></li>Simplify the setup of tests.</ul></li></ul> |
| IoC | Inversion of Control | This is the core principle of IoC. interactionManager doesn't control how these dependencies are created or configured; that's the responsibility of the code that's using it. |
| --- | pure function | One whose output depends only on its inputs, not on any external state. This makes the function more reusable and much easier to test in isolation. |


More Design Patterns: There are many other design patterns besides dependency injection that can be helpful. Explore things like the:
* Factory pattern
* Observer pattern
* Strategy pattern
* Singleton pattern (use with care!)
