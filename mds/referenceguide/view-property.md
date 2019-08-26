---
id: view-property
title: View Property
sidebar_label: View Property
---
#### Is global
By default a property value applies to just a single runtime. By setting this property to <code>yes</code>, the property becomes available to <i>all</i> runtimes of the company.

#### Data type
Data type of the property.

- <b>Username</b>: any text value, but gives the option to generate a random unique value
- <b>Password</b>: any text value, but gives the options to generate a random value; also hides the value in the overview
- <b>String</b>: any text value
- <b>Integer</b>: a positive or negative whole number
- <b>Cron trigger</b>: a text value that is a list of six fields representing a set of times

Default is <i>string</i>.

#### Name
Name for this property. Must be a unique name within the selected runtime.

<i>Required</i>

#### Value
Value for this property.

<i>Required</i>

#### Value
Value for this property.

<i>Required</i>

#### Value
Value for this property.

<i>Required</i>

#### Value
Value for this property. Must be a valid integer, i.e. a whole number between -2147483648 and 2147483647.

<i>Required</i>

#### Value
Value for this property: a pattern used by a cron-trigger to specify the trigger schedule.

The pattern is a list of six single space-separated fields, representing <code>second minute hour day month weekday</code>. Month and weekday names can be given as the first three letters of the English names.

Example patterns:

<code>0 0 * * * *</code> = the top of every hour of every day
<code>0 0 8-10 * * *</code> = 8, 9 and 10 o'clock of every day
<code>0 0/30 8-10 * * *</code> = 8:00, 8:30, 9:00, 9:30 and 10 o'clock every day
<code>0 0 9-17 * * MON-FRI</code> = on the hour nine-to-five weekdays
<code>0 0 0 25 12 ?</code> = every Christmas Day at midnight

<i>Required</i>

#### Description
Description of the property.

<i>Optional</i>

---
id: view-property
title: View Property
sidebar_label: View Property
---
#### Is global
By default a property value applies to just a single runtime. By setting this property to <code>yes</code>, the property becomes available to <i>all</i> runtimes of the company.

#### Data type
Data type of the property.

- <b>Username</b>: any text value, but gives the option to generate a random unique value
- <b>Password</b>: any text value, but gives the options to generate a random value; also hides the value in the overview
- <b>String</b>: any text value
- <b>Integer</b>: a positive or negative whole number
- <b>Cron trigger</b>: a text value that is a list of six fields representing a set of times

Default is <i>string</i>.

#### Name
Name for this property. Must be a unique name within the selected runtime.

<i>Required</i>

#### Value
Value for this property.

<i>Required</i>

#### Value
Value for this property.

<i>Required</i>

#### Value
Value for this property.

<i>Required</i>

#### Value
Value for this property. Must be a valid integer, i.e. a whole number between -2147483648 and 2147483647.

<i>Required</i>

#### Value
Value for this property: a pattern used by a cron-trigger to specify the trigger schedule.

The pattern is a list of six single space-separated fields, representing <code>second minute hour day month weekday</code>. Month and weekday names can be given as the first three letters of the English names.

Example patterns:

<code>0 0 * * * *</code> = the top of every hour of every day
<code>0 0 8-10 * * *</code> = 8, 9 and 10 o'clock of every day
<code>0 0/30 8-10 * * *</code> = 8:00, 8:30, 9:00, 9:30 and 10 o'clock every day
<code>0 0 9-17 * * MON-FRI</code> = on the hour nine-to-five weekdays
<code>0 0 0 25 12 ?</code> = every Christmas Day at midnight

<i>Required</i>

#### Description
Description of the property.

<i>Optional</i>

