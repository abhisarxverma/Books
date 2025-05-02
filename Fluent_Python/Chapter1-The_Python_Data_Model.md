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


## **How Special Methods Are Used**
