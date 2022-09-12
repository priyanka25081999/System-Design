**Event-Driven architecture (EDA) :**
       
* It is a way of designing lossely coupled applications and services that respond to real-time information based on sending and receiving of events. 
* In the traditional RPC, one service can only contact to another service. This creates a tight coupling between the services. They are communicating with one another
* In EDA, we have a separate event broker and we send events to that. Every service can have it's own broker. When task is done, they can emits the event. Services are not tightly coupled to each other. Instead they are observing the events and reacting in response to those events.
* Another is, if you want to add another service in your existing architecture. Then in RPC it may be a difficult task. But, in EDA you can easily have the new service. We don't need to modify the existing architecture.

**Apache Kafka:**
* It is the **event broker** component here. It will be used to send and receive the events.

**Why EDA?**
* Achieve encapsulation
* Mirrors the real-world
* Reduced coupling
* Near real-time latency
* Fine-grained scaling
