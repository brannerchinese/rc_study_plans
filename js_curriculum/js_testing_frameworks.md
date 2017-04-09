## JS testing frameworks

Initial list was based on [this StackOverflow post](http://stackoverflow.com/questions/300855/javascript-unit-test-tools-for-tdd) (dated 2011 but updated 2017; accessed 20170409).

I prefer to avoid BDD syntax, and also highly ramified assertion-keywords — rather than calling `notEqual`, I rather assert an inequality.

### To look into

 * [UnitJS](http://unitjs.com/): Documentation looks good. Has a number of discrete "asserters" (separate key words for different test styles). 

 * [SinonJS](http://sinonjs.org/): Documentation looks terse but serious. Syntax has separate key words for different test styles.

### Not enthusiastic

 * [Buster.js](http://busterjs.org/): Documentation looks good. Ramified assertion-keywords.
 
 * [QUnit](http://qunitjs.com/): Originally part of JQuery, but now runs standalone. Ramified assertion-keywords.

 * [Jasmine](http://jasmine.github.io/): Apparently uses BDD.

 * [Mocha.js](https://mochajs.org/): Apparently uses BDD.

 * [Karma](http://karma-runner.github.io): Derived from Angular. Website doesn't seem to have a clear link to syntax-documentation, and from a screenshot there appears to be Rspec-based syntax.

### Terminology

 * BDD: Gherkin/Rspec-like syntax. Stands for "behavior-driven development".

[end]