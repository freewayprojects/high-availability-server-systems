# high-availability-server-systems
High Availability Server Systems

<div class="foswikiTopic">

* * *

![fplogo_twiki.jpg](/foswiki/pub/FpSys/HighAvailabilityServerSystems3/fplogo_twiki.jpg)

* * *

# <a name="High_Availability_Server_Systems"></a>  High Availability Server Systems 

## <a name="Document_Details"></a>  Document Details 

<table class="foswikiTable" rules="none" border="1">
	<tbody>
		<tr class="foswikiTableOdd foswikiTableRowdataBgSorted0 foswikiTableRowdataBg0">
			<td class="foswikiTableCol0 foswikiFirstCol"> Title </td>
			<td class="foswikiTableCol1 foswikiLastCol"> High Availability Server Systems </td>
		</tr>
		<tr class="foswikiTableEven foswikiTableRowdataBgSorted1 foswikiTableRowdataBg1">
			<td class="foswikiTableCol0 foswikiFirstCol foswikiLast"> Document Type </td>
			<td class="foswikiTableCol1 foswikiLastCol foswikiLast"> Freeway Projects White Paper </td>
		</tr>
	</tbody></table>

## <a name="Table_of_Contents"></a>  Table of Contents 

<a name="foswikiTOC"></a><div class="foswikiToc"> 

