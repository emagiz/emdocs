<div class="ez-academy">
    <div class="ez-academy__body">
        <main class="micro-learning">
        <ul class="doc-nav">
            <li class="doc-nav__item"><a href="../../docs/microlearning/advanced-active-monitoring-index" class="doc-nav__link">Home</a></li>
            <li class="doc-nav__item"><a href="#intro" class="doc-nav__link">Intro</a></li>
            <li class="doc-nav__item"><a href="#theory" class="doc-nav__link">Theory</a></li>
            <li class="doc-nav__item"><a href="#practice" class="doc-nav__link">Practice</a></li>
            <li class="doc-nav__item"><a href="#solution" class="doc-nav__link">Solution</a></li>
        </ul>

<div class="doc">

##### Intro

# Preventive action based on error message
 
In an earlier [microlearning](intermediate-active-monitoring-determining-cause-of-error-message.md), we discussed determining the cause of a single error message. In that microlearning, we focused on the RCA of one single error message. However, there might be situations in which there is not one message that goes wrong but many error messages. Only solving them on an individual basis might not be enough. In those cases, you want to think about specific preventive actions that could be taken to prevent those mistakes from happening again. One example is that a complete integration has undergone changes, but only part of the solution is deployed in a specific environment. This will undoubtedly lead to loads of errors in which one common, preventable mistake is the cause.

Should you have any questions, please get in touch with academy@emagiz.com.

- Last update: November 15th, 2021
- Required reading time: 5 minutes

## 1. Prerequisites
- Advanced knowledge of the eMagiz platform
- Errors in the log that can be analyzed

## 2. Key concepts
This microlearning centers around preventive action based on error message
By preventative measure, we mean: Figuring out what was responsible for generating all those errors and determining what could solve that problem.

- Search for a common denominator that explains (all) errors
- Determine whether the fix is platform or process-related
- Implement the fix to improve your eMagiz solution further

##### Theory
  
## 3. Preventive action based on error message

In an earlier [microlearning](intermediate-active-monitoring-determining-cause-of-error-message.md), we discussed determining the cause of a single error message. In that microlearning, we focused on the RCA of one single error message. However, there might be situations in which there is not one message that goes wrong but many error messages. Only solving them on an individual basis might not be enough. In those cases, you want to think about specific preventive actions that could be taken to prevent those mistakes from happening again. One example is that a complete integration has undergone changes, but only part of the solution is deployed in a specific environment. This will undoubtedly lead to loads of errors in which one common, preventable mistake is the cause.

- Search for a common denominator that explains (all) errors
- Determine whether the fix is platform or process-related
- Implement the fix to improve your eMagiz solution further

In the example described above, the fault most likely lies within the process itself. Several individuals worked on the integration within the team but failed to communicate correctly, resulting in half a solution in that particular environment. As a result, there was a mismatch between both parts of the integration in eMagiz. This led to errors in the platform. If you would perform a retest based on one error message, you would probably conclude that in Create, the solution works as expected when running a flow test.

That realization should lead you to conclude that Create is not the same as what is currently running in that environment. That, in turn, should be a trigger to start asking questions, to yourself and others, of what went wrong leading up to this mismatch.

In other cases, the deployment resulted in deploying the correct version of everything within the integration. However, as a result, there are still errors that are being thrown on the environment. Once again, the event that leads to the problems is a deployment. However, the cause of the errors is most likely quite different. By first checking the Manage Dashboard, you can quickly see whether all (or at least most) errors are raised within a single flow (or comparable flows). You can already learn a lot about the underlying cause of the problem, especially if you start to zoom in to verify if the same component within that flow raises all the errors. Having that information is critical in determining whether multiple mistakes have the same cause or not.

The underlying cause could be that two individuals have tested their solution to a tee, determining that their solution works. However, they failed to test whether the changed process A still works against the changed process B. As a result, one of the processes needs a change in Create to align it with the other process to make the complete integration work again. After executing that change, a second deployment is necessary to test if this resolves the previously raised errors.

As you can see, due to the dependencies between several flows and even parts of flows that ultimately ensure that data is sent from A to B, finding the root cause of your error messages can be challenging. However, doing nothing about these errors is no option as that would hurt the quality of the solution you deliver.

Hopefully, this microlearning has made the thought process you can follow to analyze large volumes of error messages somewhat more clear to you.

##### Practice

## 4. Assignment

Search for problems within your model and see if you can find out a common problem that causes all those problems. This assignment can be completed with the help of the (Academy) project that you have created/used in the previous assignment.

## 5. Key takeaways

- Search for a common denominator that explains (all) errors
- Determine whether the fix is platform or process-related
- Implement the fix to improve your eMagiz solution further

##### Solution

## 6. Suggested Additional Readings

No suggested additional readings for this microlearning.

## 7. Silent demonstration video

As this is a more theoretical microlearning, we have no video for this.

</div>
</main>
</div>
</div>