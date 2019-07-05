---
id: destination-filter
title: Destination filter
sidebar_label: Destination filter
---
### 
The option <b>if exists</b> checks if the source attribute node is present in the source XML message. If you enable the option <i> With empty check</i>  the condition will also check that the source attribute node has content. Note that this option is only available for <i> String</i> data types that accept empty content like 
<code>xs:string</code> or <code>xs:base64Binary</code>

Only when this is true, the transformation to the destination attribute is performed. This simple option is mainly intended for mapping rules where both the source and destination attributes are <i>optional</i>. 

The <b>XPath</b> option allows you to fully customize the condition with a custom XPath expression. Technically, the XPath you enter will be used as the condition of a <code>&lt;xsl:if&gt;</code> statement in the generated stylesheet. Use the <i>view XSLT</i> button to see a preview how your XPath will be embedded in the resulting XSLT.

### 
If this option is enabled,  an extra condition will be added  to the <i>ifExist</i> check. This extra condition will check if the source attribute has content. If both conditions are true, the transformation to the destination attribute is performed

This is mainly useful for <code>xs:string</code> source attributes, since an empty <code>xs:string</code> will pass the <i>XSD validating filter</i> and the <i>ifExists</i> check will not be sufficient to filter messages where the node does not have content. 

#### Only generates the destination attribute if the specified condition is met.


This operation only generates the destination attribute if the specified condition is met. This is particularly useful for <i>optional</i> destination attributes.

The option <b>if exists</b> checks if the source attribute node is present in the source XML message. If the option <i> With empty check</i> is enabled the condition will also check that the source attribute has content.  Note that this option is only available for <i> String</i> data types that accept empty content like <code>xs:string</code>

Only when this is true, the transformation to the destination attribute is performed. This simple option is mainly intended for mapping rules where both the source and destination attributes are <i>optional</i>.

The <b>XPath</b> option allows you to fully customize the condition with a custom XPath expression. Technically, the XPath you enter will be used as the condition of a <code>&lt;xsl:if&gt;</code> statement in the generated stylesheet. Use the <i>view XSLT</i> button to see a preview how your XPath will be embedded in the resulting XSLT.

