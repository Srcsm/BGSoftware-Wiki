# Expressions
Expressions consist of **conditions** and **getting** or **setting values**! There are a variety of conditions, and you as the configurator have many expressions to work with.

Look at the tab on the left, to select different type of expressions.

### Syntax
Within the scripting system, you can format it very similarly to code, so if you come from a background of code, this will be fairly easy for you.

* You're able to to use expressions inside of expressions.<br>
  **Example:**
```yaml
requirement:
    "moneyxp requirement":
        display: 'XP based on Money'
        value: 'random num between {{get balance of %prisoner%}*2} and {{get balance of %prisoner%}*5}'
        getter: 'get xp of %prisoner%'
        checker: '%getter% is more than or equal to %value%'
        taker: 'take %value% from %prisoner% balance'
```

* You're able to use Math (explained [here](superiorprison/scripting/maths))
* You're able to use a variety of expressions with your script (look under the Expressions tab)
