# High volume analytics 

## Requirements Snapshot

We are building an app that will accept requests to buy stocks.  

It will allow the “user” to submit a <b>request</b> to purchase a <b>stock</b> based upon: 
- Stock <b>symbol</b>
- <b>Quantity</b> to purchase
- Purchase <b>price</b>
- <b>Date/time</b> of purchase

We need to feed these <b>transactions</b> to a <b>settlements system</b> to acquire the stock.  We are not concerned with the payment flow, at this time.  We will deal with that later.  (consider using https://www.trade.it/quickstart#get-started#simulation-broker as <b>broker</b>) 

The real purpose of our effort is to aggregate data related to trades.  Anticipate 200,000+ transactions per second.  Every <b>minute</b>, we need to catch a <b>snapshot</b> of each stock symbol.  We want to understand:  <b>minimum, maximum and average bid</b> <i>for that minute</i> and over <i>the lifetime</i> of the application.

Users can <b>query</b> for data related to a stock symbol and get back <b>trend data</b> over time related to stock prices.

### Building this project

#### Java
This is a java project.  You should have a JDK on your local system and Apache maven installed, as a minimum.  

WE ASSUME YOU HAVE GIT INSTALLED OR YOU WOULD NOT HAVE THIS PROJECT ON YOUR LOCAL.

<p>If you need a JDK, we recommend the most recent version available.  
Here is the preferred OpenJDK download for the most recent at the time of this writing: 
<a href="https://jdk.java.net/11/">OpenJDK 11 Download </a>

If you have a strong preference to use the Oracle jdk, then you can find it here :  
  <a href="https://www.oracle.com/technetwork/java/javase/downloads/jdk11-downloads-5066655.html">Oracle jdk downloads</a>
</p>

After running your installation, you can check that it is properly set up with the following: 

At a command line: 

```bash
 machine-name$ java -version
 openjdk version "11.0.1" 2018-10-16
 OpenJDK Runtime Environment 18.9 (build 11.0.1+13)
 OpenJDK 64-Bit Server VM 18.9 (build 11.0.1+13, mixed mode)
```

When you enter java -version at your prompt, you should see something similar to the above as a response.  Do not worry if there are minor differences.  
If you get an error that java is not defined or the system does not understand the command, then you have not properly installed the jdk.  You may need to restart your machine, in some instances.

**PLEASE NOTE:  Your fearless leader has not used Windows forr about 10 years.  I will do my best to support you in setup on a windows machine, but we'll have to recruit help from those in the group who are day-to-day users.
Here is a helpful link for setting up a JDK in a windows environment: 
<a href="https://docs.oracle.com/en/java/javase/11/install/installation-jdk-microsoft-windows-platforms.html#GUID-C11500A9-252C-46FE-BB17-FC5A9528EAEB">Installing Oracle jdk on Windows</a>
While this is the Oracle site and it will refer to Oracle paths, it is referred to from the openJDK site, so it should work for either.

#### Apache Maven

It is likely you already have mvn installed on your machine if you have done development work.  
A good way to test this is to use this at a command line: 

```bash
machine-name$ mvn -version
Listening for transport dt_socket at address: 5005
Apache Maven 3.3.9 (bb52d8502b132ec0a5a3f4c09453c07478323dc5; 2015-11-10T08:41:47-08:00)
Maven home: /mvn
Java version: 11.0.1, vendor: Oracle Corporation
Java home: /Library/Java/JavaVirtualMachines/openjdk-11.0.1.jdk/Contents/Home
Default locale: en_US, platform encoding: UTF-8
OS name: "mac os x", version: "10.14.1", arch: "x86_64", family: "mac"
```

The feedback from mvn -version is more verbose than for java -version.
This is because it is showing you which version of mvn is installed AND which version of Java is used as the library for mvn.  
This does not mean that all of your projects have to use this version of java.  It simply means that mvn is using this version.  We can talk about the interesting and obscure issues that occur because of this at a later time.

Note:  your mvn -version will likely not produce the first line regarding listening on socket 5005.  I have my mvn set up to debug automatically.  This is why mine looks like this.
If you do not get a productive result from mvn -version, set your JAVA_HOME and MVN_HOME in your .profile or Windows environmental variables and make sure you add both to PATH.

#### Simple build

```bash
machine-name$ mvn clean install
```

From the project root, type mvn clean install.  
This will do the following: 
1.  Download dependencies from a central maven repository.
2.  Run all unit tests
3.  Compile all java code and package into a jar (unless we specify otherwise)
4.  Create the target directory and put all compiled items and artifacts into that directory
5.  Locally save the jar file and some manifest data into your local m2 repository.

#### The Docs directory
Docs directory is created as a workspace for setting up any diagrams or other analysis material that you want to keep with the project.  Currently, it is set up to categorize based on UML diagram type.  Feel free to change this and make it your own.  

All diagrams are created using plantUML.  It is a syntax driven modeling tool that is, quite simply, the best free UML tool available.  Learn it, live with it, use it.  If you are using IntelliJ, there is a plantUML plugin so that you can create and edit diagrams in your IDE.

<a href="http://plantuml.com/">plant uml website</a> - try not to judge the tool by its website.  The website is a bit rough.  The tool, however, is not.

<a href="https://plugins.jetbrains.com/plugin/7017-plantuml-integration">IntelliJ plantUML plugin</a>

There is also an ecplise plugin for the tool.  I don't use it, but here is documentation on it: 
<a href="http://plantuml.com/eclipse">Eclipse plantUML plugin</a>

