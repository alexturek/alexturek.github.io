# Intro

I was an early adopter of GraphQL at Convoy.
I implemented a lot of the early backend infrastructure, and spent 6 years intermittently maintaining the GraphQL APIs.

The last time I worked in GraphQL was 2022, so I'm probably a bit out of date on the actual technical libraries.
But regardless of the implementation, I think GraphQL is a fundamentally flawed concept.

Here is why I would never add GraphQL to any new project, and would instead use vanilla JSON-over-HTTP (REST, if you like).

Experience:
- set up early graphql resolver backend infrastructure in Convoy's monolith
  - authorization
  - data loaders

# What does GraphQL get right?

* It makes it very easy for clients to request more data on existing API calls
* It makes client-side API performance management simpler

# What's better about REST?

Simplicity
* Authorization is far more straightforward
* No N+1 queries by default

Parallelism
* Schema awareness much more limited in intermediate systems. Method and route are all you need
* There's less need for a global API authority to limit what gets added
* You can iterate on and deprecate APIs separately from each other
