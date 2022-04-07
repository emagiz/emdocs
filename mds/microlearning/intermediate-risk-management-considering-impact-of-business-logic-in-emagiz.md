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

# Considering the impact of business logic

In this microlearning, we will learn what you should consider determining the impact of business logic within your integration solution. An eMagiz model is most useful when exchanging data between systems while taking care of data and protocol transformations. For example, an eMagiz model is generally less suited for incorporating business logic as these rules cannot be defined dynamically and are relatively complex. Filling your eMagiz model with a lot of business logic opens you up for a continuous discussion about data and interpretations of business rules. As that is not the core goal of an eMagiz model, you should always ask yourself what the most suitable place is to incorporate pieces of logic.

Should you have any questions, please get in touch with academy@emagiz.com.

- Last update: April 6th, 2021
- Required reading time: 4 minutes

## 1. Prerequisites
- Advanced knowledge of the eMagiz platform

## 2. Key concepts
This microlearning centers around considering the impact of business logic
By business logic, we mean: Rules that determine what should happen to a message

The most interesting point when talking about business logic is:
- Where to draw the line?

##### Theory

## 3. Considering the impact of business logic

In this microlearning, we will learn what you should consider determining the impact of business logic within your integration solution. An eMagiz model is most useful when exchanging data between systems while taking care of data and protocol transformations. For example, an eMagiz model is generally less suited for incorporating business logic as these rules cannot be defined dynamically and are relatively complex. Filling your eMagiz model with a lot of business logic opens you up for a continuous discussion about data and interpretations of business rules. As that is not the core goal of an eMagiz model, you should always ask yourself what the most suitable place is to incorporate pieces of logic.

The most exciting point when talking about business logic is:
- Where to draw the line?

What is acceptable and what is not acceptable in eMagiz then quickly becomes the question. You could argue that any business rule is too much in eMagiz. However, that is a bit too strict of a definition as there are scenarios in which it is pretty helpful to manipulate the destination of messages while transporting them between systems. One example of this would be logic in the asynchronous routing that allows you to develop functionality within the routing and ensure that each piece of the functionality comes with an on/off switch. This way, you reduce problems when deploying and make it clear to all that data can be sent (or not sent) to certain offramps.

Another valid scenario would be to filter messages based on a single criterion to reduce the data load sent to specific systems. For example, when you have one system that sends out employee information that needs to be sent to ten different systems, you could use the messaging pattern and filter out the relevant information in the offramp. However, you could also publish all employee information on a topic, let all those systems consume from it, and do the filtering themselves. Both are possible. The most interesting question in this scenario would be whether it can hurt if all systems access all employee information. If that is the case, then filtering in eMagiz becomes highly relevant suddenly.

On the flip side, you should not implement business logic in eMagiz if the rules consist of multiple criteria and are dependent on other (tables of) information. So gathering all that and making the decision will become so complex that you should consider moving the logic to the business application itself. That way, you reduce the complexity of the integration. This reduces the risks of things going wrong and reduces the time needed to develop and maintain the integration.

The main takeaway should be that adding business logic comes at a price. Depending on the specific requirements, you have to decide whether the pros outweigh the cons. The most crucial part of using business logic is proper documentation. That way, it is clear what the business logic does, why it is there, and how it can be controlled.

##### Practice

## 4. Assignment

See if you can determine which business logic is implemented in your project and whether that was a wise decision. This assignment can be completed with the help of the (Academy) project that you have created/used in the previous assignment.

## 5. Key takeaways

- Check out the pros and cons to determine whether business logic in eMagiz makes sense
- Documentation is key

##### Solution

## 6. Suggested Additional Readings

- [Asynchronous Routing](crashcourse-messaging-asynchronous-routing.md)

## 7. Silent demonstration video

There is no video for this microlearning.

</div>
</main>
</div>
</div>