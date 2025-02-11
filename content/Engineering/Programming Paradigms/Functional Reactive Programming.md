
### What is Functional Reactive Programming?

- Also known as **data-flow programming**, builds on concepts of [[Functional Programming]]
- Is a combination of Functional Programming and Reactive Programming
- It allows you to react to data changes over time using **declarative, functional transformations**

Think of it like **a spreadsheet**:

- If **cell A** changes, **cell B (which depends on A)** updates automatically.
- You don’t need to manually update **cell B**—the relationship is **declared** and updates **reactively**.
- FRP works similarly: **data flows automatically based on dependencies.**

> _FRP allows us to express data flows over time using declarative, functional transformations._

🔗 **Further Reading:** [Wikipedia - Functional Reactive Programming](https://en.wikipedia.org/wiki/Functional_reactive_programming)

---

### Differences Between FRP and FP
| Feature              | Functional Programming (FP)                    | Functional Reactive Programming (FRP)     |
| -------------------- | ---------------------------------------------- | ----------------------------------------- |
| **Focus**            | Data transformation                            | Data flow over time                       |
| **Execution Model**  | Applies transformations on existing data       | Continuously reacts to new data           |
| **State Management** | Stateless, pure functions                      | Reactive streams manage state changes     |
| **Mutation**         | Avoids mutation, but still works on fixed data | Avoids mutation, and data is event-driven |

---

### Example

```swift
import Combine

// 1. Define a reactive stream for user input
let userInput = PassthroughSubject<String, Never>()

// 2. Apply functional transformations (functional part)
let validatedInput = userInput
    .filter { $0.count > 3 } // Only allow strings longer than 3 characters
    .map { $0.uppercased() } // Convert to uppercase

// 3. Subscribe to changes (reactive part)
let cancellable = validatedInput
    .sink { print("📢 Valid Input Received: \($0)") }

// 4. Simulate user typing (reactive updates)
userInput.send("Hi")    // No output (filtered out)
userInput.send("Hello") // Output: 📢 Valid Input Received: HELLO
userInput.send("Swift") // Output: 📢 Valid Input Received: SWIFT

```

**Why is this FRP?**  
✅ **Functional** → Uses `filter` and `map` to transform data.  
✅ **Reactive** → The subscriber automatically reacts to new values.  
✅ **Event-Driven** → The program reacts as input changes, instead of executing once.