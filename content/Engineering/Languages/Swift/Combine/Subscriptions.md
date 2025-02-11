### What are Subscriptions?  

A **Subscription** in Combine **manages the connection** between **[[Publishers]]** and **[[Subscribers]]**.  
It controls **when data flows**, **how much data is requested**, and **when the connection should stop**.

Think of a **Subscription** as a **newspaper subscription**:
- A subscriber **chooses** which news they want.
- The publisher **only sends newspapers when requested**.
- The subscription **can be canceled at any time**.

> *Subscriptions allow for demand-driven data flow, unlike traditional push-based Notifier patterns.*

🔗 **Official Docs:** [Apple Documentation](https://developer.apple.com/documentation/combine/subscription)  

---

### How Subscriptions Work  

- **A Subscriber must request values** from a Publisher before receiving them.  
- **The Publisher does not send data unless requested** (demand-driven model).  
- **Supports backpressure** → The Subscriber can **control the rate of data flow**.  
- **Manages lifecycle** → Can be **canceled** when no longer needed.  

---

### **Difference Between Combine & a Notifier Pattern**  

| Feature                 | Notifier Pattern                    | Combine Framework |
|-------------------------|------------------------------------|------------------|
| **Basic Concept**       | A subject (notifier) sends events to registered listeners (observers). | A publisher emits values over time, and subscribers react to them. |
| **Flow of Data**        | Push-based: The notifier calls methods on all observers. | Demand-driven: Subscribers request values via a **Subscription**. |
| **Subscription Model**  | Listeners are registered and receive updates whenever an event occurs. | **Backpressure support**: Subscribers **request** data when they need it. |
| **Memory Management**   | Observers must manually unsubscribe to avoid memory leaks. | **Cancellable** objects automatically manage subscriptions. |
| **Data Transformation** | No built-in way to transform data before delivery. | **Operators** allow for filtering, mapping, and combining data. |
| **Threading**           | Observers are notified on the thread that emits the event. | **Schedulers** control where and when work happens (e.g., background or UI thread). |
| **Error Handling**      | Typically requires custom error-handling logic. | Combine has built-in **error propagation** via `tryMap`, `catch`, etc. |
| **Declarative Syntax**  | Typically imperative (`notifier.notifyAll()`). | Fully declarative (`publisher.map().filter().sink()`). |

---

### **The Role of Subscriptions in Combine**  
Subscriptions **change the way values flow** compared to a **generic Notifier pattern**:

#### **1. Notifier Pattern: Push-Only Model**
- The **notifier** sends values to all listeners **as soon as they are available**.  
- The **subscriber has no control** over when or how often it receives data.  
- Example:
```swift
  protocol Notifier {
      func addListener(_ listener: Listener)
      func notifyAll(data: String)
  }
```

#### **2. Combine: Demand-Driven Model**

- A **Subscription** creates a structured relationship between the Publisher and Subscriber.
- **Subscribers request values**, and **Publishers only send what is requested**.
- Supports **Backpressure** (controlling the rate of emitted values).
- Example"
```swift
let publisher = ["Hello", "Combine"].pusblisher
let subscription = publisher.sink {print($0)}
```

---

### Example: Notifier vs. Combine Subscriptions

**Notifier Pattern**
```swift
class NewsNotifier {
    private var listeners: [((String) -> Void)] = []
    
    func subscribe(_ listener: @escaping (String) -> Void) {
        listeners.append(listener)
    }
    
    func publish(news: String) {
        for listener in listeners {
            listener(news)
        }
    }
}

// Usage
let newsNotifier = NewsNotifier()
newsNotifier.subscribe { print("📢 Received: \($0)") }
newsNotifier.publish(news: "Breaking News!")
```
*Problems:*
- no control over when values arrive
- no filtering, transforming, or error handling 
- manual memory management required

**Combine Alternative**
```swift
import Combine

class NewsPublisher {
    let news = PassthroughSubject<String, Never>()
    
    func publish(news: String) {
        print("📰 News Published: \(news)")
        news.send(news)
    }
}

// Usage
let publisher = NewsPublisher()
let cancellable = publisher.news
    .filter { $0.contains("Breaking") } // Only get breaking news
    .sink { print("📢 Subscriber received: \($0)") }

publisher.publish(news: "Breaking News!") // ✅ Received
publisher.publish(news: "Regular News") // ❌ Ignored due to filter
```
*Problems:*
- Subscribers control when they receive data (demand-driven model)
- Built-in operators (`filter`, `map`) allow transforming data easily 
- [[Cancellable]] ensures memory is managed safely