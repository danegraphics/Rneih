# Rneih
Rnieh (pronounced "Renée") is an optimized keyboard layout designed for minimal strain and comfortable typing.

<p align="center">
<img width="675" height="191" alt="RneihLayout" src="https://github.com/user-attachments/assets/37ffaddb-ff5b-4c33-9516-46fd3089fef9" />
</p>

Written out:

```
X B W G V J Q U Y ; [ ]
 S O A T D R N E I H /
  Z K F P C L M , . '
```

# Design Considerations
The keyboard follows the Colemak philosophy of keeping alphabet keys in the same region as qwerty, but swapping the two right pinky keys to put an alpha character on the home row and the `;` key above it.

With the character region decided, a hill climbing algorithm, weighted by individual character and bigram frequencies in English, was used to find layouts that optimized for the following properties:

- Minimal finger travel/strain.
- More common characters on stronger fingers and easier to reach keys.
- Minimize using the same finger twice in a row on different keys.
- Minimize jumping from top-to-bottom rows (and vice versa) on the same hand.
- Minimize switching hands.
- When using the same hand, prefer rolling inward more often than outward.
- When a middle column character is being used, prefer to switch hands instead of rolling.
- When two keys are hit by the same hand, the outer key should be on a higher row or in-line with the inner key.
- Because punctuation is on the right hand, prefer to end words on the left hand.
- The center key of the bottom row can be hit by either index finger, not just the left.

After many, *many* iterations (from thousands of randomized starting points to avoid local minimums), various tweaks to weights, and manual testing of several resulting layouts, the winning layout is as seen above.

A final manual swap of the `/` and `'` keys was done primarily to minimize accidentally hitting the `enter` key when using apostrophes, a frequent problem in chat appliations. Also it's just a better placement given how frequently the `'` key is used.

After running the hill climbing algorithm thousands of times, a clear patten emerged among the local minimum layouts. In more than half of all candidates, the right hand home row was `RNEIH`, hence the name of the layout.

# Limitations

### English 
Designing for other or multiple languages would require an entirely different dataset for letter and bigram frequencies, potentially even completely different character sets. I'm not even sure if multilanguage arrangements are viable outside of closely related language families.

### Not Quite For Ortholinear, Column-Staggered, or Separated Keyboards
This keyboard was designed with the standard staggered layout in mind. This especially applies to the middle key of the bottom row, equidistant from both index fingers, which is considered by the evaluation algorithm to be usable by *either* index finger in any context.

However, I did test setting that key to left-hand only (as would be in ortholinear or separated "ergonomic" keyboards), and the algorithm actually gave the same layout, just with a different score, so it's possible this layout works with such keybaords as well. The only real issue I found with it is `CT` and `TC` combinations, which you *could* potentially roll-type by using the middle finger on `T`, but whether you're okay with that is up to you.

### Punctuation Heavy Right Hand
It felt awkward for me to stuff punctuation in the middle of the alpha characters, and I actually enjoy the punctuation where it is now (mostly), so I committed to the same alpha character region as Colemak. Though I may consider other punctuation layours in the future, especially if I get into more ergonomic layouts.

### Not For Smartphones
Designing for smartphones is an entirely different challenge. Rolling obviously doesn't work on a smartphone keyboard, so alternating is significantly preferable, among other considerations like thumb hover position and so on.

### No Thumb Keys
Given the constraint to stay within the standard alphabet key region, thumbkeys were not considered.

### Keyboard Shortcuts
Unless it uses `Z`, `M`, `,`, or `.`, keyboard shortcuts are going to be different. While I did consider Colemak's philosophy of trying to keep the important shortcuts in the same place, I felt that constraint would be too limiting for my goals here. However, I may revisit that idea in the future.

### Right Pinky Usage
Given how rarely the right pinky is used on a qwerty layout, I imagine it can be difficult to get used to. While that isn't an issue with training and practice, it is something to consider before switching to this layout, especially since it was given the letter `H` of `TH` fame.

### Personal Biases
Obviously, my personal biases are baked into this layout. The finger strain weights are manually calibrated to fit my personal experience with which keys are easier or harder to press. In fact, all property weights were manually calibrated based on what I felt was more important or resulted in the most comfortable typing experience for me.

There are many other possibilities for what properties should be considered or weighted when evaluating a keyboard layout. For example: Should pinky-to-ring combinations be discouraged? Is the top row preferable to the bottom row? On which fingers? Are adjacent finger combos better or worse than separated finger combos? Should I balance how often each finger is used? And so on...

The properties I selected for are simply the ones that I personally care about and was able to identify while designing the evaluation script.
