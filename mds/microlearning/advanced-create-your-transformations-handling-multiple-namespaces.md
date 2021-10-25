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

# Handling multiple namespaces

Sometimes you encounter definitions of external systems that refer to other definitions that are in different namespaces. As a result, the XML message you need to send or receive contains multiple namespaces. As one definition in eMagiz (and in XSD) can only include one namespace and eMagiz does not support references to other definitions, you need to have the ability to transform from one (or zero) namespace to multiple and vice versa. In this microlearning, we will discuss both variants to provide insight on how to achieve this.

Should you have any questions, please get in touch with academy@emagiz.com.

- Last update: October 25th, 2021
- Required reading time: 6 minutes

## 1. Prerequisites
- Advanced knowledge of the eMagiz platform

## 2. Key concepts
This microlearning focuses on handling multiple namespaces.

With namespace, we mean a set of uniquely named elements and attributes in an XML document.

To achieve this, we need an intermediate step:
- Remove namespaces (when receiving the message)
- Adding namespaces (when sending the message)

##### Theory

## 3. Handling multiple namespaces

Sometimes you encounter definitions of external systems that refer to other definitions that are in different namespaces. As a result, the XML message you need to send or receive contains multiple namespaces. As one definition in eMagiz (and in XSD) can only include one namespace and eMagiz does not support references to other definitions, you need to have the ability to transform from one (or zero) namespace to multiple and vice versa. In this microlearning, we will discuss both variants to provide insight on how to achieve this.

To achieve this, we need an intermediate step:
- Remove namespaces (when receiving the message)
- Adding namespaces (when sending the message)

### 3.1 Remove namespaces

Before we can validate our incoming message with the tooling of eMagiz, we need to remove all the namespaces from the message. Luckily there is a custom transformation available in the eMagiz store that removes all namespaces from a message. Search for remove namespace in the eMagiz store. This custom transformation searches for all namespaces and removes them, including their prefixes. See below for an example of how this will work for you.

This XSLT transformer will use a custom resource as attached and configured to perform the following actions:

1. Remove all namespaces in your XML Message. Example:

<?xml version="1.0" encoding="UTF-8"?>
<sys:root_element xmlns:sys="http://www.emagiz.com/ns/es-store/cdm/1.0/">
    <sys:envelope>
            <sys:messagetype>O2C_DESADV</sys:messagetype>
    </sys:envelope>
</sys:root_element>

will become

<root_element>
    <envelope>
            <messagetype>O2C_DESADV</messagetype>
    </envelope>
</root_element>


2. Keynotes
a. This will lead to an attribute name clash if an element contains two attributes with the same local name but different namespace prefix b. Nodes that cannot have a namespace are copied as such

### 3.2 Add namespaces

Adding namespaces is a two-part process within eMagiz currently. To make this work, you should prepare your definition in eMagiz by adding prefixes to each entity and attribute (based on which namespace they should be sent). As a result, you get a specific prefix for each particular namespace. After doing this, you can use a custom transformation (available in the eMagiz store) to transform these prefixes to the correct namespaces. Search for adding namespaces in the eMagiz store to get access to the custom transformation.

For more context on this solution, check out the store documentation and this Q&A interaction:
- https://my.emagiz.com/p/question/172825635700350785

##### Practice

## 4. Assignment

Check out whether removing or adding namespace is used within your project.
This assignment can be completed within the (Academy) project you created/used in the previous assignment.

## 5. Key takeaways

- With custom functionality, you can add and remove namespaces
- You can use the eMagiz store for this

##### Solution

## 6. Suggested Additional Readings

If you are interested in this topic and want more information, please read the help text provided by eMagiz.

## 7. Silent demonstration video

As this is more of theoretical microlearning, there is no video accompanying the microlearning.

</div>
</main>
</div>
</div>