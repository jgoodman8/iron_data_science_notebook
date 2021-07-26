# Python

## Language details

### GIL

{% hint style="info" %}
_Related sources:_

* [_Global Interpreter Lock_](https://wiki.python.org/moin/GlobalInterpreterLock)\_\_
* [_Thread State and the Global Interpreter Lock_](https://docs.python.org/3/c-api/init.html#thread-state-and-the-global-interpreter-lock)\_\_
{% endhint %}

* It's a **mutex that protects access to Python objects**, preventing multiple threads from executing Python bytecodes at once
* Necessary due to **CPython's memory management is not thread-safe**.
* It's controversial because it prevents multithreaded CPython programs from taking full advantage of multiprocessor systems in certain situations.
* **Potentially blocking or long-running operations**, such as I/O, image processing, and NumPy number crunching, happen _**outside**_ **the GIL**.
  * However, it is only **in multithreaded programs** that spend a lot of time inside the GIL, **interpreting CPython bytecode**, that the **GIL becomes a bottleneck**.

{% page-ref page="distributed-computation.md" %}

### Mutable Default Arguments

{% hint style="info" %}
_Related sources:_

* \_\_[_Common Gotchas \(The Hitchhiker’s Guide to Python!\)_](https://docs.python-guide.org/writing/gotchas/#mutable-default-arguments)\_\_
{% endhint %}

```python
# Function declaration
def append_to(element, to=[]):
    to.append(element)
    return to
    
# Code execution
my_list = append_to(12)
print(my_list)

my_other_list = append_to(42)
print(my_other_list)

# Expected output
# > [12]
# > [42]

# Actual output
# > [12]
# > [12, 42]

# Solution
def append_to(element, to=None):
    if to is None:
        to = []
    to.append(element)
    return to
```

