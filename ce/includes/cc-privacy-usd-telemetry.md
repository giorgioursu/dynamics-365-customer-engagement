﻿By enabling the Help Improve [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] feature, [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] usage information, such as operating system details, browser details, and [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] version from the computer on which the client is installed, will be sent to [!INCLUDE[cc_Microsoft](cc-microsoft.md)] through a secure connection to Organization Insights and stored in [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Table Storage.  
  
> [!NOTE]
>  Organization Insights provides the System Administrator of a [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] organization with a quick overview of how the org is being used. The System Administrator can view most active users, the number of SDK requests being initiated, and the number of being viewed by SDK users.  
  
 A [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] Administrator enables the Help Improve [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] feature, which is turned off by default, by setting the value of the Global Option: `HelpImproveUSD` to “`True`.” Setting the value to anything but `True` or removing the key from the Global Options list will turn off data collection. A [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] user provides consent for data collection by selecting (and revokes consent by de-selecting) the checkbox in the Help Improve [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] section on About page. While [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] Administrators and users can control whether or not data is collected, they cannot control the specific usage data that is collected and sent if the functionality is enabled.  
  
 A list of the [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] components and services that are involved with Help Improve Unified Service Desk functionality is provided below.  
  
> [!NOTE]
>  For more information about additional [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] service offerings, see the [Microsoft Azure Trust Center](https://azure.microsoft.com/en-us/support/trust-center/).  
  
 [Cloud Services](https://azure.microsoft.com/en-us/services/cloud-services/) OrgInsights Data REST API (Web Role)  
  
 This web role accepts requests from the charts that display data in Organization Insights. The API reads aggregated data from the [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Tables and returns it.  
  
 [Azure Blob Storage](https://azure.microsoft.com/en-us/services/storage/blobs/)  
  
 A [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] Organization’s raw telemetry data is collected by the Monitoring Agent (which runs on every scale group computer) and is uploaded in Bond Format (Binary format) to in [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage.  
  
 [Azure Table Storage](https://azure.microsoft.com/en-us/services/storage/tables/)  
  
 Raw telemetry data in [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage is aggregated and stored in Azure Table Storage, which is read by the Cloud Service.  
  
 [Azure Active Directory](https://azure.microsoft.com/en-us/services/active-directory/)  
  
 Organization Insights uses  [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] Service to authenticate web services.  
  
 [Azure Service Bus](https://azure.microsoft.com/en-us/services/service-bus/)  
  
 The Monitoring Agent creates and queues messages whenever it uploads data to [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob Storage. These messages are picked by the CMA pipe to aggregated the data uploaded.