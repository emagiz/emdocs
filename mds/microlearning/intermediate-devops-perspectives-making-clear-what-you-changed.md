<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/microlearning/intermediate-devops-perspectives-index" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>

<div class="doc">

##### Intro

# Making clear what you changed (auditability)

As you can imagine, there is a need to know what has changed when working with software tooling. By knowing you can assess the impact of your planned changes within the context of the integration data model. In this microlearning, we will look at what you can do to clarify what you changed within the eMagiz platform.

Should you have any questions, please contact academy@emagiz.com.

- Last update: August 4th, 2021
- Required reading time: 6 minutes

## 1. Prerequisites
- Basic knowledge of the eMagiz platform

## 2. Key concepts
This microlearning centers on making clear what you changed (auditability).

Auditability is defined as follows: A history trail that depicts who changed what at which moment in time containing an explanation of what has been changed

- The key aspects are:
    - The description is your way of communicating the history of the flow
    - Using vague descriptions (or placing a dot as description) hurts the auditability
    - For all things versioned in eMagiz it is crucial that you supply the correct description
    - eMagiz provides audit trails on Architectural overviews (Design and Deploy architecture) including a description
    - eMagiz provides audit trails on message definitions and transformations including a description



##### Theory

## 3. Making clear what you changed (auditability)

As you can imagine, there is a need to know what has changed when working with software tooling. By knowing you can assess the impact of your planned changes within the context of the integration data model. In this microlearning, we will look at what you can do to clarify what you changed within the eMagiz platform.

- The key aspects are:
    - The description is your way of communicating the history of the flow
    - Using vague descriptions (or placing a dot as description) hurts the auditability
    - For all things versioned in eMagiz it is crucial that you supply the correct description
    - eMagiz provides audit trails on Architectural overviews (Design and Deploy architecture) including a description
    - eMagiz provides audit trails on message definitions and transformations including a description

### 3.1 Versioning by users

Three key parts within eMagiz require versioning by a user. These parts are:

- eMagiz data models (i.e. CDM, API Gateway Data Model, Event Streaming Data Model) in Design
- eMagiz flows in Create
- eMagiz releases in Deploy

#### 3.1.1 eMagiz Data Model

On the eMagiz data model level in Design, you can version your eMagiz Data model. By doing this you can register per the eMagiz data model what you have changed. If you want practical help in learning how you can version your eMagiz data model please check out this [microlearning](intermediate-defining-your-message-structures-audit-emagiz-data-models.md). Doing so is crucial in telling others now (and in the future) what you have changed and why you have changed that portion of the eMagiz data model.

#### 3.1.2 eMagiz Flows

On the eMagiz flow level in Create, you need to create a new flow version when you are satisfied with your changes (if any are needed). Note that eMagiz allows the ability to use temporary versions while developing. When using these do note that you need to create a definitive version at some point to prevent confusion now (and in the future). If you want practical help in learning how you can version your eMagiz flows please check out this [microlearning](crashcourse-platform-create-promote-flows-to-deploy.md). On the flow level, it must become clear to anyone what you have changed. That will determine whether a certain flow version is ready to be released much easier.

#### 3.1.3 eMagiz Releases

On the eMagiz release level, you need to create a new version whenever you want to include new versions of flows in a release. There is one exception to this rule and that is when someone else has already created a new release that is not yet deployed or made active. In that scenario, you can both combine all changes that need to de deployed to create a more efficient deployment. With eMagiz releases, you have two ways of notifying others what the release is all about. The first one is the name of the release and the second one is the description of a release. If you want to learn how to create a release please check out this [microlearning](crashcourse-platform-deploy-create-new-release.md). If you want to learn more about managing releases please check out this [microlearning](nog in te vullen)

### 3.2 Versioning by eMagiz

Apart from the fact that users need to version certain parts of the integration data model within the eMagiz platform, eMagiz also keeps a log of changes that are executed on other parts. The main parts on which eMagiz keeps an audit trail are:

- Architectural overviews (Design and Deploy Architecture)
- Message definitions and transformations

In all cases, you will find a History button on the page in question that will guide you to the history (audit trail) of what has changed by whom at which point in time.

##### Practice

## 4. Assignment

Check out the history of (one of) your eMagiz data models, one of your flows, and your releases to see if you can determine how they have changed over time.

## 5. Key takeaways

- The key aspects are:
    - The description is your way of communicating the history of the flow
    - Using vague descriptions (or placing a dot as description) hurts the auditability
    - For all things versioned in eMagiz it is crucial that you supply the correct description
    - eMagiz provides audit trails on Architectural overviews (Design and Deploy architecture) including a description
    - eMagiz provides audit trails on message definitions and transformations including a description

##### Solution
    
## 6. Suggested Additional Readings

If you are interested in this topic and want more information please check out the help texts provided by eMagiz.

## 7. Silent demonstration video

As this is a more theoretical microlearning we have no video for this.


</div>
</main>
</div>
</div>