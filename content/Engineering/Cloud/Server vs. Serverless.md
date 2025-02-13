- Cloud applications and services can be deployed using **traditional servers** or **serverless architecture**, each with trade-offs dependent on the scale, cost and complexity of that application or service.

#### Server (Traditional Infrastructure)
- applications run on virtual machines (e.g., AWS EC2, Azure VM)
- full control over server configuration, networking and scaling 
- requires manual provisioning, maintenance, and scaling 
- **Best for**: Long running applications, databases, and workloads that require persistent compute power 

#### Serverless (Event-Driven Execution)
- code runs on demand without managing infrastructure (AWS Lambda, Azure Functions)
- auto-scales based on workload, reducing idle costs
- limited execution time and cold stats may impact performance 
- **Best for**: short lived. functions, microservices, APIs , and event driven workflow 