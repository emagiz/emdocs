## User Guide eMagiz Store

Below the user guide for the eMagiz Store. Within this guide we discuss the contents you can find in the store, guidelines of the store, how you can import things into the developer / company store. How you can export from the company and/or public store and how the process works of getting something of yours accepted into the public store. Should you have any questions, please contact productmanagement@emagiz.com.
Last update: November 16th 2020

### Store contents

The store contains the following items:

- Flows
	-	Connectors (entry and exit flows)
	-	Processors (onramp and offramp flows)	
- Resources
	-	Definitions
	-	CDM
	-	Message Models
	-	Mappings
	-	Other (custom XSLT's for example)
	
### Store Guidelines

#### General Guidelines

These guidelines are applicable to all the Store content you want to submit.

- Provide a short name containing key-words, a description of the main features of your content, and an extended documentation.
- Provide a contact.
- Describe typical usage scenario(s).
- Describe the features / limitations of your content.
- Describe dependencies (e.g. for connectors, the external system version).
- Describe the necessary steps to configure the content, if any (e.g. for flows, renaming of properties or other elements that is not automated).
- Describe the market and external system that are applicable for your import
- Possibly provide a logo for your content; this can be done by editing it from the Developer page.

#### Guidelines for flows
If you want to submit a flow, please also consider the following guidelines.

- Follow the naming conventions provided in the documentation https://my.emagiz.com/link/documentation/8.
- Prefer the use of properties over hardcode values.
- Logging should be added to every flow, using a logging channel adapter and global wire tap.
- Backup of files in entry and exit flows should be available.
- Maintain the flow layout as clean as possible: all support objects on the right side and no crossing lines.
- Be sure that your flow works correctly.
- Be sure that all, and only, the resources used by the flow are attached to the flow and to the components.
- If you have manually added JMS queues in your flow, be sure to add them in the ‘Extra JMS queue configurations’ tab of the ‘Edit Configuration Template’ page, with the correct name.
- Add the runtime version in the documentation.
- Add one or more screenshots of your flow as it appears in the flow designer.

#### Restrictions
If you want to submit something to the flow the following restrictions might apply.

- You cannot export a all entry to the store
- You cannot export a dummy entry to the store
- You cannot export a Mendix entry/exit to the store
- You cannot export a new version of an existing store component if you are not the original author of the store component. This to prevent 'stealing' the work of someone else.

### Import to the store

#### Resources

#### Flows

### Export from the store

#### Resources

#### Flows

### Making a store component public