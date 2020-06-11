
Release notes for build number 48
Version 48, released 2020-05-15

Small update that adds improved error handling to data pipelines.

Minor changes
- Updated bundle 'com.emagiz.batch.aws-redshift' from 1.1.0 to 1.2.0
- Updated bundle 'com.emagiz.batch.core' from 1.2.0 to 1.3.0

Bug fixes
- Improved error handling in the AWS Redshift item writer, where the status of the job sometimes (incorrectly) stated that the job completed successfully while having problems uploading the data to Redshift. To enable this new error handling behaviour, add the 'Exception job execution listener' to the listeners of your job configuration.