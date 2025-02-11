### What are Subjects?  

A **Subject** in Combine is both a **Publisher and a Subscriber**.  
It acts as a **bridge** between imperative and reactive programming, allowing you to **manually send values** into a Combine pipeline.

Think of it like a **news agency**:
- A **Publisher** automatically sends news updates (values) as they happen.  
- A **Subject** allows you to **manually create and send news updates** to subscribers.  

> *Subjects let you push values into a Combine pipeline, acting as both an input and an output.*

🔗 **Official Docs:** [Apple Documentation](https://developer.apple.com/documentation/combine/subject)  

---

### How Subjects Work  

- **Acts as both a Publisher (emitting values) and a Subscriber (receiving values).**  
- **Allows manually injecting values** into a Combine stream.  
- **Multiple subscribers** can listen to the same subject.  

---

### Types of Subjects  

1. **`PassthroughSubject`** → Emits values **as soon as they are sent**, without storing them.  
2. **`CurrentValueSubject`** → Stores the **most recent value** and sends it to new subscribers.  

---

### Example: Using a Subject to Broadcast Messages  

```swift
import Combine

// 1. Create a subject
let newsSubject = PassthroughSubject<String, Never>()

// 2. Subscribe to the subject
let cancellable = newsSubject
    .sink { print("📢 Subscriber received: \($0)") }

// 3. Manually send values
newsSubject.send("Breaking News: Swift 6 Announced!")
newsSubject.send("New Combine Features Revealed!")
```

### Example: Using `CurrentValueSubject` to Store Latest Value

```swift
import Combine

// 1. Create a CurrentValueSubject with an initial value
let latestNews = CurrentValueSubject<String, Never>("No news yet")

// 2. Subscribe to receive the latest news
let cancellable = latestNews
    .sink { print("📢 Latest news: \($0)") }

// 3. Update the stored value
latestNews.send("Breaking News: Swift 6 Announced!")

// 4. A new subscriber will get the latest value immediately
let newSubscriber = latestNews
    .sink { print("📢 New subscriber got: \($0)") }

```

---

### Key Takeaways

- Subjects act as both Publishers and Subscribers.
- **PassthroughSubject** → Does **not** store values; only sends them when available.
- **CurrentValueSubject** → Stores the **latest value** and sends it to new subscribers.
- Useful for **bridging imperative and reactive code**, such as user input handling.