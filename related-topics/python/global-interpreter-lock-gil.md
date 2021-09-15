# Global Interpreter Lock \(GIL\)

{% hint style="info" %}
_Related sources:_

* [_Global Interpreter Lock_](https://wiki.python.org/moin/GlobalInterpreterLock)\_\_
* [_Thread State and the Global Interpreter Lock_](https://docs.python.org/3/c-api/init.html#thread-state-and-the-global-interpreter-lock)\_\_
* [_Full video explanation_](https://www.youtube.com/watch?v=KVKufdTphKs)\_\_
{% endhint %}

### Overview

* It's a **mutex that protects access to Python objects**, preventing multiple threads from executing Python bytecodes at once
* CPython **supports multiple threads** within a single interpreter, but threads must request access to the GIL in order to access any object or function.
  * Necessary due to **CPython's memory management is not thread-safe**. 
    * Every python object has a **reference counter** and when it reaches zero, the garbage collector frees the memory space. 
    * So, in order to **avoid race conditions** when updating every counter, a global mutex is a legit solution. 
* It's controversial because it prevents multithreaded CPython programs from taking full advantage of multiprocessor systems in certain situations. So, **python in practice becomes single-processed**.

### When is this a problem?

* This **shouldn't be a stopper when dealing with I/O operations**. This means different threads can access the GIL while other threads wait.
* However, in **CPU-intensive** applications, this is an **issue** given you can't take advantage of multiple cores.

### How to bypass it?

* C libraries like pandas, numpy, or numba use the CPython macros to [manually release the GIL](https://stackoverflow.com/a/36480941).
* Another option to take advantage of multicore machines is **creating processes instead of threads**. However, this creates an **overhead \(**by generating a copy of the parent memory state\) and making less efficient the communication between processes \(and shared variables\).

{% page-ref page="../distributed-computation/" %}

