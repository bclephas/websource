Connascence of Timing
########################

:strength: 60
:slug: timing
:summary: Connascence of timing is when the timing of the execution of multiple components is important.

Connascence of timing is when the timing of the execution of multiple components is important.

.. code-block:: python

    import threading

    # shared variable
    count = 0

    def add_value():
        global count
        for i in range(0, 100000):
            count += 1

    def sub_value():
        global count
        for i in range(0, 100000):
            count -= 1

    if __name__ == '__main__':
        t1 = threading.Thread(target=add_value)
        t2 = threading.Thread(target=sub_value)
        t1.start()
        t2.start()

        t1.join()
        t2.join()

        # expected result is 0
        print count

Multiple invocations show the following result:

.. code-block:: shell

    $ python2 cot.py
    -5700
    $ python2 cot.py
    -3164
    $ python2 cot.py
    10665
    $ python2 cot.py
    -2505
    $ python2 cot.py
    -490

