**Typical error messages in eMagiz**

Below are some common error messages in eMagiz that can help to understand these better, and work towards a solution for these.

**Last updated:** February 14th ,2020

|#| **ClassException** | **Last Exception Message**| **Exception** | **Possible cause** |  **Potential solution**|
|--|--|--|--|--|--|
|1 |JMSException  |There is no queue with name X  |  | There is no queue known in JMS with name xxx | Update the infra flows of the container, restart the JMS so it can create the queue for you|
|2|SAXParseException|cvc-type.3.1.3: The value X of element Y is not valid.|cvc-enumeration-valid:Value X is not facet-valid with respect to enumerationY. It must be a value from the enumeration.|Value Y is unknown in enumeration Y|Add enumeration value X to the transformation|
|3|xxx|xxx|cvc-maxLength-valid: Value X with length = '4' is not facet-valid with respect to maxLength '1' for type Y.|Value can have a maximum length of 1, whilst the actual value is 4|Agree with both parties what should be send and received|
|4|SAXParseException|cvc-complex-type.2.4.b: The content of element 'X' is not complete. One of Y is expected.|xxx|Element Y can’t be found in the message whilst the message definition expects this element Y as mandatory in the message.|Please consult receiving system to understand if this field Y should be mandatory to receive or not. And how it should be filled properly.|
|5|NoSuchBean DefinitionException|No bean named X is defined|xxx|In the routing process, the message can’t be processed. The message type is not handled in any of the routing management.|To enable proper Routing of the Message, a specific channel should be added to the existing routing flow. Whenever the message shouldn’t be routed, it can be handled by adding a Recipient Router that can manage the routing or deletion of the of the message. Use the expression: '${Property}' == 'true' for this purpose|
|6|Message RejectedException|Message was rejected due to XML Validation errors|cvc-complex-type.2.4.d: Invalid content was found starting with element X. No child element is expected at this point.|The message contains element X but according to the definition it’s expected on a different location sequence wise|Change the location only when agreed between both systems|
|7|Message DeliveryException |no channel resolved by router and no default output channel defined
|xxx|In the routing process, eMagiz can’t put the message to any of the channels, nor is there a default output channel for unhandled messages|Please add a default channel for unmanaged messages in the Routing. The null Channel will result in a silent disappearance of the message.|
