### What are Operators?  

**Operators** are **modifiers** that allow you to **transform, filter, and combine** data from a **Publisher** before it reaches a **Subscriber**.  

Think of operators like **editors** for a news article:  
- Some operators **rewrite** the content (`map`)  
- Some **remove unnecessary parts** (`filter`)  
- Some **merge information from multiple sources** (`combineLatest`)  

> *Operators act as middlemen between [[Publishers]] and [[Subscribers]], modifying the data stream.*

🔗 **Official Docs:** [Apple Documentation](https://developer.apple.com/documentation/combine/operator)  

---

### How Operators Work  

- Operators **sit between a Publisher and a Subscriber**.  
- They **modify or filter the data** before it reaches the subscriber.  
- You can **chain multiple operators** together to **build complex data flows**.  

---

### Example: News Filtering  

In this example, we use an **operator** to filter out **news headlines that don’t mention Swift**.

```swift
import Combine

// 1. Create a news publisher
class NewsPublisher {
    let news = PassthroughSubject<String, Never>() 
    
    func publish(newsHeadline: String) {
        print("📰 News Published: \(newsHeadline)")
        news.send(newsHeadline)
    }
}

// 2. Create a subscriber with an operator
class NewsSubscriber {
    private var cancellable: AnyCancellable?
    
    init(publisher: NewsPublisher) {
        cancellable = publisher.news
            .filter { $0.contains("Swift") } // Only allow news about Swift
            .sink { news in
                print("📢 Subscriber received: \(news)")
            }
    }
}

// 3. Use the publisher and subscriber
let newsPublisher = NewsPublisher()
let subscriber = NewsSubscriber(publisher: newsPublisher)

newsPublisher.publish(newsHeadline: "Swift 6 Announced!") // ✅ Will be received
newsPublisher.publish(newsHeadline: "New AI Model Released") // ❌ Will be ignored
newsPublisher.publish(newsHeadline: "Swift Concurrency Improvements") // ✅ Will be received



