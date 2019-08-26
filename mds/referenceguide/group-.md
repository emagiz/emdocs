---
id: group-
title: Group 
sidebar_label: Group 
---
### 
Provides several options that allows you  to organize a list of source entities into groups. The groups are created based on common values of a grouping key or on a pattern that specifies the start of a new group.

Note that you can use this operation in combination with a <i>Filter</i> operation to restrict the source elements that you want to group.

If the option <b>Group By</b> is selected, the groups will be created based on the selected  <i>Key attribute</i>. If your grouping-key is more complex you can select the option <i>Custom Key</i> and write a custom XPath expression.

The option <b>Starting with</b> allows you to write an XPath expression that  specifies the start of a new group. The <i>Start with</i> expression can be an attribute or entity from your source list. From that point, every item goes into the new group until another element that match the condition is found. For example, if your source file would contain HTML where <code>h1</code> describe the name of a book chapter and the following <code>p</code> elements describe a summary of the chapter. You could use this operation to start a new group for each <code>h1</code> that is found and add them inside a <code>chapter</code> element. Example of the output of such an XML structure: 
 
         &nbsp;&nbsp;&lt;chapters&gt;
         &nbsp;&nbsp;&nbsp;&nbsp;&lt;chapter&gt;
         &nbsp;&nbsp;&nbsp;&nbsp;&lt;h1&gt;Chapt1&nbsp;&lt;/h1&gt;
         &nbsp;&nbsp;&nbsp;&nbsp;&lt;p&gt;summary 1&nbsp;&lt;/p&gt;
         &nbsp;&nbsp;&nbsp;&nbsp;&lt;/chapter&gt;
         &nbsp;&nbsp;&nbsp;&nbsp;&lt;chapter&gt;
         &nbsp;&nbsp;&nbsp;&nbsp;&lt;h1&gt;Chapt2&nbsp;&lt;/h1&gt;
         &nbsp;&nbsp;&nbsp;&nbsp;&lt;p&gt;summary 2&nbsp;&lt;/p&gt;
         &nbsp;&nbsp;&nbsp;&lt;/chapter&gt;
         &nbsp;&nbsp;&lt;/chapters&gt;

Finally, the option <b>Use current group</b> allows you to use the output of the current group in a list to list mapping. This is handy when you want to iterate through each item in the current group.


#### Provides several options that allows you  to organize a list of source entities into groups. The groups are created based on common values of a grouping key or on a pattern that specifies the start of a new group.
Provides several options that allows you  to organize a list of source entities into groups. The groups are created based on common values of a grouping key or on a pattern that specifies the start of a new group.

Note that you can use this operation in combination with a <i>Filter</i> operation to restrict the source elements that you want to group.

If the option <b>Group By</b> is selected, the groups will be created based on the selected  <i>Key attribute</i>. If your grouping-key is more complex you can select the option <i>Custom Key</i> and write a custom XPath expression.

The option <b>Starting with</b> allows you to write an XPath expression that  specifies the start of a new group. The <i>Start with</i> expression can be an attribute or entity from your source list. From that point, every item goes into the new group until another element that match the condition is found. For example, if your source file would contain HTML where <code>h1</code> describe the name of a book chapter and the following <code>p</code> elements describe a summary of the chapter. You could use this operation to start a new group for each <code>h1</code> that is found and add them inside a <code>chapter</code> element. Example of the output of such an XML structure: 
 
         &nbsp;&nbsp;&lt;chapters&gt;
         &nbsp;&nbsp;&nbsp;&nbsp;&lt;chapter&gt;
         &nbsp;&nbsp;&nbsp;&nbsp;&lt;h1&gt;Chapt1&nbsp;&lt;/h1&gt;
         &nbsp;&nbsp;&nbsp;&nbsp;&lt;p&gt;summary 1&nbsp;&lt;/p&gt;
         &nbsp;&nbsp;&nbsp;&nbsp;&lt;/chapter&gt;
         &nbsp;&nbsp;&nbsp;&nbsp;&lt;chapter&gt;
         &nbsp;&nbsp;&nbsp;&nbsp;&lt;h1&gt;Chapt2&nbsp;&lt;/h1&gt;
         &nbsp;&nbsp;&nbsp;&nbsp;&lt;p&gt;summary 2&nbsp;&lt;/p&gt;
         &nbsp;&nbsp;&nbsp;&lt;/chapter&gt;
         &nbsp;&nbsp;&lt;/chapters&gt;

Finally, the option <b>Use current group</b> allows you to use the output of the current group in a list to list mapping. This is handy when you want to iterate through each item in the current group.


