---
id: log-entry-trigger
title: Log entry trigger
sidebar_label: Log entry trigger
---
#### Apply trigger to
Select how to determine to which runtimes this triggers applies.

<b>1. all runtimes</b> Applies to all runtimes of the company.
<b>2. the following runtimes</b> Applies to all runtimes selected below.
<b>3. all runtimes, except for</b> Applies to all runtimes of the company, except for those selected below.


Enable trigger
If enabled, this trigger creates alerts for all events that match the specified rules.
The alerts are tagged with the specified tags.

These tags can be used for notification settings.

#### Evaluate only on 
Restrict the days and time when the trigger should be evaluated.

The restriction is based on the time that the monitored object sends the data, not on the time that the data arrives at the portal. Therefore, alerts may still be triggered outside the specified times.

This may be used to not trigger some alerts during the weekend or outside of working hours.

