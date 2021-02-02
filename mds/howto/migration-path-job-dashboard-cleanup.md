## Migration Path - Job Dashboard Cleanup

Below you will find a document describing the migration path to add the Job Dashboard Cleanup functionality to a datapipeline solution you have previously build.
In case you want to implement a new datapipeline make sure to import it from the store as that will guarantee that this functionality will be included.

Should you have any questions, please contact productmanagement@emagiz.com.
Last update: February 2th 2021

## Pre-requisites
- Basic knowledge of the eMagiz platform
- Understanding of Data pipelining concepts
- A existing Data pipeline solution within your eMagiz project.

## 1. Remove unnecessary components

First we will delete components that have become obsolete as of late. The components you can remove from the flow are:

- support.bus-connection-plain
- support.bus-connection-caching

Furthermore you could remove the following debug components as every interesting step is already monitored and can therefore be tracked without the help of the debugger:

- global channel interceptor
- activate.debug-bridge
- send.debug
- entry.channel.debug-queue
- debugBridgeChannel

## 2. Add new components to cleanup the Job Dashboard

With the new functionality we have made it possible to cleanup the Job Dashboard for you. This to ensure that you can keep accessing the job info of the last month of job activity.

To make sure that your existing data pipeline will function in the same way you should execute the following steps:

- Add a support object called top level poller and configure it as follows
	<p align="center"><img src="../../img/howto/migration-path-job-dashboard-cleanup-top-level-poller-config.png"></p>
- Add a channel called clean
- Add a standard inbound channel adapter called clean.cron and configure it as follows (As you can see it cleans the job dashboard every day at five in the morning)
	<p align="center"><img src="../../img/howto/migration-path-job-dashboard-cleanup-clean-cron-config.png"></p>
- Add a standard inbound channel adapter called startup.cron and configure it as follows (It cleans the job dashboard on startup)
	<p align="center"><img src="../../img/howto/migration-path-job-dashboard-cleanup-startup-cron-config.png"></p>
- Add a JDBC outbound channel adapter to your flow
	- Use the clean channel as input
	- Link it to the h2 database that is in your flow
	- Enter the query that you can find below
	<p align="center"><img src="../../img/howto/migration-path-job-dashboard-cleanup-jdbc-outbound-config.png"></p>
	
### 2.1 Query you need for cleanup

The following query is needed to cleanup all relevant parts of the job dashboard to ensure that only the jobs of the last month are still visible.

DELETE FROM BATCH_JOB_EXECUTION_CONTEXT WHERE
JOB_EXECUTION_ID IN (SELECT JOB_EXECUTION_ID FROM BATCH_JOB_EXECUTION WHERE DATEADD(MONTH, 1, CREATE_TIME) < CURDATE());
DELETE FROM BATCH_JOB_EXECUTION_PARAMS WHERE
JOB_EXECUTION_ID IN (SELECT JOB_EXECUTION_ID FROM BATCH_JOB_EXECUTION WHERE DATEADD(MONTH, 1, CREATE_TIME) < CURDATE());
DELETE FROM BATCH_STEP_EXECUTION_CONTEXT WHERE
STEP_EXECUTION_ID IN (SELECT STEP_EXECUTION_ID FROM BATCH_STEP_EXECUTION WHERE
JOB_EXECUTION_ID IN (SELECT JOB_EXECUTION_ID FROM BATCH_JOB_EXECUTION WHERE DATEADD(MONTH, 1, CREATE_TIME) < CURDATE()));
DELETE FROM BATCH_STEP_EXECUTION WHERE
JOB_EXECUTION_ID IN (SELECT JOB_EXECUTION_ID FROM BATCH_JOB_EXECUTION WHERE DATEADD(MONTH, 1, CREATE_TIME) < CURDATE());
DELETE FROM BATCH_JOB_EXECUTION WHERE DATEADD(MONTH, 1, CREATE_TIME) < CURDATE();
DELETE FROM BATCH_JOB_INSTANCE WHERE
JOB_INSTANCE_ID NOT IN (SELECT JOB_INSTANCE_ID FROM BATCH_JOB_EXECUTION);

## 3. Result

The result should look something like this:

<p align="center"><img src="../../img/howto/migration-path-job-dashboard-cleanup-result.png"></p>

