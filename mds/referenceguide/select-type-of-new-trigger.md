---
id: select-type-of-new-trigger
title: Select type of new trigger
sidebar_label: Select type of new trigger
---

Trigger to evaluate incoming error messages. The content that can be evaluated includes:
- exception class
- exception message
- header values

These triggers can be used to create alerts when errors occur.


Trigger to evaluate incoming log entries. The content that can be evaluated includes:
- log level
- logger / bundle name
- flow name
- message content
- stack trace

These triggers can be used to create alerts when specific messages are logged.


Trigger to evaluate measurement data. These triggers can be used to create alerts based on the health of:
- eMagiz runtimes
- JMS queues
- message channels
- message handlers

Alerts are created when the monitored data exceeds the specified threshold first.
These triggers create reminder alerts once a day if a value is still exceeding the threshold.
They also create end alerts when the monitored value returns to normal.


Trigger to evaluate missing data (log entries or data measurements). These triggers can be used to check if no messages have been received over a specified period from:
- eMagiz runtimes
- JMS queues
- message channels
- message handlers

A first alert is created when the data has been missing for the specified period.
These triggers create reminder alerts once a day if no data has been received yet.
They also create end alerts when a message finally does come in.

It is possible to monitor continuously, or choose a single time of day to evaluate on.

#### Evaluated object type
Select which object type should be evaluated by this trigger.

---
id: select-type-of-new-trigger
title: Select type of new trigger
sidebar_label: Select type of new trigger
---

Trigger to evaluate incoming error messages. The content that can be evaluated includes:
- exception class
- exception message
- header values

These triggers can be used to create alerts when errors occur.


Trigger to evaluate incoming log entries. The content that can be evaluated includes:
- log level
- logger / bundle name
- flow name
- message content
- stack trace

These triggers can be used to create alerts when specific messages are logged.


Trigger to evaluate measurement data. These triggers can be used to create alerts based on the health of:
- eMagiz runtimes
- JMS queues
- message channels
- message handlers

Alerts are created when the monitored data exceeds the specified threshold first.
These triggers create reminder alerts once a day if a value is still exceeding the threshold.
They also create end alerts when the monitored value returns to normal.


Trigger to evaluate missing data (log entries or data measurements). These triggers can be used to check if no messages have been received over a specified period from:
- eMagiz runtimes
- JMS queues
- message channels
- message handlers

A first alert is created when the data has been missing for the specified period.
These triggers create reminder alerts once a day if no data has been received yet.
They also create end alerts when a message finally does come in.

It is possible to monitor continuously, or choose a single time of day to evaluate on.

#### Evaluated object type
Select which object type should be evaluated by this trigger.

