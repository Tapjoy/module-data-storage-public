**Note**: This public repo contains the documentation for the private GitHub repo <https://github.com/gruntwork-io/module-data-storage>.
We publish the documentation publicly so it turns up in online searches, but to see the source code, you must be a Gruntwork customer.
If you're already a Gruntwork customer, the original source for this file is at: <https://github.com/gruntwork-io/module-data-storage/blob/master/modules/rds/README.md>.
If you're not a customer, contact us at <info@gruntwork.io> or <http://www.gruntwork.io> for info on how to get access!

# RDS Module

This module creates an Amazon Relational Database Service (RDS) cluster that can run MySQL, Postgres, or MariaDB. The 
cluster is managed by AWS and automatically handles standby failover, read replicas, backups, patching, and 
encryption.

## What is Amazon RDS?

Before [Amazon Relational Database Service](https://aws.amazon.com/rds/) (RDS) existed, teams would painstakingly configure
PostgreSQL, MySQL, or other popular databases on their own. Setting up automatic failover, read replicas, backups, encryption,
and handling upgrades are all non-trivial and AWS recognized they could implement these features according to best practices
themselves, sparing customers the time and cost of doing it themselves.

Behind the scenes, RDS runs on EC2 Instances located in subnets and protected by security groups you specify. 

Backups are handled by a snapshot taken on a nightly basis, but you can initiate a manual snapshot whenever you want. If
you select the [Multi-AZ](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Concepts.MultiAZ.html) option, RDS will
synchronously copy every write to a standby and, in the event of a failure in the master server, automatically fail over
to the standby server.

In addition, if you wish to reduce the load on your primary database, one option is to add Read Replicas and direct all
 read queries to them. RDS streamlines the process of adding and maintaining Read Replicas.

#### Common Gotcha's

- All RDS upgrades (version upgrades, instance type upgrades, etc.) require a few minutes of scheduled downtime. 
- If an RDS instance that uses Multi-AZ fails, Amazon will automatically kick off a fail-over, but you will still experience
  about 3 - 5 minutes of downtime.
- Based on the above, make sure you've written your app to gracefully handle database downtime.
- An RDS instance that runs out of disk space will stop working, so be sure to monitor and set an alert on the `FreeStorageSpace`
  CloudWatch Metric. Consider monitoring other [RDS CloudWatch Metrics](http://docs.aws.amazon.com/AmazonCloudWatch/latest/DeveloperGuide/rds-metricscollected.html)
  as well.

## How do you use this module?

See the [RDS example](/examples/rds) for an example. 

## How do you connect to the database?

This module provides the connection details as [Terraform output 
variables](https://www.terraform.io/intro/getting-started/outputs.html):

1. **Primary endpoint**: The endpoint for the primary DB. You should always use this URL for writes, as it points to 
   the primary.
1. **Read replica endpoints**: A comma-separated list of read replica URLs.
1. **Port**: The port to use to connect to the endpoints above.

You can programmatically extract these variables in your Terraform templates and pass them to other resources (e.g. 
pass them to User Data in your EC2 instances). You'll also see the variables at the end of each `terraform apply` call 
or if you run `terraform output`.

Note that the database is likely behind a Bastion Host, so you may need to first connect to the Bastion Host (or use SSH
Tunneling) before you can connect to the database.

## How do you scale this database?

* **Storage**: Use the `allocated_storage` variable.
* **Vertical scaling**: To scale vertically (i.e. bigger DB instances with more CPU and RAM), use the `instance_type`,
  `storage_type`, and `iops` input variables. For a list of AWS RDS server types, see [DB Instance 
  Class](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Concepts.DBInstanceClass.html)
* **Horizontal scaling**: To scale horizontally, you can add more replicas using the `num_read_replicas` input variable, 
  and RDS will automatically deploy the new instances, begin asynchronous replication, and make them available as read 
  replicas. FOr more info, see [Working with PostgreSQL, MySQL, and MariaDB Read 
  Replicas](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_ReadRepl.html#USER_ReadRepl.Overview).

## How do you configure this module?

This module allows you to configure a number of parameters, such as backup windows, maintenance window, port number,
and encryption. For a list of all available variables and their descriptions, see [vars.tf](./vars.tf).