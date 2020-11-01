# Maths
You can use math throughout the scripting system in superior prison.

### Operations
<div style="margin-top:-10px">

You're able to add and use math operations. These consist of `+` (Addition), `-` (Subtraction), `*` (Multiplication), `/` (Division), `^` (Exponent), and `{}` (Parentheses, do not use `()`)</div>
<div class="superiorprison-clean-table">

!> **NOTE**: This uses order of operations!<br>For example, `20 - {10 + 9}` is `1`, not `19`!

**Example**:<br>
Here is an example with rank requirements using maths.

```yaml
requirements:
  "eco requirement":
    display: 'Money'
    # Times level x 200, then add 3, and then do that to the power of 3.
    value: '50% of {%index% * 200 + 3}^3'
    # Add 200 to the balance of prisoner
    getter: '{get balance of %prisoner%} + 200'
    checker: '%getter% is equal or more to %value%'
    taker: 'take %value% from %prisoner% balance'
```


<hr style="border-bottom: 1.75px solid darkgray;width:75%">
