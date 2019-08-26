---
id: microflow-invoking-message-consumer
title: Microflow invoking message consumer
sidebar_label: Microflow invoking message consumer
---
#### Message consumer that passes incoming messages to a specified Mendix microflow.
Message consumer that passes incoming messages to a specified <i>Mendix microflow</i>.

The message is mapped to the input parameters of the microflow as follows:

- Any <i>message header</i> with the same name (after removal of illegal characters) and type (after conversion) as one of the <i>microflow parameters</i>, is passed using that parameter.
- If <i>Payload parameter</i> is not set, the message payload is not passed at all.
- If <i>Payload parameter</i> is set and <i>Pass payload as path</i> is disabled, the message payload is passed using <i>Payload parameter</i>(if the payload type can be converted).
- If <i>Payload parameter</i> is set and <i>Pass payload as path</i> is enabled, the message payload is stored in a temp file and the path to this file (a string value) is then passed using <i>Payload parameter</i>.

Any temp files that are created are only guaranteed to exist while the microflow is running. After execution, the file will be deleted. 

#### Microflow
Microflow name, which must be an existing Mendix microflow

#### Payload parameter
Specify the microflow parameter that should be used for passing the message payload to Mendix. 
Leave empty to disable passing the payload as a parameter.

Default: <i> empty </i>

<i>If set, the parameter must exist in the microflow. If 'pass payload as path' is enabled this parameter must be of type String, otherwise the type should be that of the (expected) message payload.</i>

#### Execute in transaction
Specifies whether to execute the microflow in a Mendix transaction or not.

Default: <i> true</i>

#### Pass payload as path
If set, the message payload will be stored in a temp file and the path (as a string) will be passed to the microflow. 
Else the message payload will be passed directly to the microflow.

#### Channel
Channel to consume messages from.

<i>Required</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

