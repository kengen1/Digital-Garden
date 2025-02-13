ref: https://refactoring.guru/replace-inheritance-with-delegation

- allows an object to pass (or delegate) a task to another helper object instead of handling it itself
- promotes separation of concerns and allows for more flexible and reusable code
#### How It Works
1. a delegator class contains a reference to a delegate
2. the delegator forwards (delegates) certain operations to the delegate
3. the delegate handles the actual implementation of the delegated behaviour 

#### Common Use Cases
- **user interface design**: delegates are often used in UI frameworks to handle events 
- **event handling**: delegates can be used as callbacks mechanisms in event-driven programming 
- **code reusability**: instead of subclassing, delegation allows multiple objets to share behaviour by using different delegate implementations 
- **asynchronous programming**: delegation allows tasks to be performed asynchronously without blocking the main thread

#### Caveat
- Increased complexity due to indirect method calls