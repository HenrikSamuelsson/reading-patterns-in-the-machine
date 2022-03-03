# Reading Patterns in the Machine

Notes and material related to reading the book Patterns in the Machine written by John T. Taylor and Wayne T. Taylor.

## Chapter 1 Introduction

The book as a whole is about software development for embedded systems, and the goal of the book is to present good strategies and ways of working in this field.

The book is at an intermediate to advanced level, it is assumed that the reader can already read and write code, ideally C and C++ code, and have been involved in one or more team projects.

Embedded software development is often done in a more primitive way compared to other flavours of software, such as web development, it does not have to be like this. Embedded software development do come with some unique type of challenges the book aims to resolve some of these challenges.

Two categories of best practices:

- Tactical; which is about design and construction of individual modules

- Strategic; the bigger picture, how features can be added and how modules work together, how to test.

There is no clear divider what is a strategic and tactical practice but in general so are tactical practices at a low level i.e. something close to the actual source code, and strategic are high level and can hence be more abstract.

It is easy to fall into the trap and only focus on the tactical best practices resulting in poor quality and rigid software that is hard maintain and add new features to.

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
SCM = Software Configuration Management  
SOLID = SRP OCP LSP ISP DIP  
SRP = Single Responsibility Principle  
