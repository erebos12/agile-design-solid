# SOLID

## Single Responsibility Principle
- Related concepts:
  - Coupling - Coupling refers to how inextricably linked different aspects of an application are
  - Cohesion - Cohesion refers to how closely related the contents of a particular class or package may be. For more details [Cohesion metrics][bef0d6a2]
  - Do-One-Thing-Rule (DOT-Rule) - A module i.e. function or class should only do one thing!

  [bef0d6a2]: https://www.aivosto.com/project/help/pm-oo-cohesion.html "Cohesion metrics"

### GOD classes

The most effective way to break applications it to create _**GOD classes**_.
That are classes that keeps track of a lot of information and have several responsibilities.
One code change will most likely affect other parts of the class and therefore indirectly all other classes that uses it.
That in turn leads to an even bigger maintenance mess since no one dares to do any changes other than adding new functionality to it.

### How to Recognize a Break of the SRP?

#### Method/constructor Has Too Many Parameters
Too many paramaters are passed to constructor or method.

**Method arguments come in various flavours: Niladic, Monadic, Dyadic & Triadic**

  - Niladic - The method contains no arguments, this one can be easy understand, for example, Java's `toString()` method
  - Monadic - The method contains a single argument. Java's base class `Object.equals(Object obj)`
  - Dyadic  - A method with 2 arguments, for example the String method replace....... replace(char oldChar, char newChar).
  - Triadic - Method with 3 arguments. Example StringBuffer's replace method.... `replace(int start, int end, String str)`
  - Polyadic - A method that for some reason has more than 3 arguments

**_AVOID POLYADICS! TRIADICS JUST IN EXCEPTIONS!_**

#### The Test Class Becomes Too Complicated
If the test has too many variants, it might suggest that the class has too many responsibilities. It might suggest that some methods do too much.


#### Class / Method is Long
If a method is long, it might suggest it does too much. Same goes for a class.
My rule of thumb:
  - A class should not exceed 50-70 LOC. Imports included ;-)
  - A method should not exceed 10-20 LOC.

**When you think a class/method is small, it must be smaller!**


#### Descriptive Naming
If you need to describe what your class / method / package is doing with the AND/OR world, it probably breaks the SRP.
Example is a class that registers a user and send an email (class name would be `register_user_AND_send_email`)

**When you need AND/OR to describe a class or method, it breaks SRP!**

#### Class With Low Cohesion
Cohesion is an important topic of its own and should have its own post. But Cohesion and SRP are closely related and it is important to mention it here.
In general, if a class (or module) is not cohesive, it probably breaks the SRP. A hint for a non-cohesive class:
The class has two fields. One field is used by some methods. The other field is used by the other methods.


#### Change In One Place Breaks Another
If a change in the code to add a new feature or simply refactor broke a test which seems unrelated, it might suggest a breaking the SRP.

#### Shotgun Effect
If a small change makes a big ripple in your code. If you need to change many locations it might suggest, among other smells, that the SRP is broken.
