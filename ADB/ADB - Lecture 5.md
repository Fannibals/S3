#### ADB - Lecture 5

---

##### 1. Isolation Concepts

+ Isolation guarantees **consistency** provided each transaction itself is consistent

  + Checksum field/CRC of each page must be correct
  + Accounts balances must be positive

+ How to achieve it?

  + Runs sequentially — Batch processing
    + not efficient
  + lock
    + concurrent reads of an object is permitted but concurrent write operation with other write or read operation is prohibited

  + $O_i \cap (I_j \cup O_j) = empty\,for\, all \,i \ne j$
  + 

+ Dependencies

  + WRITE -> READ
  + WRITE-> WRITE
  + READ -> WRITE
  + READ -> READ — ignore

+ **Lost update :**

  + Write - Write conflict

+ **Dirty read:**

  + a transaction reads an object written by another transaction which afterwards aborts.

+ **Non-repeatable read**



+ **Lock Compatibility Matrix**





##### Actions

+ READ, WRITE, XLOCK, SLOCK, UNLOCK, BEGIN, COMMIT, ROLLBACK
+ Exclusive lock conflicts with shared lock as well as itself
+ rollback if conflict



##### Isolation Theorem

+ Cycle appears when conflict between t1 and t2

**DEP — Dependency relations**

DEP(H) = { (Ti,O,Tj) | Tj depends on Ti }

 

##### History

+ a history is said to be isolated if it is equal to a serial history 

T is a wormhole transaction if T << T' << T

Which implies a cycle in the dependency graph of the history



A serial history is an isolated history

##### Wormhold theorem

+ A history is isolated if and only if it has no wormholes

**Locking theorem**

+ If all transactions are **well formed** and **two-phased**, then any legal history will be isolated.

**Locking theorem (converse)**

+ If a transaction is **not well formed** or is **not two-phase**, then it is possible to write another transaction such that it is a wormhole.

**Rollback theorem**

+ An update transaction that does an UNLOCK and then does a ROLLBACK is not two phase.

  

##### SUMMARY

+ A transactions is a sequence of READ, WRITE, SLOCK,
  XLOCK actions on objects ending with COMMIT or ROLLBACK.
+ A transaction is well formed if each READ, WRITE and
  UNLOCK operation is covered earlier by a corresponding lock
  operation.
+ A history is **legal** if does not grant conflicting grants.
+ A transaction is **two phase** if its all lock operations precede its
  unlock operations.





----

**Four degrees**

+ Degree 0
+ Degree 1
+ Degree 2
+ Degree 3



**Phantoms and Predicate locks**

+ If locks are taken at finest possible granularity then we may be performing updates which otherwise should be delayed.

+ <http://www.mysqlab.net/knowledge/kb/detail/topic/innodb/id/5429>

Problems with predicate locks

+ set intersection = predicate satisfiability is NP complete
+ Hard to capture predicates
+ Pessimistic



**Granular locks**

+ we need to build some hierarchy and locks can be taken at any level will
  automatically grant the locks on its descendants



**LOCKS**

+ None:
  + no lock is taken, all requests are granted

+ X : exclusive lock
+ S: Shared lock
+ U: Update lock
+ IS: Intent to set Shared locks at finer granularity 
  + allows IS and S mode locks at finer granularity and preveents others from holding X on this node.
+ IX: Intent to set shared or exclusive locks at finer granularity
  + allows to set IS, IX, S, SIX< U and X mode locks at finer granularity and prevents others holding S, SIX, X, U, on this node 
+ SIX: a coarse granularity shared lock with an intent to set finer granularity exclusive locks

----

WARNING:

+ read whole notes during the holiday

















































