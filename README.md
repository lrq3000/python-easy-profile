python-easy-profile
==============
Easy to use profiler libraries for Python (most being pure-python and allowing line-by-line CPU and memory profiling, or with a GUI).

This is mostly a set of scripts containing decorators to easily interface with other libraries I did not make, such as pprofile, memory_profiler and runsnakerun.

This library was initially made for private profiling on one project, but finally I reused them for lots of other projects, thus I figured out they are pretty generic and could be useful for others.

The libraries were made on 2010-09-06, but they are still working as of 2015-03-16.

Install
---------
To install this library, simply copy all the files into a subfolder of your project (you may call it "profilers" or any other name you want), and just import the profiler you want.

Usage
----------
The easiest way to use this library is to use easy_profile.py:

    python easy_profile.py --script target.py --cpu --arg1_of_target_script --arg2_of_target_script ...

More usage information will maybe be provided in this readme in the future (when I've got some spare time).
