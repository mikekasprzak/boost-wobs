# Boost without Bullshit (boost-wobs)
An open source hack by Mike Kasprzak.

Boost without Bullshit is exactly what it says: a subset of Boost, without the BS. No configuration, no fat, add it directly to your project, and done. Where possible, the goal is to tweak the Boost headers so they don't require any external dependencies (config, workarounds, etc). The changes should be minimal, making it easier to upgrade components to newer versions.

This project exists because many developers (including myself) hate boost. It's arguably one of the most popular C++ libraries, full of useful little modules, but the main project is ignorant of the idea that a module should be self sufficent: When you include something, you often get more than what you asked for.


Here's what's included:

### operators.hpp
* http://www.boost.org/doc/libs/1_57_0/libs/utility/operators.htm
* No dependencies
* Exactly the same as what's documented, except boost iterators are not supported.

