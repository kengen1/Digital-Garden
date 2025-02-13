#### Core Differences 
- **SQL** → Relational Database
	- tables, rows, and strict schema
	- ACID compliance (Atomicity, Consistency, Isolation, Durability)
	- good for structured, consistent data

* **NoSQL** → Non-relational Database
	* flexible schema
	* horizontal scaling (increasing of complexity or capacity without reimplementation)
	* good for fast reads/writes, semi-structured or unstructured data

	*future write up required* → CAP theorem (Consistency, Availability, Partition Tolerance - pick two)

---
#### When to Use SQL?
- strict schema enforcement (structured data)
- complex queries 
	- JOINs
	- aggregations
	- multi-row transactions
- need for data integrity 
- long term data storage with well-defined relationships 

🔴 Not good for:
* write heavy workloads
* rapidly evolving data structures 
#### When to use NoSQL?
- big data, high velocity workloads (social media, IoT, analytics)
- flexible schema
- frequent changes or iteration (e.g. startup)
- horizontal scaling (distributed databases, shared clusters)

🔴 Not good for:
- complex transactions and deep relational queries 

---

#### Thoughts

- **latency tradeoffs**: 
	- SQL often optimised for consistency
	- NoSQL optimised for availability and partition tolerance
- hybrid approaches are available
- schema changes in SQL can be painful, but they enforce discipline 
- scaling SQL isn't impossible - just more difficult than NoSQL
- its quite clear that picking based on use case rather than familiarity or comfort is critical

