## Keto
Ory Keto Permission Server is an open source implementation of "Zanzibar: Google's Consistent, Global Authorization System".

> Zanzibar provides a uniform data model and configuration language for expressing a wide range of access control policies from hundreds of client services at Google, including Calendar, Cloud, Drive, Maps, Photos, and YouTube. Zanzibar scales to trillions of access control lists and millions of authorization requests per second to support services used by billions of people. https://research.google/pubs/pub48190/ 

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
   
     * **Namespace:**  To organise and configure relation tuples
     * **Object:** identifier for some kind of application object
     * **Relation:** type of relation (edit/view etc)
     * **Subject:** a polymorphic datatype to denote a user/set of users/actors etc.
    
 
####  Resource tuple:     <p align="center"> namespace:object#relation@subject</p>
   Subject can be subject_sets as well :  
   ##### <p align= "center"> (namespace:object#relation) </p>

### Example
   ```
   roles:moderator#member@jack  
   roles:normalUser#member@Lily 
   roles:normalUser#member@Sam 
   roles:normalUser#(users:moderator#member).   //composite role. anyone who is a moderator is also a normal user.
   
   resources: files/reports#view@(roles:normalUser@member) 
   resources: files/reports#edit@(roles#moderator#member) 
  
   ```
  
  Keto can now answer questions like:
   * Does Jack have edit permission on files/reports?   **CHECK API :**  true
   + Does Lily have edit permission on the files/reports? **CHECK API :** false
   * Who all have view/edit permissions on files/reports. **Expand API :** \< returns the traversed tree containing subjects and subject sets \> 


###### More Examples :  
   *  https://www.ory.sh/docs/keto/examples/olymp-file-sharing              
   * https://www.ory.sh/docs/keto/quickstart 
   * Ory permission language: https://github.com/ory/keto/blob/master/docs/ory_permission_language_spec.md 
   
###### To get started with Ory keto in Java 
   - init a soringboot maven project with springweb dependency
   - add Keto dependency:  
     ```       
           <dependency>  
                  <groupId>sh.ory.keto</groupId>  
                  <artifactId>keto-client</artifactId>  
                  <version>0.10.0-alpha.0</version>  
            </dependency>
      ```
* Read the docs for available APIs and how to use them:  https://github.com/ory/keto-client-java
   
