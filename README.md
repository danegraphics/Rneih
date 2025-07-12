# Rneih
Rnieh (pronounced "Renée") is an optimized keyboard layout designed for minimal strain and comfortable typing.

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

With the character region decided, a hill climbing algorithm, weighted by individual character and bigram frequencies in English, was used to find layouts that optimized for the following properties:

- Minimal finger travel/strain.
- More common characters on stronger fingers and easier to reach keys.
- Minimize using the same finger twice in a row on different keys.
- Minimize jumping from top-to-bottom rows (and vice versa) on the same hand.
- Minimize switching hands. (prefer rolling)
- When a middle column character is being used, prefer to switch hands instead of rolling.
- When rolling (hitting keys with the same hand), roll from pinky-to-index more often than index-to-pinky.
- When two keys are hit by the same hand, the outer key should be above or in-line with the inner key.
- Because punctuation is on the right hand, prefer to end words on the left hand.

After many, *many* iterations (from thousands of randomized starting points to avoid local minimums), various tweaks to weights, and manual testing of several resulting layouts, the winning layout is as seen above.

A final manual swap of the `/` and `'` keys was done primarily to minimize accidentally hitting the `enter` key when using apostrophes, a frequent problem in chat appliations. Also it's just a better placement given how frequently the `'` key is used.

After running the hill climbing algorithm thousands of times, a clear patten emerged among every local minimum layout. In more than half of all candidates, the right hand home row was `RNEIH`, hence the name of the layout.

# Limitations

### English 
Designing for other or multiple languages would require an entirely different dataset for letter and bigram frequencies, potentially even completely different character sets. I'm not even sure if multilanguage arrangements are viable outside of closely related language families.

### Not Ortholinear
This keyboard was designed with the standard staggered layout in mind. This especially applies to the middle key of the bottom row, equidistant from both index fingers, which is considered by the evaluation algorithm to be usable by *either* index finger in any context.

However, I did test setting that key to left-hand only (as would be in ortholinear or separated "ergonomic" keyboards), and the algorithm actually gave the same layout, just with a different score, so it's possible this layout works with ortholinear keybaords as well. The only real issue I found with it is `CT` and `TC` combinations, which you *could* potentially roll-type by using the middle finger on `T`, but whether you're okay with that is up to you.

### Not For Smartphones
Designing for smartphones is an entirely different challenge. Rolling obviously doesn't work on a smartphone keyboard, so alternating is significantly preferable, among other considerations like thumb hover position and so on.

### No Thumb Keys
Given the constraint to stay within the standard alphabet key region, thumbkeys were not considered.

### Personal Biases
Obviously, my personal biases are baked into this layout. The finger strain weights are manually calibrated to fit my personal experience with which keys are easier or harder to press. In fact, all property weights were manually calibrated based on what I felt was more important or resulted in the most comfortable typing experience for me.

There are many other possibilities for what properties should be considered or weighted when evaluating a keyboard layout. For example: Should pinky-to-ring combinations be discouraged? Is the top row preferable to the bottom row? On which fingers? Are adjacent finger combos better or worse than separated finger combos? And so on...

The properties I selected for are simply the ones that I personally care about and was able to identify while designing the evaluation script.
