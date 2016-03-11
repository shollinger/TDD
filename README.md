Benefits
------------------------------------------------------------------

- Automated tests at build-time to ensure new builds and releases contain code that's working.
- Know all the requirements of the unit.
- Know immediately if modified code breaks another requirement of the unit.
- Can sleep at night knowing the code is working as you expect!
- Can easily reason about how to write tests.
- Write testable code!


Write Test Spec
------------------------------------------------------------------

- Model System's Units

- Create Unit Shell
-- Empty block in all public-facing functions

- Dependencies
-- What is this unit doing?  What does it need to do it's job (no more, no less).  Only the direct interfaces, not the dependency's dependencies.
-- Mock dependencies, allowing for control of how they interact with the unit (what they return when the unit uses them)
-- Often good to create an initialization function that accepts dependencies as arguments.  This allows you to easily mock them and spy on their functions

- Create Test Shells
-- Test name: <unit> <does something> <when something> OR <when something>, <unit> <does something>
-- Use 'describe' to organize tests in a consistent way.  I like 'happy path', 'error handling', 'edge cases'

- Test Reset Function
-- beforeEach
-- Create unit and dependency varibles, and initialize them
-- Some dependencies will be modified in each test along with the input, to cover each test scenario.

- Input generating functions

-- Sometimes a common 'expects' function is appropriate.  If you want a set of tests to behave the same way over a set of given inputs (e.g. error handling), and/or there are common things to check between tests, even if there are others scenarios each individual test will check for.

-- Go through each test, 1 by 1, and fill them in
-- Set up input and dependency states (if needed)
-- Set up spys (if needed)
-- Run the module function you're testing with the given input
-- Call expects for the scenario you're testing

- Other Notes
-- As you write tests, you'll notice where you have clean interfaces (easy to mock what the unit needs) and where units are too coupled or complicated (unnecessary dependencies, hard to spy on functions, unable to be deterministic about results)

//////////// HAVE A BEER ////////////


Write Unit Code
--------------------------------------------------------------------

** Run the entire test suite - ALL TESTS WILL FAIL! This is good - we want to know our code is making things better.
** Turn on file watcher
** 1 test at a time, fill in the code until the test passes.  Don't forget good code design!
-DRY
-SLAP
-Style Guide
-Logging
** When all tests pass, YOU'RE DONE! Now you know the unit is doing what you'd expect and you can use the unit in another place.


** Other Notes
- If you really think the test should pass based on what you coded, make sure the test is set up correctly- Controller unit will likely just want to make sure each unit is being used properly - don't 'dig into' the unit because you'll end up duplicating testing effort.
