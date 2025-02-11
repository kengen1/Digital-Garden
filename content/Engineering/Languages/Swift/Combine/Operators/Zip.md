### What is `zip` in Combine?  

The **`zip` [[Operators|operator]]** in Combine **combines values from multiple publishers** into **pairs (tuples)**.  
It waits for each publisher to **emit a value** before sending the combined result.

Think of it like **pairing people in a three-legged race**:
- Each person (publisher) needs a partner before they can start moving.  
- If one publisher emits a value but the other hasn’t, it **waits**.  
- Once both publishers emit, **they move forward together**.  

> *`zip` waits for each publisher to emit a value before combining them into a single output.*

🔗 **Official Docs:** [Apple Documentation](https://developer.apple.com/documentation/combine/publisher/3204751-zip)  

---

### How `zip` Works  

- **Combines values from two or more publishers** into a tuple.  
- **Waits for all publishers** to emit a value before producing an output.  
- **Pairs values one-to-one** (it doesn’t repeat values if one publisher emits more than the other).  

---

### Example: Pairing News Headlines & Authors  

```swift
import Combine

// 1. Create two publishers
let newsHeadlines = ["Swift 6 Released!", "Combine Improvements!", "iOS 18 Announced!"].publisher
let authors = ["Alice", "Bob"].publisher

// 2. Zip the publishers
let cancellable = newsHeadlines
    .zip(authors)
    .sink { headline, author in
        print("📰 \(headline) - by \(author)")
    }

(The third headline **is not printed** because `zip` only pairs **matching values**.)
```

### Key Takeaways

- `zip` **waits for all publishers** to emit before sending combined values.
- **Pairs values one-to-one**, discarding extra emissions from faster publishers.
- Useful when **data must be synchronized**, such as **matching requests and responses**.