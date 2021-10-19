# Design a compute solution

## recommend a solution for compute provisioning

### [Choose an Azure compute service for your application](https://docs.microsoft.com/en-us/azure/architecture/guide/technology-choices/compute-decision-tree?WT.mc_id=thomasmaurer-blog-thmaure)

![Compute Choices](https://docs.microsoft.com/en-us/azure/architecture/guide/technology-choices/images/compute-choices.png)

Definitions:

- "Lift and shift" is a strategy for migrating a workload to the cloud without redesigning the application or making code changes. Also called rehosting. For more information, see Azure migration and modernization center.
- Cloud optimized is a strategy for migrating to the cloud by refactoring an application to take advantage of cloud-native features and capabilities.

#### Understand the basic features

If you're not familiar with the Azure service selected in the previous step, read the overview documentation to understand the basics of the service.

- App Service. A managed service for hosting web apps, mobile app back ends, RESTful APIs, or automated business processes.
- Azure Spring Cloud. A managed service designed and optimized for hosting Spring Boot apps.
- Azure Kubernetes Service (AKS). A managed Kubernetes service for running containerized applications.
- Batch. A managed service for running large-scale parallel and high-performance computing (HPC) applications
- Container Instances. The fastest and simplest way to run a container in Azure, without having to provision any virtual machines and without having to adopt a higher-level service.
- Functions. A managed FaaS service.
- Service Fabric. A distributed systems platform that can run in many environments, including Azure or on premises.
- Virtual machines. Deploy and manage VMs inside an Azure virtual network.

#### Understand the hosting models

Cloud services, including Azure services, generally fall into three categories: IaaS, PaaS, or FaaS. (There is also SaaS, software-as-a-service, which is out of scope for this article.) It's useful to understand the differences.

**Infrastructure-as-a-Service** (IaaS) lets you provision individual VMs along with the associated networking and storage components. Then you deploy whatever software and applications you want onto those VMs. This model is the closest to a traditional on-premises environment, except that Microsoft manages the infrastructure. You still manage the individual VMs.

**Platform-as-a-Service** (PaaS) provides a managed hosting environment, where you can deploy your application without needing to manage VMs or networking resources. Azure App Service is a PaaS service.

**Functions-as-a-Service** (FaaS) goes even further in removing the need to worry about the hosting environment. In a FaaS model, you simply deploy your code and the service automatically runs it. Azure Functions is a FaaS service.

There is a spectrum from IaaS to pure PaaS. For example, Azure VMs can autoscale by using virtual machine scale sets. This automatic scaling capability isn't strictly PaaS, but it's the type of management feature found in PaaS services.

In general, there is a tradeoff between control and ease of management. IaaS gives the most control, flexibility, and portability, but you have to provision, configure and manage the VMs and network components you create. FaaS services automatically manage nearly all aspects of running an application. PaaS services fall somewhere in between.

|Criteria	|Virtual Machines	|App Service	|Azure Spring Cloud	|Service Fabric	|Azure Functions	|Azure Kubernetes Service	|Container Instances	|Azure Batch|
|:--|:--|:--|:--|:--|:--|:--|:--|:--|
|Application composition	|Agnostic	|Applications, containers|	Applications, microservices	|Services, guest executables, containers	|Functions	|Containers	|Containers	|Scheduled jobs|
|Density	|Agnostic|	Multiple apps per instance via app service plans	|Multiple apps per service instance|	Multiple services per VM	|Serverless 	|Multiple containers per node	|No dedicated instances|	Multiple apps per VM|
|Minimum number of nodes	|1|	1	|2|	5|	Serverless|	3|	No dedicated nodes|	1|
|State management|	Stateless or Stateful|	Stateless|	Stateless|Stateless or stateful|	Stateless|	Stateless or Stateful|	Stateless	|Stateless|
|Web hosting	|Agnostic	|Built in	|Built in	|Agnostic	|Not applicable	|Agnostic	|Agnostic	|No|
|Can be deployed to dedicated VNet?	|Supported	|Supported|	Supported|	Supported	|Supported|	Supported	|Supported	|Supported|
|Hybrid connectivity	|Supported|	Supported |Supported|	Supported|	Supported |Supported|	Not supported	|Supported|

#### DevOps

|Criteria	|Virtual Machines	|App Service	|Azure Spring Cloud	|Service Fabric	|Azure Functions	|Azure Kubernetes Service|	Container Instances|	Azure Batch|
|:--|:--|:--|:--|:--|:--|:--|:--|:--|
|Local debugging	|Agnostic	|IIS Express, others|	Visual Studio Code, Intellij, Eclipse|	Local node cluster|	Visual Studio or Azure Functions CLI|	Minikube, others|	Local container runtime	|Not supported|
|Programming model	|Agnostic	|Web and API applications, WebJobs for background tasks	|Spring Boot, Steeltoe|	Guest executable, Service model, Actor model, Containers|	Functions with triggers	|Agnostic|	Agnostic	|Command line application|
|Application update	|No built-in support|	Deployment slots|	Rolling upgrade, Blue-green deployment|	Rolling upgrade (per service)|	Deployment slots|Rolling update	|Not applicable||

#### Scalability

|Criteria	|Virtual Machines	|App Service	|Azure Spring Cloud	|Service Fabric	|Azure Functions|	Azure Kubernetes Service	|Container Instances	|Azure Batch|
|:--|:--|:--|:--|:--|:--|:--|:--|:--|
|Autoscaling	|Virtual machine scale sets	|Built-in service	|Built-in service	|Virtual machine scale sets	|Built-in service	|Pod auto-scaling1, cluster auto-scaling2	|Not supported|	N/A|
|Load balancer|	Azure Load Balancer	|Integrated|	Integrated	|Azure Load Balancer	|Integrated	|Azure Load Balancer or Application Gateway|	No built-in support	|Azure Load Balancer|
|Scale limit	|Platform image: 1000 nodes per scale set, Custom image: 600 nodes per scale set|	30 instances, 100 with App Service Environment|	500 app instances in Standard|	100 nodes per scale set	|200 instances per Function app|100 nodes per cluster (default limit)	|20 container groups per subscription (default limit).	|20 core limit (default limit).|

#### [Availability](https://docs.microsoft.com/en-us/azure/architecture/guide/technology-choices/compute-decision-tree?WT.mc_id=thomasmaurer-blog-thmaure#availability)

#### [Security](https://docs.microsoft.com/en-us/azure/architecture/guide/technology-choices/compute-decision-tree?WT.mc_id=thomasmaurer-blog-thmaure#security)

#### [Cost](https://docs.microsoft.com/en-us/azure/architecture/guide/technology-choices/compute-decision-tree?WT.mc_id=thomasmaurer-blog-thmaure#other-criteria)

|Criteria	|Virtual Machines	|App Service	App |Spring Cloud	|Service Fabric	|Azure Functions	|Azure Kubernetes Service	|Container Instances|	Azure Batch|
|:--|:--|:--|:--|:--|:--|:--|:--|:--|
|SSL	|Configured in VM	|Supported|	Supported|	Supported	|Supported	|Ingress controller	|Use sidecar container	|Supported|
|Suitable architecture styles	|N-Tier, Big compute (HPC)|	Web-Queue-Worker, N-Tier|	Spring Boot, Microservices|	Microservices, Event-driven architecture|	Microservices, Event-driven architecture|	Microservices, Event-driven architecture	|Microservices, task automation, batch jobs|	Big compute (HPC)|

## determine appropriate compute technologies, including virtual machines, App Services, Service Fabric, Azure Functions, Windows Virtual Desktop, and containers

### [Choose an Azure compute service for your application](https://docs.microsoft.com/en-us/azure/architecture/guide/technology-choices/compute-decision-tree?WT.mc_id=thomasmaurer-blog-thmaure)

See above

### [App Service](https://docs.microsoft.com/en-us/azure/app-service?WT.mc_id=thomasmaurer-blog-thmaure)

### [Azure Kubernetes Service (AKS)](https://docs.microsoft.com/en-us/azure/aks/intro-kubernetes?WT.mc_id=thomasmaurer-blog-thmaure)

Azure Kubernetes Service (AKS) simplifies deploying a managed Kubernetes cluster in Azure by offloading the operational overhead to Azure. As a hosted Kubernetes service, Azure handles critical tasks, like health monitoring and maintenance. Since Kubernetes masters are managed by Azure, you only manage and maintain the agent nodes. Thus, AKS is free; you only pay for the agent nodes within your clusters, not for the masters.

You can create an AKS cluster using:

- The Azure CLI
- The Azure portal
- Azure PowerShell
- Using template-driven deployment options, like Azure Resource Manager templates and Terraform

When you deploy an AKS cluster, the Kubernetes master and all nodes are deployed and configured for you. Advanced networking, Azure Active Directory (Azure AD) integration, monitoring, and other features can be configured during the deployment process.

For more information on Kubernetes basics, see [Kubernetes core concepts for AKS](https://docs.microsoft.com/en-us/azure/aks/concepts-clusters-workloads).

>  Note
>
> This service supports Azure Lighthouse, which lets service providers sign in to their own tenant to manage subscriptions and resource groups that customers have delegated.

> AKS also supports Windows Server containers.

#### Access, security, and monitoring

For improved security and management, AKS lets you integrate with Azure AD to:

- Use Kubernetes role-based access control (Kubernetes RBAC).
- Monitor the health of your cluster and resources.

#### Identity and security management

##### Kubernetes RBAC

To limit access to cluster resources, AKS supports Kubernetes RBAC. Kubernetes RBAC controls access and permissions to Kubernetes resources and namespaces.

##### Azure AD

You can configure an AKS cluster to integrate with Azure AD. With Azure AD integration, you can set up Kubernetes access based on existing identity and group membership. Your existing Azure AD users and groups can be provided with an integrated sign-on experience and access to AKS resources.

For more information on identity, see [Access and identity options for AKS](https://docs.microsoft.com/en-us/azure/aks/concepts-identity).

To secure your AKS clusters, see [Integrate Azure Active Directory with AKS](https://docs.microsoft.com/en-us/azure/aks/azure-ad-integration-cli).

#### Integrated logging and monitoring

Azure Monitor for Container Health collects memory and processor performance metrics from containers, nodes, and controllers within your AKS cluster and deployed applications. You can review both container logs and the [Kubernetes master logs](https://docs.microsoft.com/en-us/azure/aks/monitor-aks-reference#resource-logs), which are:

- Stored in an Azure Log Analytics workspace.
- Available through the Azure portal, Azure CLI, or a REST endpoint.

For more information, see [Monitor Azure Kubernetes Service container health](https://docs.microsoft.com/en-us/azure/azure-monitor/containers/container-insights-overview).

#### Clusters and nodes

AKS nodes run on Azure virtual machines (VMs). With AKS nodes, you can connect storage to nodes and pods, upgrade cluster components, and use GPUs. AKS supports Kubernetes clusters that run multiple node pools to support mixed operating systems and Windows Server containers.

For more information about Kubernetes cluster, node, and node pool capabilities, see [Kubernetes core concepts for AKS](https://docs.microsoft.com/en-us/azure/aks/concepts-clusters-workloads).

#### Cluster node and pod scaling

As demand for resources change, the number of cluster nodes or pods that run your services automatically scales up or down. You can adjust both the horizontal pod autoscaler or the cluster autoscaler to adjust to demands and only run necessary resources.

For more information, see [Scale an Azure Kubernetes Service (AKS) cluster](https://docs.microsoft.com/en-us/azure/aks/tutorial-kubernetes-scale).

#### Cluster node upgrades

AKS offers multiple Kubernetes versions. As new versions become available in AKS, you can upgrade your cluster using the Azure portal or Azure CLI. During the upgrade process, nodes are carefully cordoned and drained to minimize disruption to running applications.

To learn more about lifecycle versions, see [Supported Kubernetes versions in AKS](https://docs.microsoft.com/en-us/azure/aks/supported-kubernetes-versions). For steps on how to upgrade, see [Upgrade an Azure Kubernetes Service (AKS) cluster](https://docs.microsoft.com/en-us/azure/aks/upgrade-cluster).

#### GPU-enabled nodes

AKS supports the creation of GPU-enabled node pools. Azure currently provides single or multiple GPU-enabled VMs. GPU-enabled VMs are designed for compute-intensive, graphics-intensive, and visualization workloads.

For more information, see [Using GPUs on AKS](https://docs.microsoft.com/en-us/azure/aks/gpu-cluster).

#### Confidential computing nodes (public preview)

AKS supports the creation of Intel SGX-based, confidential computing node pools (DCSv2 VMs). Confidential computing nodes allow containers to run in a hardware-based, trusted execution environment (enclaves). Isolation between containers, combined with code integrity through attestation, can help with your defense-in-depth container security strategy. Confidential computing nodes support both confidential containers (existing Docker apps) and enclave-aware containers.

For more information, see [Confidential computing nodes on AKS](https://docs.microsoft.com/en-us/azure/confidential-computing/confidential-nodes-aks-overview).

#### Storage volume support

To support application workloads, you can mount static or dynamic storage volumes for persistent data. Depending on the number of connected pods expected to share the storage volumes, you can use storage backed by either:

- Azure Disks for single pod access, or
- Azure Files for multiple, concurrent pod access.

For more information, see [Storage options for applications in AKS](https://docs.microsoft.com/en-us/azure/aks/concepts-storage).

Get started with dynamic persistent volumes using [Azure Disks](https://docs.microsoft.com/en-us/azure/aks/azure-disks-dynamic-pv) or [Azure Files](https://docs.microsoft.com/en-us/azure/aks/azure-files-dynamic-pv).

#### Virtual networks and ingress

An AKS cluster can be deployed into an existing virtual network. In this configuration, every pod in the cluster is assigned an IP address in the virtual network, and can directly communicate with:

- Other pods in the cluster
- Other nodes in the virtual network.

Pods can also connect to other services in a peered virtual network and to on-premises networks over ExpressRoute or site-to-site (S2S) VPN connections.

For more information, see the [Network concepts for applications in AKS](https://docs.microsoft.com/en-us/azure/aks/concepts-network).

#### Ingress with HTTP application routing

The HTTP application routing add-on helps you easily access applications deployed to your AKS cluster. When enabled, the HTTP application routing solution configures an ingress controller in your AKS cluster.

As applications are deployed, publicly accessible DNS names are autoconfigured. The HTTP application routing sets up a DNS zone and integrates it with the AKS cluster. You can then deploy Kubernetes ingress resources as normal.

To get started with ingress traffic, see [HTTP application routing](https://docs.microsoft.com/en-us/azure/aks/http-application-routing).

#### Development tooling integration

Kubernetes has a rich ecosystem of development and management tools that work seamlessly with AKS. These tools include Helm and the Kubernetes extension for Visual Studio Code.

Azure provides several tools that help streamline Kubernetes, such as DevOps Starter.

#### DevOps Starter

DevOps Starter provides a simple solution for bringing existing code and Git repositories into Azure. DevOps Starter automatically:

- Creates Azure resources (such as AKS);
- Configures a release pipeline in Azure DevOps Services that includes a build pipeline for CI;
- Sets up a release pipeline for CD; and,
- Generates an Azure Application Insights resource for monitoring.

For more information, see [DevOps Starter](https://docs.microsoft.com/en-us/azure/devops-project/overview).

#### Docker image support and private container registry

AKS supports the Docker image format. For private storage of your Docker images, you can integrate AKS with Azure Container Registry (ACR).

To create a private image store, see [Azure Container Registry](https://docs.microsoft.com/en-us/azure/container-registry/container-registry-intro).

### [Batch](https://docs.microsoft.com/en-us/azure/batch/batch-technical-overview?WT.mc_id=thomasmaurer-blog-thmaure)

Use Azure Batch to run large-scale parallel and high-performance computing (HPC) batch jobs efficiently in Azure. Azure Batch creates and manages a pool of compute nodes (virtual machines), installs the applications you want to run, and schedules jobs to run on the nodes. There's no cluster or job scheduler software to install, manage, or scale. Instead, you use [Batch APIs and tools](https://docs.microsoft.com/en-us/azure/batch/batch-apis-tools), command-line scripts, or the Azure portal to configure, manage, and monitor your jobs.

Developers can use Batch as a platform service to build SaaS applications or client apps where large-scale execution is required. For example, you can build a service with Batch to run a Monte Carlo risk simulation for a financial services company, or a service to process many images.

There is no additional charge for using Batch. You only pay for the underlying resources consumed, such as the virtual machines, storage, and networking.

For a comparison between Batch and other HPC solution options in Azure, see [High Performance Computing (HPC) on Azure](https://docs.microsoft.com/en-us/azure/architecture/topics/high-performance-computing/).

#### Run parallel workloads

Batch works well with intrinsically parallel (also known as "embarrassingly parallel") workloads. These workloads have applications which can run independently, with each instance completing part of the work. When the applications are executing, they might access some common data, but they don't communicate with other instances of the application. Intrinsically parallel workloads can therefore run at a large scale, determined by the amount of compute resources available to run applications simultaneously.

Some examples of intrinsically parallel workloads you can bring to Batch:

- Financial risk modeling using Monte Carlo simulations
- VFX and 3D image rendering
- Image analysis and processing
- Media transcoding
- Genetic sequence analysis
- Optical character recognition (OCR)
- Data ingestion, processing, and ETL operations
- Software test execution

You can also use Batch to run [tightly coupled workloads](https://docs.microsoft.com/en-us/azure/batch/batch-mpi), where the applications you run need to communicate with each other, rather than running independently. Tightly coupled applications normally use the Message Passing Interface (MPI) API. You can run your tightly coupled workloads with Batch using [Microsoft MPI](https://docs.microsoft.com/en-us/message-passing-interface/microsoft-mpi) or Intel MPI. Improve application performance with specialized [HPC](https://docs.microsoft.com/en-us/azure/virtual-machines/sizes-hpc) and [GPU-optimized](https://docs.microsoft.com/en-us/azure/virtual-machines/sizes-gpu) VM sizes.

Some examples of tightly coupled workloads:

- Finite element analysis
- Fluid dynamics
- Multi-node AI training

Many tightly coupled jobs can be run in parallel using Batch. For example, you can perform multiple simulations of a liquid flowing through a pipe with varying pipe widths.

#### Additional Batch capabilities

Batch supports large-scale rendering workloads with rendering tools including Autodesk Maya, 3ds Max, Arnold, and V-Ray.

You can also run Batch jobs as part of a larger Azure workflow to transform data, managed by tools such as [Azure Data Factory](https://docs.microsoft.com/en-us/azure/data-factory/transform-data-using-dotnet-custom-activity).

#### How it works

A common scenario for Batch involves scaling out intrinsically parallel work, such as the rendering of images for 3D scenes, on a pool of compute nodes. This pool can be your "render farm" that provides tens, hundreds, or even thousands of cores to your rendering job.

The following diagram shows steps in a common Batch workflow, with a client application or hosted service using Batch to run a parallel workload.

![How Batch works](https://docs.microsoft.com/en-us/azure/batch/media/batch-technical-overview/tech_overview_03.png)

|Step	|Description|
|:--|:--|
|1. Upload **input files** and the **applications** to process those files to your Azure Storage account.	|The input files can be any data that your application processes, such as financial modeling data, or video files to be transcoded. The application files can include scripts or applications that process the data, such as a media transcoder.|
|2. Create a Batch **pool** of compute nodes in your Batch account, a **job** to run the workload on the pool, and **tasks** in the job.	|[Compute nodes](https://docs.microsoft.com/en-us/azure/batch/nodes-and-pools) are the VMs that execute your [tasks](https://docs.microsoft.com/en-us/azure/batch/jobs-and-tasks). Specify properties for your pool, such as the number and size of the nodes, a Windows or Linux VM image, and an application to install when the nodes join the pool. Manage the cost and size of the pool by using [low-priority VMs](https://docs.microsoft.com/en-us/azure/batch/batch-low-pri-vms) or by [automatically scaling](https://docs.microsoft.com/en-us/azure/batch/batch-automatic-scaling) the number of nodes as the workload changes.<br /><br />When you add tasks to a job, the Batch service automatically schedules the tasks for execution on the compute nodes in the pool. Each task uses the application that you uploaded to process the input files.|
|3. Download **input files** and the **applications** to Batch	|Before each task executes, it can download the input data that it will process to the assigned node. If the application isn't already installed on the pool nodes, it can be downloaded here instead. When the downloads from Azure Storage complete, the task executes on the assigned node.|
|4. Monitor **task execution**	|As the tasks run, query Batch to monitor the progress of the job and its tasks. Your client application or service communicates with the Batch service over HTTPS. Because you may be monitoring thousands of tasks running on thousands of compute nodes, be sure to [query the Batch service efficiently](https://docs.microsoft.com/en-us/azure/batch/batch-efficient-list-queries).|
|5. Upload **task output**	|As the tasks complete, they can upload their result data to Azure Storage. You can also retrieve files directly from the file system on a compute node.|
|6. Download **output files**	|When your monitoring detects that the tasks in your job have completed, your client application or service can download the output data for further processing.|

Keep in mind that the workflow described above is just one way to use Batch, and there are many other features and options. For example, you can execute [multiple tasks in parallel](https://docs.microsoft.com/en-us/azure/batch/batch-parallel-node-tasks) on each compute node. Or you can use [job preparation and completion tasks](https://docs.microsoft.com/en-us/azure/batch/batch-job-prep-release) to prepare the nodes for your jobs, then clean up afterward.

See [Batch service workflow and resources](https://docs.microsoft.com/en-us/azure/batch/batch-service-workflow-features) for an overview of features such as pools, nodes, jobs, and tasks. Also see the latest [Batch service updates](https://azure.microsoft.com/updates/?product=batch).

#### In-region data residency

Azure Batch does not move or store customer data out of the region in which it is deployed.

- [ ] [Container Instances](https://docs.microsoft.com/en-us/azure/container-instances/container-instances-overview?WT.mc_id=thomasmaurer-blog-thmaure)
- [ ] [Functions](https://docs.microsoft.com/en-us/azure/azure-functions/functions-overview?WT.mc_id=thomasmaurer-blog-thmaure)
- [ ] [Service Fabric](https://docs.microsoft.com/en-us/azure/service-fabric/service-fabric-overview?WT.mc_id=thomasmaurer-blog-thmaure)
- [ ] [Virtual machines](https://docs.microsoft.com/en-us/azure/virtual-machines?WT.mc_id=thomasmaurer-blog-thmaure)
- [ ] [What is Windows Virtual Desktop?](https://docs.microsoft.com/en-us/azure/virtual-desktop/overview?WT.mc_id=thomasmaurer-blog-thmaure)

## recommend a solution for containers

- [ ] [Azure Kubernetes Service (AKS)](https://docs.microsoft.com/en-us/azure/aks/intro-kubernetes?WT.mc_id=thomasmaurer-blog-thmaure)
- [ ] [What is Azure Container Instances?](https://docs.microsoft.com/en-us/azure/container-instances/container-instances-overview?WT.mc_id=thomasmaurer-blog-thmaure)
- [ ] [Introduction to private Docker container registries in Azure](https://docs.microsoft.com/en-us/azure/container-registry/container-registry-intro?WT.mc_id=thomasmaurer-blog-thmaure)

## recommend a solution for automating compute management

- [ ] [An introduction to Azure Automation](https://docs.microsoft.com/en-us/azure/automation/automation-intro?WT.mc_id=thomasmaurer-blog-thmaure)

- [ ] [Overview – What is Azure Logic Apps?](https://docs.microsoft.com/en-us/azure/logic-apps/logic-apps-overview?WT.mc_id=thomasmaurer-blog-thmaure)