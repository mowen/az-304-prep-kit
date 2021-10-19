#  Design Infrastructure (25-30%)

## [Design a compute solution](/5-infrastructure/notes-compute.md)

- [x] recommend a solution for compute provisioning
  - [x] [Choose an Azure compute service for your application](https://docs.microsoft.com/en-us/azure/architecture/guide/technology-choices/compute-decision-tree?WT.mc_id=thomasmaurer-blog-thmaure)

- [ ] determine appropriate compute technologies, including virtual machines, App Services, Service Fabric, Azure Functions, Windows Virtual Desktop, and containers
  - [x] [Choose an Azure compute service for your application](https://docs.microsoft.com/en-us/azure/architecture/guide/technology-choices/compute-decision-tree?WT.mc_id=thomasmaurer-blog-thmaure)
  - [x] [App Service](https://docs.microsoft.com/en-us/azure/app-service?WT.mc_id=thomasmaurer-blog-thmaure)
  - [x] [Azure Kubernetes Service (AKS)](https://docs.microsoft.com/en-us/azure/aks/intro-kubernetes?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [Batch](https://docs.microsoft.com/en-us/azure/batch/batch-technical-overview?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [Container Instances](https://docs.microsoft.com/en-us/azure/container-instances/container-instances-overview?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [Functions](https://docs.microsoft.com/en-us/azure/azure-functions/functions-overview?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [Service Fabric](https://docs.microsoft.com/en-us/azure/service-fabric/service-fabric-overview?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [Virtual machines](https://docs.microsoft.com/en-us/azure/virtual-machines?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [What is Windows Virtual Desktop?](https://docs.microsoft.com/en-us/azure/virtual-desktop/overview?WT.mc_id=thomasmaurer-blog-thmaure)

- [ ] recommend a solution for containers
  - [ ] [Azure Kubernetes Service (AKS)](https://docs.microsoft.com/en-us/azure/aks/intro-kubernetes?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [What is Azure Container Instances?](https://docs.microsoft.com/en-us/azure/container-instances/container-instances-overview?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [Introduction to private Docker container registries in Azure](https://docs.microsoft.com/en-us/azure/container-registry/container-registry-intro?WT.mc_id=thomasmaurer-blog-thmaure)

- [ ] recommend a solution for automating compute management
  - [ ] [An introduction to Azure Automation](https://docs.microsoft.com/en-us/azure/automation/automation-intro?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [Overview – What is Azure Logic Apps?](https://docs.microsoft.com/en-us/azure/logic-apps/logic-apps-overview?WT.mc_id=thomasmaurer-blog-thmaure)

## Design a network solution

- [ ] recommend a network architecture (hub and spoke, Virtual WAN)
  - [ ] [Hub-spoke network topology with Azure Virtual WAN](https://docs.microsoft.com/en-us/azure/architecture/networking/hub-spoke-vwan-architecture?WT.mc_id=thomasmaurer-blog-thmaure)

- [ ] recommend a solution for network addressing and name resolution
  - [ ] [Name resolution for resources in Azure virtual networks](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [Use Azure DNS to provide custom domain settings for an Azure service](https://docs.microsoft.com/en-us/azure/dns/dns-custom-domain?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [Tutorial: Host your domain in Azure DNS](https://docs.microsoft.com/en-us/azure/dns/dns-delegate-domain-azure-dns?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [Quickstart: Create an Azure private DNS zone using the Azure portal](https://docs.microsoft.com/en-us/azure/dns/private-dns-getstarted-portal?WT.mc_id=thomasmaurer-blog-thmaure)

- recommend a solution for network provisioning
  - [ ] [What is Azure Virtual Network?](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-networks-overview?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [Virtual network service endpoint policies for Azure Storage](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-network-service-endpoint-policies-overview?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [Virtual Network service endpoints](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-network-service-endpoints-overview?WT.mc_id=thomasmaurer-blog-thmaure)

- [ ] recommend a solution for network security including Private Link, firewalls, gateways, network segmentation (perimeter networks/DMZs/NVAs)
  - [ ] [Network security groups](https://docs.microsoft.com/en-us/azure/virtual-network/security-overview?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [Application security groups](https://docs.microsoft.com/en-us/azure/virtual-network/security-overview?WT.mc_id=thomasmaurer-blog-thmaure#application-security-groups)
  - [ ] [Virtual network service endpoints](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-network-service-endpoints-overview?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [Virtual network security FAQ](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-networks-faq?WT.mc_id=thomasmaurer-blog-thmaure#security)
  - [ ] [What is Azure Firewall?](https://docs.microsoft.com/en-us/azure/firewall/overview)
  - [ ] [Deploy highly available NVAs](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/dmz/nva-ha?WT.mc_id=thomasmaurer-blog-thmaure)

- [ ] recommend a solution for network connectivity to the Internet, on-premises networks, and other Azure virtual networks
  - [ ] [What is VPN Gateway?](https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpngateways?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [ExpressRoute overview](https://docs.microsoft.com/en-us/azure/expressroute/expressroute-introduction?WT.mc_id=thomasmaurer-blog-thmaure)

- [ ] recommend a solution for automating network management
  - [ ] [What is Azure Virtual Network?](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-networks-overview?WT.mc_id=thomasmaurer-blog-thmaure)

- [ ] recommend a solution for load balancing and traffic routing
  - [ ] [Overview of load-balancing options in Azure](https://docs.microsoft.com/en-us/azure/architecture/guide/technology-choices/load-balancing-overview?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [Front Door](https://docs.microsoft.com/en-us/azure/frontdoor/front-door-overview)
  - [ ] [Traffic Manager](https://docs.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [Application Gateway](https://docs.microsoft.com/en-us/azure/application-gateway/overview?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [Azure Load Balancer](https://docs.microsoft.com/en-us/azure/load-balancer/load-balancer-overview?WT.mc_id=thomasmaurer-blog-thmaure)

## Design an application architecture

- [ ] recommend a microservices architecture including Event Grid, Event Hubs, Service Bus, Storage Queues, Logic Apps, Azure Functions, and webhooks
  - [ ] [Microservices architecture style](https://docs.microsoft.com/en-us/azure/architecture/guide/architecture-styles/microservices?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [Event Grid](https://docs.microsoft.com/en-us/azure/event-grid/overview?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [Event Hub](https://docs.microsoft.com/en-us/azure/event-hubs/event-hubs-features?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [Service Bus](https://docs.microsoft.com/en-us/azure/service-bus-messaging/service-bus-messaging-overview?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [Storage Queues](https://docs.microsoft.com/en-us/azure/storage/queues/storage-queues-introduction?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [Logic Apps](https://docs.microsoft.com/en-us/azure/logic-apps/logic-apps-overview?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [Azure Functions](https://docs.microsoft.com/en-us/azure/azure-functions/functions-overview?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [webhooks](https://docs.microsoft.com/en-us/azure/automation/automation-webhooks?WT.mc_id=thomasmaurer-blog-thmaure)

- [ ] recommend an orchestration solution for deployment of applications including ARM templates, Logic Apps, or Azure Functions
  - [ ] [Extend Azure Resource Manager template functionality](https://docs.microsoft.com/en-us/azure/architecture/building-blocks/extending-templates?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [Azure Resource Manager templates overview](https://docs.microsoft.com/en-us/azure/azure-resource-manager/templates/overview?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [Tutorial: Create and deploy your first Azure Resource Manager template](https://docs.microsoft.com/en-us/azure/azure-resource-manager/templates/template-tutorial-create-first-template?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [Logic Apps](https://docs.microsoft.com/en-us/azure/logic-apps/logic-apps-overview?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [Azure Functions](https://docs.microsoft.com/en-us/azure/azure-functions/functions-overview?WT.mc_id=thomasmaurer-blog-thmaure)

- [ ] recommend a solution for API integration
  - [ ] [Basic enterprise integration on Azure](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/enterprise-integration/basic-enterprise-integration?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [API Management](https://azure.microsoft.com/en-us/services/api-management?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [Integration Services](https://azure.microsoft.com/en-us/product-categories/integration?WT.mc_id=thomasmaurer-blog-thmaure)

## Design migrations

- [ ] assess and interpret on-premises servers, data, and applications for migration
  - [ ] [Azure migration center](https://azure.microsoft.com/en-us/migration/)
  - [ ] [About Azure Migrate](https://docs.microsoft.com/en-us/azure/migrate/migrate-services-overview?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [Prepare VMware VMs for assessment and migration to Azure](https://docs.microsoft.com/en-us/azure/migrate/tutorial-prepare-vmware?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [Assess VMware VMs by using Azure Migrate Server Assessment](https://docs.microsoft.com/en-us/azure/migrate/tutorial-assess-vmware?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [About assessments in Azure Migrate](https://docs.microsoft.com/en-us/azure/migrate/concepts-assessment-calculation?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [Assess the readiness of a SQL Server data estate migrating to Azure SQL Database using the Data Migration Assistant](https://docs.microsoft.com/en-us/sql/dma/dma-assess-sql-data-estate-to-sqldb?WT.mc_id=thomasmaurer-blog-thmaure)

- [ ] recommend a solution for migrating applications and VMs
  - [ ] [About Azure Migrate](https://docs.microsoft.com/en-us/azure/migrate/migrate-services-overview?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [Select a VMware migration option](https://docs.microsoft.com/en-us/azure/migrate/server-migrate-overview?WT.mc_id=thomasmaurer-blog-thmaure)

- [ ] recommend a solution for migration of databases
  - [ ] [Assess the readiness of a SQL Server data estate migrating to Azure SQL Database using the Data Migration Assistant](https://docs.microsoft.com/en-us/sql/dma/dma-assess-sql-data-estate-to-sqldb?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [SQL Server Migration Assistant](https://docs.microsoft.com/en-us/sql/ssma/sql-server-migration-assistant?WT.mc_id=thomasmaurer-blog-thmaure)

- [ ] determine migration scope, including redundant, related, trivial, and outdated data
  - [ ] [How to migrate](https://azure.microsoft.com/en-us/migration/migration-journey?WT.mc_id=thomasmaurer-blog-thmaure)

- [ ] recommend a solution for migrating data (Storage Migration Service, Azure Data Box, Azure File Sync-based migration to hybrid file server)
  - [ ] [Storage Migration Service overview](https://docs.microsoft.com/en-us/windows-server/storage/storage-migration-service/overview?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [What is Azure Data Box?](https://docs.microsoft.com/en-us/azure/databox/data-box-overview?WT.mc_id=thomasmaurer-blog-thmaure)
  - [ ] [What is Azure File Sync?](https://docs.microsoft.com/en-us/azure/storage/file-sync/file-sync-introduction?WT.mc_id=thomasmaurer-blog-thmaure)