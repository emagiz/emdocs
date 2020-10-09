# How to use releases in Deploy?
After finishing integrations in the Create phase, it is time to deploy the integrations. The main idea behind this feature in eMagiz is to release integrations to the available environments and support the release cyle of your integration landscape. 

## How to create a release?
After finishing or updating flows in create, go to Deploy --> Releases. 
When you arrive here for the first time, there is no release yet, so by clicking the ‘New release’ button, an initial release is created. 
This initial release is added to the list on the right menu of your screen. Currently there are two releases visible: Create Phase and Initial release.
For all releases that you want to create after this (after you have updated or added another flow) you should base the release on the release that is currently active. 

## How to configure a release?

With the help of the following options you can configure each release to best suit your used case.
 
- **Details:**  in this pop-up the details of the release are shown. In here you can see which flows are part of your release by navigating to the flows tab.
- **Check properties:**  With this functionality you can validate whether or not flows that are in your release are missing properties which are required for the flow to run.
- **Batch Update / Update flows to latest version:** With this functionality you can upgrade all flows within your release to the latest version. Especially usefull when upgrading to a higher build number.
- **Compare:** the release which is currently selected, is marked green in the menu on the right. It is possible to compare a running release with another release by selecting both the releases. If you want to compare an older version with the Create Phase, do not forget to press the 'Refresh' button. The differences between the releases will be shown in colors:\
  <i>Green</i>: These components are added. \
  <i>Red</i>: Deleted flows compared to the installed release will turn red. \
  <i>Blue</i>: Versions of the flow have changed. \
When hovering over the flows, you see which version number of the flow is released.
- **Edit:** when clicking on the edit button, flows can be deleted, added or adapted. To do this, you have to hover over a flow or integration and click on the flow you want to delete or add. By right clicking on a flow, the available version numbers are shown in a dropdown. The version of the flow can be adapted by selecting the version number you want. For a special case, namely the flows of an infra, can only be changed in this dropdown menu. Deleted flows will turn red, the added flows will turn green.
- **Filters:** when the bus is large or you just want to see what flows have been edited, you can filter on tags. These tags function the same as the tags in the phases: Capture, Design and Create.


## Deploy a release

As a user you have the option to execute the deployment plan when you want to Deploy a certain Release to a certain environment. This can easily be done by pressing the Deploy icon next to your release name.
Clicking on this icon will lead you to the Deploy Widget (via a popup) which will guide you through the steps as you have configured them in your Deployment Plan

<p align="center"><img src="../../img/howto/implementation-deploymentplan-3.png"></p>

Below you will see a visual representation of how the Deploy page looks like. In here you can press the play button or execute the deployment plan manually per step

<p align="center"><img src="../../img/howto/implementation-deploymentplan-4.png"></p>
