## Microservice Granularity

Determining the right sizing or granularity for microservices is crucial for building an effective and maintainable system. 
Domain Driven Design (DDD) helps you to decompose the domain into multiple subdomains or business capabilities (bounded contexts) that can be independently manageable. Identifying the independent bounded contexts is crucial in decomposing the domains into Microservices.

Microservice architecture offers the significant advantage of team autonomy. The team responsible for a microservice can independently decide which features to release and when, without coordinating with other teams.

A microservice should be micro in nature. But, what does that mean - is it based on lines of code, the number of APIs, or the number of classes? Overly fine-grained services can result in high inter-service communication, causing tight coupling and performance issues. Conversely, excessively coarse-grained services may encounter similar challenges to those of a monolithic architecture.

Discussion around a business context always helps to understand things better, hence, well-known business requirements are a starting point where a team should focus.

The other challenge that teams always come across is that, does it requires one composite microservice or multiple smaller Microservices.

Let us take an example to deep-dive into this.

Let us take an example of a bank account. 

Here are some key considerations and guidelines to help you achieve the right granularity:
