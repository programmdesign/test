==============================
No Exception Type(s) Specified
==============================
PyLint:W0702

A catch-all exception clause was encountered. A catch-all exception clause is one that
does not specify the type of exception(s) to catch.

Description
===========

In general, an exception clause should be as specific as possible. Exception clauses should only be used for scenarios that the program can actually handle. This implies that the program knows the types of exceptions that can be raised and has prepared for each exception in advance (via an exception clause tailored for that particular situation).

However, in practice it is sometimes useful to implement a catch-all exception clause for general error handling. For example, an application that interacts with a database may use a catch-all exception clause to attempt to roll back the system to a safe state. For another example, a module that interacts with a large codebase (and therefore cannot predict all possile exception scenarios) may use the catch-all exception for logging unanticipated errors.

Example
=======

The following code snippet uses a catch-all exception to handle the division by zero error. This violates the general best practice in programming of making exceptions as specific as possible.

.. code:: python

    import sys
    (x, y) = (5, 0)
    try:
        z = x / y
    except: # Catch-all exception clause
        e = sys.exc_info()[0]
        print("Unexpected Exception:", e) // Prints "Exception: ZeroDivisionError"

Solution
========

Make the exception clause as specific as possible. In the case of this example, use the built-in Python exception "ZeroDivisionError" to handle the division by zero exception. Note that the code still uses a catch-all exception for general reporting purposes.

.. code:: python

    import sys
    (x, y) = (5, 0)
    try:
        z = x / y
    except ZeroDevisionError:
        print "Expected Exception: Divide By Zero"
    except: # Catch-all exception clause
        e = sys.exc_info()[0]
        print("Unexpected Exception:", e) // Prints "Exception: ZeroDivisionError"

References
==========

_"Handling Exceptions" - Python Software Foundation Wiki:https://wiki.python.org/moin/HandlingExceptions

_"W0702" - PyLint Messages Wiki:http://pylint-messages.wikidot.com/messages:w0702

_"Catch What You Can Handle" - Cunningham & Cunningham:http://c2.com/cgi/wiki?CatchWhatYouCanHandle

_"Built-In Exceptions" - Python 2.7.8 Documentation:https://docs.python.org/2/library/exceptions.html
