<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/microlearning/crashcourse-platform-index" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>

<div class="doc">

##### Intro

# Configure an integration

In this microlearning, we will focus on learning how to configure an integration. 
Configuring the integration itself is the third and final step in designing an integration within eMagiz

Should you have any questions, please contact academy@emagiz.com.

- Last update: July 26th 2021
- Required reading time: 8 minutes

# Intro

## 1. Prerequisites
- Basic knowledge of the eMagiz platform

## 2. Key concepts
This microlearning centers around configuring an integration.
With configuration we mean: Adding, Editing, and/or Deleting an integration
With integration we mean: A method to exchange data between an external party and eMagiz based on agreed-upon rules and definitions

To configure an integration you need the following:
- Connection information (how are you going to exchange information)
- Content information (what are you going to exchange)
- Security information (how are you going to secure the data exchange)

##### Theory

## 3. Configure an integration

As specified before with configure we refer to adding, editing, and/or deleting an integration. Below we will explain the steps in detail.

### 3.1 Adding a integration

To add an integration you simply drag a line from or to a system on the canvas

<p align="center"><img src="../../img/microlearning/crashcourse-platform-capture-configure-a-message-type--drag-message-type-on-canvas-start.png"></p> 

After you have connected the system to eMagiz (located in the center) you will immediately be presented with the following pop-up. In this pop-up you have a choice to make:

- Re-use a message type (in case another system already supplies Orders and you want to send these Orders to another system for example)
- Add a new message type

<p align="center"><img src="../../img/microlearning/crashcourse-platform-capture-configure-a-message-type--new-message-type-first-popup.png"></p>

In case you want to add a new message type, please study the microlearning **Configure a message type**.

In this microlearning, we will assume that the message type you want to use for this particular integration is already available within your eMagiz project.
Therefore we will select the message type Configure a message type from the drop-down menu.

<p align="center"><img src="../../img/microlearning/crashcourse-platform-capture-configure-a-integration--select-message-type.png"></p>

### 3.2 Editing a integration

Editing an integration can mean two things within the context of eMagiz. 
The first time you connect a system to eMagiz it means filling in the detailed information belonging to the integration.
Later on, editing is keeping the information up to date when changes occur.

Providing detailed information in Capture helps you to better Design, Create, Deploy and Manage your integration. 
This detailed information is available when you double click on the line you have just drawn (or select the Edit integration option via the context menu).

<p align="center"><img src="../../img/microlearning/crashcourse-platform-capture-configure-a-integration--edit-integration-context-menu.png"></p>

After you have selected the integration a pop-up will be shown. This pop-up is divided into three segments:

- General
- Connectivity/Security
- Content

#### 3.2.1 General
This segment answers several general questions surrounding this integration. With the help of the questions on this tab, you can set the stage in terms of the context of what the integration should do and when it is active (or not).

<p align="center"><img src="../../img/microlearning/crashcourse-platform-capture-configure-a-integration--edit-message-type-general-empty.png"></p>

After you have filled in the general details the information should look similar to something as depicted below

<p align="center"><img src="../../img/microlearning/crashcourse-platform-capture-configure-a-integration--edit-message-type-general-filled-in.png"></p>


#### 3.2.2 Connectivity/Security
The second segment has to do with the connectivity (i.e. how will the data be sent to eMagiz or from eMagiz to an external system) and security (i.e. how can you tell the external system to accept your data as coming from you).

In this segment you will answer questions on:
- how the messages will be send (i.e. REST web service, file drop, etc.)
- What are the specific connectivity details
- What do we know about the security of the external system
- Retention policy (in case of Event Streaming)
- GDPR

If you have filled in all this information you have learned a lot about how you need to Design and Create your integration.

<p align="center"><img src="../../img/microlearning/crashcourse-platform-capture-configure-a-integration--edit-message-type-connectivity-security.png"></p>

#### 3.2.3 Content
The third segment is focused on the content of the message. 
Remind yourself, in the previous segment we determined the format of the message, now we can zoom in to determine the actual content of the messages that will be exchanged.

In this question you can add various documents retrieved from the external party that define how messages will be exchanged:
- Example messages (i.e. examples of how a message could look like, very useful when unit testing your flow)
- Definitions (i.e XSD or WSDL, that define the exact structure, order, and data types of the message)
- Specification Document (i.e. detailing the method of authentication, order of actions needed to successfully post a message, etc.)

You can do so by adding attachments to this specific implementation of the message type.

<p align="center"><img src="../../img/microlearning/crashcourse-platform-capture-configure-a-integration--add-example-message-attachment.png"></p>

<p align="center"><img src="../../img/microlearning/crashcourse-platform-capture-configure-a-integration--add-xsd-attachment.png"></p>

All attachments linked to this specific implementation of the message type are shown in a grid on this third segment.

<p align="center"><img src="../../img/microlearning/crashcourse-platform-capture-configure-a-integration--message-content-overview.png"></p>

Note that you could also add additional remarks in this segment to provide even more context to those that will be actually building the integration.

### 3.3 Deleting a integration

Deleting an integration can be done with the help of the context menu on integration level. 
If you right-click on the line you have just finished you will see an option Delete Integration. 
Selecting that option will delete your integration.

<p align="center"><img src="../../img/microlearning/crashcourse-platform-capture-configure-a-integration--delete-integration.png"></p>

Be aware that you can only delete an integration if the integration is not part of the Create phase (anymore).

##### Practice

## 4. Assignment

The assignment is simple this time. Simply fill in the relevant details on the message type level. 
This assignment can be completed with the help of an associated Mendix project linked to the (Academy) project that you have created/used in the previous assignment.

## 5. Key takeaways

- A integration refers to a specific implementation between a specific external party and eMagiz based on a message type (data object)
- Several integrations can re-use the same message type
- Filling in the detailed information in Capture helps you to better Design, Create, Deploy and Manage your integration.
- Deleting an integration can only be done **after** the integration has been untransferred from Create (or never existed in Create in the first place)

##### Solution

## 6. Suggested Additional Readings

If you are interested in this topic and want more information on it please read the help text provided by eMagiz.

## 7. Silent demonstration video

This video demonstrates how you could have handled the assignment and gives you some context on what you have just learned. Disclaimer, you only see the eMagiz part but if you follow the above steps you are good to go!

<iframe width="1280" height="720" src="../../vid/microlearning/crashcourse-platform-capture-configure-a-integration.mp4" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

</div>
</main>
</div>
</div>