Streprogen - the Python strength program generator.
===================================================
.. image:: https://badge.fury.io/py/streprogen.svg
   :target: https://pypi.org/project/streprogen/
   :alt: PyPi
   

.. image:: https://readthedocs.org/projects/streprogen/badge/?version=latest
   :target: http://streprogen.readthedocs.io/en/latest/?badge=latest
   :alt: Documentation Status

 
.. image:: https://travis-ci.com/tommyod/streprogen.svg?branch=master	
    :target: https://travis-ci.com/tommyod/streprogen	
    :alt: Test Status
   

Install locally using ``pip install streprogen``, or run live notebooks online.

Run code in your browser
------------------------

If you don't have Python installed, you can run code in your browser.

Learn how to make strength training programs
********************************************

* Run code live: `Streprogen - Essential Features <https://colab.research.google.com/github/tommyod/streprogen/blob/master/examples/Streprogen%20-%20Essential%20features.ipynb>`_
* Run code live: `Streprogen - Intermediate Features <https://colab.research.google.com/github/tommyod/streprogen/blob/master/examples/Streprogen%20-%20Intermediate%20features.ipynb>`_
* Run code live: `Streprogen - Advanced Features <https://colab.research.google.com/github/tommyod/streprogen/blob/master/examples/Streprogen%20-%20Advanced%20features.ipynb>`_

Example strength training program library
*****************************************

* Run code live: `Example - Beginner 5x5 program <https://colab.research.google.com/github/tommyod/streprogen/blob/master/examples/Example%20-%20Beginner%205x5%20program.ipynb>`_
* Run code live: `Example - Beginner 5x5 program modified <https://colab.research.google.com/github/tommyod/streprogen/blob/master/examples/Example%20-%20Beginner%205x5%20program%20modified.ipynb>`_
* Run code live: `Example - 3 day split with periodization <https://colab.research.google.com/github/tommyod/streprogen/blob/master/examples/Example%20-%203%20day%20split%20with%20periodization.ipynb>`_

Check out the `example PDF output <https://github.com/tommyod/streprogen/blob/master/examples/3DaySplitWithPeriodization.pdf>`_.

Multi-day meal planning with mathematical optimization
******************************************************

* Run code live: `Example - Meal planning <https://colab.research.google.com/github/tommyod/streprogen/blob/master/examples/Example%20-%20Meal%20planning.ipynb>`_


**Instructions for live code:**
Click "*Runtime*", then "*Run all*".
To download a saved file, click on the arrow on the top left, left click the file and "*Download*".
A downloaded ``.html`` file can be printed from your local browser.

Project summary
---------------

Streprogen (short for **stre**\ ngth **pro**\ gram **gen**\ erator) is a
Python_ 3.5+
package which allows the user to easily create dynamic, flexible
strength training programs. The main features are:

* **Sensible defaults**\ : We aim for sensible default values for all input parameters,
  giving the novice strength athlete some guidance on parameter selection.
  The software will raise warnings for unreasonable input parameters, but will still run.
* **High level of customization**\ : Every important parameter can be changed by the user.
  It is possible to create long-term training programs with several layers of periodization
  for advanced planning.
* **Simple interface**\ : The software should be usable even by people with little Python knowledge.
* **Pretty output**\ : Training programs may be saved as ``.txt``, ``.html`` or ``.tex`` files.
  Print it and bring it to the gym.
  
  
.. image:: https://raw.githubusercontent.com/tommyod/streprogen/master/examples/streprogen_overview.png


Installation
------------

Here's the layman guide to installation.

(1) Download Anaconda_ distribution of Python_ 3.x from the Anaconda_ Website.
(2) Install ``streprogen`` from PyPI_.

    (a) **Windows**: Open the Anaconda prompt from the start menu and run
        ``pip install streprogen``.
    (b) **Linux**: Open the terminal and run
        ``pip install streprogen``.

(3) Open a Python Editor (such as Spyder, which comes with Anaconda_).
(4) Copy the example below and run it to get started.


.. _Python: http://www.python.org/
.. _Anaconda: https://www.continuum.io/downloads
.. _PyPI: https://pypi.org/project/streprogen/


Sample code
-----------------

.. code-block:: python

    from streprogen import Program
    
    # Create a 4-week program, rounding every exercise to nearest unit og 5kg
    program = Program("My first program!", duration=8, units="kg", round_to=5)
    
    with program.Day("Day A"):
        program.DynamicExercise("Bench press", start_weight=80, min_reps=3, max_reps=8)
        program.DynamicExercise("Squats", start_weight=100, min_reps=3, max_reps=8)
        
    with program.Day("Day B"):
        program.DynamicExercise("Deadlifts", start_weight=100, min_reps=2, max_reps=7)
        program.StaticExercise("Curls", "3 x 10 @ 18kg")

    # Render the program, then print it
    program.render()
    print(program)


.. code-block::

    ----------------------------------------------------------------
    Program: My first program!
    
    Program parameters
      duration: 8
      reps_per_exercise: 25
      intensity: 80
      units: kg
    ----------------------------------------------------------------
    Exercise information
      Day A
       Bench press    80kg -> 89.6kg 
        reps: [3, 8]   weekly inc.: 1.5%
       Squats        100kg -> 112.0kg
        reps: [3, 8]   weekly inc.: 1.5%
      Day B
       Deadlifts     100kg -> 116.0kg
        reps: [2, 7]   weekly inc.: 2.0%
       Curls         3 x 10 @ 18kg
    ----------------------------------------------------------------
    Program
     Week 1
      Day A
       Bench press   7 x 60kg   6 x 65kg   5 x 65kg   4 x 70kg   3 x 70kg   
       Squats        7 x 75kg   6 x 80kg   5 x 80kg   4 x 85kg   3 x 90kg   
    
      Day B
       Deadlifts     6 x 80kg   6 x 80kg   5 x 80kg   4 x 85kg   
       Curls         3 x 10 @ 18kg
    
     Week 2
      Day A
       Bench press   7 x 60kg   7 x 60kg   7 x 60kg   6 x 65kg   5 x 65kg   4 x 70kg   
       Squats        7 x 75kg   7 x 75kg   7 x 75kg   6 x 80kg   5 x 85kg   4 x 90kg   
    
      Day B
       Deadlifts     6 x 80kg   6 x 80kg   6 x 80kg   6 x 80kg   
       Curls         3 x 10 @ 18kg
    
     Week 3
      ...
       ...
