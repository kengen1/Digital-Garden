### What are Subscribers?  

A **Subscriber** listens to a **Publisher** and reacts when it receives new values.  
It’s like a **news reader** who subscribes to a **news publisher** and gets updates whenever news is published.

- A subscriber **only receives data if it is subscribed**.  
- It can **process, transform, or react** to the data it gets.  
- If a publisher **stops sending values**, the subscriber also stops receiving them.  

> *A Subscriber listens for values and reacts to them when they arrive.*

🔗 **Official Docs:** [Apple Documentation](https://developer.apple.com/documentation/combine/subscriber)  

---

### Types of Subscribers  

- **sink** → A simple way to receive values and errors.  
- **assign(to:on:)** → Assigns a value to an object’s property.  
- **Custom Subscribers** → Implement your own subscriber by conforming to `Subscriber`.  

---

### How Subscribers Work  

- A subscriber **must be attached to a publisher** to start receiving data.  
- A subscriber **controls its lifecycle** and can cancel at any time.  
- A publisher can have **multiple subscribers** listening at once.  

---

### Example: News Subscriber  

This example models a **news publishing system** where a **NewsPublisher** sends news updates, and multiple **subscribers** receive them.

```swift
import Combine

// 1. Create a news publisher
class NewsPublisher {
    let news = PassthroughSubject<String, Never>() // Publishes news headlines
    
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

newsPublisher.publish(newsHeadline: "Swift 6 Announced!")
newsPublisher.publish(newsHeadline: "New Combine Features in iOS 18!")
