---
id: xslt-snippet
title: XSLT snippet
sidebar_label: XSLT snippet
---
#### Allows you to fully control the entity transformation by entering custom XSLT.


This operation allows you to fully control the entity transformation by entering custom XSLT. The entered XSLT will be used as the content of a <code>&lt;xsl:template&gt;</code> section in the resulting stylesheet. Use the <i>view XSLT</i> button to see a preview how your code will be embedded in the resulting XSLT.

Note that because the custom XSLT completely replaces the template that would otherwise have been generated automatically, mapping child attributes has no effect whatsoever. Mapping child entities can still have an effect, but only if you call the corresponding auto-generated templates from your custom XSLT snippet. For example:
<code>&lt;xsl:apply-templates select="cdm:ChildEntity"/&gt;</code>

Be aware that auto-generated templates might use a <code>mode</code>, in which case you should do the same in your <code>&lt;xsl:apply-templates&gt;</code> calls. Again, you can use the <i>view XSLT</i> button to see a preview how the resulting XSLT will look.

