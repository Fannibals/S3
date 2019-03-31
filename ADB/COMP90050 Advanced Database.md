#### COMP90050 Advanced Database

##### Content:

+ Introduction
+ Database architectures
+ Indexing structures
+ Relational operators
+ Transaction processing 

+ Performance benchmark

##### Performance of a database

+ Systems depends on: 
  + Hardware
  + Software
  + Database tuning



##### Database Technologies:

**1. Simple file systems like Unix file system**

+ Example: direct

+ **\+ **
  + very fast for simple apps but can be slow for complex apps
+ **\-**
  + <font color = orange>application dependent optimisation</font>
  + less reliable
    + if system crashes, may not recovery
  + hard to maintain (concurrency issues)
  + ??? Many of the features exist in RDB need to be incorporated  ???

**2. Relational database systems(RDBs)**

- **+ **
  - proven tech
  - very reliable
    - not lose info even the system crashes
  - application independent optimization
    - higher logical sql language
  - well suited to many applications related to commerce and other domains and becoming very fast due to large main memory machines and SSDs
- **\-**



**3. Object Oriented (OO) Database Systems**

**+**

+ reliable
+ well suited for apps requiring complex data
+ ***XML*** based Database Systems are becoming dominant
+ many apps now use XML docs



**4. Deductive database systems(DDBS)**

**\+**

+ most of the application can be developed entirely using DDBS



**5. Key-value pair based DBSs**

+ Used for building **very fast,** highly parallel processing of large data

+ Examples:

  + MapReduce and Hadoop

+ many apps do not require the expressive functionality of transaction processing 

  + web search, big data analytics

+ Atomic updates at Key-value pair level only

  

**6. NoSQL**

+ provides a mechanism for storage and retrieval of data which is modelled in means other than the tabular relations used in relational databases
+ NoSQL stores comprimise consistency in favour of availability, partition tolerance and speed.
  + in the sense of the CAP theorem
+ Most NoSQL databases offer a concept of "eventual consistency"





##### Database Architectures

**1. Centralised database systems**

+ Data is stored in one location
+ System administration is simple
+ Optimisation process is generally very effective
  + centralized , easy to understand underlying architecture
+ Cloud Computing/ Data farms/ data centres are examples



**2. Client-server**

+ Processing is shared between client processes and server processes
+ Client and server may be in different locations
+ system administration is relatively simple
+ Recovery as centralised system
  + all in one place, relatively simple



**3. Distributed databse systems**

+ Data is distributed across several nodes
+ Transparency
+ Hard to process queries efficiently
+ Transaciton processing can be very inefficient
  + any node failure 
+ Sys admin is very hard
+ sys recovery after a crash is complicated



**4. World Wide Web**

+ Data consistency is not guaranteed
+ security could be a potential problem
+ very  convenient to use
+ 



**5. Grid Computing/Databases**



**6. P2P Databases**

+ Data and processing is shared among a group of computer systems which may be geographically seperated as in Grid Databases systems
+ need duplication of data for reliability



**7. Cloud Computing**

+ offers online computing , storage and a range of new services for data and devices that are accessible through the Internet
+ Cloud services offered in several forms:
  + Iaas - Infrastructure as a service
    + Provide virtual machines
  + Paas - Platform as a service
    + provide env like Linux, windows
  + Saas - Software as a service
    + RDB, Mail, etc.



**An Example: AWS**

+ Attributes of Cloud Computing
  + NO capital expenditure
  + Pay as you go and pay only for what you use
  + True elastic capacity; Scale up and down
  + Improves time to market



#### Basic Hardware

##### Memories

+ Moore's law:
  + memory chip capacity grows at a rate
  + doubles every 18 moths since 1970

+ Joy's law:
  + processor performance grows at a rate
  + doubles every two years since 1984



+ Fastest Computer IBN Summit


----


#### Lecture 4
##### Transaction Processing
+ Definition
  + A transaction is collection of operations that need to be performed on the physical and abstract application state.

+ ACID properties
  + Atomicity
    - A transaction's changes to the state are atomic implying : ==
      - Either all actions happen or none happen
  + Consistency
    - Transaction are a correct transformation of the state.
    - Actions taken as a whole by a transaction do not violate the integrity of the application state.
  + Isolation
    - Even when several transactions are executed simultaneously, it appears to each transaction T that 
      others executed either happen before T or after T but not at the same time.
  + Durability
    - copies for preventing losing information

+ Reliable communication
  + recording every msg sent or received on stable storage
  + time
  + 





+ Flat Transactions
	+ In a flat transaction, each transaction is decoupled from and independent of other transactions in the system. Another transaction cannot start in the same thread until the current transaciton ends.

	+ exec sql BEGIN WORK
		+ delta:
			+ positive means debit
			- negative means credit

	+ :delta => preprocess the c variable


+ Limitations of Flat Transactions
	+ Flat transactions do not model many real applications
		+ booking flight (cancel from the middle part)
	+ waste

	+ solutions：
		+ Transaction with save points

+ Nested Transactions
	+ Rules:
		+ Commit rule
			+ parent > child
		+ Roll back rule
		+ Visibility Rules


+ TP monitor computing styles
	+ batch processing
	+ Time-sharing
	+ Real-Time processing

+ TP services
	+ Hetergeneity
	+ Control communication
	+ Terminal management
	+ Presentation service
	+ Context management
	+ Start/Restart

+ TP process structure



#### Lecture Set4
+ Concurrency Problems

+ Implementation of exclusive access (atomic operations)
	+ Dekker's algorithm
		+ busy waiting
		+ takes lots of storage space
		+ efficient if the lock contention is low
	+ Lock / Unlock -- Spin Locks
		+ ```if (*lock == 1){*lock = 0; return (true)}
			else return (false) ```

	+ Lock Manager
		+ ``` if (*cell == *old) { *cell = *new; return TRUE;}
				else { *old = *cell; return FALSE;}```

		+ Counter => Global varaible == cell
		+ temp => local var for each thread == old

		+ if the counter value == one I read
			+ => no body else came between
			+ change it to the new value

		+ NULL in sem means free, no one is using the resource


+ Deadlocks
	+ Solutions
		+ have enough resources so that no waiting occurs
		+ simply do not allow a process to wait simply rollback.
			- this can create live locks which are worse than deadlocks
		+ Linearly order the resources and request of resources should follow this order
			- there should no cycle here



	+ Deadlock avoidance/mitigation
		+ Pre-declare all the resources that are needed and allocate all the resources in a single request.
		+ Allow a transaction to wait for certain maximum time 
		+ Periodically check the resource dependency graph for cycles.
		+ Many distriubted database systems maintain only local dependency graphs and use time outs for global deadlocks.
		+ Phantom Deadlocks














