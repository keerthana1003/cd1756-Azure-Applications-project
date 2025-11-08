# Write-up Template

### Analyze, choose, and justify the appropriate resource option for deploying the app.

- 1. Overview
For deploying the Flask-based Article CMS application on Azure, there are two main hosting options available — Azure Virtual Machines (VMs) and Azure App Service.
Both allow web application deployment but differ in their level of control, scalability, cost, and ease of management.
This write-up compares both options and concludes with the reasoning behind choosing Azure App Service for deployment.
- 2. Azure Virtual Machine (VM)
     Definition:
     An Azure Virtual Machine (VM) is an Infrastructure-as-a-Service (IaaS) offering that provides full control over the operating system, software installations, and
     environment configurations.
     Developers are responsible for setting up the runtime, dependencies, and web servers (like Gunicorn or Nginx) needed to run the application.
     Pros:
     -Full control: You can configure the operating system, network, security, and installed software as needed.
     -Flexibility: Suitable for hosting multiple services on one machine (e.g., backend, database, or other servers).
     -Custom environment: You can install any version of Python, dependencies, or custom libraries.

     Cons:
     -High maintenance: You must manage OS updates, patches, security, and monitoring manually.
     -Manual scalability: Scaling up or down requires creating and configuring additional VMs.
     -Higher costs: Continuous uptime incurs more charges compared to managed services.
     
  -3. Azure App Service
      Definition:
      Azure App Service is a Platform-as-a-Service (PaaS) offering that allows developers to deploy web applications easily without managing infrastructure.
      It automatically handles scaling, load balancing, patching, and deployment. Developers only need to focus on the application code, while Azure manages the rest.
      Pros:
      -Ease of deployment: Integrates directly with GitHub for continuous deployment (CI/CD).
      -Built-in scaling and availability: Automatically scales based on traffic and ensures high uptime.
      -Seamless integration: Works perfectly with Azure SQL Database, Blob Storage, and Azure Active Directory.
      -Cost-effective: Pay only for what you use, with no need to manage underlying servers.
      -Automatic management: Azure handles OS updates, SSL certificates, and health monitoring.
      -Complex workflow: Deployment, configuration, and troubleshooting require SSH access and manual setup.
     
      Cons:
      -Limited control: You can’t access or modify the underlying operating system.
      -Less flexibility for background tasks: Long-running or scheduled background processes may require separate services (like Azure Functions).

  For this project, Azure App Service is the most appropriate choice for deploying the Flask CMS application.
  It offers a managed, scalable, and secure environment that eliminates the need for infrastructure maintenance.
  Since this project integrates multiple Azure services — such as Azure SQL Database, Azure Blob Storage, and Azure Active Directory (for Microsoft login) — App Service simplifies
  deployment by offering built-in integrations for all of these.
  The ability to automatically scale and the ease of deployment using GitHub Actions make App Service highly suitable for a project of this scale and nature.
### Assess app changes that would change your decision.
*Detail how the app and any other needs would have to change for you to change your decision in the last section.* 
When the Decision Might Change:
A Virtual Machine might be considered instead of App Service if:
The application needs custom OS configurations or software installations unavailable in App Service.
The app must run background daemons, batch jobs, or non-HTTP services.
There’s a requirement for fine-grained control over the server environment.
The system scales into multiple interconnected services (in which case Azure Kubernetes Service might also be suitable).
If the CMS added features such as: Background AI/ML tasks (e.g., automated image tagging, analytics) ,File conversions or large video uploads, Batch data processing then App Service’s request-timeout and runtime limits could become restrictive.
In that case, I would use a Virtual Machine or integrate with Azure Functions or Azure Batch to handle long-running or compute-intensive tasks.

Conclusion:
In conclusion, Azure App Service is the ideal choice for deploying the Article CMS web application.
It provides a cost-effective, scalable, and fully managed environment that perfectly supports the project’s architecture — connecting a Flask web app to Azure SQL, Blob Storage, and Microsoft Authentication with minimal configuration.
By choosing App Service, the focus remains on building and improving the application, rather than managing infrastructure, resulting in faster development, simplified maintenance, and reliable performance.
