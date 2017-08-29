# Why Containers and Serverless


## What is serverless?

Code that is executed in response to an event, that isn't tied to a specific server.

- In the cloud
  - It means AWS lambda, code execute in context to some event

You can subscribe
  - S3 events
  - SNS Events
  - Kinesis streams
  - HTTP Events through Api Gateways


### Downside

  - Tied to a specific implmentation
  - You can't just use your Rails, or Django app

### Upsides

- Institutions
  - The contract process to utilize cloud providers is extended

## Handling lockin

- There are open source versions of lambada

- How practical is it to be portable
  - How do we handle moving if they sunset
  - It's easy to think about serverless

# Building local serverless

- Camel sounds like it consumes, and produces messages
  - But it can filter messages
  - Camel could be backend of serverless, yes


## Why not containers?

If you can't use serverless, maybe use containers because it's kind of a decomposition

Sounds like the work to containers get's you ready for serverless

In order to breakdown software into containers we must know how our software works. This in of its self is going to be the same steps you must need to do get to severless.





