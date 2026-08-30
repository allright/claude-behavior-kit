# Code Style

## Principles

### KISS (Keep It Simple, Stupid)
- Write simple, readable code
- Avoid premature optimization
- Don't add "just in case" functionality
- If solution seems complex — find a simpler one

### DRY (Don't Repeat Yourself)
- Don't duplicate code — extract to functions/modules
- Single source of truth for data and configs
- But: 3 lines of copy-paste is better than unnecessary abstraction

### YAGNI (You Aren't Gonna Need It)
- Don't write code you don't need right now
- Delete dead code without regrets
- Don't create "universal" solutions for single use case

## SOLID

### S — Single Responsibility
- One class/function = one task
- If description requires "and" — split it

### O — Open/Closed
- Open for extension, closed for modification
- Use composition and interfaces

### L — Liskov Substitution
- Subclasses must be interchangeable with parent
- Don't violate base class contract

### I — Interface Segregation
- Many small interfaces better than one large
- Client shouldn't depend on methods it doesn't use

### D — Dependency Inversion
- Depend on abstractions, not implementations
- Inject dependencies, don't create inside

## Code Rules

### Naming
- Names should explain intent
- Functions are verbs: `getUserById`, `calculateTotal`
- Booleans are questions: `isValid`, `hasPermission`, `canEdit`
- Constants in UPPER_SNAKE_CASE

### Functions
- Do one thing
- No more than 3-4 parameters (otherwise use object)
- Return early: guard clauses instead of nested ifs
- No side effects unless obvious from name

### Comments
- Code should be self-documenting
- Comments explain "why", not "what"
- Don't comment the obvious — `sm.resetPeerConnection()` does NOT need `// Reset our connection`
- Never restate function/method names: `// Send answer to remote peer` above `sendAnswerMessage()` is noise
- JSDoc on methods only if it adds info beyond the signature
- Class-level JSDoc describing purpose/strategy — keep, it's architecture docs
- TODO only with context and reason

### Error Handling
- Fail fast — fail early with clear message
- Don't swallow errors silently
- Validate at system boundaries (input, API)
- Inside system — trust your code

### Structure
- Imports grouped: stdlib, external, internal
- Public methods above private
- Related code together
- File no longer than 300-400 lines (signal to split)
