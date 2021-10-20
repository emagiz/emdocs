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

# Considering Impact of business logic

In this microlearning, we will learn what you should consider determining the impact of business logic within your integration solution. An eMagiz model is most useful when exchanging data between systems while taking care of data and protocol transformations in the process. An eMagiz model is generally less suited for incorporating business logic as these rules cannot be defined dynamically and are relatively complex. Filling your eMagiz model with a lot of business logic, therefore, opens you up for a continuous discussion about data and interpretations of business rules. As that is not the core goal of an eMagiz model, you should always ask yourself what the most suitable place is to incorporate pieces of logic.

Should you have any questions, please get in touch with academy@emagiz.com.

- Last update: October 19th, 2021
- Required reading time: 6 minutes

## 1. Prerequisites
- Advanced knowledge of the eMagiz platform

## 2. Key concepts
This microlearning centers around considering the impact of business logic
With business logic, we mean: Rules that determine what should happen to a message

Most interesting point when talking about business logic is:
- Where to draw the line?

##### Theory

## 3. Considering Impact of business logic

In this microlearning, we will learn what you should consider determining the impact of business logic within your integration solution. An eMagiz model is most useful when exchanging data between systems while taking care of data and protocol transformations in the process. An eMagiz model is generally less suited for incorporating business logic as these rules cannot be defined dynamically and are relatively complex. Filling your eMagiz model with a lot of business logic, therefore, opens you up for a continuous discussion about data and interpretations of business rules. As that is not the core goal of an eMagiz model, you should always ask yourself what the most suitable place is to incorporate pieces of logic.

Most interesting point when talking about business logic is:
- Where to draw the line?

What is acceptable and what is not acceptable in eMagiz then quickly becomes the question. In essence you could argue that any business rule is too much in eMagiz. However that is a little bit to strict of a definition as there are scenarios in which it is quite useful to manipulate the destination of messages while transporting them between systems. One example of this would be logic in the asynchronous routing that allows you to develop functionality within the routing but also ensure that each piece of the functionality comes with an on/off switch. This way you reduce problems when deploying and makes it clear to all that data can be send (or not send) to certain offramps.

Another valid scenario would be to filter messages based on a single criteria to reduce the data load that is send to a specific systems. For example when you have one system that sends out employee information that needs to be send to ten different systems you could use the messaging pattern and filter out the relevant information in the offramp. However, thruth be told you could also publish all employee information on a topic and let all those systems consume from it and do the filtering themselves. Both are possible, the most interesting question in this scenario would be whether it can hurt if all systems have access to all employee information. If that is the case than filtering in eMagiz becomes highly relevant all of a sudden.

On the flip side of things you should really not implement business logic in eMagiz if the rules consists of multiple criteria and is dependent on other (tables of) information. Gathering all that and making the decision will become so complex so fast that you should really consider moving the logic to the business application itself. That way you reduce the complexity of the integration. This not only reduces the risks of things going wrong but it also reduces the time that is needed to develop and maintain the integration.


When talking about the impact of downtime, we should always start to ask ourselves what the scope of the downtime is and when the downtime occurs. Imagine a scenario in which an eMagiz model runs 50 different integrations on a production environment, and of those 50, two integrations experience downtime. The first question we should ask ourselves is which integrations experience downtime. And more specifically, which flows are not doing their work.

Let us assume the two flows in question that are down are two separate offramps towards two different systems. Now that we know this, there are two things we need to ask ourselves. At first, we should verify whether there is data flowing through these flows since the problem occurred. Suppose the answer is no, and we also do not expect data to flow through these flows soon. In that case, we have more time to investigate the issue than flows that already have data in them and when timely delivery of data is of the essence. So this is where the timing aspect comes into play.

Downtime, when it does not bother anyone, has less impact than downtime when data flows at peak rates and needs to end up in the target systems before a particular time of day.

If we broaden our view and assume these two flows are down, but the complete integration solution is down. Once again, timing matters. However, there is a complicated factor that we should acknowledge. What is the full integration solution? For this discussion, we define the complete integration solution as any eMagiz component that integrates systems. So that means that we need to consider which integration patterns we use to integrate those systems. 

For event streaming, it would mean that the topics have become unreachable. For API Gateway, it would mean that our API endpoints are inaccessible. And for messaging, it can mean many things depending on how your architecture is set up. For example, suppose you have only file retrieval actions that trigger data being integrated between the systems. In that case, the file retrieval will stop, but you will not lose the data as eMagiz will continue where it left off when the solution is available again. However, the consequences would be the same when you host endpoints in the messaging pattern that are all running in the same way as you would with API endpoints.

As you can imagine, the impact within one eMagiz model that is implemented for customer A can differ from the impact of downtime of another eMagiz model implemented at customer B. It even means that the impact can vary between models that have been implemented for the same customer A.

That is why it is of utmost importance to understand how each pattern works within eMagiz, and the impact of parts (or the whole) integration solution is down.

Let us now complicate things further by considering the scenario in which the integration solution is running; however, the target system(s) have become unreachable. Once again, a lot boils down to the specific implementation you have chosen to integrate between systems. For example, the consuming party is responsible for consuming data and keeping track of which data is already consumed with event streaming. This means that eMagiz will retain the information on the topic (for the assigned amount of time). It becomes the responsibility of the consumer to get up and running and catch up before data is deleted from the topic.

However, if you call an endpoint in messaging, you probably retry several times, but the message is sometimes sent to the error queue. This also means that when the endpoint is down, and many messages are sent around that time, the messages will not arrive in the target system but will end up in the error message dashboard of eMagiz. On the contrary, when data is temporarily stored somewhere and retrieved only from there based on a successful check towards the target system, things could look quite different. 

If a target system becomes highly unreliable, you could consider the message redelivery functionality of eMagiz. This functionality can help you redeliver failed messages when the target system is up again. Note that this solution is only available for asynchronous messaging.

To conclude the theoretical portion of this microlearning, we have listed several mitigations that come with the platform. We recorded several mitigations you should consider as a user when determining the impact of downtime.

### 3.1 Mitigations performed by the platform

- Auto-healing (when running in the eMagiz cloud)
- H2 Database that acts as a bridge in entries (for messaging)
- Queuing (for messaging) in case no consumers are registered on the next queue
- Data retention (for event streaming) in case consumers temporarily stop consuming data
- Feedback loop to the client calling the API endpoint (for API Gateway) in case the target system is down.
- Ability to set up alerts
- Logging and error messages available to perform analysis

### 3.2 Mitigations to consider as a user

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

There are no suggested additional readings on this topic.

## 7. Silent demonstration video

There is no video for this microlearning.

</div>
</main>
</div>
</div>