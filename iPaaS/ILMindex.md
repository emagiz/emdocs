
# Integration Lifecycle Management (ILM)

ILM is an approach to data and storage management that recognizes that the value of information changes over time and that it must be managed accordingly. ILM seeks to classify data according to its business value and establish policies to migrate and store data on the appropriate storage tier and, ultimately, remove it altogether. ILM has evolved to include upfront initiatives like master data management and compliance. It consists of five phases:  

  1) **CAPTURE** requirements
      * Define integrations
      * Obtain test data
  2) **DESIGN** solution
     * Architecture
     * Message definitions
  3) **CREATE** flows
  4) **DEPLOY** flow to the environment
  5) **MANAGE** and monitor flows  
  
<p align="center" > <img width=""300" height="300" src="eMagiz-diagram.png"> </p>
  
  ## 1. Capture
  
   * **Why** capture requirements?  
   
     * Determine scope
     * Provides guidelines for designing flows first time right
     * Reduces chance of overlooking key decisions
     * Centralized documentation of requirements
     * Support developer during the design phase
   
   * **HowTo** capture requirements?  
      * Determine systems that are integrated  
      * Determine information flows/message types  
      * Determine alerts/events you want to be notified of  
      * Connect the systems with information flows  
    
   * **Result**
      <p align="center" > <img width="959" height="114" src="capture-result.png"> </p>  
  
  ## 2. Design
  
   * Design phase objective  
      * Design the solution based on the requirements of the capture phase  
      * Design tasks:  
       -> Systems connection settings  
       -> CDM  
       -> Message definitions (x 3: CDM, system 1, system 2)  
       -> Message mappings  
       -> Architecture  
      
   * Results  
     * Message bus:  
      <p align="center" > <img width=""960" height="262" src="design-result.png"> </p>  
     
     * CDM:  
      <p align="center" > <img width=""960" height="262" src="CDM-result.png"> </p>  
     
     * CDM message definition:  
      <p align="center" > <img width=""960" height="262" src="CDM-msg-def-result.png"> </p>  
     
     * System message:  
      <p align="center" > <img width=""960" height="262" src="sys-msg-result.png"> </p>  
     
     * Message mapping:  
      <p align="center" > <img width=""960" height="262" src="msg-format-result.png"> </p>  
     
     * Architecture:  
      <p align="center" > <img width=""960" height="262" src="arch-result.png"> </p>  
     
   ## 3. Create  
    
   * Build the solution that has been designed in the prior phase
   * Transfer the integrations from Design to Create
   * Fill in missing details:  
     * Flows
     * Definitions
     * Transformations

<p align="center"> <b> Graphical representation of an integration </b></p>

<p align="center"> <img width="810" height="300" src="integration-model.png"> </p>  

  * **Entry connector**  
  
    * First entry point for messages on the bus.
    * Deals with transport from the application to the message bus.  
    * Separate interface from transformation logic.  
    
    <img width="810" height="300" src="entry-connector.png">  

  * **Onramp process**  
  
    * Validates source application data
    * Transforms source application data to common data model  
    * Adds metadata for routing purposes
    
    <img width="810" height="300" src="onramp-process.png">  
 
  * **Routing process**  
  
    * Routes messages to the designated offramp based on: metadata, message content or pre-defined routing rules.  
    
    <img width="810" height="300" src="routing-process.png">  

  * **Offramp process**  
  
    * Validates common data model data
    * Transforms common data model data to destination format
    
    <img width="810" height="300" src="offramp-process.png">  

  * **Exit connector**  
  
    * Exit point for messages on the bus.
    * Deals with transport from the message bus to the target application e.g. call a webservice, drop a file, post a http request.  
    * Separate interface from transformation logic.  
    
    <img width="810" height="300" src="exit-connector.png">


### eMagiz diagram notation
    
  - inbound channel adapter  
    <img width="79" height="79" src="ica.png">
  - outbound channel adapter  
    <img width="79" height="79" src="oca.png">
  - channel  
    <img width="115" height="69" src="c.png">
  
  - **Channels**
    - Decouples Producers from Consumers
    - Provide extension points for interceptors
    - May follow Point-to-Point or Pub-Sub
    - Messages may be queued / buffered
    - Synchronous / Asynchronous
  
   <img width="726" height="82" src="Channels.png">


 
  - **Endpoints**
    - Producers send Messages to Message Channels
    - Consumers receive Messages from Message Channels
    - Endpoints can be both Consumer and Producer
    - Message driven or polling, depending on the input Channel
  
   <img width="800" height="100" src="Endpoints.png">


 
  - **Channel adapters**
    - Connects a channel to some other system or transport
    - Inbound or outbound
    - Unidirectional
    - Implementations including: JMS, File, FTP(S), HTTP, JDBC, TCP, IMAP/Mail, XMPP.
  
   <img width="575" height="79" src="channel-adapaters.png">


 
  - **Filter**
    - Discard messages based on boolean evaluation
    - Implementations: XML validating filter, XPath filter, Standard filter.
  
   <img width="60" height="61" src="filter.png">


 
  - **Transformer**
    - Convert payload or modify headers
    - Implementations including: XSLT, XPath, Flat file to XML, ISO8583 bytes to XML, JSON to XML, File to String and many more.
  
   <img width="80" height="69" src="transformer.png">


 
  - **Router**
    - Determine next channel based on content of the Message
    - Implementations: XPath router, Header value router, Payload type router,  Recipient list router.
  
   <img width="83" height="83" src="router.png">


 
  - **Support object**
    - Provide additional functionality used by other messaging components
    - Reusable
    - Not connected to message channels
    - Implementations including: FTP connection settings, Property placeholder, Jetty server and many more

  
   <img width="79" height="69" src="support-object.png">


 
  - **Gateway****
    - Same as Channel Adapter, but bidirectional
    - Implementations including: Web services, HTTP, JMS, TCP, JDBC.

  
   <img width="498" height="136" src="gateway.png">


 
  - **Splitter**
    - Generate multiple messages from one
    - Implementations: XPath splitter, Standard splitter.

  
   <img width="79" height="65" src="splitter.png">  




  - **eMagiz entry message flow example**  
  
  <img width="504" height="185" src="entry-example.png">  
  
  

  - **eMagiz onramp process flow example**  
  
  <img width="659" height="218" src="onramp-example.png">  
  
  
  
  - **eMagiz routing process flow example**  
  
  <img width="697" height="238" src="routing-example.png">  
  
  
  
  - **eMagiz offramp process flow example**  
  
  <img width="687" height="232" src="offramp-example.png">  
  
  
  
  - **eMagiz exit message flow example**  
  
  <img width="557" height="223" src="exit-example.png">  
  
  

 

   ## 4. Deploy 


