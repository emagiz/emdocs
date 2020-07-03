
How to EDIFACT
Issue date: 03-Jul-2020
 
This document describes best practices on EDIFACT. It discusses what EDIFACT is, how to transform an EDIFACT file to XML and from XML to EDIFACT.

## Introduction – What is EDIFACT?
EDIFACT stands for Electronic Data Interchange For Administration, Commerce and Transport. The standard is developed by the United Nations to create an international standard for exchanging messages electronically between organizations. It is often named EDI, but EDI stands for Electronic Data Interchange which is the way of work how organizations can exchange data while EDIFACT defines the structure how these messages are exchanged. 
In EDIFACT, you have multiple standard. UN/EDIFACT is the most comprehensive and worldwide most common standard. This document will be about UN/EDIFACT messages standard.
EDIFACT contains a set of standard message types which define what kind of information is exchanged and in what format. Each message type supports a specific process, for example an order or an invoice.  
Examples of message types which are common in the B2B communication are:
-	ORDERS – It describes an order
-	ORDRSP – It describes an order response, this is the confirmation that the orders is accepted or declined
-	INVOIC – It describes an invoice
-	APERAK – It describes an acknowledgement of receipt
EDIFACT has a hierarchical structure consisting of multiple components. The topmost unit of an EDIFACT message is the Interchange (UNB), which can be thought of as an envelope. The interchange defines the message recipient, the message sender, the message number, the message date, etc. An interchange can in turn contain several individual Groups (UNG) representing message groups. Alternatively, an interchange can also contain individual messages (concrete messages).A message itself is enclosed by a header (UNH) and a trailer segment (UNT). 
A message group is surrounded by an UNG and UNE segment. Within a message, there are several segments and segment groups, which represent individual related message parts (for example, information about the biller, a specific invoice line, etc.). 
A segment group is initiated by a so-called trigger element. Segments consist of data elements and composite data elements. The smallest unit of an EDIFACT file are simple data elements.
A group or segment can be mandatory (M) or conditional (C) and can be specified to repeat. For example :
- C99 indicates between 0 and 99 repetitions of a segment or group
- M99 signifies between 1 and 99 repetitions of a segment or group
A group, like a message, is a sequence of segments or groups. The first segment or group beneath a group must be mandatory, and the group should be made conditional if the logic of the situation demands it.


 |_Service String Advice              UNA  Optional
 |____Interchange Header              UNB  Mandatory
 :    |___Functional Group Header     UNG  Conditional
 :    :   |___Message Header          UNH  Mandatory
 :    :   :   |__ User Data Segments          As required
 :    :   |__ Message Trailer         UNT  Mandatory
 :    |__ Functional Group Trailer    UNE  Conditional
 |___ Interchange Trailer             UNZ  Mandatory

An example of how an EDIFACT file (partly) looks like is:
UNA:+.? ' UNB+UNOC:3+SENDERCODE+RECEIVERCODE+270217:1438+ID:f57cbf19-fc' UNH+1+ORDERS:D:96A:UN' BGM+220+AB123456+9' DTM+137:20170115212655:204' RFF+ON:'
More information about the different message types and their structure can be found here:
https://www.truugo.com/edifact/
An example of an EDIFACT file and a EDIFACT file transformed into XML can be found here:

