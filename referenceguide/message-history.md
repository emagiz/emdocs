
Registers Message History writer which will track message history.
<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/system-management-chapter.html#message-history" target="_blank">Documentation</a>

Allows to keep track of all traversed components of a message, including the name of each channel and endpoint as well as the timestamp of that traversal.

A <i> message history </i> header  is added to the Message and is updated every time a message passes through a tracked component. 

Note: There can 
only be one Message History writer per ApplicationContext.


Tracked components
Some times you might not want to track all of the components. To accomplish this all you need is provide tracked-components attribute where you can specify comma delimited list of component names and/or patterns you want to track.

Example:
<code>*Gateway, sample*, foo</code>

In the above example, Message History will only be maintained for all of the components that end with 'Gateway', all components that start with 'sample' and 'foo' component. 



