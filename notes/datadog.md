# Datadog

1. **Universal service monitoring (USM)**: Services might be running on multiple instances but we need to monitor them aggregately. So, datadog collects data about your existing services
   which can then be viewed through the service catalog.
 
2. **Service catalog**: The service catalog is a centralized place to view all of the services in your application.

3. **Universal Service Monitoring (USM)** offers a view of service health metrics across your entire technology stack, without the need to instrument your code. Instead,
   it relies on the presence of a configured Datadog Agent and Unified Service Tagging to collect data about your existing services, which can then be viewed through the Service Catalog.
   Instead of requiring you to edit your application code and redeploy applications, USM requires only a little configuration of your Agent.

4. **Unified Service Tagging**: Universal Service Monitoring is capable of identifying services through commonly used container tags (such as app, short_image, and container_name),
   and automatically generates corresponding entries in the Service Catalog. Once these services are discovered, Datadog enables you to access request, error, and duration metrics for both
   inbound and outbound traffic. These service health metrics are helpful in setting up alerts, tracking deployments, and establishing service level objectives (SLOs), providing you with
   a comprehensive view of all the services running on your infrastructure.

5. **Service catalog**: The Service Catalog is a centralized place to view all services in your application. Service Catalog automatically includes services detected by USM.
   Developers and site reliability engineers can view all services, their structures, and links to more information. It improves the on-call experience for everyone by establishing
   correct ownership information and communication channels, alongside easy access to monitoring and troubleshooting details. In case of an incident, it can speed up recovery by
   increasing confidence and making it simpler to locate owners of upstream and downstream services and dependencies.

6. **Datadog Log Management**: It allows you to cost-effectively collect, process, *archive, explore, and monitor all your logs without limitations. When you use Datadog Log Management:
    
    a. You can collect logs from various sources, such as hosts, containers, and cloud providers.
    
    b. Once the logs are ingested, you can enhance them using pipelines and processors, create metrics from the logs, and manage storage-optimized archives with Log Configuration options.
    
    c. You can connect logs to metrics and traces from other sources for greater insights.

    d. Finally, you can search, filter, and query the ingested logs in the Log Explorer.

8. **Metrics**:
   
   a. Metrics are the smallest unit in the Datadog universe but they grant enormous insight into your infrastructure when they are visualized, measured, and monitored.
   
   b. Metrics are numerical measurements about any aspect of your system over a period of time, such as latency, error rates, or user registrations. In Datadog, metric data is received and
      retained as data points that include a value and timestamp. Monitors send notifications when metrics fall outside of the tolerances that you define.

   c. Service Level Objectives track metrics over long periods of time to help you define quality standards.

10. **Datadog agent**: The Datadog Agent is software that runs on your hosts. It collects process- level events and metrics and sends them to Datadog,
   where you can analyze your monitoring and performance data.

   There are three main types of integrations: Agent-based, authentication-based, and library. You can even build your own integration!
    a. **Agent-based integrations** are installed with the Datadog Agent (on your host or in containers) and use a Python class method called check to define the metrics to collect.
    b. **Authentication (crawler) based integrations** are set up in Datadog where you provide credentials to obtain metrics and data from APIs. These include popular integrations
       like Slack, AWS, Azure, and PagerDuty.
    c. **Library integrations** use the Datadog API to allow you to monitor applications based on the language they’re written in, like Node.js or Python.

11. **Dashboards**:

     a. Dashboards display charts, tables, and notes about the data that you’ve sent to Datadog. With Dashboards, you can easily track and monitor critical metrics
        that are crucial to the health of your system. It is a central location for monitoring key data, making it easier to identify issues, detect trends, and take action to
        improve your application performance. Therefore, dashboards provide a clear and concise overview of your infrastructure, allowing you to quickly assess the state of your
        system and make informed decisions.
   
     b. You can share these dashboards with people outside of Datadog. By sharing a dashboard through a URL or email link, others can view the contents of that dashboard in real-time,
        without any ability to modify the data.
   
     c. Datadog offers a wide range of out-of-the-box dashboards that can help you get started quickly. For example, you could find a dashboard based on an integration you have added
        (such as Postgres or Docker) or a feature you use in your application (such as Real User Monitoring).
   
     d. These dashboards can be cloned and customized to meet your specific needs, or you can even create your own dashboards from scratch.
        By leveraging these out-of-the-box dashboards, you can quickly get started with monitoring your infrastructure and applications and gain critical insights into system performance.
   
     e. When you create your dashboard, there are three layout options to choose from: grid-based dashboards (the default), timeboards, and screenboards. For all these layouts,
        you can add images, graphs, and logs.
