---
id: cron-trigger-helper
title: Cron-trigger helper
sidebar_label: Cron-trigger helper
---
#### Triggers on
Helper used to set up a cron-trigger to specify the trigger schedule.

The cron-trigger will start on the times predefined in the helper.

It is also possible to define a custom specified value by selecting the <code>specified</code> option.

Each field allows the following values

<b>Minutes:</b> The numbers 0 to 59
<b>Hours:</b> The numbers 0 to 23
<b>Days of month:</b> The number 1-31
<b>Months:</b> The numbers 1-12
<b>Days in week:</b> The numbers 0-6 where 0 equals Sunday.

<b>Example</b>
It is also possible to specify a range with a Hyphen <code>-</code> e.g.
0-45 specifies each minute between 0 and 45 minutes.

Besides specifying a range it is also possible to specify a set of values by separating the values with a comma <code>,</code>. e.g. 10,20,40,50 specifies 4 times in one hour 10 minutes past the hour, 20 minutes past the hour 40 minutes past the hour and 50 minutes past the hour.





#### Triggers with an interval (only trigger on the nth member)
Besides selecting a set of times to trigger it is also possible to set an interval within this set. The interval is an Integer that equals the nth member of the set. e.g.

In the range of 0-59 minutes the interval 3 will set the trigger to only trigger on every 3rd member starting with 0. Thus it will trigger on 0,3,6 etc.

#### Triggers on
Helper used to set up a cron-trigger to specify the trigger schedule.

The cron-trigger will start on the times predefined in the helper.

It is also possible to define a custom specified value by selecting the <code>specified</code> option.

Each field allows the following values

<b>Minutes:</b> The numbers 0 to 59
<b>Hours:</b> The numbers 0 to 23
<b>Days of month:</b> The number 1-31
<b>Months:</b> The numbers 1-12
<b>Days in week:</b> The numbers 0-6 where 0 equals Sunday.

<b>Example</b>
It is also possible to specify a range with a Hyphen <code>-</code> e.g.
0-45 specifies each minute between 0 and 45 minutes.

Besides specifying a range it is also possible to specify a set of values by separating the values with a comma <code>,</code>. e.g. 10,20,40,50 specifies 4 times in one hour 10 minutes past the hour, 20 minutes past the hour 40 minutes past the hour and 50 minutes past the hour.





#### Triggers with an interval (only trigger on the nth member)
Besides selecting a set of times to trigger it is also possible to set an interval within this set. The interval is an Integer that equals the nth member of the set. e.g.

In the range of 0-59 minutes the interval 3 will set the trigger to only trigger on every 3rd member starting with 0. Thus it will trigger on 0,3,6 etc.

