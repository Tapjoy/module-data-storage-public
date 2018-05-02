**Note**: This public repo contains the documentation for the private GitHub repo <https://github.com/gruntwork-io/module-data-storage>.
We publish the documentation publicly so it turns up in online searches, but to see the source code, you must be a Gruntwork customer.
If you're already a Gruntwork customer, the original source for this file is at: <https://github.com/gruntwork-io/module-data-storage/blob/master/examples/rds/README.md>.
If you're not a customer, contact us at <info@gruntwork.io> or <http://www.gruntwork.io> for info on how to get access!

# RDS Example

This folder contains examples of how to use the [RDS module](/modules/rds) to create an Amazon 
Relational Database Service (RDS) cluster that can run MySQL, Postgres, or MariaDB. The cluster is managed by AWS and 
automatically handles leader election, replication, failover, backups, patching, and encryption. 

The templates show two examples, one that runs MySQL and one that runs Postgres.

## How do you run this example?

To run this example, you need to:

1. Install [Terraform](https://www.terraform.io/).
1. Open up `vars.tf` and set secrets at the top of the file as environment variables and fill in any other variables in
   the file that don't have defaults. 
1. `terraform init`.
1. `terraform plan`.
1. If the plan looks good, run `terraform apply`.

When the templates are applied, Terraform will output the IP address of the cluster endpoint (which points to the 
master) and the instance endpoints (which point to the master and all replicas). 