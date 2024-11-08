Don’t talk about monitoring performance for your systems if you don’t know about these 3 crucial metrics: P90, P95, and P99 latencies.

Understanding latency metrics is essential for evaluating system performance and identifying bottlenecks impacting the user experience. 

Here’s a quick masterclass on the key latency metrics, their importance, and how they work:

1. Latency Metrics 101
 - Latency measures how long it takes for a system to respond to a request.
 - Lower latency = faster response; higher latency = slower response.
 - Crucial for ensuring optimal performance and user experience.

2. What Is SLA (Service Level Agreement)?
 - An SLA is essentially a service commitment between the provider and the user.
 - Sets performance standards, like guaranteeing a certain percentage of uptime (e.g., 99%).
 - Holds the provider accountable if the standard isn’t met.

3. The Key Percentiles: P90, P95, and P99 Latencies
 
 - P90 (90th Percentile): 90% of requests complete within this time, and only 10% take longer.
 - Example: If P90 is 80 ms, then 90 out of 100 requests are handled in under 80 ms.

 - P95 (95th Percentile): 95% of requests complete within this time, with only 5% taking longer.
 - Example: If P95 is 90 ms, 95 out of 100 requests finish in under 90 ms.

 - P99 (99th Percentile): 99% of requests complete within this time, with just 1% taking longer.
 - Example: If P99 is 120 ms, 99 out of 100 requests are done within 120 ms. P99 is critical for catching the slowest 1% of requests, which could impact user experience.

 These metrics help evaluate overall performance and detect bottlenecks or outliers that may affect user experience.

4. P99 vs. Median (Middle) Latency

 - P99 Latency: Represents the 99th percentile of response times, meaning 99% of requests are completed within this timeframe. It helps identify outliers and capture the worst 1% of requests that could degrade user experience.

 - Median Latency: Represents the middle value of all response times. It provides a more balanced view of system performance, as it’s less affected by outliers.


5. Mean and Max Latency

 - Mean Latency: The average response time of all requests, useful for general insights.

 - Calculated by summing all latencies and dividing by the number of requests.
 - Example: If response times are 2, 3, 4, 5, and 6 seconds, the mean latency is 4 seconds.

 - Max Latency: The longest time taken for any request, indicating the worst-case delay.
 - Example: If most video loads take 2-5 seconds but one user experiences 20 seconds, max latency is 20 seconds.
