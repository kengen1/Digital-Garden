
* Design for usability, not just implementation
- If the user needs to Google "what does this status code mean" - you failed
- **Versioning** : if you need to depreciate something, announce it properly (clear versioning format in the URL)
- **Auth and Security:**
	- Don't use plain passwords in requests
	- Rate limit requests to prevent abuse of the API
	- CORS restrictions to control where your API is called from 
	- Always validate input (preventative measure for SQL Injection / XSS)
	- Log and monitor usage 
#### REST vs. GraphQL vs. RPC vs. WebSockets

- **REST** → Standard, resource-based, simple & predictable (`GET /users/123`)
- **GraphQL** → Client decides what data they need (`{ user { id, name, email } }`)
- **RPC (gRPC, JSON-RPC, etc.)** → Faster, compact, function calls over HTTP (`GetUser(123)`)
- **WebSockets** → Real-time, bi-directional (`ws://chat`)

**Pick based on your use case:**
- CRUD-heavy? **REST**
- Complex queries, multiple frontends? **GraphQL**
- Low-latency, high-performance? **gRPC**
- Real-time updates? **WebSockets**
