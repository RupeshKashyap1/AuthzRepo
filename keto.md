## Keto
Ory Keto Permission Server is an open source implementation of "Zanzibar: Google's Consistent, Global Authorization System".

> Zanzibar provides a uniform data model and configuration language for expressing a wide range of access control policies from hundreds of client services at Google, including Calendar, Cloud, Drive, Maps, Photos, and YouTube. Zanzibar scales to trillions of access control lists and millions of authorization requests per second to support services used by billions of people

* Keto serves the purpose of policy decision point in the Authn & Authz system.  
+ Ory Keto provides basic HTTP and gRPC APIS to check and manage permissions.  
* A detailed Guide about the Ory Keto is available here: https://www.ory.sh/docs/keto 

### Why Keto?
+ **Lightweight** : Ory keto is light weight that can be used to develop an Authz as service.
* **Fast** : can handle a million requests per second
+ **Reliable**: Can handle Trillions of ACLs. Zanzibar is used in Google cloud, calendar etc systems. 


### Basic Concepts

* Ory keto underlying datatype is called a "Relation Tuple". 
+ A relationship tuple has following four entities:  
     1. Namespace
     2. Object
     3. Relation
     4. Subject
    
 
