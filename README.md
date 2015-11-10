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

For your script "target.py" to be profilable by easy_profile.py, you need to implement a main(argv=None) function in your "target.py" script, and it needs to be able to parse string arguments. An example of a typical script with a profilable main() function:

    import shlex

    def main(argv=None):
        if argv is None: # if argv is empty, fetch from the commandline
            argv = sys.argv[1:]
        elif isinstance(argv, basestring): # else if argv is supplied but it's a simple string, we need to parse it to a list of arguments before handing to argparse or any other argument parser
            argv = shlex.split(argv) # Parse string just like argv using shlex

        # Constructing the parser
        desc = '''Your script description'''
        ep = ''' '''
        main_parser = argparse.ArgumentParser(add_help=True, description=desc, epilog=ep, formatter_class=argparse.RawTextHelpFormatter)
        # Defining arguments
        main_parser.add_argument('-i', '--input', metavar='/path/to/root/folder', type=is_dir, nargs=1, required=True,
                            help='Path to the root folder from where the scanning will occur.')

        # Parsing the arguments (formatted in a list)
        args = main_parser.parse_args(argv) # Storing all arguments to args

        # ... rest of your script here ...

    # Calling main function if the script is directly called (not imported as a library in another program)
    if __name__ == "__main__":
        sys.exit(main())

In fact, making your script profilable is in other words making your script importable by any other Python script.

About direct usage of the profilers without using easy_profiler.py, you can check the sourcecode to see the comments. More usage information will maybe be provided in this readme in the future (when I've got some spare time).

Todo
----
- Look at emulation profilers, so that we don't need to run the application fully to profile it. For example: https://github.com/radical-cybertools/radical.synapse
- Add "program slicing" libraries (both statical and dynamical)? http://en.wikipedia.org/wiki/Program_slicing
- Add coverage? http://nedbatchelder.com/code/coverage/
- https://github.com/tobami/codespeed
- https://github.com/pydata/vbench
- https://github.com/bdarnell/plop
