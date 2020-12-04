# Taker
The taker set or take values of prisoners.

<hr style="border-bottom: 1.75px solid darkgray;width:75%">

<!-- Generated with SP Table Generator -->
#### TAKE MONEY
<div style="margin-top:-19px">Take money from a prisoner's balance</div>
<div class="superiorprison-clean-table">

|||
|-|-|
|Category|Money|
|Syntax|`take <amount> from %prisoner%`|
|Example|<pre v-pre data-lang="yaml" style="padding:0px;background-color:#fff"><code style="padding:0px; background-color:#fff;" class="lang-yaml"><br>  <span class="token key atrule">requirements</span><span class="token punctuation">:</span><br>    <span class="token key atrule">"Money Requirement"</span><span class="token punctuation">:</span><br>      <span class="token key atrule">display</span><span class="token punctuation">:</span> <span class="token string">'Money'</span><br>      <span class="token key atrule">value</span><span class="token punctuation">:</span> <span class="token string">'50% of {%index% * 200}'</span><br>      <span class="token key atrule">getter</span><span class="token punctuation">:</span> <span class="token string">'get balance of %prisoner% balance'</span><br>      <span class="token key atrule">checker</span><span class="token punctuation">:</span> <span class="token string">'%getter% is more than %value%'</span><br>      <span class="token comment"># Take value (50% of the index times 200) from prisoner.</span><br>      <span class="token key atrule">taker</span><span class="token punctuation">:</span> <span class="token string">'take %value% from %prisoner% balance'</span><br>  </code></pre>|

</div>
<hr style="border-bottom: 1.75px solid darkgray;width:75%">

<!-- Generated with SP Table Generator -->
#### SET XP
<div style="margin-top:-19px">Set XP of Prisoner</div>
<div class="superiorprison-clean-table">

|||
|-|-|
|Category|XP|
|Syntax|`set xp of %prisoner% to <amount>`|
|Example|<pre v-pre data-lang="yaml" style="padding:0px;background-color:#fff"><code style="padding:0px;background-color:#fff" class="lang-yaml"><br>  <span class="token key atrule">requirements</span><span class="token punctuation">:</span><br>    <span class="token key atrule">"XP Requirement"</span><span class="token punctuation">:</span><br>      <span class="token key atrule">display</span><span class="token punctuation">:</span> <span class="token string">'XP'</span><br>      <span class="token key atrule">value</span><span class="token punctuation">:</span> <span class="token string">'50% of {%index% * 200}'</span><br>      <span class="token key atrule">getter</span><span class="token punctuation">:</span> <span class="token string">'get xp of %prisoner%'</span><br>      <span class="token key atrule">checker</span><span class="token punctuation">:</span> <span class="token string">'%getter% is more than %value%'</span><br>      <span class="token comment"># Take value from prisoner XP.</span><br>      <span class="token key atrule">taker</span><span class="token punctuation">:</span> <span class="token string">'set xp of %prisoner% to {%getter% - %value%}'</span><br>  </code></pre>|

</div>
<hr style="border-bottom: 1.75px solid darkgray;width:75%">

<!-- Generated with SP Table Generator -->
#### SET XP LEVEL
<div style="margin-top:-19px">Set XP Level of Prisoner</div>
<div class="superiorprison-clean-table">

|||
|-|-|
|Category|XP|
|Syntax|`set xp level of %prisoner% to <amount>`|
|Example|<pre v-pre data-lang="yaml" style="padding:0px;background-color:#fff"><code style="padding:0px;background-color:#fff" class="lang-yaml"><br>  <span class="token key atrule">requirements</span><span class="token punctuation">:</span><br>    <span class="token key atrule">"XPL Requirement"</span><span class="token punctuation">:</span><br>      <span class="token key atrule">display</span><span class="token punctuation">:</span> <span class="token string">'XP Level'</span><br>      <span class="token key atrule">value</span><span class="token punctuation">:</span> <span class="token string">'25% of {%index% * 500}'</span><br>      <span class="token key atrule">getter</span><span class="token punctuation">:</span> <span class="token string">'get xp level of %prisoner%'</span><br>      <span class="token key atrule">checker</span><span class="token punctuation">:</span> <span class="token string">'%getter% is more than or equal to %value%'</span><br>      <span class="token comment"># Take value from prisoner xp level.</span><br>      <span class="token key atrule">taker</span><span class="token punctuation">:</span> <span class="token string">'set xp level of %prisoner% to {%getter% - %value%}'</span><br>  </code></pre>|

</div>
<hr style="border-bottom: 1.75px solid darkgray;width:75%">

<!-- Generated with SP Table Generator -->
#### COMMAND
<div style="margin-top:-19px">Run a command. Note that this formatted a bit differently.</div>
<div class="superiorprison-clean-table">

|||
|-|-|
|Category|Command|
|Syntax|<pre v-pre data-lang="yaml" style="padding:0px"><code style="padding:0px" class="lang-yaml"><br>  <span class="token key atrule">taker</span><span class="token punctuation">:</span><br>    <span class="token key atrule">type</span><span class="token punctuation">:</span> command<br>    <span class="token key atrule">command</span><span class="token punctuation">:</span> <span class="token string">'&lt;command>'</span><br>  </code></pre>|
|Example|<pre v-pre data-lang="yaml" style="padding:0px;background-color:#fff"><code style="padding:0px;background-color:#fff" class="lang-yaml"><br>  <span class="token key atrule">requirements</span><span class="token punctuation">:</span><br>    <span class="token key atrule">"cell back requirement"</span><span class="token punctuation">:</span><br>      <span class="token key atrule">display</span><span class="token punctuation">:</span> <span class="token string">'Cell Bank'</span><br>      <span class="token key atrule">value</span><span class="token punctuation">:</span> <span class="token string">'50% of {%index% ^ 3}'</span><br>      <span class="token key atrule">getter</span><span class="token punctuation">:</span> <span class="token string">'parse %superior_island_bank_raw% placeholder as %prisoner%'</span><br>      <span class="token key atrule">checker</span><span class="token punctuation">:</span> <span class="token string">'%getter% is greater than %value%'</span><br>      <span class="token comment"># Run a command in console</span><br>      <span class="token key atrule">taker</span><span class="token punctuation">:</span><br>        <span class="token key atrule">type</span><span class="token punctuation">:</span> <span class="token string">'command'</span><br>        <span class="token key atrule">command</span><span class="token punctuation">:</span> <span class="token string">'is admin withdraw %prisoner% %value%'</span><br>  </code></pre>|

</div>
<hr style="border-bottom: 1.75px solid darkgray;width:75%">
