---
id: header-filter
title: Header filter
sidebar_label: Header filter
---
#### Header names
Specify one or more header names (as a comma separated list) to be removed from the messages handled by this transformer.

<i>Required</i>

#### Pattern match
Whether values provided in <i>header names</i> should be treated as match patterns or literal values.

For example, <code>tmp_*</code> would mean remove all headers that begin with <code>tmp_</code> including the header named <code>tmp_*</code>. However if you want to treat <code>*</code> as literal value disabling this option will not perform pattern match and the only header that will be removed is the one that is an exact match.

Default is <code>true</code>.

#### Output channel
Channel where output messages should be sent after (successfully) processing the input message.

You can select the <code>nullChannel</code> here to silently drop the output messages.

<i>Required</i>

#### Input channel
Channel to consume the input messages from.

<i>Required</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

