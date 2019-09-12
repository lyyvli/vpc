# Overview of the hybrid access mode of ApsaraDB {#concept_ixy_vv5_sdb .concept}

This topic provides an overview of the hybrid access mode of ApsaraDB. By using the hybrid access mode, you can access ApsaraDB from classic-network ECS instances and VPC ECS instances. The hybrid access mode of ApsaraDB reserves the classic network endpoint and the VPC endpoint at the same time. In this way, service disruptions can be avoided during the migration.

When you switch the network type of ApsaraDB instances from classic network to VPC, you can specify the retention period of the classic network endpoint. After the retention period expires, the classic network endpoint is automatically deleted.

Note the following when you use the hybrid access mode of ApsaraDB:

-   The ApsaraDB types that support hybrid access are as follows:

    -   ApsaraDB for RDS MySQL, SQL Server, PPAS, and PostgreSQL in the enhanced security mode

    -   ApsaraDB for Redis/Redis cluster version

    -   New ApsaraDB for Memcache \(purchased after May 12, 2017\)

    -   ApsaraDB for MongoDB replica set

        For MongoDB instances, RDS instances, and Redis instances, you can switch their network type from classic network to VPC through the console or the relevant API. After you switch the network type, the classic network endpoint remains unchanged and a VPC endpoint is created. You can view the classic network endpoint and the VPC endpoint in the console.

        For Memcache instances, you need to switch their network type from classic network to VPC through the relevant API. If you switch the network type through the console, the classic network endpoint cannot be reserved. After you switch the network type through the relevant API, the classic network endpoint remains unchanged and a VPC endpoint is created. The VPC network endpoint is displayed in the console. The classic network endpoint can only be viewed by calling the relevant API action.

-   The ApsaraDB types that do not support hybrid access are as follows:

    -   ApsaraDB for RDS in the standard network mode. To change the network type, switch to the enhanced security mode first.

    -   ApsaraDB for MongoDB cluster version.

    -   Earlier versions of ApsaraDB for Memcache \(purchased before May 12, 2017\). To change the network type, you must purchase an instance and migrate the instance to the new ApsaraDB for Memcache.


