### What is Combine?  

- Apple's [[Functional Reactive Programming|reactive programming]] framework  
- Helps manage **asynchronous and event-driven code**  
- Used for **chaining and composing data streams**  

> *Combine declares publishers to expose values that can change over time, and subscribers to receive those values from the publishers.*  

> *Combine helps track and respond to changes but **does not store state itself.***  
> `SwiftUI + Combine = State Management`  

🔗 **Official Docs:** [Apple Documentation](https://developer.apple.com/documentation/combine)  
🔗 **Notes:** [Introduction to Combine](https://heckj.github.io/swiftui-notes/) 

---

### Primary Features of Combine  

- [[Publishers]] → **Emits values over time**  
- [[Subscribers]] → **Receives and reacts to values**  
- [[Operators]] → **Middlemen that modify or filter data before passing it on** (e.g., converting numbers to strings, removing duplicates, combining multiple values)  
- [[Subjects]] → **Hybrid of Publisher & Subscriber** (acts as both a sender and receiver)  
- [[Schedulers]] → **Thread control** (controls where and when work happens)  
- [[Cancellable]] → **Memory management** (e.g., stops a subscription when no longer needed)  
- **Combine & SwiftUI**  
  → `@Published` to make a property **reactive**  
  → `ObservableObject` for [[MVVM]] **state management**  

---

### Reference Diagram  

![Combine Lifecycle](https://heckj.github.io/swiftui-notes/images/diagrams/combine_lifecycle_diagram.svg)  
