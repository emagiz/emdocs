---
id: aggregator
title: Aggregator
sidebar_label: Aggregator
---
### 
Provides different operations that allow you to summarize the values from a source list and obtain a new single value. The new value is the result of an operation applied to the elements in the list.

The <b>Sum</b> option returns the sum of all the source attribute values present in the source list.

The <b>Avg</b> option returns the average of all the source attribute values present in the source list. This means, a sum of all values divided by the total of elements in the list.

The <b>Min</b> option returns the minimum value encountered in the source list for the selected source attribute.

The <b>Max</b> option returns the maximum value encountered in the source list for the selected source attribute.

The <b>Position</b> returns a specific value in the source list. You can select the <i>head</i> or the <i>last</i> position in the list. 

The <b>Count</b> option returns the number of items in the source entity list where the selected attribute is present. Returns 0 if the source list is empty

The <b>String join</b> option returns a string containing all the values in the source list separated by a <i>Separator</i>

The <b>XPath</b> option allows you to fully customize the aggregation operation with a custom XPath expression. Technically, the XPath you enter will be used for the <code>&lt;xsl:value-of&gt;</code> statement in the generated stylesheet. Use the <i>view XSLT</i> button to see a preview how your XPath will be embedded in the resulting XSLT.


### 
String used as a separator for the concatenation of values from the source list. 
For example for the following ('a', 'b', 'c') values, if the separator is <b>;</b> the resulting <code>xs:string</code> will be <b>a;b;c</b>. If the separator is not provided, the values will be concatenated one next to another.



#### Provides different operations that allow you to summarize the values from a source list and obtain a new single value. The new value is the result of an operation applied to the elements in the list.
Provides different operations that allow you to summarize the values from a source list and obtain a new single value. The new value is the result of an operation applied to the elements in the list.

The <b>Sum</b> option returns the sum of all the source attribute values present in the source list.

The <b>Avg</b> option returns the average of all the source attribute values present in the source list. This means, a sum of all values divided by the total of elements in the list.

The <b>Min</b> option returns the minimum value encountered in the source list for the selected source attribute.

The <b>Max</b> option returns the maximum value encountered in the source list for the selected source attribute.

The <b>Position</b> returns a specific value in the source list. You can select the <i>head</i> or the <i>last</i> position in the list. 

The <b>Count</b> option returns the number of items in the source entity list where the selected attribute is present. Returns 0 if the source list is empty

The <b>String join</b> option returns a string containing all the values in the source list separated by a <i>Separator</i>

The <b>XPath</b> option allows you to fully customize the aggregation operation with a custom XPath expression. Technically, the XPath you enter will be used for the <code>&lt;xsl:value-of&gt;</code> statement in the generated stylesheet. Use the <i>view XSLT</i> button to see a preview how your XPath will be embedded in the resulting XSLT.

