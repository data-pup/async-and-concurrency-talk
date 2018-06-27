# Async and Concurrency Talk

This is an (extremely silly) lightning talk intended to provide an introduction
to Futures, Promises, and Concurrency. This is intended to be performed in
less than 5 minutes. This talk requires 4-5 participants including a presenter
(P), and 4 other people (A, B, C, D).

---

**P:** The concepts of asynchronicity, concurrency, and parrelism are
  important to understand in order to write performant code. These are related,
  but ultimately distinct, and often confused with one another. To help clarify
  on what all of these are, I thought I would ask my *network* (hehe) of friends
  to help explain more about these topics!

**P:** Let's start with asynchronous code. Async code is important because it
  helps provide a way to efficiently handle blocking I/O operations. Network
  requests are a common example of a potentially slow operation that would
  otherwise block a program's execution if implemented without using asynchronous
  abstractions.

**P:** Futures are a common abstraction in asynchronous code. These are also
  sometimes called Promises. Regardless, I don't know very much about them.
  **A**, do you think you could tell me more about what futures are and how they
  work?

**A:** Sure thing! Hold on just a second.

(At this point, **A** should silently count to 5.)

**P:** Well, while we wait, I suppose we can move on to the next topic.
  Parallelism and threading!

(**A** should interrupt **P** after waiting, and beging speaking. When **A**
begins speaking, **P** should stop and wait for **A** to finish their point.)

**A:** Futures provide a way to reason about performing many operations in
  parallel, in an efficient and non-blocking way. A Future is a placeholder
  object for a value that may not yet exist. Generally, the value of the Future
  is supplied concurrently and can subsequently be used. Composing concurrent
  tasks in this way tends to result in faster, asynchronous, non-blocking
  parallel code.

[Source](https://docs.scala-lang.org/overviews/core/futures.html)

**P:** That makes sense to me! Well, *then* (hehe), **B**, do you think you
  could briefly explain the distinction between the words "asynchronous" and
  "concurrent?"

**B**: Sure thing! Hold on just a second.

(Bt this point, **B** should silently count to 5.)

**P:** Well, while we wait, I suppose we can move on to the next topic.
  Concurrency and threading!

(**B** should interrupt **P** after waiting, and beging speaking. When **B**
begins speaking, **P** should stop and wait for **B** to finish their point.)

**P:** Well, while we wait, I suppose we can move on to the next topic.
  Parallelism and threading!

**B:** Concurrency is the separation of tasks to provide interleaved execution.
  Parallelism is the simultaneous execution of multiple pieces of work in order
  to increase speed.

[Source](https://github.com/servo/servo/wiki/Design)

**B:** When people hear the word concurrency they often think of
  parallelism, a related but quite distinct concept. In programming, concurrency
  is the composition of independently executing processes, while parallelism is
  the simultaneous execution of (possibly related) computations. Concurrency is
  about dealing with lots of things at once. Parallelism is about doing lots of
  things at once.

[Source](https://blog.golang.org/concurrency-is-not-parallelism)

**P:** That makes sense to me! Now that is resolved, we can move on to the
  next topic. Parellelism and threading! Because time is constrained, we will
  need to cover the rest of this information quite quickly.

  We probably couldn't cover all of this information using a single-threaded
  approach, so I will need to use all of the resources I can! **A**, **B**,
  **C**, and **D**, do you think you could help me out?

(At this point, **A**, **B**, **C**, and **D** should come up to the stage.)

(Once all participants are onstage, they should look at one another, and begin
reading their parts simultaneously. This should be the peak of the talk's
chaotic hilarity.)

**A:** I want to explain the difference between native threads and "green"
  threads. A language that supports native threads can execute its threads (user
  threads) onto the operating system's threads (kernel threads). Every process
  has at least one kernel thread. Kernel threads are like processes, except that
  they share memory space in their owning process with all other threads in that
  process. A process "owns" all its assigned resources, like memory, file
  handles, etc., and these resources are all shared among its kernel threads.

  Coroutines and/or generators can be used to implement cooperative functions.
  Instead of being run on kernel threads and scheduled by the operating system,
  they run in a single thread until they yield or finish, yielding to other
  functions as determined by the programmer. Languages with generators, such as
  Python and ECMAScript 6, can be used to build coroutines. Async/await is an
  abstraction built on top of generator functions that yield futures/promises.

[Source](https://stackoverflow.com/questions/1934715/difference-between-a-coroutine-and-a-thread)

**B:** I want to explain to you what a semaphore is. The concept of semaphores
  as used in computer synchronization is due to the Dutch computer scientist
  Edsgar Dijkstra. They have the advantages of being very simple, but sufficient
  to construct just about any other synchronization function you would care to
  have.

  A mutex is essentially the same thing as a binary semaphore and sometimes uses
  the same basic implementation. The differences between them are in how they
  are used. While a binary semaphore may be used as a mutex, a mutex is a more
  specific use-case, in that only the thread that locked the mutex is supposed
  to unlock it.

[Source](http://www.cs.ucsb.edu/~rich/class/cs170/notes/Semaphores/)

**C:** I want to explain to you what a mutex is. A mutex is sometimes called
  a "lock". A mutex is a synchronization mechanism for enforcing limits on
  access to a resource in an environment where there are many threads of
  execution. A lock is designed to enforce a mutual exclusion concurrency
  control policy.

  Generally, locks are advisory locks, where each thread cooperates by acquiring
  the lock before accessing the corresponding data. Some systems also implement
  mandatory locks, where attempting unauthorized access to a locked resource
  will force an exception in the entity attempting to make the access.

**D:** I want to talk to you about barriers. A barrier is a type of
  synchronization method. A barrier for a group of threads or processes in the
  source code means any thread/process must stop at this point and cannot
  proceed until all other threads/processes reach this barrier.

  The basic barrier has mainly two variables, one of which records the pass/stop
  state of the barrier, the other of which keeps the total number of threads
  that have entered in the barrier.

[Source](https://en.wikipedia.org/wiki/Barrier_(computer_science))

  Barriers are useful when a parallel operation occurs in phases, and each phase
  requires synchronization between tasks. Barriers enable multiple tasks to
  cooperatively work on an algorithm in parallel through multiple phases.

[Source](https://docs.microsoft.com/en-us/dotnet/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier)

(**P** waits for **A**, **B**, **C**, and **D** to finish.)

**P:** Thanks everybody!

