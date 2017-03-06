**Note**: This public repo contains the documentation for the private GitHub repo <https://github.com/gruntwork-io/module-data-storage>.
We publish the documentation publicly so it turns up in online searches, but to see the source code, you must be a Gruntwork customer.
If you're already a Gruntwork customer, the original source for this file is at: <https://github.com/gruntwork-io/module-data-storage/blob/master/modules/lambda-copy-shared-snapshot/README.md>.
If you're not a customer, contact us at <info@gruntwork.io> or <http://www.gruntwork.io> for info on how to get access!

# Copy Snapshot Lambda Module

This module creates an [AWS Lambda](https://aws.amazon.com/lambda/) function that runs periodically and makes local
copies of snapshots of an [Amazon Relational Database (RDS)](https://aws.amazon.com/rds/) database that were shared 
from some external AWS account. This allows you to make backups of your RDS snapshots in a totally separate AWS 
account.

Note that to use this module, you must have access to the Gruntwork [Continuous Delivery Infrastructure Package 
(module-ci)](https://github.com/gruntwork-io/module-ci-public). If you need access, email support@gruntwork.io.




## How do you use this module?

See the [lambda-rds-snapshot example](/examples/lambda-rds-snapshot) for sample code. 

If you are using this function to copy snapshots to another AWS account, you may also want to look at the 
[lambda-create-snapshot](/modules/lambda-create-snapshot) and 
[lambda-share-snapshot](/modules/lambda-share-snapshot) modules.




## Background info

For more info on how to backup RDS snapshots to a separate AWS account, check out the [lambda-create-snapshot module
documentation](/modules/lambda-create-snapshot).