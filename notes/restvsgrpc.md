REST APIs are the standard for the web. They are human-readable ({"status": "ok"}) and easy to debug. But for high-performance internal microservices, REST is a bottleneck.

When you click "Play" on Netflix, the Playback Service has to talk to the Billing Service, the CDN Service, and the Subtitle Service - all in milliseconds. If they communicated using massive text-based JSON files, the latency would pile up.

So, Netflix (and companies like Square and Uber) moved away from internal REST. They use gRPC.

- The App Feature: Netflix Video Start. The "Orchestrator" service calling 10 other downstream services to gather metadata before the first pixel loads.
- The Concept: gRPC (Remote Procedure Call) & Protocol Buffers.


The Difference: Think of the difference between sending a Word Document vs. sending a Zip File.

1. REST (JSON) - The Chatty Tourist 🗣️

- The Message: { "movie_id": 55, "title": "Inception", "user": "premium" }
- The Problem: It sends the field names ("movie_id", "title") over the network every single time. It's text-heavy and requires the receiver to spend CPU cycles "parsing" that text back into code.
- The Transport: Usually creates a new TCP connection for every request (HTTP/1.1), which is slow.

2. gRPC (Protobuf) - The Efficient Local 🚄

- The Message: 0x37 | 0x49 | 0x01 (Binary Data).
- The Trick: Both services share a .proto file (a blueprint). They already know that Field 1 is the Movie ID. They don't need to send the field name. They just send the value in compressed binary.
- The Result: The payload is 30-50% smaller, and the CPU parses it instantly.

Technical Deep Dive (HTTP/2 Multiplexing): gRPC isn't just about smaller data; it's about the transport. It runs on HTTP/2.

- REST (HTTP/1.1): Service A sends a request. Waits. Gets a response. Sends next request. (Head-of-Line Blocking).
- gRPC (HTTP/2): Service A opens one connection and fires 50 requests simultaneously. The responses come back out of order whenever they are ready. It’s like a multi-lane highway vs. a single-lane road.

The Takeaway:
- Public API (External): Use REST. Your customers need to read the JSON.
- Private API (Internal): Use gRPC. Your servers should speak Binary to save money and latency.
