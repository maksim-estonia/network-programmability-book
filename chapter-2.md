# Chapter 2: Data Model-Driven Management

YANG is an API contract language. This means you can use YANG to write a specification for what the interface between a client and server should be on a particular topic. A specification written in YANG is referred to as a YANG module, and a set of YANG modules are collectively often called a YANG model. A YANG model typically focusses on the data that a client manipulates and observes using standardized operations, with a few actions and notificiations sprinkled in. Note that, in the NETCONF and RESTCONF terms, the controlller is the client and the network elements are the server, as the controller initiates the configuration session. 

The Key to Automation? Data Models

YANG and the Operators Requirements

The Management Architecture

A controller typically configures network elements (routers and switches in the networking world) based on the network element YANG modules—typically network interfaces, routing, quality of service, and so on.

From a controller point of view, the northbound interface is the interface towards the orchestrator, whereas the southbound interface is the one toward the server. Operators can also automate the orchestrator northbound interface to create, modify, delete their services, based on the service delivery YANG modules. 

The YANG modules, which model a specific problem domain, are loaded, compiled, or coded into the server.

The sequence of events for the typical NETCONF client/server interaction occur as follows:

1. A client application opens a NETCONF session to the server.
2. The client and server exchange `<hello>` messages containing the list of capabilities supported by each side. This hello exchange includes the list of YANG 1.0 modules supported by the server. 
3. The client builds and sends an operation defined in the YANG module, encoded in XML, within NETCONF's `<rpc>` element.
4. The server receives and parses the `<rpc>` element.
5. The server verifies the contents of the request against the data model defined in the YANG module.
6. The server performs the requested operation, possibly changing the configuration datastore. 
7. The server builds the repsonse messagee, containing the response itself, any requested data, and any errors.
8. The server sends the response, encoded in XML, within NETCONF's `<rpc-reply>` element.
9. The client receives and parses the `<rpc-reply>` element.
10. The client inspects the response and processes it as needed.

NETCONF Operations:

- get-config
- edit-config
- copy-config
- delete-config
- lock
- unlock
- get
- close-session
- kill-session
- get-data
- edit-data

