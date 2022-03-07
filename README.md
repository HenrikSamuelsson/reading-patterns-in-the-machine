# Reading Patterns in the Machine

Notes and material related to reading the book Patterns in the Machine written by John T. Taylor and Wayne T. Taylor.

## Chapter 1 Introduction

The book as a whole is about software development for embedded systems, and the goal of the book is to present good strategies and ways of working in this field.

The complete package of practices and methodologies presented in the book is by the authors given the name Patterns In The Machine (PIM). Patterns can maybe be thought of as that the practices can, and should, be reused for every new project and the in the machine part refers to embedded systems platform.

The book is at an intermediate to advanced level, it is assumed that the reader can already read and write code, ideally C and C++ code, and have been involved in one or more team projects.

Embedded software development is often done in a more primitive way compared to other flavours of software, such as web development, it does not have to be like this. Embedded software development do come with some unique type of challenges the book aims to resolve some of these challenges.

Two different categories of best practices are handled in the book:

- Tactical; about design and construction of individual modules

- Strategic; the bigger picture, how features can be added and how modules work together, how to test.

There is no clear divider between strategic and tactical practice, many practices belongs to both sides, but in general so are tactical practices things that are non-optional and at a low level i.e. something close to the actual source code, and strategic practices are often more high level and hence more abstract.

It is easy to fall into the trap to only focus on the tactical best practices and neglect the strategic best practices, resulting in poor quality and rigid software that is hard maintain and add new features to.

## Chapter 2 Core Concepts

The PIM core concepts are introduced in chapter 2:

- Software architecture, high level planning to enable all parts to work together

- Automated unit testing, provides confidence that new features do not break existing features, most part of an embedded system can be unit tested if making a little effort

- Functional simulator, the use of an ordinary PC for initial development before the hardware for the actual embedded platform have arrived

- Continuous Integration, frequent integration of changes into the main branch with automated builds and tests to have short feedback loops

- Data model, two modules shall not communicate directly instead so shall one write to a data model and the other read from this data model

- Finite State Machines, a good tool for handling the asynchronous communication often occurring in embedded systems

- Documentation, examples of documentation are software development plan, software architecture, software detailed design, best practices, source code documentation and then particularly for the modules public interfaces

## Abbreviations

CI = Continuos Integration  
CPU = Central Processing Unit  
DIP = Dependency Inversion Principle  
FSM = Finite State Machine  
IC = Integrated Circuit  
IPC = Inter-Process Communication  
ISP = Interface Segregation Principle  
ITC = Inter-Thread Communication  
LSP = Liskov Substitution Principle  
LSSSI = Layers Strategic Semantics Skinny Interfaces  
MCU = Micro Controller Unit  
OCP = Open Closed Principle  
OSAL = Operating System Abstraction Layer  
PIM = Patterns In the Machine  
SA = Software Architecture  
SCM = Software Configuration Management  
SDP = Software Development Plan  
SOLID = SRP OCP LSP ISP DIP  
SRP = Single Responsibility Principle  
