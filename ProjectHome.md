[Protothreads](http://en.wikipedia.org/wiki/Protothreads) is a programming model invented by Adam Dunkels that combines the advantages of _event-driven_ (sometimes also called _state machine_) programming and _threaded_ programming. The main advantage of the event-driven model is efficiency, both speed and memory usage.  The main advantage of the threaded model is [algorithm clarity](http://www.sics.se/~adam/dunkels06protothreads.pdf).  Protothreads gives you both. A protothread is an extremely lightweight thread. As with event-driven programming, there is a single stack; but like threaded programming, a function can (at least conceptually) block. This protothreads implementation:
  * is not an implementation of POSIX threads or any other standard API
  * does not require assembly-language code or use setjmp/longjmp
  * is independent of CPU architecture
  * schedules threads non-preemptibly and deterministically.
  * standard version does not take advantage of multiple CPUs or cores
  * multi-core version can take advantage of multiple cores

I designed and wrote the version described here from scratch and it is not compatible with other versions of protothreads. The only aspect of the implementation described here that is not standard C is its use of [gcc label variables](http://gcc.gnu.org/onlinedocs/gcc/Labels-as-Values.html).

This project includes:
  * full source code (about 400 lines including comments)
  * two synchronization facilities built on top of the base protothreads (semaphores and locks)
  * about 800 lines of test code
  * gdb (debugger) macros to print the stack traces of a given protothread or all protothreads.
  * a separate branch, called multicore, allows one to take advantage of multiple cores

Please see the wiki page for this project for more information.