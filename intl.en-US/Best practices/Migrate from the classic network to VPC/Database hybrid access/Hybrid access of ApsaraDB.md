# Hybrid access of ApsaraDB {#concept_ixy_vv5_sdb .concept}

Hybrid access means that a database can be accessed by both an ECS instance of the classic network and an ECS instance of the VPC network. To use the hybrid access/adding method to migrate your ApsaraDB from a classic network to a VPC network, you need to change ApsaraDB to the hybrid access mode \(the classic network endpoint and the VPC endpoint are reserved at the same time\), thus service interruption during the migration can be avoided.

When migrating ApsaraDB to VPC, you can specify the expiration time of the classic network endpoint. The classic network endpoint is automatically released when the time is reached.

Note the following when you use the hybrid access function of ApsaraDB:

-   Currently, the following databases support hybrid access:

    -   ApsaraDB for RDS MySQL, SQL Server, PPAS and PostgreSQL in the enhanced security mode

    -   ApsaraDB for Redis/Redis cluster version

    -   New ApsaraDB for Memcache \(purchased after May 12, 2017\)

    -   ApsaraDB for MongoDB replica set

        For MongoDB instances, RDS instances, and Redis instances, you can change the network type either on the console or through API. The classic network endpoint stays unchanged and a VPC endpoint will be added after the switchover. You can view the classic network endpoint and the VPC network endpoint on the console.

        For the new Memcache instances, you have to do the migration using the API. Currently, after you change the network type on the console, the classic network endpoint cannot be reserved. The classic network endpoint stays unchanged and a VPC endpoint will be added after the switchover. The console only displays the VPC network endpoint. You need to use API to view the classic network endpoint.

-   Currently, the following databases have not support hybrid access:

    -   ApsaraDB for RDS in the standard network mode. To change the network type, switch to the enhanced security mode first.

    -   ApsaraDB for MongoDB cluster version.

    -   Earlier versions of ApsaraDB for Memcache \(purchased before May 12, 2017\). To change the network type, purchase a new instance and migrate to the new ApsaraDB for Memcache.


