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

## Chapter 3 Design Theory for Embedded Programming

Discusses existing proven good rules of programming.

Firstly the five principles known by the abbreviation SOLID.

### Single Responsibility Principle

> Definition: Single Responsibility Principle (SRR)
> > There should never be more than one reason for a class to change.

This principle can be adhered to by having a layered architecture to separate the responsibilities.

An example of an layered architecture to handle receiving of serial data can be to split this into three layers. The lowest layer handles receive of individual bytes until a known number of needed bytes have arrived, and then signal to the middle layer. The middle layer is responsible for checking up on the data validity by controlling a check sum that is passed along with the data, if this check passes so is the top layer signaled. The top layer handles what actual action to take based on the data content, for example order that a heather is to be turned on or whatever the application actually is designed to do.

Another strategy to follow the Single Responsibility Principle is to in general keep entities small, this holds for everything from module level down to function level. Neither modules nor functions shall do many things.

### Open-Closed Principle

> Definition: Open-closed principle (OCP)
> > Software entities should be open for extension, but closed for modification.

The goal of the open-closed principle is to be able to extend or change entities of the system without need to rework and retest the entire system.

An concrete example would be to be able to change to a new type of non-volatile memory with minimal effort.

Strategies to be used to conform to the open-closed principle are:

- The preprocessor directive ifndef, that enables future extension using compile time binding

- Model points in a data model for interchanging data instead of direct communication between modules

- Introduce abstract interfaces and have the module implement these with purpose to hide the low level implementation details from other modules.

### Liskov Substitution Principle (LSP)

> Definition: Liskov Substitution Principle
> > Functions that use pointers or references to base classes must be able to use objects of derived classes without knowing it.

LSP can also be stated as:

> All implementations of an abstract interface are required to fully implement of the semantics of the interface definition.

The compiler will only partly help out in verification of the LSP by checking the interface signature correctness. Many other things are up to the developers to ensure, such as:

- Is everything initiated and up and running so a method can now be called

- How to clean up and recover from eventual error

- Management of dynamically allocated memory

### Interface Segregation Principle

> Definition: Interface Segregation Principle (ISP)  
> > Clients should not be forced to depend upon interfaces that they do not use.

Avoid monster interface that does everything. Prefer introducing multiple, smaller interfaces that target specific usage models or use cases.

Say when defining the interfaces to the HAL and there are multiple communications lines into to the system: I2C, UART, SPI, then each of these should have it's own interface. The same goes for services provided by an eventual RTOS such as thread and mutex support, split these as well into different interfaces.

### Dependency Inversion Principle

> Definition: Dependency Inversion Principle (DIP)  
> > (1) High-level modules should not depend on low-level modules. Both should depend on abstractions.  
> > (2) Abstractions should not depend on details. Details should depend on abstractions.  

The abstractions mentioned mentioned in the definition will in reality be interface definitions in a header file with few if any `#include` statements.

An example of a interface definition set for an interface for a non volatile memory could be:

```C
bool read(size_t startOffset, void* destination, size_t maxDestinationBytes);
bool write(size_t startOffset, const void* source, size_t numSourceBytes);
```

Note how the interface lacks all details about the actual underlying memory used and the mechanism used to communicate with the memory and hence satisfies the DIP.

The upper application layer will use this interface and the lower layer will implement the interface. The lower layer will know details about the actual memory type used. Should the memory type need to be changed in the future so will only the code for this lower layer need to change and the upper application layer can be left as is. Another benefit is that the different layers can be developed and tested in isolation by different developers once the interface have been defined.

## Abbreviations

CI = Continuos Integration  
CPU = Central Processing Unit  
DIP = Dependency Inversion Principle  
FSM = Finite State Machine  
HAL = Hardware Abstraction Layer
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
