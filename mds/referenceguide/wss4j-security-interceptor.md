---
id: wss4j-security-interceptor
title: WSS4J security interceptor
sidebar_label: WSS4J security interceptor
---

A WS-Security server interceptor based on Apache's WSS4J.

Use this component in combination with a <i>web service inbound gateway</i> to add a <code>&lt;wsse:Security&gt;</code> SOAP header to that gateway's responses, and/or to validate the WS-Security information in the requests.

This interceptor supports messages created by the <code>AxiomSoapMessageFactory</code> and the <code>SaajSoapMessageFactory</code>.


Settings relevant when using a <code>UsernameToken</code> securement action.


Settings relevant when using a <code>Encrypt</code> securement action.


Settings relevant when using a <code>Signature</code> securement action.

### Encryption crypto
Reference to a <code>Crypto</code> implementation that provides the certificates for encrypting SOAP responses.

### Signature crypto
Reference to a <code>Crypto</code> implementation that provides the keys for signing SOAP responses.

### _id
Reference to a <code>Crypto</code> implementation that provides the keys for decrypting SOAP requests.

### _id
Reference to a <code>Crypto</code> implementation that provides the certificates for signature verification of SOAP requests.

### Encryption crypto
Reference to a <code>Crypto</code> implementation that provides the certificates for encrypting SOAP responses.

### Signature crypto
Reference to a <code>Crypto</code> implementation that provides the keys for signing SOAP responses.

### _id
Reference to a <code>Crypto</code> implementation that provides the keys for decrypting SOAP requests.

### _id
Reference to a <code>Crypto</code> implementation that provides the certificates for signature verification of SOAP requests.

---
id: wss4j-security-interceptor
title: WSS4J security interceptor
sidebar_label: WSS4J security interceptor
---

A WS-Security client interceptor based on Apache's WSS4J.

Use this component in combination with a <i>web service outbound gateway</i> to add a <code>&lt;wsse:Security&gt;</code> SOAP header to that gateway's requests, and/or to validate the WS-Security information in the responses.

This interceptor supports messages created by the <code>AxiomSoapMessageFactory</code> and the <code>SaajSoapMessageFactory</code>.


Settings relevant when using a <code>UsernameToken</code> securement action.


Settings relevant when using a <code>Encrypt</code> securement action.


Settings relevant when using a <code>Signature</code> securement action.

### Encryption crypto
Reference to a <code>Crypto</code> implementation that provides the certificates for encrypting SOAP requests.

### Signature crypto
Reference to a <code>Crypto</code> implementation that provides the keys for signing SOAP requests.

### _id
Reference to a <code>Crypto</code> implementation that provides the keys for decrypting SOAP responses.

### _id
Reference to a <code>Crypto</code> implementation that provides the certificates for signature verification of SOAP responses.

### Encryption crypto
Reference to a <code>Crypto</code> implementation that provides the certificates for encrypting SOAP requests.

### Signature crypto
Reference to a <code>Crypto</code> implementation that provides the keys for signing SOAP requests.

### _id
Reference to a <code>Crypto</code> implementation that provides the keys for decrypting SOAP responses.

### _id
Reference to a <code>Crypto</code> implementation that provides the certificates for signature verification of SOAP responses.

