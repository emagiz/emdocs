<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/microlearning/advanced-create-your-transformations-index" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>

<div class="doc">

##### Intro

# XPath Advanced

Within the crash course, we already explained XPath conceptually. In that same microlearning, we also looked at some more uncomplicated cases of using XPath within your transformation. If you need to brush up on that knowledge, please check out this [microlearning](crashcourse-platform-create-transformation-XPath-basic.md). In the intermediate microlearning on this subject, we built upon that knowledge. Please check out this [microlearning](intermediate-create-your-transformations-xpath-intermediate.md) if you need a refresher on that. In this microlearning, we will build upon that knowledge and look at some concrete, practical examples that could be useful in your project.

Should you have any questions, please get in touch with academy@emagiz.com.

- Last update: October 25th, 2021
- Required reading time: 6 minutes

## 1. Prerequisites
- Advanced knowledge of the eMagiz platform
- [XPath Basic](crashcourse-platform-create-transformation-XPath-basic.md)
- [XPath Intermediate](intermediate-create-your-transformations-xpath-intermediate.md)

## 2. Key concepts
This microlearning focuses on more complex XPath operations.

With XPath Advanced, we mean learning that XPath options are complex but could benefit you in your daily work.

Some of the more complex XPath options are:
- dateTime calculation
- Filter list
- XPath on JSON
- SpEL notation for XPath

##### Theory

## 3. XPath Advanced

Within the crash course, we already explained XPath conceptually. In that same microlearning, we also looked at some more uncomplicated cases of using XPath within your transformation. If you need to brush up on that knowledge, please check out this [microlearning](crashcourse-platform-create-transformation-XPath-basic.md). In the intermediate microlearning on this subject, we built upon that knowledge. Please check out this [microlearning](intermediate-create-your-transformations-xpath-intermediate.md) if you need a refresher on that. In this microlearning, we will build upon that knowledge and look at some concrete, practical examples that could be useful in your project.

Some of the more complex XPath options are:
- dateTime calculation
- Filter list
- XPath on JSON
- SpEL notation for XPath

### 3.1 dateTime calculation

Sometimes we see that a dateTime calculation is needed within a transformation to determine a specific action. As these calculations are not natively supported within the eMagiz platform, you need to use XPath's functionality to calculate the new valid date (or dateTime). 

The XPath standard offers several functions to calculate with dateTime values. The two most used options are dayTimeDuration and yearMonthDuration. With the help of the dayTimeDuration, you can add, subtract, multiple, or divide seconds, minutes, hours, and days regarding the original value. The yearMonthDuration works similarly but then for months and years. An example of such an XPath is: <xsl:value-of xmlns:xs="http://www.w3.org/2001/XMLSchema" select="CDM:StartDate + xs:dayTimeDuration('P1D') - xs:yearMonthDuration('P1M')"/>. In this example, XPath adds one day and subtracts one month from the input date. Note that making this work requires the additional namespace to be defined. Therefore you need a custom snippet within your transformation or a custom transformation to make this work. Furthermore, note that the P1D and P1M could also be filled with the help of parameters to make them dynamic in nature.

Some examples that we saw during the years:
- https://my.emagiz.com/p/question/172825635700358186
- https://my.emagiz.com/p/question/172825635700352588

### 3.2 Filter list

Sometimes you have a large message which contains a certain list within it. However, logic dictates that you can only send the message if at least one entry in the list for which attribute A is filled and attribute B equals type C. To make that happen in XPath, we first need to navigate to the list within the message. As we previously learned, there are two options to do so. One is to use // to navigate to the entity somewhere in the tree directly. The other is to start at the root and walk the tree from there. In this example, we use the latter. That results in the following XPath example: /root/list[attributeB = 'type C']/attributeA !=''. With this XPath, you filter the list on the specified check and subsequently check whether one of those entries that remains has an attributeA which is filled in.

### 3.3 XPath on JSON

With the release of build number .50, we expanded our offering on JSON messages to resemble much of the functionality we previously offered for XML messages. As a result, you can use XPath expressions on JSON messages within the following components (related to XPath):

- XPath header enricher
- XPath transformer
- XPath router

To activate the functionality, simply link the JSON source factory support object to one of these components to achieve the desired result. For more information, check out: https://emagiz.github.io/docs/release-notes/build50.

### 3.4 SpEL notation for XPath

Sometimes you want to perform an XPath operation but store the header via a standard message header enricher component. As a result, you need a valid SpEL expression to help you in this cause. To do so, you need to know the correct notation for an XPath expression when using the SpEL language. An example of the correct notation is: #xpath(payload,'/root/entity/attribute')

##### Practice

## 4. Assignment

Check out which of the XPaths we have discussed today can be found within your project.
This assignment can be completed within the (Academy) project you created/used in the previous assignment.

## 5. Key takeaways

Some of the more complex XPath options are:
- dateTime calculation
- Filter list
- XPath on JSON
- SpEL notation for XPath

##### Solution

## 6. Suggested Additional Readings

If you are interested in this topic and want more information on it, please read the help text provided by eMagiz and read more information on the following link:
- https://www.w3schools.com/xml/xpath_intro.asp

## 7. Silent demonstration video

As this is more of theoretical microlearning, there is no video accompanying the microlearning.

</div>
</main>
</div>
</div>