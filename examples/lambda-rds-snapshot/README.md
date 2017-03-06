**Note**: This public repo contains the documentation for the private GitHub repo <https://github.com/gruntwork-io/module-data-storage>.
We publish the documentation publicly so it turns up in online searches, but to see the source code, you must be a Gruntwork customer.
If you're already a Gruntwork customer, the original source for this file is at: <https://github.com/gruntwork-io/module-data-storage/blob/master/examples/lambda-rds-snapshot/README.md>.
If you're not a customer, contact us at <info@gruntwork.io> or <http://www.gruntwork.io> for info on how to get access!

# RDS Lambda Snapshot Example

This folder contains examples of how to:
 
1. Use the [lambda-create-snapshot module](/modules/lambda-create-snapshot) to take periodic snapshots of an RDS DB.
1. Use the [lambda-share-snapshot module](/modules/lambda-share-snapshot) to share those snapshots with another AWS 
   account.
1. Use the [lambda-copy-shared-snapshot module](/modules/lambda-copy-shared-snapshot) to make local copies of 
   snapshots from external AWS accounts.
1. Use the [lambda-cleanup-snapshots module](/modules/lambda-share-snapshot) to delete old snapshots.

The code includes examples of Aurora on RDS and MySQL on RDS. 

Note that to use this module, you must have access to the Gruntwork [Continuous Delivery Infrastructure Package 
(module-ci)](https://github.com/gruntwork-io/module-ci-public). If you need access, email support@gruntwork.io.




## How do you run this example?

To run this example, you need to:

1. Install [Terraform](https://www.terraform.io/).
1. Open up `vars.tf` and set secrets at the top of the file as environment variables and fill in any other variables in
   the file that don't have defaults. 
1. `terraform get`.
1. `terraform plan`.
1. If the plan looks good, run `terraform apply`.

