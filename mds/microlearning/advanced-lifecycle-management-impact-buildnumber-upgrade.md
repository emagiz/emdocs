<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">

            <li class="doc-nav__item"><a href="../../docs/microlearning/advanced-lifecycle-management-index" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>

<div class="doc">

releasen notes
impact bepalen
sne;l overzetten
test en accp draaien
planbaar amaken 
 
 
##### Intro

# Impact of builnumber upgrades
 
In this microlearning, we will focus on the helping you to assess the impact of upgrading to new buildnumbers. 

Should you have any questions, please get in touch with academy@emagiz.com.

- Last update: August 27th, 2021
- Required reading time: 5 minutes

## 1. Prerequisites
- Advanced knowledge of the eMagiz platform
- Complete the microlearning that explains how to upgrade to a new buildnumber


## 2. Key concepts
With buildnumbers we mean the piece of software that used by a flow to make it operational inside the runtime. Several eMagiz libraries are loaded together with the flow components XML into the runtime (Java container). In essence that means that a new buildnumber means the flow is technically speaking different from the previous buildnumber.

eMagiz works hard to limit the number of buildnumbers. The general approach for buildnumber is that these are backwards compatible, so the impact of moving to the next buildnumber poses a minimal impact and risk.

##### Theory
  
## 3. Assessing the impact of changing buildnumbers

###3.1 Release notes & impact assessment
These can be found in the eMagiz Portal under Community --> Release notes. Check for the left hand menu called Build Numbers. Once the release notes are properly read, assess the impact. This effectively means that the key notes around the model components can be used. 

You see often a list of libraries that are updated, and these are the only notes that means that the impact is slim to none. Then make sure to read the notes above around the model components touched. These will help to asses the impact. Some model components have additional capability, and some have a limited capability or a fix.

Example
Flows containing a Jetty server (support object), primarily used to host REST and SOAP web services, require some special attention when deploying because not all combinations of build number 50 (and higher) and 48 (and lower) flows will work correctly:
- After installing any build 50 (or higher) flow, build 48 (or lower) flows containing a Jetty server on the same runtime cannot be started anymore. If it is really necessary to still install/start a build 48 (or lower) Jetty server flow: uninstall all build 50 (or higher) flows on that runtime first, then install/start the build 48 (or lower) Jetty server flow, and finally re-install the build 50 (or higher) flows.
- When deploying a flow containing a Jetty server, the infra flow of that runtime must have a matching build number, that is: if the the Jetty server flow is build 48 (or lower) the infra needs to be build 48 (or lower) as well, if the Jetty server flow is build 50 (or higher) the infra needs to be 50 (or higher) as well.

--> Impact: review the runtimes that have flows with a Jetty component and ensure that matching buildnumbers are inside these runtimes for all flows.

###3.2 Upgrade
Use the designed options in eMagiz to upgrade the flows to the new buildnumber. See the relevant microlearnings for that.

###3.3 Functional changes
Before an environment is updates to the flows with the latest releases, it is advices to first check which flows have functional changes. These flows need to be tested and put into production first so that you can isolate issues in case they occur. Once these flows are tested and live, only then move the flows witht the new buildnumbers from test to production.

###3.4 Approach
It is usually best to update the test and acceptance environment first and leave that running for a certain grace period. So that in case potential issues can be fixed still.


##### Practice

## 4. Assignment

Take a look at the release notes in the eMagiz Portal to ensure you know where to look.

## 5. Key takeaways

- Keep as close to the latest buildnumber as possible for the entire environment
- The best option is to have the entire environment run on the same buildnumber 
- A mix of buildnumbers in a runtime is not a good plan - conflicting behaviors may occur.
- Read the release notes for builnumbers carefully to assess the impact - in case the impact is minimal proceed with the upgrade
- Make the buildnumber upgrades planable so the release schedule takes these actions into account.

##### Solution

## 6. Suggested Additional Readings

If you are interested in this topic and want more information on it, please read the release notes provided by eMagiz

## 7. Silent demonstration video

There is no video available as this is more a theoretical microlearning.

</div>
</main>
</div>
</div>