*   [ High Availability Server Systems ](#High_Availability_Server_Systems)
        *   [ Introduction ](#Introduction)
            *   [ What do servers do? ](#What_do_servers_do_63)

                *   [ What are clients? ](#What_are_clients_63)

                *   [ So, it's the provision of the 'service' which is important? ](#So_44_it_39s_the_provision_of_the_39service_39_which_is_important_63)
    *   [ How to ensure the availability of server services ](#How_to_ensure_the_availability_of_server_services)
            *   [ Reliable server infrastructure ](#Reliable_server_infrastructure)
                *   [ Server hardware ](#Server_hardware)

                        *   [ Secondary servers ](#Secondary_servers)

                        *   [ Clustering and cloud services ](#Clustering_and_cloud_services)
    *   [ Backups and disaster recovery processes ](#Backups_and_disaster_recovery_processes)
            *   [ Snapshot data backups ](#Snapshot_data_backups)

                *   [ Known and tested times for a rebuild ](#Known_and_tested_times_for_a_rebuild)

                *   [ Full testing of rebuilt systems ](#Full_testing_of_rebuilt_systems)

                *   [ Disaster recovery processes ](#Disaster_recovery_processes)
                *   [ Rebuild the server infrastructure ](#Rebuild_the_server_infrastructure)

                        *   [ Reload the data ](#Reload_the_data)
    *   [ Incident management ](#Incident_management)
            *   *   [ Reporting of service degradation ](#Reporting_of_service_degradation)
                    *   [ Critcal ](#Critcal)

                                *   [ Severe ](#Severe)

                                *   [ Moderate ](#Moderate)

                                *   [ Trivial ](#Trivial)
            *   [ Initial investigation ](#Initial_investigation)

                        *   [ Allocation of resources ](#Allocation_of_resources)

                        *   [ Resolving the issue ](#Resolving_the_issue)
    *   [ Summary ](#Summary) 
</div>

## <a name="Introduction"></a>  Introduction 

Computer server systems are used by organisations worldwide as key parts of their operations and it is important that these systems are available at all times.

This white paper is aimed at non-technical management level audience and will discuss the provision of high availability server systems.

### <a name="What_do_servers_do_63"></a>  What do servers do? 

Servers usually carry out two main tasks; store databases of information and provide services to allow clients to connect.

For example, a web server can be used to host websites which are made available to computers connected to the internet.

![web_server.png](/foswiki/pub/FpSys/HighAvailabilityServerSystems3/web_server.png)

A company email server could work in a very similar way.  The server will allow connections from PC's/laptops so the staff can read and send email messages.

![email_server.png](/foswiki/pub/FpSys/HighAvailabilityServerSystems3/email_server.png)

So, servers are machines which run twenty four hours a day, hold databases of information and allow PC's/laptops to connect to access the information.  Servers are the first part of what is known as the Client/Server model.

Note: Naming terminology can be a little confusing.  The actual computers are called servers - and the programs which run on them are called server programs.

### <a name="What_are_clients_63"></a>  What are clients? 

Clients are programs, applications or apps which connect to a server.

One example could be an Email client such as Microsoft Outlook or Mozilla Thunderbird.  These programs are run on laptops/PC's and they contain settings for one or more email accounts.  These settings tell the client program the address of the Email server and the username/password to connect with.

When the user clicks on 'Get Mail' or similar the client connects to the email server and requests to download the latest emails.

For websites and web applications the client is a web browser.  The user puts the address of the web server into the URL address bar, clicks 'Go' and the web browser then sends a request to the web server.  The web server then responds by sending back text and images which the browser displays as a web page.  Some websites require the user to log in to access information - in these cases the browser shows the user a login page.  Once the user has entered a correct username and password they will be allowed further access.

Apps on smart phones can also be used as clients.  There are client apps which are used to connect to music streaming services, messaging services and social media sites.

### <a name="So_44_it_39s_the_provision_of_the_39service_39_which_is_important_63"></a>  So, it's the provision of the 'service' which is important? 

Server systems run twenty four hours a day and serve requests which are made by client programs.  Those clients will make their requests to a specific address on a network where they expect the server to be located.  If the client and the server connect using the internet then the server will usually be assigned a permanent (static) IP address.

![client_server.png](/foswiki/pub/FpSys/HighAvailabilityServerSystems3/client_server.png)

So the provision of a particular service at a particular address is what is important.  

Generally, clients are easily replaceable.  For example, email clients can easily be re-installed the the accounts settings can be re-entered.  In the case of web browsers, most PC's/laptops come with web browsers installed and so can access most websites and web applications out of the box.

## <a name="How_to_ensure_the_availability_of_server_services"></a>  How to ensure the availability of server services 

To provide high availability (HA) of server services there are three main areas which need to be addressed and fully understood.

 * Reliable server infrastructure
 * Backups and disaster recovery processes
 * Incident management

### <a name="Reliable_server_infrastructure"></a>  Reliable server infrastructure 

#### <a name="Server_hardware"></a>  Server hardware 

The first part of the HA is to use reliable server infrastructure.

This would invlove the use of highly reliable servers which have various aspects of redundancy built-in.

Advanced servers have hardware monitoring and checking systems built-in and these run continuously checking various aspects of the server hardware.  In addition to this many servers hot-swap spares built-in which can be used in the event of a component failure.  This could mean for example that a failing hard drive could be replaced by removing the faulty hard disk and putting in a new disk whilst the machine is still running.  Many servers have multiple power supply units (PSU's) built-in so that a faulty PSU can be replaced without having to power down the server.

Note - At the level on mainframes it is actually possible that any aspect of the machine hardware can be replaced without stopping the machine.  This includes processors, ram chips, hard drives, system boards etc.

#### <a name="Secondary_servers"></a>  Secondary servers 

It is very common to have complete servers doubled up with hot-swap secondary servers ready to take over from primary servers if the primary server has a problem.

In this case there is a secondary server running at all times which is regularly updated from data from the the primary server. If the primary server is no longer available then system administrators would manage the change over to the secondary server so that the service is made available to clients.

#### <a name="Clustering_and_cloud_services"></a>  Clustering and cloud services 

It is possible for a number of servers to act together to provide a single service.  This could be several database servers acting together to provide the data store for a large and busy website. The advantage of a cluster is that individual servers can be removed and replaced whilst the cluster as a whole is still performing its primary task.

Clustering technologies are used to provide cloud services.  It should be noted here that cloud services can suffer failures and in these cases data loss can occur.  Even when using cloud services it is important to have all data backed up to safe copies.

## <a name="Backups_and_disaster_recovery_processes"></a>  Backups and disaster recovery processes 

Even the server infrastructure is highly resilient it is still possible that circumstances may cause serious problems.  Regular monitoring, testing and maintenance should mean that the primary servers should be available at all times.  But for business critical services plans should be in place to deal with worst case scenarios.

### <a name="Snapshot_data_backups"></a>  Snapshot data backups 

High availability server systems should make regular backups of all data required for the service.  These are data dumps of data from databases and file systems which are made at regular intervals on to completely separate backup server systems.

There should be sufficient data dumped out to enable the whole server system to be rebuilt from new server infrastructure.  The process of rebuilding the whole server service should be documented, tested and analysed regularly to ensure that it will work correctly if it is needed.

### <a name="Known_and_tested_times_for_a_rebuild"></a>  Known and tested times for a rebuild 

The disaster recovery processes should be run regularly so that they are known processes and the recources needed and the time required and fully understood and documented.  This is a crucial part of the disaster recovery planning.

In the event of a major problem the incident mangement will need to make decisions about how to get full service restored.  Initially the original server system will be investigated and any issues found will need ot be resolved.  If however there are serious problems with the primary/secondary systems then a full rebuild of the system services may need to be rebuilt from backups.

In this case it is important to know how long a full rebuild will take to ensure that a full service is restored within the agreed time frames.

### <a name="Full_testing_of_rebuilt_systems"></a>  Full testing of rebuilt systems 

An important part of the recovery processes is that the rebuilt system should be fully tested to check that it matches the expected service.  A series of unit tests should be developed which will automate the testing process.  These tests simulate normal requests which are made by clients and then marches the results produced against a database of known good result sets.  Because these tests can be automated they can be built on and extended overtime as new features and functions are added to the service provided.

### <a name="Disaster_recovery_processes"></a>  Disaster recovery processes 

There are two main parts to a disaster recovery process:

#### <a name="Rebuild_the_server_infrastructure"></a>  Rebuild the server infrastructure 

It should be possible to rebuild the servers from new machines and to be able to set up all software services and configruation to match the server infrastructure of the original system.

#### <a name="Reload_the_data"></a>  Reload the data 

Once the server infrastructure is in place then the data should be reloaded from data which was dumped out to a snapshot backup.

## <a name="Incident_management"></a>  Incident management 

Process should be put into place so that all parties involved in a server service system know what to do in the event of problems with the service provision.

The parties involved with a server service usually fall into two groups.

 * Service users who use the services as part of there normal precesses.
 * Service providers who are responsible for providing the service and ensuring it is running as expected.
 * Service developers who are responsible for enhancing the services at the request of the service users.

This incident management will be documented and shared between all parties so that there is clear understanding of the precesses and procedures involved.

#### <a name="Reporting_of_service_degradation"></a>  Reporting of service degradation 

Initially, any experience of service degradation should be reported to known channels and the report will be analysed.  This should then be allocated a severity level.  

These are some of the severity levels which could be used:

##### <a name="Critcal"></a>  Critcal 

Service is not available

##### <a name="Severe"></a>  Severe 

Service performance is degraded.  Usually related to speed issues for accessing the system as a whole or if certain parts of the service are not available.

##### <a name="Moderate"></a>  Moderate 

The service is working and usable but certain aspects are not behaving as expected.  It is important that moderate issues are investigated in case they are an indicaiton if other underlying problems.

##### <a name="Trivial"></a>  Trivial 

Very minor points may have arisen which do not affect the usage of the service but do not work as expected.  As with moderate issues it is important that minor points are investigated in case they are an indicaiton if other underlying problems.

#### <a name="Initial_investigation"></a>  Initial investigation 

An initial investigation should be carrried out into the nature and possible causes of the issue reported.  Very often the intial investigation can narrow down the cause of the issue quite quickly.

This initial investigation should look into the following main areas of potential issues:

*   Networking - are the networks passing requests and responses as expected.

*   Services - are the services available as expected and working as expected.

*   Server infrastructure - are the servers and server software running and working as expected. 

#### <a name="Allocation_of_resources"></a>  Allocation of resources 

Once an initial investigation has been carried out then various resources can be deployed to look at the issues found.  It may be that different resources are deployed to look at different aspects of the service to ensure the all the required components are working as expected.

#### <a name="Resolving_the_issue"></a>  Resolving the issue 

During the incident there should be close liason between the service users and the service providers.  Regular feedback should be provided to keep service users aware of developments.

Service providers may decide that it may be necessary to switch to secondary server services.  In this case the switch over should be managed and service users informed of the process.

It may be that the server provider decides to implement the disaster recovery processes.  In this case, the processes needed for rebuilding the server services and reloading the data will be initiated and managed.  These should be tried and tested processes which have been run, documented and tested many times before.  The time it should take to rebuild the system would be known and service users would be kept informed of progress.

Once a plan of action has been decided on this should be worked through under the management on the service provider.

## <a name="Summary"></a>  Summary 

*   Computer server services are used by origanisations to provide services to clients which are usually conntected by a computer network.

*   Some server services are crucial and need to be available at all times.

*   The first part of providing a reliable service is to use high quality servers and software.

*   Primary servers can have hardware redundancy built-in to improve server reliability.

*   Secondary server systems can be kept up-to-date with current data to provide a backup to the primary systems.

*   Tried and tested procedure should be in place to be able to rebuild whole systems from data backups.

*   Incident management processes should be in place to manage issues which arise with service provsion. 

© 2004 by Freeway Projects Limited. All rights reserved </div>
