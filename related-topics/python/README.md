# Python

## Language details



{% page-ref page="../distributed-computation.md" %}

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

