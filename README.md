# Instructions for building the Datashot web application.

## Prerequsisites

First, configure the database, see the datashot_thick for instructions and the schema.

Install Glassfish 3.1.2.2+  (these are old instructions, works in Glassfish 4).  
[Configure jdbc resource, jdbc connection pool, jms connection factory, jms destination.]

## Component projects

Checkout the three projects that go into building the datashot EAR artifact. 

datashot_web
datashot_ejb
datashot_ee

In Eclipse: 
(1) Checkout each of the above into a separate project.

(2) Enable maven: Right click on each project in Package Explorer, select Maven/Enable Dependency Management from the popup menu.

(3) Add Glassfish runtime: From main menu Window/Preferences,
in preference dialog select Server/RuntimeEnvironment, click "Add",
in runtime environment dialog, select Glassfish 3.1, or click \
"Download additional server adapters", install Glassfish, 
then restart, return to Server/RuntimeEnvironment and add Glassfish 3.1
(specifying the path to a local glassfish install, 
e.g. /usr/local/glassfish_3122/glassfish/) then restart Eclipse, 

(4) Check Problems tab for any Errors.

## Building

Build with Maven: 

(1) datashot_ejb

    mvn clean install
    (builds a jar artifact and puts it in your local maven repository)
    
(2) datashot_war 

    mvn clean install
    (builds a war artifact and puts it in your local maven repository)

(3) datashot_ee

    mvn clean package
    (builds an ear artifact in datashot_ee/target/)
    
(4) Deploy resulting artifact 

Deploy datashot_ee/target/datashot-ear-1.0.0-SNAPSHOT.ear to the Glassfish container.
The Web application will be at localhost:8080/ic/   

You may also wish to configure maven, glassfish, and eclipse to install
the ear file directly to glassfish in step 3.
    
## Configuration    
    
The path for the web application /ic/ is set in context-root in
src/main/application/META-INF/application.xml in the datashot_ee project.

You will need to set the database JDBC connection parameters in glassfish.