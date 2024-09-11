# AsyncIO

{% hint style="info" %}
_Sources:_

* [_Parallel execution of asyncio functions_](https://hinty.io/ivictbor/parallel-execution-of-asyncio-functions/)
* [  _Python 3's Killer Feature: asyncio_](https://eng.paxos.com/python-3s-killer-feature-asyncio)
{% endhint %}

![](<../../.gitbook/assets/image (113).png>)

* Don’t have to use semaphores, you get access to shared memory, and it’s relatively easy to code
* For applications with lots of IO, the savings can be substantial

### Await coroutines

```python
import asyncio
import time

def write(msg):
    print(msg, flush=True)

async def say1():
    await asyncio.sleep(1)
    write("Hello 1!")

async def say2():
    await asyncio.sleep(1)
    write("Hello 2!")

write("start")
loop = asyncio.get_event_loop()
loop.run_until_complete(asyncio.gather(
    say1(),
    say2()
))
write("exit")

loop.close()
```

1. When `run_until_complete` runs `say1` function, the interpreter executes it line by line, and when it sees `await`, it starts asynchronous operation which later will be finished with some internal callback to loop (such callback hidden from us, developers).
2. But now, after the start, it immediately returns control to the event loop.&#x20;
   1. So it starts asynchronous sleep and our `loop` has control, so the loop is actually ready to start the next function `say2`.&#x20;
   2. When first `async` sleep is finished, it makes an internal callback to loop (hidden from us) and loop resumes execution of `say1` coroutine: next operation is printing `Hello 1!`.  After printing it returns again to the event loop.
3. At the same time, from the second sleep, the loop receives an event about finishing the second sleep (if 2 events will come at the same time they will not be lost, they will be just queued).
   1. So now `Hello 2!` is printed and the second method is also returned. `run_until_complete(gather(l1,l2,l3))` will block until all `l1`, `l2`, `l3` coroutines will be done.

It can be displayed as next (assume that all red lines are at `0s` time point, and all blue at `1s`):

![](<../../.gitbook/assets/image (117).png>)
