# Rook Application Platform

### What It Is
Rook is an enterprise application platform built upon the Java 8 ecosystem. Rook is designed as a vehicle for creating high-performance, highly-scalable, easy-to-maintain and painless to deploy applications.

Rook breaks with Java tradition and provides simple but deeply capable APIs for all of the common enterprise application needs. For example, sending a simple email with traditional JavaMail is dozens of lines of code, but sending a fully-templated, multi-lingual email with integrated open tracking, automated retries and opt-out capabilities is only two lines of code with Rook. In the end, Rook is trying to combine the quick and simple development of a scripted environment (such as Ruby or Python) with the performance of the Java ecosystem.

### Motivation for Rook
Frustrated with the failure of Clojure to evolve into a mature environment suitable for world-class production applications, we created Rook as a way of staying on mainstream technology and tool (Java), but eliminate the excessive historical baggage.

Some people are using Rook as a platform for migrating Clojure and Scala applications back into the Java fold. Rook has many of the best aspects of Clojure and Scala, including immutable objects, deep metadata and graceful reflection, but also has many capabilities unique to Rook. Also, the pendantic nature of Clojure is loosened (immutability is used when it makes sense, not as a mandatory pain point) and the cacaphony of ways of accomplishing common tasks in Scala is reduced to a single, elegant mechanism in Rook.  

## Features
#### Metadata-driven Applications
A Rook-based application uses a series of annotations to mark up the domain model objects of the application. These annotations turn into rich runtime metadata that enables all of the following:

 - Automatic and deep security model
 - Automatic CRUD operations
 - Automartic support for both SQL and NoSQL stores
 - Automatic complex queries (using Rook as the query language)
 - Automatic REST/JSON and SOAP/XML web services
 - Automatic domain model documentation generation
 - Automatic REST API documentation
 - Automatic deep validation of correctness

Typically, there is only a two lines of annotation added to each type and a
simple line of annotation added to each Java field to enable all of the above.

	
#### Unified Expression Grammar
At the heart of Rook is the Rook grammar. This grmmar is used through the Rook
platform for things like:

 - Constraints
 - Computed Values
 - Validation
 - Security
 - Object Serialization
 - Web Page Templates
 - Rich Text Documents
 - Scripted Actions

The core idea is to provide a single grammar for all of the common capatilies
needed for a modern application without requiring numerous bespoke grammars.

For those familiar with Clojure or any other Lisp variant, the grammar will
feel comfortable and familiar. The Rook grammar is a Lisp-2 (separate namespaces
for functions and values), but a fair amount of syntactic sugar added to make
expressions highly readable, even for a non-technical audience. For example,
a simple expression based upon dates:

	(if ((today) after: 2014/12/31)
		then: "Welcome to the future!"
		else: "The future has not arrived.")

Full details on the Rook grammar and its capabilities can be found in the
distribution in the _doc/rook-language.pdf_ file.

#### Plugins
Rook uses a simple interface-based plugin mechanism that requires zero configuration. Simply implement a plugin interface, provide a single annotation on your plugin class, and the plugin will be automatically recognized and used by your application the next time it boots.

#### Enterprise-Class Features Built-In
The Rook platform as a variety of APIs (layered on top of plugins to world-class service providers) that make creating new features fast and reliable. These
include:

 - Scalable batch processing
 - Managed email transmission
 - Automatic test data generation
 - Real-time event processing
 - Distributed eventual-consistency caching
 - Integrated, open authentication and authorization
 - High-performance binary web services for intra-node communication

Basically, Rook contains APIs that cover all of the core capabilities for a modern, web-scale application.

## Requirements and Dependencies
#### Java 8 Required
Rook is based upon Java 8 and takes full advantage of the capabilities of that version of the Java platform. A Java 8SE JVM is required. There are no plans to support versions of Java before 8.

#### Other Requirements
Beyond the Java 8 JVM, All of the other libraries that are required are
packaged in the lib directory of the binary release.

#### Supported Persistent Stores
Support for persistent stores are provided via plugins. Support for the following
SQL stores is provided by the core plugins:

 - MySQL
 - Oracle
 - SQLServer
 - PostgreSQL
 - SQLite
	
Support for the following NoSQL stores is also provided by core plugins:

 - VoltDB
 - Riak
 - Aerospike
 - Amazon DynamoDB
 - Amazon SimpleDB

Note that creating a new plugin is a non-trivial affair because of the depth of
automated capabilities provided by the Rook platform. This is a necessary evil
to move that programming burden from the application developer (over and over)
to the plugin developer (build the plugin just once).

#### Supported Web Servers
Support for web servers is provided via plugins. The following web servers have integrated plugins in the core platform:

 - Jetty
 - Embedded Tomcat
 - Generic Servlet 3.0 Container
	
Other embedded web servers can be integrated by simply adding a new plugin and
configuring that plugin for use.


## FAQ

- **Q.** Is anyone using Rook in a production environment?
- **A.** Yes. The creators of the Rook platform have a large-scale, mission-critical
	Rook-based application deployed on AWS that hits peeks of 20,000 TPS on
	a daily basis. There are also a few others known to be actively using the
	platform. If you'd like to get a shout-out from the Rook team, let us know!

- **Q.** Where is the documentation?
- **A.** All of the documentation for the platform can be found in the /doc
	directory of the distribution. Yes, we are aware that the documentation is
	a bit thin right now. Try using the tools in the /bin directory with the
	"help" command to get your environment setup and configured.

- **Q.** What functions are available in the Rook grammar?
- **A.** All functions are implemented as plugins (implementing either the
	KeywordFunction or ShorthandFunction plugin interfaces). Use the plugin
	tool to extract a list and associated documentation.

	
