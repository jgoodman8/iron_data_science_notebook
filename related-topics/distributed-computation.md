# Distributed computation

{% hint style="info" %}
_Sources:_

* \_\_[_Operating System: Threads and Concurrency \(Akhand Mishra\)_](https://medium.com/@akhandmishra/operating-system-threads-and-concurrency-aec2036b90f8)\_\_
{% endhint %}

## About threads and processes

* A process can create, and for instance, contain threads.
* The **threads of a process are part of the same virtual address space**. This implies they share:
  * data
  * code
  * file.
* However, each thread has its own:
  * stack, 
  * stack pointer register
  * Program Counter
  * registers.

![](../.gitbook/assets/image%20%2822%29.png)



