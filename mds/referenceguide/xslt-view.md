---
id: xslt-view
title: XSLT view
sidebar_label: XSLT view
---
#### View that renderes a response as the result of an XSLT transformation.
<a href="http://docs.spring.io/spring/docs/3.1.x/spring-framework-reference/html/" target="_blank">External documentation</a>

XSLT-driven View that allows for response context to be rendered as the result of an XSLT transformation.

The XSLT Source object is supplied as a parameter in the model and then detected during response rendering. Users can either specify a specific entry in the model via the sourceKey property or have Spring locate the Source object. This class also provides basic conversion of objects into Source implementations. See here for more details.

All model parameters are passed to the XSLT Transformer as parameters. In addition the user can configure output properties to be passed to the Transformer.

#### URL
Set the URL of the resource that this view wraps.

#### Cache templates
Turn on/off the caching of the XSLT Templates instance.

The default value is "true". Only set this to "false" in development, where caching does not seriously impact performance.

#### Indent
Set whether the XSLT transformer may add additional whitespace when outputting the result tree.

Default is true (on); set this to false (off) to not specify an "indent" key, leaving the choice up to the stylesheet.

#### Source key
Set the name of the model attribute that represents the XSLT Source. If not specified, the model map will be searched for a matching value type.

The following source types are supported out of the box: Source, Document, Node, Reader, InputStream and Resource.

#### Content type
Set the content type for this view. 

Default is "text/html;charset=ISO-8859-1"

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

