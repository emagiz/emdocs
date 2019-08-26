---
id: custom-attribute
title: Custom attribute
sidebar_label: Custom attribute
---
#### Name
Unique name for this custom attribute.

This value needs to match exactly the value used in the calls to the mapping web services that are made from eMagiz message flows.

<i>Required</i>

#### Initial value
The initial value for this custom attribute. This value is used in the following two cases:
 - when creating/modifying a CDM code, this value is copied to the (new) custom attribute for that CDM code
 - when creating/modifying a code type, this value is copied to all (new) custom attributes of CDM codes that didn't have that attribute before

In other words, this value is only used when a new custom attribute is created for a CDM code; it will never be used to replace existing values retro-actively.

<i>Optional</i>

