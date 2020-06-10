# Chapter 30: The Database is a Detail

The data model is not the database. The database is a detail. It is not an 'entity' as we learned previously. The database is a mechanism, a low level detail. It should not pollute the architecture.

## Relational Databases

RD grew in popularity in the 70s and 80s. They are elegant, but they are still a technology; a detail. While they may be convenient for certain forms of data access, it's implementation is not architecturally significant. Your application should not care nor know about this decision. In fact, tools that allow passing of database rows throughout your application is an anti-pattern as it couples this low-level detail with your entities, business rules, use cases and even your UI.

## Why are Database Systems so Prevalent?

Disks. Disks were the primary storage mechanism for decades, but even with the evolution of this storage mechanism over these decades, the impact of using a disk in terms of time to retrieve data is high. As such, indexes, caches and other optimizations were leveraged to represent the data. This split into two forms: file systems and relational database management systems (RDBMS).

File systems are great for documents that need to be retrieved by name, but slow for searching through for contents. RDBMS are great for content bases uses, but poor at storing and retrieving opaque documents. But both store stat on disk to be loaded into RAM to be manipulated.

## What if there were no Disk?

Disks are a dying breed. When the data is loaded into RAM, it is rarely kept in the form of rows and tables. It is often mutated into trees, lists, hash tables, stacks, etc. It is then accessed via pointers or references. This is what programmers do.

## Details

This is why it is a detail. The form of the data in long-term storage is irrelevant to the application that references the data in RAM. (Recall Chapter 22: Interface Adapters: Data should be in the format most convenient for the use cases and business rules.)

Hence, the disk is a detail that should not be acknowledged.

## But what about Performance?

Yes performance is a concern, but it can be encapsulated and separated from the business rules. It has nothing to do with the overall architecture of the system. (Read: It should be able to be addressed without impacting the business rules)

## Anecdote

The author discusses a case where he fought against implementing an RDBMS into a system that was perfectly functional with random access files representing their data in trees and linked lists.

Eventually, he lost the fight because it was not a fight fought on the merits of the technical solution, but rather that the clients were lead to believe that they _needed_ the RDBMS from whatever software they purchased. It was a marketing tactic similar to the concept that "Breakfast is the most important meal of the day".

This is seen today with the concept that RDBMS provide "Service-Oriented architecture" to protect your "enterprise" "data assets".. buzzwords to sell software.

The author quit and became a consultant.

## Conclusion

The data structure is architecturally significant. How that data moves onto and off of magnetic disks, is not. The database is a detail.
