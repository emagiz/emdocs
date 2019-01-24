
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
      <p align="center" > <img width=""959" height="114" src="capture-result.png"> </p>
