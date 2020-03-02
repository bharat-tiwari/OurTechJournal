# ngForTemp

\*ngFor = built-in directive , used for creating a HTML template by iterating over a collection.

\* character before ngFor =&gt; a shortcut to create a parent template like ”template=ngFor let product of products”.

```javascript
<ul>
  <li *ngFor="let item of cafeMenu">{{ item.name }}</li>
</ul>
```

The above code will yield something like below:

```markup
<ul>
  <li>Tea</li>
  <li>Coffee</li>
  <li>Latte</li>
  <li>Mocha</li>
</ul>
```

\*ngFor also provides a set of few pre-defined constants for each iteration of the for-loop:

* `index` = number =&gt; current iteration's index value
* `first` = boolean =&gt; is it the first iteration?
* `last` = boolean =&gt; is it the last iteration?
* `even` = boolean =&gt; is the current iteration index an even value?
* `odd` = boolean =&gt; is the current iteration index an odd value?

```javascript
<ul>
  <li *ngFor="let item of cafeMenu; let i=index; let isOdd=odd; let isEven=even" [class.oddRow]="isOdd"  [class.evenRow]="isEven" >
    {{i + 1}}. {{ item.name }}
  </li>
</ul>
```

This will generate HTML like below:

```markup
<ul>
  <li class="evenRow">1. Tea</li>
  <li class="oddRow">2. Coffee</li>
  <li class="evenRow">3. Latte</li>
  <li class="oddRow">4. Mocha</li>
</ul>
```

