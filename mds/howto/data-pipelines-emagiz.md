# Data pipelining in eMagiz

## 1. Introduction
In this document we take a look at implementing a data pipeline within eMagiz to support your business case. eMagiz data pipelines are flows that support high-volume data transfer using <a href="_new">Spring Batch</a> technology.

The document is structured as follows:
 * A quick overview of what a data pipeline can do and can not do for you
 * Take a look at the options you have as input and output of a data pipeline
 * Mendix to AWS Redshift example
 * Job Dashboard and the configuration of the dashboard

## 2. Data pipelines in eMagiz

A data pipeline connects a input and output stream without any or minimal transformation. This leads to the following advantages and disadvantages.

Advantages of eMagiz data pipelines
 * Supports very large tables
 * Fast Mendix to Redshift-integration development compared to message bus integrations

Disadvantages of eMagiz data pipelines
 * Does not support complex data structures (one table per data pipeline)
 * Does not support complex transformations (only column selection/renaming)
 * Data structure changes need to be applied to both source and target tables

## 3. Input and output options

Within eMagiz we support the following options for input and output of the data pipeline

Input
 * Flat file item reader (csv)
 * Odata v3 item reader (Mendix)

Output
 * Azure Event Hubs item writer
 * JDBC batch item writer
 * Amazon Redshift item writer
 * Remote flat file item writer
 
## 4. Mendix to AWS Redshift Example

### 4.1 Getting started
1. Publish the data using an OData service in your Mendix project.
1. Use the Mendix PostgreSQL data structure to create the target table in Redshift (Recommended).
1. Import the 'Mendix to Redshift' datapipeline flow from the store.
   <p align="center"><img src="../../img/howto/datapipeline-store-item.png"></p>
1. Follow the store items instructions to setup the data pipeline.
1. Follow the rest of this how-to to start using AWS materialized views.

### 4.2 Create a materialized view
1. Use SQL Workbench or the AWS Console to connect to the Redshift database.
1. Write and test the SQL statement to select data from the Redshift database. If you need help joining tables look at the 
    <a target="_new" href="https://www.w3schools.com/sql/sql_join_inner.asp">w3school tutorials</a>.
1. Execute the following statement to create the materialized view:</br>
    <code>CREATE MATERIALIZED VIEW {viewname} AS {your query};</code>
    <p align="center"><img  src="../../img/howto/datapipeline-create-materialized-view.png"></p>
1. For more info see the AWS documentation: 
    <a target="_new" href="https://docs.aws.amazon.com/redshift/latest/dg/materialized-view-overview.html">Creating materialized views in Amazon Redshift</a>

### 4.3 Refresh the materialized view
1. The example data pipeline flow from the store contains a job listener structure to refresh the AWS Materialized view after the job is complete. In this structure the <i>send.jdbc-refresh</i> component send the <code>REFRESH MATERIALIZED VIEW</code> command to AWS Redshift.
    <p align="center"><img  src="../../img/howto/datapipeline-listener-structure.png"></p>
1. It is highly recommended to have only one data pipeline in one eMagiz flow. If you have materialized views using data from different data pipelines, by default, the materialized view will be refreshed after each pipeline. If this causes invalid data in the materialized view, consider removing the refresh structure from all but the last scheduled data pipeline.
1. In case you are not using a Materialized View from the standard Store component, you have the option to remove this section alltogether or change the SQL statement where the refresh takes place to a non-functional (such as SELECT NOW() or SELECT true).

### 4.4 Delete the Materialized view
1. Use SQL Workbench or the AWS Console to connect to the Redshift database.
1. Execute the following statement to delete the materialized view:</br>
<code>DROP MATERIALIZED VIEW {viewname};</code>

## 5. Job dashboard data pipeline
On this page we will explain a bit on the job dashboard functionality within eMagiz

### 5.1 Job dashboard
On runtime level within the runtime dashboard a button named Jobs is available for users that make use of one or more data pipeline solutions within their respective eMagiz projects. By clicking on this button after you have selected a specific flow you get an overview of the Job executions of that flow.

<p align="center"><img src="../../img/howto/job-dashboard-data-pipeline-0.png"></p>

### 5.2 Explaining the inner workings of the Job Dashboard

By clicking on the Job dashboard you send a command to the flow you have selected in your runtime dashboard. This flow receives the command and thereby activates the job manager.

<p align="center"><img src="../../img/howto/job-dashboard-data-pipeline-1.png"></p>

The job manager in turn will look in the H2 database linked to that specific flow for relevant information on the executions of jobs via the data pipeline solutions.

This information is then showed to the user via a popup were you can see all executions and see the details of executions when you click through them

<p align="center"><img src="../../img/howto/job-dashboard-data-pipeline-2.png"></p>

### Best practices

- Create a separate H2 database per data pipeline you build within your project. For example if you have 10 data pipelines you should create 10 separate H2 databases. As stated in the documentation of the store component: 
	- dp.h2.message.database; database name for the local h2 database (eg: "batch"). When using multiple pipeline flows on one container, consider renaming this property by replacing 'message' with the corresponding message type name in the 'support.h2-database' component.
- Clean up the H2 database on a periodic basis to keep its contents in check to prevent that the Job dashboard will stop functioning
- Use the Job dashboard in conjuction with the Manage phase to monitor and set up alerting surrounding the performance of the data pipeline solutions