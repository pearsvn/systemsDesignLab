# Real-time Collaborative Document Editing System

This is my first time creating a design of a system. I know there are some amendments that can be made, e.g. better tools, designs, etc. to make this system more reliable, scalable, cost-effective, and so on. But this is the system I have designed based on my current knowledge:

![Diagram](./Real-time-collaborative-document-editing-system.png "System Overview")

As you can see, the diagram shows my idea of what the system would look like when considering the requirements, e.g. multiple users, document updates that synchronize with each user's display, ability to undo edits / view history of document, view user permissions via metadata, etc.

I was hoping to implement this system, using some free-tier components. I think I may be able to create this system if I'm able to find a docker image that mimics the google docs app. I will then try to spin up this container in a Kubernetes pod that acting as a server, that will use a WebSocket protocol to connect to the users through a configured load balancer, API gateway, and CDN.

If I am able to complete this first part, then I can try to find a way of storing user session states, possible with Redis caching. Perhaps Redis 8 since it's open source. If I can configure this, then I will try to move over to the operations queue which I was thinking of using Apache Kafka for, to make use of the partition key feature to parallelize queue updates. I don't know if that makes total sense, if it doesn't, then maybe it's a good idea for me to revisit the Kafka in 6 minutes video I watched for reference: https://www.youtube.com/watch?v=Ch5VhJzaoaI

In terms of the CRDT/OT engine, I may have, for good reason, underestimated all of the requirements to create such a service. My current layman understanding of networking and system design has me feeling experimental. Therefore, in creating the design for this system, I was looking at reference designs that showed the need for some collaborative services. This is probably the most highlighted feature of this system anyway, otherwise this would just be another document editor on the web.

So, according to this video: https://www.youtube.com/watch?v=5JDq7cx7nao , the requirements for building this CRDT engine include:
- Node.js
- Y.js
- IPFS.js
- browserify
- y-ipfs-connector
- http server

With this service created, the final tasks to complete would be to add a document cache, metadata database, version history store, and blob storage that acts as the document content store.

In all honesty, I don't have great knowledge of all of these things right now but I will take this in my stride since I continue to learn more.
