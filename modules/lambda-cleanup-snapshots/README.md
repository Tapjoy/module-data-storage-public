**Note**: This public repo contains the documentation for the private GitHub repo <https://github.com/gruntwork-io/module-data-storage>.
We publish the documentation publicly so it turns up in online searches, but to see the source code, you must be a Gruntwork customer.
If you're already a Gruntwork customer, the original source for this file is at: <https://github.com/gruntwork-io/module-data-storage/blob/master/modules/lambda-cleanup-snapshots/README.md>.
If you're not a customer, contact us at <info@gruntwork.io> or <http://www.gruntwork.io> for info on how to get access!

# Delete Snapshots Lambda Module

This module creates an [AWS Lambda](https://aws.amazon.com/lambda/) function that runs periodically and deletes old
snapshots of an [Amazon Relational Database (RDS)](https://aws.amazon.com/rds/) database. The module allows you to
specify the maximum number of snapshots you want to keep and any time that number of snapshots is exceeded, it will
delete the oldest snapshots.

Note that to use this module, you must have access to the Gruntwork [Continuous Delivery Infrastructure Package 
(module-ci)](https://github.com/gruntwork-io/module-ci-public). If you need access, email support@gruntwork.io.




## How do you use this module?

See the [lambda-rds-snapshot example](/examples/lambda-rds-snapshot) for sample code. 




## How do you configure this module?

This module allows you to configure a number of parameters, such as which database to backup, how often to run the 
backups, what account to share the backups with, and more. For a list of all available variables and their 
descriptions, see [vars.tf](./vars.tf).



