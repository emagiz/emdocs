---
id: jms-queue-monitoring-trigger
title: JMS queue monitoring trigger
sidebar_label: JMS queue monitoring trigger
---
#### Trigger when
Select the type of data to be evaluated

#### Trigger on
Select how to determine to which objects this triggers applies.

<b>1. all objects</b> Applies to all objects of the company in this environment.
<b>2. the following objects</b> Applies to all objects selected below.
<b>3. all objects, except for</b> Applies to all objects of the company in this environment, except for those selected below.


Enable trigger
If enabled, this trigger creates alerts for all events that match the specified rules.
The alerts are tagged with the specified tags.

These tags can be used for notification settings.

#### Auto generate summary?
If checked, the summary of this alert is automatically generated based on its attributes.

#### Auto generate short description?
If checked, the short description of this alert is generated automatically based on its attributes.

#### Auto generate description?
If checked, the description of this alert is generated automatically based on its attributes.

#### Auto generate summary?
If checked, the summary of this alert is automatically generated based on its attributes.

#### Auto generate short description?
If checked, the short description of this alert is generated automatically based on its attributes.

#### Auto generate description?
If checked, the description of this alert is generated automatically based on its attributes.

#### Auto generate summary?
If checked, the summary of this alert is automatically generated based on its attributes.

#### Auto generate short description?
If checked, the short description of this alert is generated automatically based on its attributes.

#### Auto generate description?
If checked, the description of this alert is generated automatically based on its attributes.

#### Evaluate only on 
Restrict the days and time when the trigger should be evaluated.

The restriction is based on the time that the monitored object sends the data, not on the time that the data arrives at the portal. Therefore, alerts may still be triggered outside the specified times.

This may be used to not trigger some alerts during the weekend or outside of working hours.


The threshold that will trigger the alert.

The value that is compared is an EMA: Exponential Moving Average. This helps to reduce unwanted alerts caused by jitter, poor connections, redeployments, reboots and other noise.

For example, on a connector queue where the normal number of consumers would be 1, setting the threshold to 0.9 would trigger an alert almost immediately when the number of consumers drop to 0. While this may indeed indicate something is seriously wrong, it may also be a minimal disruption in the connection. In practice, it would be better to set the threshold to 0.5, which would trigger an alert after approximately 10 minutes without consumers.

