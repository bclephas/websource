Connascence of Type
###################

:strength: 10
:slug: type
:summary: Connascence of type is when multiple components must agree on the type of an entity.


Connascence of type is when multiple components must agree on the type of an entity. In a statically typed language, these issues are often (but not always) caught by the compiler. Consider the following trivial C++ code:

.. code-block:: c++

    std::string cost;

    cost = 10.95; // OOPS!

Dynamically typed languages typically suffer from less obvious instances of connascence of type. Consider a function that calculates your age, given your day, month, and year of birth:

.. code-block:: python

    def calculate_age(birth_day, birth_month, birth_year):
        # do the calculation here:

How is this function supposed to be called? Here are a few different options:

.. code-block:: python

    calculate_age(1, 9, 1984)
    calculate_age(1, 9, 84)
    calculate_age('1', '9', '1984')
    calculate_age('1', 'September', '1984')

This can be handled by using statically types structures for languages that
support them:

.. code-block:: c++

    struct date {
        int day;
        int month;
        int year;
    };

    int calculate_age(date date_of_birth) {
        # do the calculation
    }

    date birth_date = {
        .day = 1,
        .month = 9, // "September" results in a compiler error
        .year = 1984
    };

    calculate_age(birth_date);

If the used language does not provide any means of checking types there is
always the option to fall back to reflect the type in the name of the argument:

.. code-block:: python

    def calculate_age(birth_day_asint, birth_month_asint, birth_year_asint):
        # do the calculation here

    def calculate_age(birth_day_asstring, birth_month_asstring, birth_year_asstring):
        # do the calculation here

