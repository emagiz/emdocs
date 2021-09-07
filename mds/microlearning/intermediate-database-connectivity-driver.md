<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/microlearning/intermediate-database-connectivity-index" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>

<div class="doc">

##### Intro

# Driver
 
In this microlearning, we will delve a bit deeper into connecting eMagiz with an external database. We will take a look at how to get the driver and reference it from your flow.

Should you have any questions, please get in touch with academy@emagiz.com.

- Last update: September 7th, 2021
- Required reading time: 4 minutes

## 1. Prerequisites
- Basic knowledge of the eMagiz platform


## 2. Key concepts
Each type of external database has its unique driver. So the driver for an Oracle database differs from the driver needed for a Postgres or MySQL database. Furthermore, the version of the database could influence which driver you need. Also, it would be best if you searched for JDBC drivers as other drivers do not work with the eMagiz setup. Last but not least, you might need assistance in uploading the driver if the package exceeds 1 MB.

##### Theory
  
## 3. Driver

In this microlearning, we will delve a bit deeper into connecting eMagiz with an external database. We will take a look at how to get the driver and reference it from your flow. Before we can reference the driver within the flow, we first need to find a suitable driver. The driver needs to match the following criteria:

- Suitable for the type of database
- JDBC driver
- Suitable for the version of the database you are connecting with

You can google for suitable drivers. However, some of them have already been used in other projects and will therefore be made available via the new store soon. Once you have found a suitable driver, the next step is to import the relevant resource into your project (in a similar manner as you would typically do). From there on, you only have to fill in the correct reference in the driver field. The best practice would be to use a property reference to fill in the proper reference when deploying. The correct reference should look as follows com.microsoft.sqlserver.jdbc.SQLServerDriver. Check out the help text on the component to see other driver references for different types of databases.

##### Practice

## 4. Assignment

See if you can find any database implementation within the projects you can access. This assignment can be completed with the help of the (Academy) project that you have created/used in the previous assignment.

## 5. Key takeaways

- Each type of external database has its unique driver
- You need a JDBC driver
- You might need assistance in uploading the driver if the package exceeds 1 MB


##### Solution

If you are interested in this topic and want more information, please read the help text provided by eMagiz.

## 7. Silent demonstration video

As this is more of theoretical microlearning, there is no video accompanying the microlearning.

</div>
</main>
</div>
</div>