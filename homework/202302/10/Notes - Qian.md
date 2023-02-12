# Just learned one example about FrenchDeck
FrenchDeck只实现了不可变的序列协议。可变的序列还必须提供 __setitem__ 方法。以下的代码就是实现。

```
# Let a card go to a new position on the deck.
def set_card(deck, position, card):
    deck._cards[position] = card

# Define __setitem__() for FrenchDeck
FrenchDeck.__setitem__ = set_card

# Now, we can shuffle deck.
shuffle(deck)
deck[:5]
```
