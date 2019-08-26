---
id: calculate-exponential-moving-average
title: Calculate exponential moving average
sidebar_label: Calculate exponential moving average
---
#### Expected value
The value you would normally expect the metric in question to have.

For example, in a simple message bus that uses a single container you would expect every JMS queue to have exactly <code>1.00</code> consumers.

#### Trigger value
The value for the metric in question that indicates there is a problem you want to be alerted to.

For example, you might want to be alerted when any JMS queue has <code>0.00</code> consumers.

#### Trigger period
The period (in minutes) for the metric in question to be at the trigger value before it actually triggers. Increasing this value delays the moment the alert will trigger, but also better prevents false positives by filtering out short peak values.

For example, you might want to be alerted when any JMS queue has no consumers for at least <code>6</code> (consecutive) minutes.

---
id: calculate-exponential-moving-average
title: Calculate exponential moving average
sidebar_label: Calculate exponential moving average
---
#### Expected value
The value you would normally expect the metric in question to have.

For example, in a simple message bus that uses a single container you would expect every JMS queue to have exactly <code>1.00</code> consumers.

#### Trigger value
The value for the metric in question that indicates there is a problem you want to be alerted to.

For example, you might want to be alerted when any JMS queue has <code>0.00</code> consumers.

#### Trigger period
The period (in minutes) for the metric in question to be at the trigger value before it actually triggers. Increasing this value delays the moment the alert will trigger, but also better prevents false positives by filtering out short peak values.

For example, you might want to be alerted when any JMS queue has no consumers for at least <code>6</code> (consecutive) minutes.