- [Example EDITFACT](ORDERS_edifact_example1.edifact)
- [Example XML(ORDERS-edifact-xml_example1.xml)

 
## EDIFACT to XML
In eMagiz, you are able to both transform a XML to an EDIFACT file as from EDIFACT to XML. This chapter discusses the transformation from EDIFACT to XML.
In order to transform an EDIFACT file into a XML, you need in eMagiz only one component, the UN/EDIFACT to XML Transformer. This transformation component transforms the following piece of EDIFACT message:
UNA:+.? ' 'UNB+UNOC:3+SENDERCODE+RECEIVERCODE+270217:1438+ID:f57cbf19-fc' 'UNH+1+ORDERS:D:96A:UN'
Into
<out:unEdifact xmlns:out="urn:org.milyn.edi.unedifact.v41">
	<out:UNB>
		<out:syntaxIdentifier>
			<out:id>UNOC</out:id>
			<out:versionNum>3</out:versionNum>
		</out:syntaxIdentifier>
		<out:sender>
			<out:id>SENDERCODE</out:id>
		</out:sender>
		<out:recipient>
			<out:id>RECEIVERCODE</out:id>
		</out:recipient>
		<out:dateTime>
			<out:date>270217</out:date>
			<out:time>1438</out:time>
		</out:dateTime>
		<out:controlRef>ID:f57cbf19-fc</out:controlRef>
	</out:UNB>
	<out:interchangeMessage>
		<out:UNH>
			<out:messageRefNum>1</out:messageRefNum>
			<out:messageIdentifier>
				<out:id>ORDERS</out:id>
				<out:versionNum>D</out:versionNum>
				<out:releaseNum>96A</out:releaseNum>
				<out:controllingAgencyCode>UN</out:controllingAgencyCode>
			</out:messageIdentifier>
		</out:UNH>

Based on this XML file, you can transform the messages via a XSLT. The transformation component has several features. The Basic settings view is:
<p align="center"><img src="../../img/howto/edifact-how2-image1"></p>

 The Id, Input channel and Output channel are known and will not be discussed. 
-	UN/EDIFACT version: This is the version of the incoming EDIFACT message. This determines what transformation eMagiz will use and how the EDIFACT file should be interpreted. You can find your EDIFACT version in the UNH segment:
UNH+1+ORDERS:D:96A:UN'. In this case the version is D:96.
-	Delete files: Specify whether the source file should be deleted. Used if you picked up the file from a local folder of SFTP. Best practice is to delete your original files, as you do not need them anymore in most cases.

The advanced settings that are available. Mostly you don’t need to change the settings here. Use the target selector f you need to split a EDIFACT file into multiple XML files. You can enter in this field the entity where you would like to split the files.
-	Target selector: Expression for splitting the EDI message into smaller fragments. Default is the entire EDI message.
-	Selector namespace: If required, you can add here the namespace for the expression above.
-	Requires reply: Set to true if you expect that the result of this transformer always leads to at least one output message.
-	Apply sequence: Set to true if you would like to have a sequence number to your output messages.
-	Send timeout: Set if the transformation cannot take longer than a certain amount of time.
-	Validate: Set to true if the incoming message validates against the EDIFACT content fields as data type, min and max length. Structure of the document is always validated during this transformation.
-	Ignore new lines: Set to true if you would ignore unexpected new lines.
-	Ignore empty nodes: Set to true if you would ignore unexpected empty nodes.

<p align="center"><img src="../../img/howto/edifact-how2-image2"></p>


## XML to EDIFACT
In order to transform a XML to an EDIFACT file, you can use the XML to UN/EDIFACT transformer component. Important is to structure your XML correctly in EDI-XML. Since the EDIFACT message can grow rapidly due to its many features, its XML structure can be complex to build. 

<p align="center"><img src="../../img/howto/edifact-how2-image3"></p>

-	UN/EDIFACT version: This is the version of the outgoing EDIFACT message. This determines what transformation eMagiz will use and how the XML file should be interpret. Your EDIFACT version should meet with what is stated in the UNH component. Voorbeeld?
In comparison to the advanced settings for incoming EDIFACT messages, the advanced settings for the outgoing EDIFACT messages are more relevant to use. 
<p align="center"><img src="../../img/howto/edifact-how2-image4"></p>

-	Validate: Set this value to Yes if you would like to validate the structure of the EDIFACT file. This means that not the values are checked but data validation on data type, minimal length or maximal length.
-	Segment line break: If you would like to add new lines, you can set delimiter character. This could be for example the ‘ character as shown in the example earlier in this document.
-	Charset: Character set which is used to decode the incoming XML message into text. Default is UTF-8.
-	Send timeout: This setting is not widely used. Use it if you want to have a timeout when the component takes too much time to transform the message into an EDIFACT file.
