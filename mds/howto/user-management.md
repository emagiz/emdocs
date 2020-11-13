## User Management
With the arrival of the API Gateway and Event Streaming modules within our platform a need for proper user management within the portal is needed. 
With the current functionality you have a clear way to define‘consuming’ entities of an API Gateway and assign the correct roles and rights on role and user level. This is done in a two part process.

*In upcoming releases of the platform this functionality will be changed and expended to serve more and other purposes*

### Capture
In Capture you can add a so called 'consuming' system of an API Gateway. 
To define a 'consuming' system you need to draw a line from the system to eMagiz indicating that an external system is 'consuming' the API Gateway.
The type of system you choose does not matter. Both single tenant and multi-tenant systems can fullfil this purposes.

The choice between creating a standard system or a multi-tenant system is based on what you want to achieve in terms of given access to roles and users.
By choosing the standard system you make the implicit choice that one user (i.e that system) has one specific role. 
By choosing the multi-tenant system you state that multiple users have the same role.

If you already have a system that also wants to 'consume' an API Gateway you don't have to create a new system but can simply draw a line from the existing system towards eMagiz.

<p align="center"><img  src="../../img/howto/user-management-capture.png"></p>

### Design
When you add a ‘consuming’ system of type API Gateway in Capture you have the ability in Design to assign rights to that ‘consuming’ system on one or more operations. 
This can be done by activating the checkbox in Design. By activating the checkbox in Design you’re telling eMagiz that this particular system (and all underlying users) has rights to access the operation you have just selected.

<p align="center"><img  src="../../img/howto/user-management-design.png"></p>
 
### Deploy
Changes made in Design are automatically updated in Deploy when you navigate to the User management tab.
This means that when you open the User management tab you will see all users and roles in the correct configuration based on the checkboxes selected in Design.
In this screen you do have to create a authentication string (i.e ApiKey) per user.
After you have done this and are satisfied with the manner in which the rights per role and user are configured you can update these settings per environment by pressing the Apply to environment button.
By pressing this button you indicate that the choices you made in Design can be actualized in Deploy for that particular environment.

<p align="center"><img  src="../../img/howto/user-management-deploy.png"></p>

After you have pressed the Apply to environment button you can retrieve the correct ApiKey per user under the corresponding property and you can test the settings via the Swagger UI which you can access via the Runtime Dashboard -> View Swagger UI


