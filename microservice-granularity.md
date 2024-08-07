## Microservice Granularity

Determining the right sizing or granularity for microservices is crucial for building an effective and maintainable system. 
Domain Driven Design (DDD) helps you to decompose the domain into multiple subdomains or business capabilities (bounded contexts) that can be independently manageable. Identifying the independent bounded contexts is crucial in decomposing the domains into Microservices.

Microservice architecture offers the significant advantage of team autonomy. The team responsible for a microservice can independently decide which features to release and when, without coordinating with other teams.

A microservice should be micro in nature. But, what does that mean - is it based on lines of code, the number of APIs, or the number of classes? Overly fine-grained services can result in high inter-service communication, causing tight coupling and performance issues. Conversely, excessively coarse-grained services may encounter similar challenges to those of a monolithic architecture.

Discussion around a business context always helps to understand things better, hence, well-known business requirements are a starting point where a team should focus.

The other key focused area should be whether they need one composite microservice or multiple smaller Microservices.

Let us take an example to deep-dive into this.

Let us consider a bank account as an example. Bank accounts contain multiple account types like current accounts, mortgage accounts, credit card accounts, Loan Accounts, and various other types.  Let us take a very simple use case of displaying the account balance when a customer asks CHAT BOT to display the account balance.

With the above use case, there are two possible options.
1. A composite, coarse-grained Account Balance microservice — handling all the account types
2. Multiple smaller fine-grained microservices, one per account type

Logically, the function of the account balance service is to display the account balance. This feature appears highly cohesive, so a single coarse-grained microservice following the principle of single responsibility should suffice.

Conversely, fetching the balances to various account types, each with its own challenges, suggests the need for multiple fine-grained microservices, with one per product/account type.

The decision is certainly challenging. How do you determine whether to implement a single composite microservice or multiple smaller microservices?

Here are some key considerations and guidelines to help you achieve the right granularity:

**Bounded Context:** Use bounded contexts from DDD to define clear boundaries within your domain. Ensure each microservice operates within its own bounded context.
Each microservice should represent a single business capability. 

**Single Responsibility Principle**: The functionality offered by a microservice should be Single Purpose and Highly Cohesive. Ensure each microservice has a single, well-defined responsibility. Avoid combining multiple responsibilities into a single service.

**Service-to-Service Communication**: Minimize the number of interactions and dependencies between microservices. Excessive communication can indicate that services are too granular and should be combined. 

**Scalability, Performance, and Load**: Identify components that need to scale independently.Services that require different scaling characteristics should be separated.
Consider the impact of network latency and inter-service communication on performance. Ensure that splitting services does not introduce significant performance bottlenecks.
Ensure that the load can be evenly distributed across services. Services with disproportionate load can indicate improper granularity.

**Team Autonomy**: Align microservices with the structure of your development teams. Ensure that a team can fully own and manage a microservice without excessive dependencies on other teams.

**Data Ownership and Management**: Each microservice should own its data. Avoid shared databases across microservices to maintain loose coupling and independent scalability.
If two services frequently need the same data, reconsider the boundaries to optimize data flow.

**Technical Constraints and Complexity**: Avoid making services too small, which can lead to excessive complexity in managing inter-service communication and dependencies.
Strike a balance between simplicity and maintainability. Consider technology constraints and the feasibility of managing multiple microservices.
Use tools and platforms that support your microservice architecture effectively.
