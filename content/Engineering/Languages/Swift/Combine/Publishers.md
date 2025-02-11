### What are Publishers?  

A **Publisher** is a source of data in Combine that emits values over time.  
It **produces a sequence of values** that can be observed by **Subscribers**.

- Think of it like a **news publisher** that **broadcasts news updates**.
- **Subscribers** (readers) receive the updates and react to them.
- Publishers do not send values unless there is an **active Subscriber**.

> *A Publisher emits values to a Subscriber, which then processes those values.*

🔗 **Official Docs:** [Apple Documentation](https://developer.apple.com/documentation/combine/publisher)  

---

### Types of Publishers  

- **Built-in Publishers**  
  → `Just(value)` → Emits a **single value** and finishes.  
  → `Future { promise in }` → Performs work and emits **one value** asynchronously.  
  → `Empty()` → Emits **no values** and immediately finishes.  
  → `Fail(error)` → Emits **an error** immediately.  
  → `PassthroughSubject` → A **manually triggered publisher**.  
  → `CurrentValueSubject` → **Stores a value** and emits new ones when updated.  
  → `URLSession.shared.dataTaskPublisher` → Emits **network request results**.  

---

### How Publishers Work  

- Publishers **emit values asynchronously**.  
- They need a **Subscriber** to **start sending data**.  
- Can be **transformed or combined** using [[Operators]] before reaching a Subscriber.  

---

### Example: News Publisher  

This example models a **news publishing system** where a **NewsPublisher** sends news updates, and multiple **subscribers** receive them.

```swift
import Combine

// 1. Create a news publisher (PassthroughSubject)
class NewsPublisher {
    let news = PassthroughSubject<String, Never>() // Publishes strings (news headlines)
    
    func publish(newsHeadline: String) {
        print("📰 News Published: \(newsHeadline)")
        news.send(newsHeadline) // Send news to subscribers
    }
}

// 2. Create a subscriber (news reader)
class NewsSubscriber {
    private var cancellable: AnyCancellable?
    
    init(publisher: NewsPublisher) {
        // Subscribe to news updates
        cancellable = publisher.news.sink { news in
            print("📢 Subscriber received: \(news)")
        }
    }
}

// 3. Use the publisher and subscriber
let newsPublisher = NewsPublisher()
let subscriber1 = NewsSubscriber(publisher: newsPublisher)
let subscriber2 = NewsSubscriber(publisher: newsPublisher)

newsPublisher.publish(newsHeadline: "Breaking: Swift 6 Announced!")
newsPublisher.publish(newsHeadline: "New Combine Features in iOS 18!")
