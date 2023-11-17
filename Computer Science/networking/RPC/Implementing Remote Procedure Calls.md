
[Implementing Remote Procedure Calls](https://web.eecs.umich.edu/~mosharaf/Readings/RPC.pdf)

Remote procedure calls (RPC) appear to be a useful **paradigm for providing communication across a network between programs written in a high-level language **

### background

#### Idea:
It is based on the observation that **procedure calls** are a well-known and well-understood mechanism for transfer of control and data within a program running on a single computer
Therefore, it is proposed that this **same mechanism** be extended to provide for transfer of control and data across a communication network

#### How it works:
When a remote procedure is invoked, the calling environment is suspended, the parameters are passed across the network to the environment where the procedure is to execute (which we will refer to as the callee), and the desired procedure is executed there. When the procedure finishes and produces its results, the results are passed backed to the calling environment, where execution resumes as if returning from a simple single-machine call. While the calling environment is suspended, other processes on that machine may still execute

#### Pros:
- **clean and simple semantics**: these should make it easier to build distributed computations, and to get them right
- **efficiency**: procedure calls seem simple enough for the communication to be quite rapid.
- **generality**: in singie-machine computations, procedures are often the most important mechanism for communication between parts of the algorithm.


#### Major issues and decision to make:
- the precise semantics of a call in the presence of **machine and communication failures**
- the semantics of address-containing arguments in the (possible) **absence of a shared address space**
- **integration** of remote calls into **existing (or future) programming systems**
- binding (how a caller determines the location and identity of the callee)
- suitable **protocols for transfer of data and control** between caller and callee
- provide **data integrity and security**

### Aim

- make distributed computation easy:
    The existing communication mechanisms appeared to be a major factor constraining further development of distributed computing.
    Our hope is that by providing communication with almost **as much ease as local procedure calls,** people will be encouraged to build and experiment with distributed applications
    RPC will, we hope, **remove unnecessary difficulties**, leaving only the fundamental difficulties of building distributed systems: timing, independent failure of components, and the coexistence of independent execution environments.
- make RPC communication highly efficient:
    lest communication become so expensive that application designers strenuously avoid it. The applications that might otherwise get developed would be distorted by their desire to avoid communicating.
- make the semantics of the RPC package as powerful as possible, without loss of simplicity or efficiency:
    Otherwise, the gains of a single unified communication paradigm would be lost by requiring application programmers to build extra mechanisms on top of the RPC package
- provide secure communication

### Fundamental Decisions

- rpc v.s message passing: 
    would not make a major difference,
    The problems of reliable and efficient transmission of a message and of its possible reply are quite similar to the problems encountered for remote procedure calls.
- no parallel paradigm
- discarded the possibility of emulating some form of shared address space
- semantics of remote procedure callsshould be as close as possible to those of local(single-machine) procedure call

### Structure

![[rpc structure.png]]

#### workflow
When the user wishes to make a remote call, it actually makes a perfectly normal local call which invokes a corresponding procedure in the user-stub. The user-stub is responsible for placing a specification of the target procedure and the arguments in to one or more packets and asking the RPCRuntime to transmit these reliably to the callee machine.

The server-stub unpacks them and again makes a perfectly normal local call, which invokes the appropriate procedure in the server

Meanwhile, the calling process in the caller machine is suspended awaiting a result packet. When the calling the server completes, it returns to the server-stub and the results are passed back to the suspended process in the caller machine.

#### components

RPCRuntime is responsible for **retransmissions, acknowledgments, packet routing, and encryption**

The user and server are written as part of the distributed application. But the user-stub and server-stub are automatically generated

This generation is specified by use of Mesa interface modules. An `interface module` is mainly a list of procedure names, together with the types of their arguments and results.
This is sufficient information for the caller and callee to independently perform `compile-time type checking` and to generate appropriate calling sequences

A program module that implements procedures in an interface is said to `export that interface`. A program module calling procedures from an interface is said to `import that interface`