---
id: group-
title: Group 
sidebar_label: Group 
---
### 
Provides several options that allows you  to organize a list of source entities into groups. The groups are created based on common values of a grouping key or on a pattern that specifies the start of a new group.

Note that you can use this operation in combination with a <i>Filter</i> operation to restrict the source elements that you want to group.

If the option <b>Group By</b> is selected, the groups will be created based on the selected  <i>Key attribute</i>. If your grouping-key is more complex you can select the option <i>Custom Key</i> and write a custom XPath expression.

The option <b>Starting with</b> allows you to write an XPath expression that  specifies the start of a new group. The <i>Start with</i> expression can be an attribute or entity from your source list. From that point, every item goes into the new group until another element that match the condition is found. For example, if your source file would contain HTML where <code>h1</code> describe the name of a book chapter and the following <code>p</code> elements describe a summary of the chapter. You could use this operation to start a new group for each <code>h1</code> that is found and add them inside a <code>chapter</code> element. Example of the output of such an XML structure: 
 
         &nbsp;&nbsp;&lt;chapters&gt;
         &nbsp;&nbsp;&nbsp;&nbsp;&lt;chapter&gt;
         &nbsp;&nbsp;&nbsp;&nbsp;&lt;h1&gt;Chapt1&nbsp;&lt;/h1&gt;
         &nbsp;&nbsp;&nbsp;&nbsp;&lt;p&gt;summary 1&nbsp;&lt;/p&gt;
         &nbsp;&nbsp;&nbsp;&nbsp;&lt;/chapter&gt;
         &nbsp;&nbsp;&nbsp;&nbsp;&lt;chapter&gt;
         &nbsp;&nbsp;&nbsp;&nbsp;&lt;h1&gt;Chapt2&nbsp;&lt;/h1&gt;
         &nbsp;&nbsp;&nbsp;&nbsp;&lt;p&gt;summary 2&nbsp;&lt;/p&gt;
         &nbsp;&nbsp;&nbsp;&lt;/chapter&gt;
         &nbsp;&nbsp;&lt;/chapters&gt;

Finally, the option <b>Use current group</b> allows you to use the output of the current group in a list to list mapping. This is handy when you want to iterate through each item in the current group.


#### Provides several options that allows you  to organize a list of source entities into groups. The groups are created based on common values of a grouping key or on a pattern that specifies the start of a new group.
Provides several options that allows you  to organize a list of source entities into groups. The groups are created based on common values of a grouping key or on a pattern that specifies the start of a new group.

Note that you can use this operation in combination with a <i>Filter</i> operation to restrict the source elements that you want to group.

If the option <b>Group By</b> is selected, the groups will be created based on the selected  <i>Key attribute</i>. If your grouping-key is more complex you can select the option <i>Custom Key</i> and write a custom XPath expression.

The option <b>Starting with</b> allows you to write an XPath expression that  specifies the start of a new group. The <i>Start with</i> expression can be an attribute or entity from your source list. From that point, every item goes into the new group until another element that match the condition is found. For example, if your source file would contain HTML where <code>h1</code> describe the name of a book chapter and the following <code>p</code> elements describe a summary of the chapter. You could use this operation to start a new group for each <code>h1</code> that is found and add them inside a <code>chapter</code> element. Example of the output of such an XML structure: 
 
         &nbsp;&nbsp;&lt;chapters&gt;
         &nbsp;&nbsp;&nbsp;&nbsp;&lt;chapter&gt;
         &nbsp;&nbsp;&nbsp;&nbsp;&lt;h1&gt;Chapt1&nbsp;&lt;/h1&gt;
         &nbsp;&nbsp;&nbsp;&nbsp;&lt;p&gt;summary 1&nbsp;&lt;/p&gt;
         &nbsp;&nbsp;&nbsp;&nbsp;&lt;/chapter&gt;
         &nbsp;&nbsp;&nbsp;&nbsp;&lt;chapter&gt;
         &nbsp;&nbsp;&nbsp;&nbsp;&lt;h1&gt;Chapt2&nbsp;&lt;/h1&gt;
         &nbsp;&nbsp;&nbsp;&nbsp;&lt;p&gt;summary 2&nbsp;&lt;/p&gt;
         &nbsp;&nbsp;&nbsp;&lt;/chapter&gt;
         &nbsp;&nbsp;&lt;/chapters&gt;

Finally, the option <b>Use current group</b> allows you to use the output of the current group in a list to list mapping. This is handy when you want to iterate through each item in the current group.


