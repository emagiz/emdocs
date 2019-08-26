---
id: notification-setting
title: Notification setting
sidebar_label: Notification setting
---

Enable setting
If enabled, notifications will be send when alerts are created that match the specified tags. 



#### Notify on alerts with all of these tags:
Notify when alerts are created that are tagged with all of these tags

#### Notify by:
Specify the type of the notification. 


#### Include notifications in daily digest.
When selected the notifications will be included in the daily digeset e-mail instead of sending them immediately in one message.

Note that you can't use daily digeset in combination with congestion control.

#### Notify recipients:
Specify the recipients of these notifications.

Note, only the recipients that you can add or remove are visible. 

#### External recipients:
Comma separated email adresses for external recipients.

For example: <code>info@emagiz.com, jane.doe@yahoo.com, support@example.com</code



#### Subject
Specify the subject of the notification. 

Maximum length of this field is 140 characters. 
If the notification type is 'email', this will be the subject of the e-mail.

The following tokens can be used for the subject and the content and will be replaced by the corresponding data: 
{DESCRIPTION} : Description of the alert
{SHORT_DESCRIPTION} : Short description of the alert
{SUMMARY} : Summary of the alert
{TIMESTAMP} : The date and time when the alert is created

#### Content
Specify the content of the notification. 

If the notification type is 'email', this will be the body of the e-mail.

The following tokens can be used for the subject and the content and will be replaced by the corresponding data: 
{DESCRIPTION} : Description of the alert
{SHORT_DESCRIPTION} : Short description of the alert
{SUMMARY} : Summary of the alert
{TIMESTAMP} : The date and time when the alert is created


#### Enable congestion control
Specify if congestion control is enabled for this type of notification.

If congestion control is active there is a maximum of alerts that will be processed to notifications. Alerts that aren't processed to notifications are skipped entirely and will never be processed again. 

Congestion control will limit the alerts every time the alerts are converted to notification.

For example: if there are 60 alerts and the congestion control maximum is set to 1 then only 1 email will be sent. 

When there is 1 alert over 60 notifications then 60 e-mails will be sent.  

Congestion control can't be used in combination with daily digest.

#### Maximum number of notifications created
Specify the maximum amount of alerts that will be handeled by this notification setting. 


Enable setting
If enabled, notifications will be send when alerts are created that match the specified tags. 



#### Notify on alerts with all of these tags:
Notify when alerts are created that are tagged with all of these tags

#### Notify by:
Specify the type of the notification. 


#### Include notifications in daily digest.
When selected the notifications will be included in the daily digeset e-mail instead of sending them immediately in one message.

Note that you can't use daily digeset in combination with congestion control.

#### Notify recipients:
Specify the recipients of these notifications.

Note, only the recipients that you can add or remove are visible. 

#### External recipients:
Comma separated email adresses for external recipients.

For example: <code>info@emagiz.com, jane.doe@yahoo.com, support@example.com</code



#### Subject
Specify the subject of the notification. 

Maximum length of this field is 140 characters. 
If the notification type is 'email', this will be the subject of the e-mail.

The following tokens can be used for the subject and the content and will be replaced by the corresponding data: 
{DESCRIPTION} : Description of the alert
{SHORT_DESCRIPTION} : Short description of the alert
{SUMMARY} : Summary of the alert
{TIMESTAMP} : The date and time when the alert is created

#### Content
Specify the content of the notification. 

If the notification type is 'email', this will be the body of the e-mail.

The following tokens can be used for the subject and the content and will be replaced by the corresponding data: 
{DESCRIPTION} : Description of the alert
{SHORT_DESCRIPTION} : Short description of the alert
{SUMMARY} : Summary of the alert
{TIMESTAMP} : The date and time when the alert is created


#### Enable congestion control
Specify if congestion control is enabled for this type of notification.

If congestion control is active there is a maximum of alerts that will be processed to notifications. Alerts that aren't processed to notifications are skipped entirely and will never be processed again. 

Congestion control will limit the alerts every time the alerts are converted to notification.

For example: if there are 60 alerts and the congestion control maximum is set to 1 then only 1 email will be sent. 

When there is 1 alert over 60 notifications then 60 e-mails will be sent.  

Congestion control can't be used in combination with daily digest.

#### Maximum number of notifications created
Specify the maximum amount of alerts that will be handeled by this notification setting. 

