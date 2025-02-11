### What is Functional Programming?  

**Functional programming (FP)** is a way of writing code that focuses on **transforming data through reusable functions** instead of changing state or using loops.  
It’s about **breaking problems into small, predictable building blocks** and combining them to get the result you want.

Think of it like **assembling a burger**:
- You **start with ingredients** (data).  
- You apply **steps in a fixed order** (functions).  
- You always get **the same burger** if the ingredients are the same (predictable output).  

> *Functional programming is about writing code in small, reusable, and predictable steps—just like following a recipe.*  


✅ Functional programming focuses on *declaring what should happen* rather than how it should happen* (declarative programming).  

✅ Higher-order functions take this declaration* and *handle the procedural execution* of data transformations behind the scenes.


🔗 **Further Reading:** [Wikipedia - Functional Programming](https://en.wikipedia.org/wiki/Functional_programming)  

---

### Key Principles of Functional Programming  

- **Pure Functions** → Always return the same result for the same input, without modifying anything outside.  
- **Immutability** → Once data is created, it doesn’t change (instead, you create new data).  
- **First-Class Functions** → Functions are treated like variables (can be passed around and returned).  
- **Higher-Order Functions** → Functions that take other functions as input or return them as output.  
- **Declarative Code** → Focuses on **what** to do rather than **how** to do it (less manual control).  

---

### Example: Functional vs. Imperative  

#### **Imperative (Step-by-Step) Approach**  
```swift
var total = 0
let numbers = [1, 2, 3, 4, 5]

for number in numbers {
    total += number
}

print(total) // Output: 15
```

- Uses **mutable state** (`total` changes)
- Uses **loops** to control flow manually 

#### Functional Approach
```swift
let numbers = [1, 2, 3, 4, 5]
let total = numbers.reduce(0, +)

print(total) // output: 15
```

- No mutation (no variable is reassigned)
- Uses **higher-order function** (`reduce`)
- More readable and declarative 

---
### Functional Concepts in Swift

- `map` → Applies a transformation to each element in a collection.
- `filter` → Removes elements that don’t meet a condition.
- `reduce` → Combines elements into a single result.
- `flatMap` → Flattens nested collections while applying a transformation.
- `compactMap` → Removes `nil` values while transforming the data.

### Example: Transforming Data Functionally
```swift
let numbers = [1, 2, 3, 4, 5]

// Double each number
let doubled = numbers.map { $0 * 2 } 
print(doubled) // Output: [2, 4, 6, 8, 10]

// Keep only even numbers
let evens = numbers.filter { $0 % 2 == 0 }
print(evens) // Output: [2, 4]

// Sum all numbers
let sum = numbers.reduce(0, +)
print(sum) // Output: 15

```

### Key Takeaways
- Functional programming focuses on transforming data rather than modifying state
- Pure functions prevent unexpected changes, making debugging easier 
- Immutability makes code safer and avoids unintended side effects
- Higher-order functions (`map`, `filter`, `reduce`) simplify how you process data
