# Mutability

{% hint style="info" %}
__[_Python Basics: Mutable vs Immutable Objects_](https://towardsdatascience.com/https-towardsdatascience-com-python-basics-mutable-vs-immutable-objects-829a0cb1530a)__
{% endhint %}

### Some concepts

* An **object’s identity never changes** once it has been created.
* An **object’s type** defines the **possible values** **and operations.** It is **unchangeable** like the identity.
* The _value_ of some objects can change, depending on the type.

&#x20;Some objects contain references to other objects, these objects are called **containers** (like tuple, list, or dictionary).

{% hint style="success" %}
_All **variable names** in Python are said to be **references to the values.**_&#x20;

_Python keeps an **internal counter** on **how many references** an object has**.**_&#x20;

Once the **counter goes to zero **_****_ the **GB** in Python removes the object, thus **freeing up the memory**.
{% endhint %}

### Immutable Objects

{% hint style="warning" %}
&#x20;Every time when we try to **update the value of an immutable object**, a **new object is created** instead.
{% endhint %}

That’s when we have updated the first string it doesn’t change the value of the second. Immutable data types:

* int
* float
* decimal
* bool
* string
* tuple
* range

```python
a = "foo"
# the variable a points to the memory address 4000
# 4000 reference count is 1

a += "!"
# 1. the new content is stored in a different memory address
# 2. the reference points to the new memory adress 4016
# 3. 4016 has one reference and 4000 another
# 4. reference to 4000 is removed and count is 0
# 5. 4000 is ready to by free by the GC


```

### Mutable Objects

* list
* dictionary
* set
* user-defined classes

### Container objects

&#x20;Some objects contain references to other objects, these objects are called **containers** (ie, tuple, list, or dictionary). The **value of an immutable container** that contains a reference to a mutable object **can be changed** if that mutable object is changed.&#x20;

However, the **container is still considered immutable** because when we talk about the mutability of a container **only the identities of the contained objects are implied**.

```python
skills = ["Programming", "Machine Learning", "Statistics"]
person = (129392130, skills)
print(type(person))
> <class 'tuple'>

print(person)
> (129392130, ['Programming', 'Machine Learning', 'Statistics'])

skills[2] = "Maths"
print(person)
> (129392130, ['Programming', 'Machine Learning', 'Maths'])
```

### Mutable Default Arguments

{% hint style="info" %}
_Related sources:_

* __[_Common Gotchas (The Hitchhiker’s Guide to Python!)_](https://docs.python-guide.org/writing/gotchas/#mutable-default-arguments)__
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

