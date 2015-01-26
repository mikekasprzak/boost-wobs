# Boost without Bullshit (boost-wobs)
An open source hack by [Mike Kasprzak](http://twitter.com/mikekasprzak).

Boost without Bullshit is exactly what it says: a subset of Boost, without the BS. No configuration, no fat, add only what you need directly to your project, and done. Ultimately you should be able to pick and choose what parts of Boost you actually need. Where possible, the goal is to tweak the Boost headers so they don't require any external dependencies (config, workarounds, etc).

This project exists because many developers (including myself) hate Boost. It's arguably one of the most popular C++ libraries, full of useful little modules, but the main project is ignorant of the idea that a module should be self sufficent: When you include something, you often get more than what you asked for.


**TIP:** Boost libraries expect to find fellow Boost libraries in include paths like `<boost/mylib.hpp>`, so you're encouraged to place the files under a `/boost/` directory in your project (all lower case), and to add the directory containing the `/boost/` directory to your Library Search Path (`-Lmy/library/path` with GCC and Clang, and `/LIBPATH:my/library/path` with MSVC).


Here's what's currently available:

### boost/operators.hpp
* http://www.boost.org/doc/libs/1_57_0/libs/utility/operators.htm
* Default:
  * No dependencies.
  * No `std::iterator` (boost::iterator) support.
* With `BOOST_OPERATORS_WITH_ITERATOR` defined:
  * Requires `<iterator>` and `<cstddef>`.
  * Everything works as documented, except there is no boost::iterator type (`std::iterator` instead)


Generally, I will only be adding what I use myself, but contributions are welcome. Try to have as few dependencies as possible, yet keep the code as close to the original as you can (for better DIFFs). If something relies on a standard/platform specific library, this is fine, but if a feature does not require a library to be useful, then consider making it optional. If you're changing how something works internerally, leave a note for future maintainers to understand why you did it. The majority of work needed to make Boost libraries a **boost-wobs** library is commenting out redunant includes, changing MSVC checks to directly check `_MSC_VER`, and wrapping optional things in #ifdef blocks.

Add an entry to this file when you add libraries. Link the specific version of documentation for the Boost version used. When updating libraries to newer Boost versions, update the documentation URL. It is fine for libraries to require other Boost libraries, but make sure you list all dependencies here. This README is a reference of what you need to use a library, and what is optional.
