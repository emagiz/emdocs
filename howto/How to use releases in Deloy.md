# How to use releases in Deploy?
After finishing the Create phase, it is time to deploy the bus. The main idea behind the new functionality in eMagiz is that an user does not have to build packages himself anymore, but all flows can be released and installed at once.

## How to create a release?
After finishing all flows in create, go to Deploy --> Releases. Initially, there is no release yet, so by clicking the ‘New release’ button, an initial release is created. This initial release is added to the list on the right menu of your screen. Currently there are two releases visible: Create Phase and Initial release. 

The Create Phase has two options; refresh and details.
- ![alt text](https://github.com/emagiz/emdocs/blob/master/howto/Refresh.JPG) **Refresh:** when you are still working on your bus and flows or integrations are added in Create, these changes have to be released as well. In this case, you can use the ‘Refresh’ button. This button updates the Create Phase release. When clicking on the 'New Release' button, a new release from Create is made.  
- ![alt text](https://github.com/emagiz/emdocs/blob/master/howto/Details.JPG) **Details:**  in this pop-up the details of the release are shown. Open this pop-up to rename or delete the release. To delete a release, there is a button on the bottom of the pop-up 'Delete'.

## How to install a release?
All the other releases have the same funcionalities, which are edit, details, install and update to next environment.
- **Compare:** the release which is currently selected, is marked green in the menu on the right. It is possible to compare a running release with the latest version of a release by selecting both the releases. The differences between the releases will be shown in colors:\
  Green: These components are added \
  Grey: Deleted flows compared to the installed release will turn grey. \
When hovering over the flows, you see which version number of the flow is released.

- ![alt text](https://github.com/emagiz/emdocs/blob/master/howto/Edit.JPG) **Edit:** when clicking on the edit button, flows can be deleted or added. To add or delete flows, you have to hover over a flow. Deleted flows will turn grey, the added flows will turn green.

- ![alt text](https://github.com/emagiz/emdocs/blob/master/howto/Install.JPG) **Install:** to install your release, you first need to have a running bus. So download your runtimes from the container page and start them. Then click the install button and your release is installed. The release will be locked (there is a lock in front of the release), which means that this release is not editable anymore. If you want to edit this release, you have to select this release and click on the button 'New Release'. A duplicate of the release is made and now you can edit the duplicate of the release.

- **Installing a Mendix System:** when you have a Mendix System in your bus, the flows inside this system will not be automatically installed. To install these flows, you have to go to packages and select the accompanying packages and click on install.
- **Update to next environment:** when clicking on this button, the release will be updated to the next environment. As the pop-up shows, the release is not editable anymore. When switching to that environment, you will see that the release is on that environment.

- **Filters:** when the bus is large or you just want to see what flows have been edited, you can filter on tags. These tags function the same as the tags in the phases: Capture, Design and Create.

