<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/microlearning/intermediate-solution-architecture-index" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>

<div class="doc">

##### Intro

# System vs Multi-tenant System
 
Within Capture, you need to drag and drop systems on the canvas. In the crashcourse platform, we have focused on the basic concepts to [Configure a system](crashcourse-platform-capture-configure-a-system.md). In this microlearning, we will zoom in on the differences between selecting a 'standard' system and a multi-tenant system to build your integration solution with. Knowing the differences between the two is relevant so you can make an informed decision on which option to select when.

Should you have any questions, please contact academy@emagiz.com.

- Last update: July 28th, 2021
- Required reading time: 5 minutes

## 1. Prerequisites
- Basic knowledge of the eMagiz platform

## 2. Key concepts
This microlearning centers on a 'standard' system vs a multi-tenant system.

With a multi-tenant system we mean: A system that can be deployed in various locations but uses the same functionality across those locations

The focal point of this microlearning will be to explain the difference between a 'standard' system and a multi-tenant system.

- The key aspects are:
    - A system has an individual connection and data exchange with a system
    - A multi-tenant system reuses the integration solution but can be deployed differently per tenant
    - Multi-tenant solution is handy in case you want to standardize but the supplying (or receiving) applications are deployed on varying locations instead of a single location
    - In case all communication can run through the eMagiz cloud the API Gateway could be an alternative
    - Choosing between API Gateway and multi-tenant in messaging is a question on synchronous vs asynchronous

##### Theory
  
## 3. System vs Multi-tenant System

Within Capture, you need to drag and drop systems on the canvas. In the crashcourse platform, we have focused on the basic concepts to [Configure a system](crashcourse-platform-capture-configure-a-system.md). In this microlearning, we will zoom in on the differences between selecting a 'standard' system and a multi-tenant system to build your integration solution with. Knowing the differences between the two is relevant so you can make an informed decision on which option to select when.

The focal point of this microlearning will be to explain the difference between a 'standard' system and a multi-tenant system.

- The key aspects are:
    - A system has an individual connection and data exchange with a system
    - A multi-tenant system reuses the integration solution but can be deployed differently per tenant
    - Multi-tenant solution is handy in case you want to standardize but the supplying (or receiving) applications are deployed on varying locations instead of a single location
    - In case all communication can run through the eMagiz cloud the API Gateway could be an alternative
    - Choosing between API Gateway and multi-tenant in messaging is a question on synchronous vs asynchronous

As stated above when summarizing the key aspects of the choice we first need to look at how we look at the world when creating the integration data model. Do we adhere to the structure as dictated by each system with whom we want to connect? If so we should always opt for the standard system in Capture as each of those systems will also vary in the data structure, connectivity, and authentication.

However, when we turn our viewpoint from inside out to outside in and determine that for some structures (i.e. Order entry process) it would be very handy to define a standard set of rules in terms of the data structure, connectivity, and authentication using a multi-tenant system could be very beneficial. This way you can build a solution once and deploy it many. With that construction, you can significantly save time while developing and while managing the solution. 

But then what about the API Gateway? Does that not also define a standard set of rules in terms of the data structure, connectivity, and authentication. Yes, it does. There are however two key differences when choosing between the API Gateway solution and a multi-tenant messaging system. The first key difference lies in synchronicity. The API Gateway deals with synchronous traffic (i.e. request and reply structures) whereas the multi-tenant option would handle data asynchronously (i.e. fire and forget). The second key difference lies in the strictness of the pattern. If you want to implement the API Gateway you need to adhere to a stricter set of rules as most in eMagiz is autogenerated for you. The same does not apply to messaging in that regard as you would typically start with an empty canvas and are relatively free to do with it what you see fit.

Based on the above considerations you should be able to determine which solution fits your integration challenge.

##### Practice

## 4. Assignment

Reflect on the choices made within various projects and see if you would, with what you know now, change the specific implementation.

## 5. Key takeaways

- The key aspects are:
    - A system has an individual connection and data exchange with a system
    - A multi-tenant system reuses the integration solution but can be deployed differently per tenant
    - Multi-tenant solution is handy in case you want to standardize but the supplying (or receiving) applications are deployed on varying locations instead of a single location
    - In case all communication can run through the eMagiz cloud the API Gateway could be an alternative
    - Choosing between API Gateway and multi-tenant in messaging is a question on synchronous vs asynchronous

##### Solution

## 6. Suggested Additional Readings

If you are interested in this topic and want more information on it please read the help texts provided by eMagiz

## 7. Silent demonstration video

As this is a more theoretical microlearning we have no video for this

</div>
</main>
</div>
</div>