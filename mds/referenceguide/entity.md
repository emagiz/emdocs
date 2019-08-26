---
id: entity
title: Entity
sidebar_label: Entity
---
### 
Name of the entity. Must be unique amongst its siblings.

This will also be the (local) name of the corresponding XSD element.

### 
Whether this entity is optional (can be omitted) or is required (must always appear). The root entity of a message is always required.

On the corresponding XSD element, this will result in <code>minOccurs="0"</code> or <code>minOccurs="1"</code> respectively.

### 
Whether this represents a list of entities or a single entity. The root entity of a message is always a single entity.

On the corresponding XSD element, this will result in <code>maxOccurs="unbounded"</code> or <code>maxOccurs="1"</code> respectively.

### 
Name of the entity. Must be unique amongst its siblings.

This will also be the (local) name of the corresponding XSD element.

### 
Whether this entity is optional (can be omitted) or is required (must always appear). The root entity of a message is always required.

On the corresponding XSD element, this will result in <code>minOccurs="0"</code> or <code>minOccurs="1"</code> respectively.

### 
Whether this represents a list of entities or a single entity. The root entity of a message is always a single entity.

On the corresponding XSD element, this will result in <code>maxOccurs="unbounded"</code> or <code>maxOccurs="1"</code> respectively.

### 
By default entities will be represented in the XSD as a <code>xs:complexType</code> with a <code>xs:sequence</code> containing all child attributes and entities. Example of such an XML structure:
<i>&nbsp;&nbsp;&lt;Weight&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&lt;Unit&gt;kg&lt;/Unit&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&lt;Value&gt;100&lt;/Value&gt;
&nbsp;&nbsp;&lt;/Weight&gt;</i>

Sometimes an external system requires an entity to be represented in the XSD as a <code>xs:complexType</code> with a <code>xs:simpleContent</code> that extends a simple type. In these specific cases you should switch to using "simple content". The same XML example would then look like this:
<i>&nbsp;&nbsp;&lt;Weight unit="kg"&gt;100&lt;/Weight&gt;</i>

To achieve this for the above example, you'd have to enable <i>XSD simple content</i> for attribute <i>Value</i>. Visually this is indicated by showing the attribute name in parentheses. The following restrictions apply to entities with "simple content":
<ul><li><b>Exactly one</b> attribute may have <i>XSD simple content</i> enabled and must <b>not</b> have <i>XSD attribute</i> enabled</li><li>All other attributes of the same entity <b>must</b> have <i>XSD attribute</i> enabled</li><li>The entity is not allowed to contain any child entities</li></ul>

---
id: entity
title: Entity
sidebar_label: Entity
---
### 
Name of the entity. Must be unique amongst its siblings.

This will also be the (local) name of the corresponding XSD element.

### 
Whether this entity is optional (can be omitted) or is required (must always appear). The root entity of a message is always required.

On the corresponding XSD element, this will result in <code>minOccurs="0"</code> or <code>minOccurs="1"</code> respectively.

### 
Whether this represents a list of entities or a single entity. The root entity of a message is always a single entity.

On the corresponding XSD element, this will result in <code>maxOccurs="unbounded"</code> or <code>maxOccurs="1"</code> respectively.

### 
Name of the entity. Must be unique amongst its siblings.

This will also be the (local) name of the corresponding XSD element.

### 
Whether this entity is optional (can be omitted) or is required (must always appear). The root entity of a message is always required.

On the corresponding XSD element, this will result in <code>minOccurs="0"</code> or <code>minOccurs="1"</code> respectively.

### 
Whether this represents a list of entities or a single entity. The root entity of a message is always a single entity.

On the corresponding XSD element, this will result in <code>maxOccurs="unbounded"</code> or <code>maxOccurs="1"</code> respectively.

### 
By default entities will be represented in the XSD as a <code>xs:complexType</code> with a <code>xs:sequence</code> containing all child attributes and entities. Example of such an XML structure:
<i>&nbsp;&nbsp;&lt;Weight&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&lt;Unit&gt;kg&lt;/Unit&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&lt;Value&gt;100&lt;/Value&gt;
&nbsp;&nbsp;&lt;/Weight&gt;</i>

Sometimes an external system requires an entity to be represented in the XSD as a <code>xs:complexType</code> with a <code>xs:simpleContent</code> that extends a simple type. In these specific cases you should switch to using "simple content". The same XML example would then look like this:
<i>&nbsp;&nbsp;&lt;Weight unit="kg"&gt;100&lt;/Weight&gt;</i>

To achieve this for the above example, you'd have to enable <i>XSD simple content</i> for attribute <i>Value</i>. Visually this is indicated by showing the attribute name in parentheses. The following restrictions apply to entities with "simple content":
<ul><li><b>Exactly one</b> attribute may have <i>XSD simple content</i> enabled and must <b>not</b> have <i>XSD attribute</i> enabled</li><li>All other attributes of the same entity <b>must</b> have <i>XSD attribute</i> enabled</li><li>The entity is not allowed to contain any child entities</li></ul>

