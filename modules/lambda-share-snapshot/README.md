**Note**: This public repo contains the documentation for the private GitHub repo <https://github.com/gruntwork-io/module-data-storage>.
We publish the documentation publicly so it turns up in online searches, but to see the source code, you must be a Gruntwork customer.
If you're already a Gruntwork customer, the original source for this file is at: <https://github.com/gruntwork-io/module-data-storage/blob/master/modules/lambda-share-snapshot/README.md>.
If you're not a customer, contact us at <info@gruntwork.io> or <http://www.gruntwork.io> for info on how to get access!

# Share Snapshot Lambda Module

This module creates an [AWS Lambda](https://aws.amazon.com/lambda/) function that can share snapshots of an [Amazon 
Relational Database (RDS)](https://aws.amazon.com/rds/) database with another AWS account. Typically, the snapshots
are created by the [lambda-create-snapshot module](/modules/lambda-create-snapshot), which can be configured to 
automatically trigger this lambda function after each run.




## How do you use this module?

See the [lambda-rds-snapshot example](/examples/lambda-rds-snapshot) for sample code. 

You may also want to look at the [lambda-create-snapshot](/modules/lambda-create-snapshot) and 
[lambda-copy-shared-snapshot](/modules/lambda-copy-shared-snapshot) modules.




## Background info

For more info on how to backup RDS snapshots to a separate AWS account, check out the [lambda-create-snapshot module
documentation](/modules/lambda-create-snapshot). 
 




