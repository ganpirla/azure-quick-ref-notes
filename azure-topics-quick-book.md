	✓	Azure Storage Account

	⁃	Access Keys  -  Gives access at Storage accunt level, which means all the containers and its blobs, file shares will be accessible 
	⁃	shared Access Signatures
	⁃	Access Policies
	⁃	Active Directory
	⁃	Storage Account Replications

	✓	Azure Virtual machines

	⁃	Availability Zones
	⁃	Availability Set
	⁃	VM Scale set
	⁃	Terminating the VM
	⁃	Public IP l/ Temp storage unavailable while we do stop only from Portal
	⁃	Azure additional data disk
	⁃	secondary interface
	⁃	VM Resize
	⁃	Custom Image
	⁃	VM conversion to VM scale set
	⁃	VM conversion to VM availability set
	⁃	Dedicated hosts
	⁃	VM can’t be part of 2 different networks but can be part of 2 subnets in a same network
	⁃	Fault Domain 
	⁃	Update domain

	✓	Azure  cloud Shell

	✓	Azure Storage Explorer

	✓	NSG

	✓	ASG

	✓	Jump Server

	✓	Bastion

	✓	Service Endpoints

	✓	Private Endpoints

	✓	Routing

	⁃	System route table ( Default )
	⁃	Custom/User defined route table

	✓	Hub-Spoke model topology

	⁃	Useful blog :  https://blog.kloud.com.au/2018/08/10/hub-spoke-communication-using-vnet-peering-and-user-defined-routes/
	⁃	Useful while setting up connectivity between On-Prem to Azure cloud 
	⁃	Hub-Vnet is the endpoint vNet in Azure Cloud with gateway transit so that we can avoid gateway network from each vNet
	⁃	Can avoid many peering between vNets as well.
	⁃	Peering between Hub and other  Vnets
	⁃	Peering with Gateway transit allowed.
	⁃	Communication  between spoke Vnet to Spoke Vnet ? Create routable for each spoke network and add as a resource in each spoke Vnet subnet. Route next hop must be 4th IP address of gateway subnet.
	⁃	spoke route table should  have Address CIDR as other Spoke CIDR and Next HOP as a GW 4th IP address. 


	✓	gateway Transit 

	⁃	Useful while setting up connectivity between On-Prem to Azure cloud 
	⁃	Hub-Vnet is the endpoint vNet in Azure Cloud with gateway transit so that we can avoid gateway network from each vNet
	⁃	Can avoid many peering between vNets as well.
	⁃	Gateway transit is a peering property that lets one virtual network use the VPN gateway in the peered virtual network for cross-premises or VNet-to-VNet connectivity. 

	✓	gateway subnet

	⁃	The gateway subnet is part of the virtual network IP address range that you specify when configuring your virtual network. It contains the IP addresses that the virtual network gateway resources and services use. 
	⁃	

	✓	VPN gateway

	⁃	Microsoft Azure gives you the possibility to work in a hybrid work environment with which you can integrate the servers and physical equipment of your company with the cloud. To carry out this task, our proposal is based on the use of a virtual private network (azure Virtual Private Network or VPN) that works as a gateway.  

	✓	Virtual Network  gateway

	⁃	used to send encrypted traffic between an Azure virtual network and an on-premises location over the public Internet. 

	✓	Local gateway

	⁃	Representation of On-Prem network Address details
	⁃	In must be needed to be created in Azure for S2S
	⁃	Need to mentioned On-Prem Datacnter public router details and what IP address  need to connect to Azure 


	✓	Virtual network Peering

	⁃	Can establish a connection between different vNets via Azure backbone network.

	✓	Point-to-Site VPN

	⁃	Blog:  https://techcommunity.microsoft.com/t5/itops-talk-blog/step-by-step-creating-an-azure-point-to-site-vpn/ba-p/326264
	⁃	root, Client Certification based VPN connection via Public network.
	⁃	We can use Windows Radius Server as well for centrally managed policy server along with Windows Activity Directory.
	⁃	root Certificate has to me mentioned while creating the P2S connection and then VPN binary can be downloaded and can be installed in client machine.
	⁃	if at we need to use more clients we can generate client  certificate from root certificate and then we can have as many as clients to use P2S connection
	⁃	root certificate do not export as a private key and save it locally to copy the key in Azure while  creating the P2S connection.
	⁃	Client certificate export as a private key and enable certificate privacy with password.
	⁃	Only root certificate will be used in Azure VPN, Client certificate can be installed on client machines which need P2S connections
	⁃	P2S authentication types are - Azure Certification, Radium Authentication and azure Active Directory
	⁃	If there are many clients to use P2S, client certificate has to be copied locally and installed after VPN is installed.
	⁃	This sort of connection is based off certificates for authentication
	⁃	You need to have a root certificate in place that needs to be uploaded to Azure for the point-to-site connection.
	⁃	A client certificate needs to be generated from the root certificate. This client certificate needs to be on each client computer that needs to connect to the Azure virtual network via the Point-to-Site connection.
	⁃	To generate the certificates, you can use a Certificate authority or generate a self-signed certificate using PowerShell. 


	✓	Site-to-Site VPN

	⁃	Local gateway with On-Prem Routing device IP address and On-Prem Company network CIDR Range
	⁃	Virtual Network gateway is created in Hub-Vnet 
	⁃	S2S also created by user Hub-Vnet
	⁃	Local gateway created under Hub-Vnet with IP address of Routing device and On Prem Address range 
	⁃	Peering from Hub-Vnet to remaining Prod, Test and Dev
	⁃	Dail in setup created for Virtual network gateway created under Hub-Vnet
	⁃	Static routes added for Prod, Dev and Test
	⁃	Because of Peering is already done from Hub-Vnet to Prod, Dev and test Vnet able to access all the servers from Pros, Dev and test from On-Prem
	⁃	To Have connection between Prod, Dev and Test -  Need to create route rule for Prod, Dev and test and  add route rule for each  subnet of Prod, Dev and test

	✓	Azure Expressroute

	⁃	https://channel9.msdn.com/Blogs/bfrank/Hybrid-Network-ExpressRoute-interxion-Azure
	⁃	Create Express Route Circuit 
	⁃	It gives you a service key
	⁃	Share the service key to Provider to complete the provision process , Wait until circuit status as enabled and provider status as provisioned 
	⁃	
	⁃	

	✓	Azure Site Recovery

	⁃	Source Site : Cache Storage Account will be created  in source Site under  site recovery vault RG which is in target region  while deploying the Disaster Recovery  for Data changes from Virtual machines to Cache Storage.cache storage which will be used to temporarily store data in the source region before replicating to target. Replicating VM disks to temporary storage in the same region.
	⁃	There will be 2  RG will be created in Target Site 1)  RG for VM to maintain  in that RG with all needed network, Disk replicas of source vm as well   2)  Recovery vault RG that is with  automation  backup account and site recovery vault to maintain replicated items of the Soure VMs data replicated  with replication policy not VMs and cache storage that is located in source site.
	⁃	During the testfailover VMs will be created based on the data have it in Recovery vault
	⁃	While doing the test failover it does following -  Do validate Prerequisites, Create Virtual machine, Prepare Virtual machine, Start virtual machine. At this stage VM will be running in both locations as it is test failover and new VM in target site won’t be having Public IP address If need we need to assign Public IP address to Newly failover vm in Target Site and it will have Same Private IP address.New Disk will be created based on the vm disk replica we have it in Target site RG.
	⁃	Failover - In real situation we can initiate a failover to have Source Site vm to be available in target Site with same name this means source vm can’t be running.Please note that VM won’t be having Public IP we need to add Public IP address if need dependency.At this stage we can use the application in Secondary site with new application data would be available to the users.
	⁃	After failover completed we can commit to change the  recovery point with the failover happened.
	⁃	Before we plan to failover to primary region we need to make sure to do re-protect VM in Secondary region  because of re-protect would sync the new data changes to primary region so that new application data would be available in Primary region as well. During the re-protect one cache storage account will be created in Secondary site to copy the new data changes from the vm disk in secondary site  inside secondary site site recovery vault RG and replicate the vm disk from secondary site to Primary Site for synchronization.
	⁃	At this state the VM in Secondary site status would show as healthy and Protected which means ready for failover to primary region to maintain application accessible from Primary Site. Thats it. Now we have an access back to application from Primary Region with application data we updated in Secondary site. Now commit the recovery point in Primary site and following by Re-Protect. This makes VM in Primary site would replicate  with Secondary site.
	⁃	Site Recovery also would be helpful in situation if VM deleted by mistake in Primary Site we can initiate a failover to restore in Secondary location.
	⁃	Since VM deleted we would be able to commit after failover done but not Re-Protect due to VM deleted  this mean we need to reset Site Recovery again from scratch

 
	✓	Azure Site Recovery HyperV

	⁃	Create a Recovery vault 
	⁃	Prepare a Infrastructure  for HyperV ( This step varies based on the On-Prem environment example for Vmware process is different )
	⁃	Create Hyper-V site 
	⁃	Add HyperV servers -  In order to do that we need to download Azure Site Recovery Provider install file and  key file to register HyperV server in the wizard download these 2 files in to HyperV server 
	⁃	Install Azure Site Recovery Provider in HyperV and provide key file ( Subscription, Vaultname, Hyperv Site name )  while it asks that helps registering the HyperV server in to HyperV site in Azure.
	⁃	Now HyperV hosts would show as connected state in Azure.
	⁃	Create Replication policy to start replicate data from HyperV to Azure
	⁃	Now Associate HyperV Site create in Azure with Replication Policy
	⁃	Now start the Replicate HyperV Site which is already registered with on-removed HyperV  to Azure  while  doing that we need mention the target environment details like - RG, Storage Account, Network for the replicated Onprem HyperV vm we are creating recovery to use in future.Storage ( no soft delete enabled )  will maintain all the data changes from On-Prem HyperV to replicate in to Azure.
	⁃	This will start the replication now and on-Prem VM should as healthy and Protected.
	⁃	We can also create a backup recovery as well for On-Prem HyperV for Virtual machines and also for files and folders if need.
	⁃	Planned Failover, test failover,  Failover, Commit, Re-synchronize 


	✓	Azure Migrate Service

	⁃	Create a Azure Migrate Project Which has assessment tools and Migrate tools.
	⁃	Assessment tool - Discover, Analyse Dependencies, Asses
	⁃	Migarte Tool - Discover, Replicate, Migrate
	⁃	To discover your on-premises environment, you will need to deploy the Azure Migrate appliance.generate the project key. The project key is needed during the configuration of the Azure Migrate appliance.
	⁃	Name azure migrate appliance and generate a key and copy it in location where you can refer it later.project key to register the appliance for discovery of Hyper-V virtual machines.Here at this state key vault  gets created to maintain appliance key.
	⁃	Download Azure migrate appliance  .VHD file and copy it in to On-Prem Server and launch a appliance  in HyperV and Assign IP address to appliance to have network
	⁃	Connect to Appliance Configuration manager with link https://hostname:44368 and configure it and register the HyperV with Azure migrate Project by adding all the HyperV list of servers.
	⁃	Configure Appliance and Initiate a Discovery.
	⁃	Wait for the appliance to be connected, discovery to be completed, performance data to be collected.
	⁃	Now in Azure Migrate we can see the discovered servers.
	⁃	Under Discovered server there is option to create assessment . Create assessment for group of servers and assess health status  whether those servers ready for azure or not and cost it would be caused for those VMs.
	⁃	Now it is time to start Migrate - Use Azure migrate tool and start use discovery and it start creates the resource based on the region we mention and it uses the site recovery service to replicate the data from the HyperV VMs  to recovery vault to have data 
	⁃	Now it asks us to download Azure site recovery provider along with Key to register  the hyperV servers and install it on HyperV
	⁃	Now it is time to replicate the discovered servers. During this process mention the target details like network,Storage, RG and Subnet  and this is where we can change the vm size 
	⁃	At this state only data being migrated to Azure which means that replicated items shows healthy and protected and the replication is continuous process.
	⁃	This is the time to do whether test migrate of VMs and see if any issue. This let us to continue to run the application in on-prem and we can validate the application in cloud in a cloned copy.
	⁃	Finally we can do migrate.
	⁃	Once you have performed a final migration to Azure and the on-premises source machine was shut down, you cannot perform a rollback from Azure to your on-premises environment. 
	⁃	When you stop replication, the Azure Migrate: Server Migration tool cleans up the managed disks in the subscription that were created for replication. If you do not stop replication after a migration, you will continue to incur charges for these disks. Stop replication will not impact the disks attached to machines that have already been migrated.


	✓	Azure Load Balancer

	⁃	Load balancer to equally distribute the load to backend pool.
	⁃	OSI Layer 4 Model LB
	⁃	2 Load Balancers - Basic LB, Standard LB
	⁃	Basic LB - 1 VM, Availability Set, Scale Set
	⁃	Standard LB - Multiple VM, Availability Set, Scale Set. High SLA 99.99%
	⁃	External LB will have public IP address
	⁃	Internal LB will have Private IP address.
	⁃	LB is Regional Delivery LB
	⁃	Resources gets created LB - Frontend IP, Backend Pool, Inbound Rules, Health Probe
	⁃	session persistence, is a process in which a load balancer creates an affinity between a client and a specific network server for the duration of a session, (i.e., the time a specific IP spends on a website).

	✓	Azure Application gateway

	⁃	OSI Layer 7 Model LB
	⁃	AGW LB need to be created in virtual network with empty subnet, AGW would use that empty subnet for ingestion for  AGW.
	⁃	AGW LB will contain web application firewall on it.
	⁃	Secure Socket Layer (  SSl/TLS ) Termination.proxy server that acts as an intermediary point between client and server applications, and is used to terminate and/or establish TLS (or DTLS) tunnels by decrypting and/or encrypting communications.
	⁃	Autoscale for AGW resource can be done.This allows AGW to scale up based on the traffic load patterns.
	⁃	URL Path based route to backend pool
	⁃	We can also enable WAF for AGW and create WAF service plan policy and deny traffic based on the rule we create like - we can deny traffic particular IP address as well.
	⁃	AGW can be used to have backend pool for - VM,VSS and app service
	⁃	AGW LB can be in different location as well than VM, App service, VSS location

	✓	Azure Traffic Manager

	⁃	DNS based traffic LB.
	⁃	Routing methods -  priority, Weight, Performance, Geographic, multivalue, subnet 
	⁃	Traffic distribution across multiple endpoints - different location, on-Prem as well. Endpoint just need to be an internet facing service.
	⁃	It is Global Delivery
	⁃	Endpoints can be Azure endpoints, External Endpoints, Nested endpoints
	⁃	Performance routing method has intelligence to reach the least latency endpoint for traffic.
	⁃	Priority – Route traffic to another endpoint in case the primary fails.
	⁃	Performance - you want end users to use the "closest" endpoint in terms of the lowest network latency.
	⁃	Weight - Route traffic to different endpoints based on weight.  
	⁃	Geographic - geographic location their DNS query originates from.
	⁃	multivalue - Here different endpoints are sent to the client. The client then selects the endpoint to send the request to.
	⁃	subnet - This maps a set of end-user IP address ranges to a specific endpoint within a Traffic Manager profile.  


	✓	Azure Front Door Service

	⁃	Global Delivery resource
	⁃	It is combination of AGW and Traffic manager
	⁃	We can use Priority and Weight together in Front Door 
	⁃	URL based path routing
	⁃	
	⁃	

	✓	Azure Firewall
	
	⁃	Azure Firewall is a managed cloud-based network security service that protects your Azure Virtual Network resources. It is a fully stateful firewall as a service with built-in high availability and unrestricted cloud scalability. You can centrally create, enforce, and log application and network connectivity policies across subscriptions and virtual networks. Azure Firewall uses a static public IP address for your virtual network resources allowing outside firewalls to identify traffic originating from your virtual network. The service is fully integrated with Azure Monitor for logging and analytics.
	⁃	Azure Firewall very useful service to use specially in Remote Desktop/WVD environment.
	⁃	Make sure firewall service must be in the same network where VMs in.
	⁃	There should be one subnet must be created as AzureFirewallSubnet 
	⁃	Create a route rule mention next hop as a Azure firewall Private IP address.
	⁃	create a Azure Firewall in the same network where VMs ln.
	⁃	Create NAT rule 
	⁃	Application rule also can be create to restrict particular websites deny

	✓	Azure Webapp Service

	⁃	IaaS
	⁃	PaaS. Has a ability to auto scale and capable of devops oriented for CI/CD 
	⁃	App Service Plan - Dev, Test, Production  and Isolated
	⁃	Publish .net core Projects / publish to Azure app service 
	⁃	Custom domain configure for app service to access with custom domain name
	⁃	App service plan gets created based on OS version and one app service plan can be used for same OS and if OS are different app service plan has to be separated based on OS.
	⁃	Azure web apps publish from GitHub 
	⁃	We can connect Create a project in visual studio 2019 and push to GitHub 
	⁃	And then we can connect Azure web app with Github as a CI/CD pipeline and as when changes happens web application would be able to get the changes.
	⁃	Webjobs easy way to run programme or script in the background with cron expression as well.
	⁃	Application logs can be downloaded of not can be downloaded to Storage account
	⁃	Basic App service plan max 3 scale we can do but manual 
	⁃	Standard App service plan scale in and scale out conditions.
	⁃	We cab change app service plan from basic to standard so that we can also use auto scale based on rule for different utilization methods.
	⁃	App service deployment slots can be only created under standard plan
	⁃	Once staging slot created it will only come up with cloned settings and doesn’t come up with existing GitHub connected if any. 
	⁃	We start deploy app updates to production slot and if any issues we can swap the slot to rollback
	⁃	slots eliminate the application downtime and easy rollback online.
	⁃	We can connect GitHub with Staging slot and we can test the application and as when deployment fully ready we can swap the slot for new version to take affect. And if need we can still roll back to before version again doing slot swap.
	⁃	Some of percentage of Traffic can be transferred to stage slot as well to validate before swap to production

	✓	Azure Webapp - Azure network integration

	⁃	Azure webapp will have  public  IP and if it has dependency with DB tier which doesn’t have a public IP address  we can integrate Azure webapp with Azure network to have DB tier connection to app service
	⁃	Once we added Vnet to app service that specific Subnet would be used by app service web app.The subnet which is used by app service won’t be supported for other resources.
	⁃	Webapp project we need to mention the DB connection string with private IP address so that web app can communicate with DB via Private IP since we already connected web app to the same vnet already.

	✓	Azure Functions:





	✓	Azure Logic Apps:


	✓	Azure SQL Database 

	⁃	Azure SQL DB can be IaaS and PasS as well.
	⁃	While creating SQL Database it create we need to create sql DB and SQL server
	⁃	this SQL Server has inbuilt firewall on it so that it can control the access.Later we can also add client IP address if anyone need an access to SQL server.
	⁃	We can use SQL server management studio to access the SQL servers.
	⁃	Network connectivity to sql server can be with public endpoint and also using private endpoint this can be configured while creating the sql db/server if not we can do later as well.
	⁃	We can import a database from on-prem to Azure SQL server using import database.
	⁃	Firewall and network we need to control from SQL server which already had sql DB on it. 
	⁃	We can mention specific Client IP address to grant an access if not we can also grant based on the Vnet as well.
	⁃	SQL visual machines also we can use it for in order to have a control in to OS.
	⁃	SQL database is suitable for workload mainly in cloud and 
	⁃	SQL managed instances mainly used for migrations from on-prem
	⁃	DTU is an abbreviation for the “Database Transaction Unit” and it describes a performance unit metric for the Azure SQL Database. ... DTU represents a mixture of the following performance metrics as a single performance unit for Azure SQL Database: CPU. Memory. Data I/O and Log I/O
	⁃	backup storage redundancy method for Azure managed instance as well.
	⁃	The Database can be multiple azure sql database on same server. Example like for customer data one db, receipt DB for receipt , order separate order Db. 
	⁃	

	✓	Azure SQL Elastic Pool

	⁃	Elastic pool quite handy in using mainly to maintain DB like unpredictable  DB usage demands.Because of resource can be shared across all the DB in the Pool.
	⁃	The databases that are part of elastic pool those DB must be in single server and if we have a different DB in different servers we need to maintain different elastic pools.
	⁃	the databases would share the resources like cpu and memory
	⁃	backup storage redundancy method for Azure managed instance as well.


	✓	Azure SQL Managed Instances

	⁃	Azure SQL Managed Instance is the intelligent, scalable cloud database service that combines the broadest SQL Server database engine compatibility with all the benefits of a fully managed and evergreen platform as a service.
	⁃	SQL Managed Instance allows existing SQL Server customers to lift and shift their on-premises applications to the cloud with minimal application and database changes. At the same time, SQL Managed Instance preserves all PaaS capabilities (automatic patching and version updates, automated backups, high availability) that drastically reduce management overhead and TCO.
	⁃	While creating the azure managed instance we can choose server tier with number of vCores and Storage and also backup storage redundancy method for Azure managed instance as well.

	✓	Azure SQL Active Geo Replication

	⁃	It works as a Primary Database server which contains primary DB and secondary database server which contained secondary  database.
	⁃	It allows to create readable secondary database
	⁃	secondary database can be on same server or different server in same region as well.
	⁃	This is not supported for Azure sql managed instances.
	⁃	We can use this for database failover as well, it has to be either manual or application.
	⁃	If at all would like to stop the replication we can stop replication from secondary database in geo replication blade.This doesn’t delete the secondary database and it will be still available.
	⁃	This replication works at DB level and failover can only be done manually.
	⁃	Auto failover groups - This feature built on top of active geo replication.This feature available for Sql managed instance as well.Here we can replicate and failover group of databases on a server this can be done automatically if not by using policy as well.The secondary server must be in different region.
	⁃	Just need to create a failover group with failover policy . The failover group consists of Azure Sql servers.This replication/failover works at Azure db server level
	⁃	failover group to automatically failover databases in it.
	⁃	as when new database created in primary server we need to initial do replication and following by add that new DB to failover group for auto failover to happen.
	⁃	we recommend that you upgrade the secondary database first, and then upgrade the primary. When downgrading, reverse the order: downgrade the primary first, and then downgrade the secondary. 

	✓	Azure SQL Database  version upgrade

	⁃	???????
