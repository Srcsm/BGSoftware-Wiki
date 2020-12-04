# Conditions

<hr style="border-bottom: 1.75px solid darkgray;width:75%">

<!-- Generated with SP Table Generator -->
#### LESS THAN
<div style="margin-top:-19px">Compare two numbers, where value 1 is less than value 2</div>
<div class="superiorprison-clean-table">

|||
|-|-|
|Category|Conditions|
|Syntax|`%getter% is less than %value%`|
|Example|<pre v-pre data-lang="yaml" style="padding:0px;background-color:#fff"><code style="padding:0px;background-color:#fff" class="lang-yaml"><br>  <span class="token key atrule">requirements</span><span class="token punctuation">:</span><br>    <span class="token key atrule">"eco requirement"</span><span class="token punctuation">:</span><br>      <span class="token key atrule">display</span><span class="token punctuation">:</span> <span class="token string">'Money'</span><br>      <span class="token key atrule">value</span><span class="token punctuation">:</span> <span class="token string">'50% of {%index% * 200}'</span><br>      <span class="token key atrule">getter</span><span class="token punctuation">:</span> <span class="token string">'{get balance of %prisoner%}'</span><br>      <span class="token comment"># You can also use '<' instead of 'is less than'.</span><br>      <span class="token key atrule">checker</span><span class="token punctuation">:</span> <span class="token string">'%getter% < %value%'</span><br>      <span class="token key atrule">taker</span><span class="token punctuation">:</span> <span class="token string">'take %value% from %prisoner% balance'</span><br>  </code></pre>|

</div>
<hr style="border-bottom: 1.75px solid darkgray;width:75%">

<!-- Generated with SP Table Generator -->
#### MORE THAN
<div style="margin-top:-19px">Compare two numbers, where value 1 is more than value 2</div>
<div class="superiorprison-clean-table">

|||
|-|-|
|Category|Conditions|
|Syntax|`%getter% is more than %value%`|
|Example|<pre v-pre data-lang="yaml" style="padding:0px;background-color:#fff"><code style="padding:0px;background-color:#fff" class="lang-yaml"><br>  <span class="token key atrule">requirements</span><span class="token punctuation">:</span><br>    <span class="token key atrule">"eco requirement"</span><span class="token punctuation">:</span><br>      <span class="token key atrule">display</span><span class="token punctuation">:</span> <span class="token string">'Money'</span><br>      <span class="token key atrule">value</span><span class="token punctuation">:</span> <span class="token string">'50% of {%index% * 200}'</span><br>      <span class="token key atrule">getter</span><span class="token punctuation">:</span> <span class="token string">'{get balance of %prisoner%}'</span><br>      <span class="token comment"># This will check if the balance is more than the required value that we specified in 'value'</span><br>      <span class="token key atrule">checker</span><span class="token punctuation">:</span> <span class="token string">'%getter% is more than %value%'</span><br>      <span class="token key atrule">taker</span><span class="token punctuation">:</span> <span class="token string">'take %value% from %prisoner% balance'</span><br>  </code></pre>|

</div>
<hr style="border-bottom: 1.75px solid darkgray;width:75%">

<!-- Generated with SP Table Generator -->
#### LESS THAN OR EQUAL TO
<div style="margin-top:-19px">Compare two numbers, where value 1 is less than or equal to value 2</div>
<div class="superiorprison-clean-table">

|||
|-|-|
|Category|Conditions|
|Syntax|`%getter% is less than or equal to %value%`|
|Example|<pre v-pre data-lang="yaml" style="padding:0px;background-color:#fff"><code style="padding:0px;background-color:#fff" class="lang-yaml"><br>  <span class="token key atrule">requirements</span><span class="token punctuation">:</span><br>    <span class="token key atrule">"eco requirement"</span><span class="token punctuation">:</span><br>      <span class="token key atrule">display</span><span class="token punctuation">:</span> <span class="token string">'Money'</span><br>      <span class="token key atrule">value</span><span class="token punctuation">:</span> <span class="token string">'50% of {%index% * 200}'</span><br>      <span class="token key atrule">getter</span><span class="token punctuation">:</span> <span class="token string">'{get balance of %prisoner%}'</span><br>      <span class="token comment"># This will check is the balance of the prisoner is less than or equal to the value.</span><br>      <span class="token key atrule">checker</span><span class="token punctuation">:</span> <span class="token string">'%getter% is less than or equal to %value%'</span><br>      <span class="token key atrule">taker</span><span class="token punctuation">:</span> <span class="token string">'take %value% from %prisoner% balance'</span><br>  </code></pre>|

</div>
<hr style="border-bottom: 1.75px solid darkgray;width:75%">

<!-- Generated with SP Table Generator -->
#### MORE THAN OR EQUAL TO
<div style="margin-top:-19px">Compare two numbers, where value 1 is more than or equal to value 2</div>
<div class="superiorprison-clean-table">

|||
|-|-|
|Category|Conditions|
|Syntax|`%getter% is more than or equal to %value%`|
|Example|<pre v-pre data-lang="yaml" style="padding:0px;background-color:#fff"><code style="padding:0px;background-color:#fff" class="lang-yaml"><br>  <span class="token key atrule">requirements</span><span class="token punctuation">:</span><br>    <span class="token key atrule">"eco requirement"</span><span class="token punctuation">:</span><br>      <span class="token key atrule">display</span><span class="token punctuation">:</span> <span class="token string">'Money'</span><br>      <span class="token key atrule">value</span><span class="token punctuation">:</span> <span class="token string">'50% of {%index% * 200}'</span><br>      <span class="token key atrule">getter</span><span class="token punctuation">:</span> <span class="token string">'{get balance of %prisoner%}'</span><br>      <span class="token comment"># You can also use >= instead of 'is more than or equal to'</span><br>      <span class="token key atrule">checker</span><span class="token punctuation">:</span> <span class="token string">'%getter% >= %value%'</span><br>      <span class="token key atrule">taker</span><span class="token punctuation">:</span> <span class="token string">'take %value% from %prisoner% balance'</span><br>  </code></pre>|

</div>
<hr style="border-bottom: 1.75px solid darkgray;width:75%">
