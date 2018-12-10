# How to use releases in Deploy?
After finishing integrations in the Create phase, it is time to deploy the integrations. The main idea behind this feature in eMagiz is to release integrations to the available environments and support the release cyle of your integration landscape. 

## How to create a release?
After finishing all flows in create, go to Deploy --> Releases. Initially, there is no release yet, so by clicking the ‘New release’ button, an initial release is created. This initial release is added to the list on the right menu of your screen. Currently there are two releases visible: Create Phase and Initial release. 

The Create Phase has two options; refresh and details.

1.1 ![alt text](https://github.com/emagiz/emdocs/blob/master/howto/Refresh.JPG) **Refresh:** <i>everytime</i> when something is changed in Create and you want to release or compare this, you have to click the button 'Refresh'. This button updates the Create Phase release. When clicking on the 'New Release' button, a new release from Create is made. 

1.2 ![alt text](https://github.com/emagiz/emdocs/blob/master/howto/Details.JPG) **Details:**  in this pop-up the details of the release are shown. Open this pop-up to rename or delete the release. To delete a release, there is a button on the bottom of the pop-up 'Delete'.

## How to install a release?
All the other releases have the same features, which are edit (2.2), show details (1.2), install (2.3), update to next environment(2.4), filter (2.5).

2.1 **Compare:** the release which is currently selected, is marked green in the menu on the right. It is possible to compare a running release with another release by selecting both the releases. If you want to compare an older version with the Create Phase, do not forget to press the 'Refresh' button. The differences between the releases will be shown in colors:\
  <i>Green</i>: These components are added. \
  <i>Red</i>: Deleted flows compared to the installed release will turn red. \
  <i>Blue</i>: Versions of the flow have changed. \
When hovering over the flows, you see which version number of the flow is released.

2.2 ![alt text](https://github.com/emagiz/emdocs/blob/master/howto/Edit.JPG) **Edit:** when clicking on the edit button, flows can be deleted, added or adapted. To do this, you have to hover over a flow or integration and click on the flow you want to delete or add. By right clicking on a flow, the available version numbers are shown in a dropdown. The version of the flow can be adapted by selecting the version number you want. For a special case, namely the flows of an infra, can only be changed in this dropdown menu. Deleted flows will turn red, the added flows will turn green.

2.3 ![alt text](https://github.com/emagiz/emdocs/blob/master/howto/Install.JPG) **Install:** to install your release, you first need to have a running bus. So, firstly set the release you want to install as 'active' ( can be done by going to the details of the release -> advanced actions -> set as active) and download your runtimes from the container page and start them. Then click the install button and your release is installed. The release will be locked (there is a lock in front of the release), which means that this release is not editable anymore. If you want to edit this release, you have to select this release and click on the button 'New Release'. A duplicate of the release is made and now you can edit the duplicate of the release.

2.3.1 **Installing a Mendix System:** when you have a Mendix System in your bus, the flows inside this system will not be automatically installed. To install these flows, you have to go to packages and select the accompanying packages and click on install.

2.4 ![alt text](https://github.com/emagiz/emdocs/blob/master/howto/PromoteToNextEnvironment.JPG) **Update to next environment:** when clicking on this button, the release will be updated to the next environment. As the pop-up shows, the release is not editable anymore. When switching to that environment, you will see that the release is on that environment.

2.5 **Filters:** when the bus is large or you just want to see what flows have been edited, you can filter on tags. These tags function the same as the tags in the phases: Capture, Design and Create.

![How to use releases in Deploy?](https://github.com/emagiz/emdocs/blob/master/howto/Infographic%20releases%20-%20comparing%20v2.png)

