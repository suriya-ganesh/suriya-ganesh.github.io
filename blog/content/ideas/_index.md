---
emoji: 💡 
title: Startup Ideas
description: General ideas that I come up with.
date: 2023-03-14, Tue, 2:7
---

### cicd

- pipeline taking too long to run is an issue. There are a lot of optimisation players who are coming up.
  - [depot.dev](https://depot.dev/)
    - build containers faster.
    - test faster, [lambdatest](https://www.lambdatest.com/intl/en-in), browserstack and others.
    - I've faced pipelines, where 70% of the 2-hour pipeline time spent on building containers, because it is pulling a lot of the previous layers and reassembling everything, every time.
- Being able to test the pipeline locally would be awesome for devops engineers who are trying to test the pipelines
- There are not a lot of solutions to test infra directly. If we think about it, testing infra should be the top priority. Because infra people are constantly shifting things in blackboxed, json or yaml files and infra is the critical part that can get messed up easily.
  - Something like [biceplang](https://github.com/Azure/bicep) or [AWS CDK](https://docs.aws.amazon.com/whitepapers/latest/introduction-devops-aws/aws-cdk.html), should create a template that would test your infra end to end.
  - Think of this, like a full-fledged integration test, but with some type of containment.
  - similar stuff, https://www.datree.io/

### serverless

If ec2 made the jump from having to own a machine to just spinning one up virtually from a bigger machine managed by someone else. Serverless will do the same thing to ec2. From having to spin up containers and manage their resources to shifting that responsibility to the platform underneath.

I predict that, very similar to "traditional" softwares vs virtualised machines. Hardcore software would take a while to get converted to serverless, but until then it will be for tinkering, small projects and hobby projects. eg. netlify, vercel

There are also accelerators to these in the forms of web assembly, which lets deployment and rollbacks for compute, easy.

- Serverless eventually consistent database
  - https://www.cockroachlabs.com/blog/how-we-built-cockroachdb-serverless/
  - https://github.com/rqlite/rqlite
  - https://aws.amazon.com/rds/aurora/serverless/
- A framework to build completely serverless applications, from storage to compute. 
  - Imagine a software service, that is able to leverage a serverless distributed database, does computation on micro-vms, serves the user and then goes silent.
  - There definitely is scope for having abstracted framework that will be able to expose these in different formats.
  - eg. 
    - [webiny](https://github.com/webiny/webiny-js), a serverless cms
    - [aws chalice](https://github.com/aws/chalice), but only (python x aws)
    - [jets](https://github.com/boltops-tools/jets), ruby framework for serverless
- Testing serverless services is still very immature without proper tooling and a lot of emulation
- When serverless
- There would also be scope for offering traditional services, like UDP streaming, pdf/image/whatever processing. through serverless machines and offering them at a much cheaper rate.

- Resources
  - https://firecracker-microvm.github.io/

### Event driven
Event driven architectures are gaining a lot of momentum. There are a few problems inherent to that system,

- since calls are async, there are queues everywhere, this is generally addressed through a pub-sub system like kafka to relay the mesages in a a queue.
- Managing state across pods/instances is hard, despite kafka's guarantees, message misses do happen.
- Rolling back, when something goes haywire is hard.
- Retry seems to be the hailmary in most cases.
- If the publisher is sending buggy messages and crashing the subscribers, it is inherently hard.

### Integrations

- integrations with multiple services and offerings to make them homogenous or generic is something almost everybody is interested in.
  - eg. Zapier,
  - Problem with these integration services is that, the APIs won't be able to handle the edge cases, hence end up being too generic.
  - eg. There are a lot of scope for integrated experiences. eg, whatsapp/discord/slack message management through a single interface for community managers.
  - Kubernetes for notifications infra. Basically a generic phone call/sms, email service which lets us switch the underlying providers easily like, twilio, gupshup .notification apis are
  - Generic payments gateway that lets us A/B testing

### ETL

ETL solutions, either to aggregate data in some form or matter
- Services that take one format of input and transform to another are also very much in demand. The problem is, there is no clear path to productisation other than providing the underlying infra to run these workflows or building tools to build these workflows, of which there are many.
  - https://www.alteryx.com/products/designer-cloud and appian and many many others.

### Privacy

privacy is the hot new talk of the town and there are a lot of gaps in the ecosystem.

- Cryptography x privacy
  - There are a lot of privacy invading services coming like, [needl.ai](https://www.needl.ai/), [needl.tech](https://www.needl.tech/) and others, who are basically offering a personal/personlized Knowledge Management Service (KMS). These services are powered by integrating/scraping across multiple data entrypoints, like google docs, imessage, whatsapp, telegram, slack, rss feeds etc. The amount personal data captured by these services is incredible. While, I'm sure these services will have encryption at rest. It would be really hard to run it on an encrypted database, with good asymmetric encryption like the one offered by keybase.
    - For services like these, it makes sense to offer a database that is completely isolated from the infra and only accessible as an api, that encrypts while active and supports heavy operations like, range queries and full text search.
  - FHE is too slow to be useful, today.
- Machine learning x privacy
  - Moving ML inferences from the server to the client.
    - There are a lot of Local ML platforms like ONNX and TFlite that are enabling people to run ML models on lightweight devices like mobile phones.
  - Some form of Federated learning, to collect the derivations instead of the data. Basically compute will be meeting data instead of beaming up the data and doing compute.
    - prediction: Moving data around is going to be increasingly complex and difficult, as countries start safeguarding their data, in those cases training ML models remotes and then aggregating the models is a very smart way of getting the knowledge from the data, without the data itself.
    - Imagine 100s of hospitals with their patient details and X-rays for tumor siloed out, no hospital is actually going to share that data with another, but with FL and other methods, it would be ridiculously simple to train models in the location where the data is and then slowly start aggregating them globally. With a bit of differential privacy and a loss to accuracy, we can develop very good prediction models 
    - https://www.thepullrequest.com/p/the-future-of-ads-privacy


A lot of these ideas are future facing. Every future facing idea is usually a little twist on top of whatever is standard/hot/obvious right now. which means there will always be a huge middleground full of players who would be far enough behind that, they would need help covering the distance between past and the present. Which means, there is some type of consulting opportunity with every single piece above as well. 