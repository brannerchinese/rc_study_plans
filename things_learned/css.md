## Things learned: CSS

 * centering `div`s. There are two principal ways:

   1. inner objects:  

      ```css
      display: block;
      margin: auto;
      width: <actual>;
      ```
      I've thought about supplying the actual width from a measurement of that object itself, in JS.

   1. outer object:

      ```css
      text-align: center;
      ```

      inner object:

      ```css
      display: inline;
      ```

[end]
