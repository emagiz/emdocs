<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/microlearning/intermediate-discover-your-integration-landscape-index" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>

<div class="doc">

##### Intro

# Determining Integration Pattern
 
In eMagiz, we differentiate between three "first-class" integration patterns. Each of these patterns is best suited for particular integration challenges. In this microlearning, we will see how to compare the three integration patterns to decide which pattern to choose.

Should you have any questions, please get in touch with academy@emagiz.com.

- Last update: August 5th, 2021
- Required reading time: 7 minutes

## 1. Prerequisites
- Basic knowledge of the eMagiz platform

## 2. Key concepts
This microlearning centers on determining integration patterns.

The focal point of this microlearning will be to figure out how you can best decide between the various "first-class" integration patterns.

- The key aspects are:
    - The three "first-class" patterns are messaging, event streaming, and API gateway
    - Each pattern has pros and cons
    - Decide which pattern suits best based on business and technical checks and balances

##### Theory
  
## 3. Determining Integration Pattern

In eMagiz, we differentiate between three "first-class" integration patterns. Each of these patterns is best suited for particular integration challenges. In this microlearning, we will see how to compare the three integration patterns to decide which pattern to choose.

The focal point of this microlearning will be to figure out how you can best decide between the various "first-class" integration patterns.

- The key aspects are:
    - The three "first-class" patterns are messaging, event streaming, and API gateway
    - Each pattern has pros and cons
    - Decide which pattern suits best based on business and technical checks and balances

As stated above, there are three "first-class" integration patterns within eMagiz. Each of these patterns has a unique way of processing the data. In this microlearning, we will look at how to decide which pattern best fits your integration challenge. Before we do that, let us first quickly look at the three integration patterns. In the picture below, you see a visual representation of each of the three patterns.

<p align="center"><img src="../../img/microlearning/intermediate-discover-your-integration-landscape-determining-integration-pattern--the-three-patterns-visualized.png"></p>

As you can see, each pattern works differently. If you want an in-depth introduction to messaging, please check out this [microlearning](crashcourse-messaging-introduction.md). If you want an in-depth introduction to event streaming, please check out this [microlearning](crashcourse-eventstreaming-event-streaming-introduction.md). If you want an in-depth introduction to API gateway, please check out this [microlearning](crashcourse-api-gateway-introduction.md).

Because each pattern works differently, each pattern has its pros and its cons. Depending on your specific use case, the balance between the pros and cons of one of the patterns will favor the pros. As a result, you should choose that option. But then, you ask, on what grounds should I make the decision? The answer is a series of checks and balances that look both at the business and technical aspects.

### 3.1 Checks and balances

At first, look at the business side of your integration scenario before delving into the technical disqualifiers. You should ask the first question: **Does the business process require a real-time response (for both success and error messages)?**. This question inevitably leads to the following question: **What is required?** In this case, required means that a person or system needs to wait for the answer (good or bad) before continuing with their process. If the answer is irrelevant for the progress of the process, real-time response is **not** required.

Based on your response to this first question, you have already made a distinctive choice that eliminates various possibilities. With that in mind, we will continue our quest in two 'lanes'. We start with asynchronous, and after that, we come back to synchronous.

#### 3.1.1 Asynchronous

Now that we have determined that our integration should run asynchronously, it becomes time to ask ourselves a second question: **With what frequency is the data delivered to eMagiz?**. If there is a high throughput requirement, the choice might differ when you only receive data once. You should ask yourself directly following this question: **How much data do I expect to process within one specific time frame?**. So, if the data is delivered five times a day, it will become relevant to determine how much data is produced each time. If the volume becomes vast in terms of numbers or size, selecting a particular pattern might change. As a rule of thumb, if you have low-frequency low throughput traffic **messaging** will be a solid choice. If you have high-frequency high throughput traffic, **event streaming** looks to be the best candidate at this point.

We are not done yet with our investigation. The next part of our investigation is about filtering and availability. A good question to ask yourself is: **Do all receiving systems want to receive the same dataset, or will this differ?**. The answer to this question will tell you something about the solution. If you opted for **event streaming** in this case, that would mean that you need to filter between topics to ensure that each consuming party gets the correct data set. This choice automatically implies that you need some additional storage capacity to make this happen. 

