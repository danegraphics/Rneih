# Rneih
Rnieh (pronounced "Renée", which means "Reborn") is an optimized keyboard layout designed for minimal strain and comfortable typing.

<p align="center">
<img width="675" height="191" alt="RneihLayout" src="https://github.com/user-attachments/assets/37ffaddb-ff5b-4c33-9516-46fd3089fef9" />
</p>

Written out:

```
XBWGVJQUY;[]
SOATDRNEIH/
ZKFPCLM,.'
```

# Design Considerations
The keyboard follows the Colemak philosophy of keeping alphabet keys in the same region as qwerty, but swapping the two right pinky keys to put an alpha character on the home row and the `;` key above it.

With the character region decided, a hill climbing algorithm, weighted by individual character and bigram frequencies, was used to find layouts that optimized for the following properties:

- Minimal finger travel.
- More common characters on stronger fingers and easier to reach keys.
- Minimize using the same finger twice in a row on different keys.
- Minimize switching hands (switching hands is actually slower than rolling on a single hand)
- When rolling (hitting keys with the same hand), roll from pinky-to-index more often than index-to-pinky.
- When two keys are hit by the same hand, the outer key should be above or in-line with the inner key.
- When a middle column character is being used, prefer to switch hands between characters.
- Because punctuation is on the right hand, prefer to end words on the left hand.

After many, *many* iterations (from thousands of randomized starting points to avoid local minimums), various tweaks to weights, and manual testing of several resulting layouts, the winning layout is as seen above.

A final manual swap of the `/` and `'` keys was done to minimize accidentally hitting the `enter` key when using apostrophes, a frequent problem in chat appliations.

After running the hill climbing algorithm thousands of times, a clear patten emerged among every local minimum layout. In more than half of all candidates, the right hand home row was `RNEIH`, hence the name of the layout.
