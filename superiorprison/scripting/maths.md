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

### Math Expressions
<div style="margin-top:-10px">These are expressions that are math related. </div>

<hr style="border-bottom: 1.75px solid darkgray;width:75%">

<!-- Generated with SP Table Generator -->
#### RANDOM NUMBER
<div style="margin-top:-19px">Generate random number between two numbers</div>
<div class="superiorprison-clean-table">

|||
|-|-|
|Category|Math|
|Syntax|`random num between <num1> and <num2>`|
|Example|<pre v-pre data-lang="yaml" style="padding:0px;background-color:#fff"><code style="padding:0px;background-color:#fff" class="lang-yaml"><br>  <span class="token key atrule">requirements</span><span class="token punctuation">:</span><br>    <span class="token key atrule">"money requirement"</span><span class="token punctuation">:</span><br>      <span class="token key atrule">display</span><span class="token punctuation">:</span> <span class="token string">'Money'</span><br>      <span class="token key atrule">value</span><span class="token punctuation">:</span> <span class="token string">'random num between {%index% * 3} and {%index% * 5}'</span><br>      <span class="token key atrule">getter</span><span class="token punctuation">:</span> <span class="token string">'get balance of %prisoner%'</span><br>      <span class="token key atrule">checker</span><span class="token punctuation">:</span> <span class="token string">'%getter% is greater than %value%'</span><br>      <span class="token key atrule">taker</span><span class="token punctuation">:</span> <span class="token string">'take %value% from %prisoner% balance'</span><br>  </code></pre>|

</div>
<hr style="border-bottom: 1.75px solid darkgray;width:75%">

<!-- Generated with SP Table Generator -->
#### PERCENT
<div style="margin-top:-19px">Get a percent of a number</div>
<div class="superiorprison-clean-table">

|||
|-|-|
|Category|Math|
|Syntax|`<percent> of <number>`|
|Example|<pre v-pre data-lang="yaml" style="padding:0px;background-color:#fff"><code style="padding:0px;background-color:#fff" class="lang-yaml"><br>  <span class="token key atrule">requirements</span><span class="token punctuation">:</span><br>    <span class="token key atrule">"money requirement"</span><span class="token punctuation">:</span><br>      <span class="token key atrule">display</span><span class="token punctuation">:</span> <span class="token string">'Money'</span><br>      <span class="token key atrule">value</span><span class="token punctuation">:</span> <span class="token string">'50% of {%index% + {get xp of %prisoner%}}'</span><br>      <span class="token key atrule">getter</span><span class="token punctuation">:</span> <span class="token string">'get balance of %prisoner%'</span><br>      <span class="token key atrule">checker</span><span class="token punctuation">:</span> <span class="token string">'%getter% is greater than %value%'</span><br>      <span class="token key atrule">taker</span><span class="token punctuation">:</span> <span class="token string">'take %value% from %prisoner% balance'</span><br>  </code></pre>|

</div>
<hr style="border-bottom: 1.75px solid darkgray;width:75%">
