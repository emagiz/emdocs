<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/microlearning/advanced-risk-management-index" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>

<div class="doc">

##### Intro

# Considering Impact of Downtime

In this microlearning, we will learn what you should consider determining the impact of downtime on the business. We will consider the impact when some specific part of the integration solution experiences downtime. We broaden our view to determine when multiple parts or even the whole integration solution experiences downtime. What should not be forgotten is the potential impact when the entire integration solution is running but specific target systems are unreachable. For example, it would be best to discuss what to do when it happens and mitigate the risks involved in all these scenarios. Note that downtime of an external system could also impact the business, leading to a loss of data. For this microlearning, we will look at the complete landscape in which eMagiz operates as the integration platform.

Should you have any questions, please get in touch with academy@emagiz.com.

- Last update: April 5th, 2021
- Required reading time: 6 minutes

## 1. Prerequisites
- Advanced knowledge of the eMagiz platform

## 2. Key concepts
This microlearning centers around considering the impact of downtime.
By downtime, we mean The amount of time the solution could not process messages.

Several viewpoints will be discussed:
- What if a specific part of the integration solution is down?
- What if multiple parts of the integration solution are down?
- What is the complete integration solution is down?
- What if a target system is down and therefore unreachable?

##### Theory

## 3. Considering Impact of Downtime

In this microlearning, we will learn what you should consider determining the impact of downtime on the business. We will consider the impact when some specific part of the integration solution experiences downtime. We broaden our view to determine when multiple parts or even the whole integration solution experiences downtime. What should not be forgotten is the potential impact when the entire integration solution is running but specific target systems are unreachable. It would be best to discuss what to do when it happens and mitigate the risks involved in all these scenarios.

Several viewpoints will be discussed:
- What if a specific part of the integration solution is down?
- What if multiple parts of the integration solution are down?
- What is the complete integration solution is down?
- What if a target system is down and therefore unreachable?

### 3.1 A specific part of the integration is down

When talking about the impact of downtime, we should always start to ask ourselves what the scope of the downtime is and when the downtime occurs. For example, imagine a scenario in which an eMagiz model runs 50 different integrations on a production environment, and of those 50, two integrations experience downtime. So the first question we should ask ourselves is which integrations experience downtime. And more specifically, which flows are not doing their work.

Let us assume the two flows in question that are down are two separate offramps towards two different systems. Now that we know this, there are two things we need to ask ourselves. At first, we should verify whether there is data flowing through these flows since the problem occurred. Suppose the answer is no, and we also do not expect data to flow through these flows soon. In that case, we have more time to investigate the issue than flows that already have data in them and when timely delivery of data is of the essence. So this is where the timing aspect comes into play.

When it does not bother anyone, downtime has less impact than downtime when data flows at peak rates and needs to end up in the target systems before a particular time of day.

### 3.2 Complete integration solution is down

Suppose we broaden our view and assume that the complete integration solution is down. Once again, timing matters. However, there is a complicated factor that we should acknowledge. For example, what is the full integration solution? We define the complete integration solution as any eMagiz component that integrates systems. So that means that we need to consider which integration patterns we use to integrate those systems. 

For event streaming, it would mean that the topics have become unreachable. For API Gateway, it would mean that our API endpoints are inaccessible. And within messaging, it can mean many things depending on how your architecture is set up. For example, suppose you have only file retrieval actions that trigger integrated data between the systems. In that case, the file retrieval will stop, but you will not lose the data as eMagiz will continue where it left off when the solution is available again. However, the consequences would be the same when you host endpoints in the messaging pattern running in the same way as you would with API endpoints.

As you can imagine, the impact within one eMagiz model implemented for customer A can differ from the effects of downtime of another eMagiz model implemented for customer B. It even means that the impact can vary between models that have been implemented for the same customer A.

That is why it is of utmost importance to understand how each pattern works within eMagiz, and the impact of the parts (or the whole) integration solution is down.

### 3.3 A target system is down

Let us now complicate things further by assuming that the integration solution is running, but the target system(s) have become unreachable. Once again, a lot boils down to the specific implementation you have chosen to integrate between systems. For example, the consuming party is responsible for consuming data and track which data is already consumed with event streaming. This means that eMagiz will retain the information on the topic (for the assigned amount of time). It becomes the responsibility of the consumer to get up and running and catch up before data is deleted from the topic.

However, if you call an endpoint in messaging, you probably retry several times, but the message is sometimes sent to the error queue. This also means that when the endpoint is down and many messages are sent around that time, the messages will not arrive in the target system but will end up in the error message dashboard of eMagiz. On the contrary, when data is temporarily stored somewhere and retrieved only from there based on a successful check towards the target system, things could look quite different. 

If a target system becomes highly unreliable, you could consider the message redelivery functionality of eMagiz. This functionality can help you redeliver failed messages when the target system is up again. Note that this solution is only available for asynchronous messaging.

To conclude the theoretical portion of this microlearning, we have listed several mitigations that come with the platform. Secondly, we recorded several mitigations you should consider as a user when determining the impact of downtime.

### 3.4 Mitigations performed by the platform

- Auto-healing (when running in the eMagiz cloud)
- H2 Database that acts as a bridge in entries (for messaging)
- Queuing (for messaging) in case no consumers are registered on the next queue
- Data retention (for event streaming) in case consumers temporarily stop consuming data
- Feedback loop to the client calling the API endpoint (for API Gateway) in case the target system is down.
- Ability to set up alerts
- Logging and error messages available to perform analysis

### 3.5 Mitigations to consider as a user

- Set up alerting
- Daily monitoring
- Discuss potential risks and appropriate actions beforehand with the customer
- Use the most suitable integration pattern for the needs of the customer

##### Practice

## 4. Assignment

See if you can determine the impact of downtime and assign risk-mitigating rules to this impact. This assignment can be completed with the help of the (Academy) project that you have created/used in the previous assignment.

## 5. Key takeaways

- Impact of downtime is a case of what and when
- Impact of downtime is model specific
- eMagiz offers several mitigations out of the box
- You should consider which additional measures need to be taken

##### Solution

## 6. Suggested Additional Readings

- [eMagiz Cloud](../fundamental/fundamental-emagiz-cloud-inner-workings.md)
- [Messaging](../fundamental/fundamental-messaging-introduction.md)
- [API Gateway](../fundamental/fundamental-api-gateway-introduction.md)
- [Event Streaming](../fundamental/fundamental-event-streaming-introduction.md)
- [Alerting](crashcourse-platform-manage-alerting-in-emagiz.md)
- [Daily Monitoring](intermediate-devops-perspectives-daily-monitoring.md)

## 7. Silent demonstration video

There is no video for this microlearning.

</div>
</main>
</div>
</div>