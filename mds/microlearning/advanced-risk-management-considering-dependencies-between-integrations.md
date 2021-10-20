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

# Considering Dependencies between integrations

In this microlearning, we will learn what you should consider when looking at dependencies between integrations. An integration solution can consist of loads of different integrations, and several of those integrations can depend on each other. For example, when looking at an Order 2 Cash process in which an order travels from system A to B, and as a result, various messages are returned in sequence (i.e., conformation, shipment, invoice). Logic dictates that, for example, when the order never arrives, the other integrations will also not receive any data. Therefore it is relevant to consider these dependencies while performing a risk assessment.

Should you have any questions, please get in touch with academy@emagiz.com.

- Last update: October 19th, 2021
- Required reading time: 4 minutes

## 1. Prerequisites
- Advanced knowledge of the eMagiz platform

## 2. Key concepts
This microlearning centers around considering dependencies between integration
With dependencies, we mean: The matter in which the outcome of another integration dictates the working of one integration

When looking at dependencies, we ought to consider:
- Are there dependencies?
- Will the failure of integration block another?

##### Theory

## 3. Considering Dependencies between integrations

In this microlearning, we will learn what you should consider when looking at dependencies between integrations. An integration solution can consist of loads of different integrations, and several of those integrations can depend on each other. For example, when looking at an Order 2 Cash process in which an order travels from system A to B, and as a result, various messages are returned in sequence (i.e., conformation, shipment, invoice). Logic dictates that, for example, when the order never arrives, the other integrations will also not receive any data. Therefore it is relevant to consider these dependencies while performing a risk assessment.

When looking at dependencies, we ought to consider:
- Are there dependencies?
- Will the failure of integration block another?

At first, need to consider whether there are dependencies or whether each integration can perform its job without being influenced by other integrations. In scenarios of no dependence, there is also no risk of dependencies creating a cascade of problems. However, in situations where there are dependencies, one action could impact other integrations. An excellent example in a messaging environment is asynchronous routing. All asynchronous data traffic is passing the asynchronous routing and therefore changes to the routing directly impact all asynchronous integrations. So considering how, if and when to deploy an asynchronous routing is something worth thinking about.

The same applies to when you deploy other parts of the solution that could impact different integrations. Always ask yourself whether the quality of the answer will be upheld by the action you are about to perform.

Apart from the dependencies while deploying, there can also be dependencies while running the solution. These dependencies are primarily characterized in the sense that you need to receive something first before triggering another process (i.e., Order2Cash). Or for example, in the case of the API Gateway, you might first need to retrieve each invoice and do a subsequent call to retrieve all InvoiceLines. That has the consequence that when the Invoice integration is not working, the InvoiceLines integration will probably also not function as designed. So in a sense, the failure of one integration blocks the business process as it prevents API clients from retrieving the complete invoice in this example.

Being aware of these dependencies can significantly improve the choices you and the business make in terms of risk mitigation before developing your solutions via the eMagiz platform.

##### Practice

## 4. Assignment

See if you can determine the dependencies within your model. This assignment can be completed with the help of the (Academy) project that you have created/used in the previous assignment.

## 5. Key takeaways

- Dependencies are relevant when deploying and when running the model
- Failure in one integration can block other integrations (or reduce its value)

##### Solution

## 6. Suggested Additional Readings

There are no suggested additional readings on this topic.

## 7. Silent demonstration video

There is no video for this microlearning.

</div>
</main>
</div>
</div>