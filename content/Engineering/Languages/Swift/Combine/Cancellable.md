### What is Cancellable?  

A **Cancellable** in Combine is an object that **controls the lifecycle** of a subscription.  
It allows you to **stop receiving updates** when you no longer need them, preventing memory leaks.

Think of it like a **Netflix subscription**:
- As long as you are subscribed, you **keep getting to watch Netflix**.
- If you **cancel**, the publisher **stops access to Netflix**.
- If you forget to cancel, you might **keep access to Netflix but also will continue paying for that subscription**.

> *Cancellable objects help manage memory by stopping subscriptions when they’re no longer needed.*

🔗 **Official Docs:** [Apple Documentation](https://developer.apple.com/documentation/combine/cancellable)  

---

### How Cancellable Works  

- **Created when a subscriber subscribes to a publisher.**  
- **Holds the subscription until canceled.**  
- **Prevents memory leaks by stopping updates when not needed.**  

---

### Example: Stopping a Subscription  

```swift
import Combine

let publisher = ["Breaking News", "Swift 6 Released"].publisher

let cancellable = publisher
    .sink { print("📢 Subscriber received: \($0)") }

// Stop receiving updates
cancellable.cancel()