For **messaging**, this would mean filtering per offramp towards a system. The second question is on availability: **Are the target systems always online?** With availability, we mean 99,5% or more. When systems are not online or are hindered in their core process by data coming in at all hours of the day, you might want to retain data for a certain amount of time and let the consuming application consume the data when they want. If so **event streaming** will become more and more interesting over **messaging**.

Now that we are in the retention area, the question becomes how long data needs to be retained. Therefore we need to ask ourselves: **Does the data need to be retained for less than seven days?** If the answer is yes, we need to ask ourselves a follow-up question. **Are we allowed to keep this data under the compliance rules of the company?**. If the answer to that question is no, you cannot use event streaming.
As a consequence, the best pattern, in this case, will be messaging. Note that data is not retained within the **messaging** pattern but can be redelivered in case of emergency (i.e., when the system is down that one hour per year). If eMagiz can (temporarily) store the data, we will need to look at the technical aspect of the connected systems. The question then becomes: **Can the systems directly connect to a Kafka cluster?**. If so **event streaming** is your best choice. If not, you should consider a **hybrid case of messaging and event streaming** or go **complete messaging** is the frequency and throughput is shallow.

But then what if I have to retain the data for a period longer than seven days? In those cases, you will need an extension on the pattern to store data in S3 or another storage facility. Depending on what needs to be stored, eMagiz offers specific standardized store components to help you with this.

#### 3.1.2 Synchronous

Now that we have determined that our integration should run synchronously, we should first ask ourselves: **Can the data provider give back a timely response?** With timely in this context, we mean within 20 seconds. If the answer is yes, the **API gateway** pattern becomes the front runner. If not, you should see what kind of response the system calls your integration solution needs to continue. Is this simply an acknowledgment, or does the response need to contain specific data? If the latter is the case, you have a mismatch between the way both systems operate and a challenge on your hand. In those cases, the **messaging** pattern should be utilized. Note that the integration alone cannot be synchronous anymore but should be set up asynchronously to remove the time constraint on the response.

Assuming the data provider can respond promptly, we need to continue our investigations. As the **API gateway** requires that clients calling the API gateway call it via a REST interface, the next question becomes: **Can the client calling the API Gateway to communicate via the REST protocol?**. If the answer is yes, the **API gateway** is the preferred option. If the answer is no, you should select the **messaging** pattern. This time, however, the integration should be synchronous in nature.

Another aspect to consider is user management. The **API gateway** pattern comes with build-in user management functionality, whereas the **messaging** does not. So you should ask yourself the question: **Is centralized API Access required**? If so, the **API gateway** pattern best suits your needs. If not, you should base your decision on information gather before.

The last consideration we need to make concerns security. The **API gateway** pattern is set up so that all clients need to provide the same type of authentication. So, for example, when you have secured your API Gateway via the OAuth2.0 protocol, all clients that want to call your API Gateway should authorize themselves via this protocol. This could be a technical disqualifier for a particular integration solution. So the question becomes: **Can the client provide the proper authorization that we require?**. Note that when it is your first **API gateway** implementation, you might want to discuss the alternatives to agree upon a security protocol that best suits all parties involved.

Taking this all into consideration should guide you to select a particular integration pattern based on various business and technical checks and balances.

### 3.2 Licensing & Implementation Costs

Apart from the above considerations, there are also costs involved in making the decision. Unlocking a specific pattern will incur a licensing fee. So only using a particular pattern for only one integration solution might be less attractive. On the other hand, each pattern has differing implementation costs within eMagiz. Below you will see the patterns ranked based on the implementation costs (low to high):

- Event Streaming
- API Gateway
- Messaging

So that means that you might save money in the short with sticking what you know but could end up paying more due to (significantly) higher implementation costs. Hopefully, this microlearning will help you to make the correct decision per integration question.


##### Practice

## 4. Assignment

Reflect on the choices made within various projects and see if you would change the specific implementation with what you know now.

## 5. Key takeaways

- The key aspects are:
    - The three "first-class" patterns are messaging, event streaming, and API gateway
    - Each pattern has pros and cons
    - Decide which pattern suits best based on business and technical checks and balances

##### Solution

## 6. Suggested Additional Readings

If you are interested in this topic, please get in touch with academy@emagiz.com.

## 7. Silent demonstration video

As this is a more theoretical microlearning, we have no video for this.

</div>
</main>
</div>
</div>