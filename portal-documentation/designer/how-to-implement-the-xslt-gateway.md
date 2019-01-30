# How to implement the XSLT gateway

https://my.emagiz.com/link/documentation/117

## 1.   Introduction
In a transformation we normally map from one source attribute to another destination attribute, in short: it is a closed environment. However, there are cases that a transformation needs external information to realize the mappings. One of the examples is the code mapping in which we need to look up CDM codes by system codes which are registered in the code mapping module of eMagiz. But, what about the more complicated situation, for example, mapping a username to a security key which is stored in 3rd party system? The new component – XSLT extension gateway – with the support of a new mapping operation – external transformation – will be the solution.

 

_XSLT extension gateway is the component that allows an XLST transformer to perform another XSLT transformation and then use the result in its mapping._

 

## 2.   How does it work 

To make use of the XSLT extension gateway we need to configure two parameters in in the first transformer (number 2).The first one points to the gateway which is capable of connecting to the second transformer (number 5). We use an _XSLT parameter_ in this situation. The second is to specify which information we need to send to Transformer 2. The new external transformation operation of mapping tool allows us to do that.

 

### 2.1. Configure components in The Flow Designer.
You need (at least) the following components:

 

  1. _Standard header enricher_ to add a custom header with a reference to the XSLT extension gateway. We have to configure a header with the name “gateway” and refer to the extension gateway (testgateway.receive.extensiongateway in this case).  
  
  2. _XSLT transformer_, map this header to an XSLT parameter   

  3. Another _Standard header enricher_  to remove the header(s) referring to the XSLT extension gateway from the message.  

  4. The _XSLT extension gateway_ which is referred by the header of the first XSLT transformer.  

  5. The second _XSLT transformer_ performs the external transformation and its results will be used in the first transformer.  

### 2.2. Configure the external transformation in the mapping tool.  

Suppose that we want to call the XSLT extension gateway to look up the country of a city, in the mapping tool, we choose external transformation. We will need to use a gateway call which will be configured with a parameter and an element/attribute.   

These parameters are connected to what we configured in components in the Flow Designer:

  - _$gateway_ is a parameter of _gateway_ datatype, named after the _XSLT parameter_ we configured in the first transformer (number 2)

  - _City_ is the information we want to send to the second transformer

  - _Output XSD_ is the definition of the result which will be send back by the second transformer

Now we can map the result of the gateway call to the Country attribute in the mapping tool. This can be done easily, since we have the definition of the result. 

## 3. Conclusion
As this is the first version there are still a lot of optimizations to be made to the process of creating an extension gateway. For example, in the next release we will be able to extract a new XSD from an existing one, which can then be used as input for a second transformation.
