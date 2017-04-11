## JS syntax

 * `...`: "spread" operator, for unpacking multiple elements (like Python `*`)
 * equivalent of Python `range(n)`: [...Array(n).keys()]
 * `new`: In creating a new empty string or array, I like using Native wrapper objects rather than literals (`Array()` rather than `[]`) for readability. But I wonder whether it is better to use the keyword `new` or not. Is there a difference between these two things?

   ```js
   s1 = new String();
   s2 = String();
   ```

   The completion values of these two statements are slightly different:

   ```js
   >> s1 = new String()
   ⬅ String { "", 1 more… }
   >> s2 = String()
   ⬅ ""
   ```

   `typeof(s1)` returns `"object"`, while `typeof(s2)` returns `"string"`. They seem to have the same properties, but the `__proto__` property on `s2` has no properties of its own, unlike that of `s1`. So it seems that the unique effect of using `new` is to instantiate a fully reproducible `String`.

[end]
