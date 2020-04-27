Chapter 12
Components are the smallest entities that can be deployed as a part of an environment .
In compiled languages a component is an aggregation of binary files
In Interpreted Language - aggregation of source files

Well deployed components always maintain the ability to be independently deployable and independently operable

A Brief History of Components

In the early years programmers controlled the memory locations of their programs. They devices when the programs needed to be loaded into memory and the programs were not relocatable.

Source code of library functions was included with application code and compiled into a single program. Many devices were slow and memory was expensive and compilers needed to make multiple passes through the code and this could take hours. To shorten this time the programmers separated the code from the function library and loaded the binary at a known address. A symbol table was created for the function library and compiled in with the application code.

When running a program they would load the binary function and then the application and most of the time this worried well as long as the application and the function library could fit between the address 0000 and 1779. In time the programs kept growing larger and had to then be split into two address segments .

As programs kept getting larger, they kept exceeding their bounds and more space was needed to able to allocate them and programs kept getting fragmented

Relocability

Relocating binaries -> compilers were changed to output the binary code that can be output in memory by a smart loaded
This relocated code was instrumented with flags which told the loaded what parts of the loaded data has to be altered to be loaded at the selected address

From this improvement, the programmer was able to test the loader where to load the application and where to put the function library and then the loader could accept many inputs and load them into memory relocating items as they were loaded , This helped the programmer to only load those things that were actually needed

Compilers were changed to emit the name of the functions as metadata in the emitted library then the library functions were called .
The compiler emitted the name s of the library functions an external definition and this gave birth to the linked loader

Linked Loader (60s-70s)
The linked loader helped programmers to separately compile and load segments and it worked well for small libraries linked into small programs

As programs got better linked loaders became too slow. It would take hours to load all of the things that were needed by a program. From this the linking and loading were put into two different phases . The slow part that did the linking was put into a separate application that was called the linker and then output of the liner was a linked relocatable. This allowed the programmer to prepare an executable using a slow liker that they can load at any time.

80s

Programmers working in a high level language such as C, source modules were compiled from .c files to .o files and then fed into a linker to create an executable file . Compiling 1 module awas fast but compiling a lot of modules took a lot of time . This compile link process continued to be the bottleneck.

As the 80’s progressed, with Moore’s law the disk size started to shrink and got significantly faster. Memory started to get cheap enough for the data on the disk to be cached into the ram as clock rates increased from 1mhz to 100 mhz

Mid 1990

Time spent liming had shrunk to a matter of seconds and the linked loader was again feasible for small jobs.
The era or Active x and shared jar files had begun. Computer and devices had gotten faster and it made linking at load time alot mode feasible. This gave birth to the component plugin architecture.

Conclusion
Dynamically Linked Files which can be plugged together at runtime have taken 50 years but we have arrived at a a place where the architecture can bethe casual default rathen rnat the herculean effort that it was
