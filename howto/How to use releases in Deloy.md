# How to use releases in Deploy?
After finishing the Create phase, it is time to deploy the bus. The main idea behind the new functionality in eMagiz is that a user does not have to build packages himself anymore, but all flows can be released and installed at once.

## How to create a release?
After finishing all flows in create, go to Deploy --> Releases. Initially, there is no release created yet, so by clicking the ‘New release’ button, an initial release will be created. For all flows you can see that this initial release is added to the list in the right corner of your screen. Currently there are two releases visible: Create Phase and Initial release. 

The Create Phase has two buttons; refresh and details.
- **Refresh.**
When you are still working on your bus and flows are added in Create, these changes have to be released as well. In this case, you can use the ‘Refresh’ button. This button updates the current release, so all flows which are added in Create are also added in Release as well. 
- **Details.**
In this popup the details of the release are shown. Open this popup to rename or delete the release. To delete a release, there is a button on the bottom of the popup 'Delete'.

## How to install a release?
All the other releases have the same funcionalities, which are edit, details, install and update to next environment.
- **Compare.** The release which is currently selected, is marked green in the menu on the right. It is possible to compare a running release with the latest version of a release by selecting both the releases. The differences between the releases will be shown in colors.
Green: These components are added 
Grey: Deleted flows compared to the installed release will turn grey.
Blue: 
- **Edit.** When clicking on the edit button, flows can be deleted. These flows will turn grey.

- **Install.** To install your release, you first need to have a running bus. So download your runtimes from the container page and start them. Then click the install button and your release is installed. The release will be locked (there is a lock in front of the release), which means that this release is not editable anymore. If you want to edit this release, you have to select this release and click on the button 'New Release'. Now you can edit the release again.

- **Installing a Mendix System.** When you have a Mendix System in your bus, the flows inside this system will not be automatically installed. To install these flows, you have to go to packages and select the accompanying packages and click on install.
- **Update to next environment.** When clicking on this button, the release will be updated to the next environment. As the popup shows, the release is not editable anymore. When switching to that environment, you will see that the release is on that environment.

- **Filters.** When the bus is large or you just want to see what flows have been edited, you can filter on tags. These tags function the same as the tags in the phases: Capture, Design and Create.

