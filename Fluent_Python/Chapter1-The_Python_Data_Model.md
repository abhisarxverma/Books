# **Chapter 1 - The Python Data Model** 🃏

## **A Pythonic Card Deck**

### **🔹 Example 1 - The Power of `__getitem__` and `__len__`**

> *Implementing two special methods (`__getitem__` and `__len__`) makes our custom class behave like a sequence!*  

### **📝 Code Example: A Deck of Playing Cards**
```python
import collections
Card = collections.namedtuple('Card', ['rank', 'suit'])

class FrenchDeck:
    ranks = [str(n) for n in range(2, 11)] + list('JQKA')
    suits = 'spades diamonds clubs hearts'.split()

    def __init__(self):
        self._cards = [Card(rank, suit) for suit in self.suits
                                        for rank in self.ranks]
    
    def __len__(self):
        return len(self._cards)

    def __getitem__(self, position):
        return self._cards[position]
```


### New Learnings
**🔢 len(deck)	Calls __len__**       - returns total card count.

**📏 Slicing (deck[x:y:z])**	        - Works automatically because of __getitem__.

**🌀 Iterability (for card in deck)**	- Class becomes iterable without extra code.

**🔍 Membership (in deck)**	            - Enables efficient searching within the deck.

> *An abstract base class (ABC) in Python is a class that cannot be instantiated and serves as a blueprint, enforcing the implementation of specific methods in its subclasses using the ABC module.*

## **Collections API**

- **Collections ABC** inherit from the **Iterable**, **Sized**, **Container** ABC's.
- **Reversible ABC** inherit form only the **Iterable ABC**.
- **Sequence**, **Mapping**, **set** inherit from the **collections ABC**.
- **Sequence** only also inherit from the **Reversible ABC**.

## Chapter Summary
By  implementing  ==special  methods==,  your  objects  can  behave  like  the  built-in  types,
enabling the expressive coding style the community considers Pythonic.

A basic requirement for a Python object is to provide usable string representations of
itself,  one  used  for  debugging  and  logging,  another  for  presentation  to  end  users.
That is why the special methods __repr__ and __str__ exist in the data model.

Emulating  sequences,  as  shown  with  the  FrenchDeck  example,  is  one  of  the  most
common  uses  of  the  special  methods.  For  example,  database  libraries  often  return
query  results  wrapped  in  sequence-like  collections.

Thanks to operator overloading, Python offers a rich selection of numeric types, from
the  built-ins  to  decimal.Decimal  and  fractions.Fraction,  all  supporting  infix
arithmetic operators. 