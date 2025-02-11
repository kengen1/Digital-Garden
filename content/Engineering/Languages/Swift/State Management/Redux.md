### What is Redux?  

- Redux is a **[[state|State]] management pattern** that helps manage application state in a **predictable, centralised, and immutable** way.  
- It’s commonly used in **front-end frameworks like React**, but it can also be applied in **Swift applications** using Combine.

Think of Redux like **a central control system**:
- There is **one source of truth** (a single state store).  
- The **only way to change state is through actions** (controlled updates).  
- The **state updates predictably** based on dispatched actions.  

> *Redux helps manage global state changes in a predictable way by enforcing a unidirectional data flow.*  

🔗 **Further Reading:** [Redux Docs](https://redux.js.org/)  

---

### How is Combine Used with Redux in Swift?
- Combine enhances Redux in Swift by making state updates reactive 
- Instead of manually updating UI when state changes, Combine automatically propagates changes to subscribers, ensuring that views stay in sync with the state 

*How Redux and Combine Work Together*
1️⃣ State is stored in a single `@Published` property** inside a `Store`.
2️⃣ Reducers update the state in response to dispatched actions.
3️⃣ Views subscribe to state changes** using `@ObservedObject` or `@StateObject`, ensuring automatic UI updates.

---

### Key Principles of Redux

✔ **Single Source of Truth** → The entire state of the app is stored in one object.  
✔ **State is Read-Only** → The only way to change state is by **dispatching actions**.  
✔ **Pure Functions (Reducers)** → State updates are handled by pure functions called **reducers**. 
✔ **Unidirectional Data Flow** → State flows **in one direction**, making it predictable.  

---

###  Reference Diagram (Redux Flow)

1️⃣ [[View]] Dispatches an Action
2️⃣ [[Actions|Action]] Describes What Happened
3️⃣ [[Reducer]] Updates the State Based on Action
4️⃣ New State is [[Store|stored]] and Used by the View

![Flow Diagram](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*qI_Y-6Wrn8i8ckVXeB341w.png)

---

### Key Takeaways

- Redux centralises state management, ensuring a **single source of truth**.
- Reducers handle state updates predictably through **pure functions**.
- State is immutable, and the only way to update it is by dispatching **actions**.
- Swift’s Combine framework works well with Redux for reactive state management.
- Useful for **large applications where state needs to be shared across multiple views**.