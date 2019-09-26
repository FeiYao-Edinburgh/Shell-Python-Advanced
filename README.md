This repository will mainly contain notes that I further enhance my programming capabilities using Python and Shell. Meanwhile, it also contains good resources for absolutely beginners that I will also expplore over and over again.



### Excuting a script, either Shell or Python
Supposing you have the following two *hello world* scripts named *helloworld.sh* and *helloworld.py* written in Shell and Python, respectively, you have two ways of excuting them. For convenience the first method, namely `bash helloworld.sh` or `python helloworld.py`, is recommended as long as the paths of `bash` and `python` interpreters are contained in `$PATH`.
```
echo "Hello World"
```
```
print("Hello World")
```
As an alternative, you can also add one line of code to the first line of the scripts shown above, make the scripts executable by `chmod u+x helloworld.sh` and `chmod u+x helloworld.py`, and run them directly by `./helloworld.sh` and `./helloworld.py`.
```
#!/usr/bin/bash
echo "Hello World"
```
```
#!/exports/csce/datastore/geos/users/s1855106/miniconda/base/envs/geo/bin/python
print("Hello World")
```
The `#!` character sequence is, in fact, a special construct called a shebang. The shebang is used to tell the system the name of the interpreter that should be used to execute the script that follows. You can use `which bash` or `which python` to show the location of your interpreters. For each language, you might have several interpreters at the same time. For example you might also have another `bash` in `/bin/bash`.

### Advanced topics of Python
1. **`sys.stdout.write()` vs. `print()`**. While `print(obj)` has become a function in Python 3.x, it calls `sys.stdout.write(obj+'\n')` for the most of the time. I personally regard `sys.stdout.write()` something like `printf()` function in C language. With `sys.stdout.write()` you can achieve more like [displaying progress](https://github.com/FeiYao-Edinburgh/Shell-Python-Advanced/blob/master/Scripts/sys_stdout_write.py).
2. Determine the location of a package by printing the package's \_\_file\_\_ attribute, e.g. `import minisom; print(minisom.__file__)`, then we can change the original codes if applicable.
3. In Python 3, taking quotient and remainder has become `//` and `%`. `/` will always return numbers with decimals.
4. `try/except/else/finally` in Python 3. This [link](https://www.cnblogs.com/windlazio/archive/2013/01/24/2874417.html) greatly explains the logical sequence of `try/except/else/finally`. We can also use `raise` statement to raise an error mandatorily so as to achieve some of the effects that we want. Note that `raise` must be followed by an `Exception` class, for convenience, we can just use `Exception`. See [my script](https://github.com/FeiYao-Edinburgh/Shell-Python-Advanced/blob/master/Scripts/try_except_else_finally_raise.py) for more details.
5. `with` in Python 3.

### Advanced topics of Shell
1. When you cannot terminate a process by `Ctrl-C`, you can use `Ctrl-Z` to stop the command first, then use `jobs` to obtain its jobspec, finally use `kill -9 %jobspec` to kill it.
2. Short-cuts in Terminal to make life easier: Ctrl-left/right arrows to move between words quickly. Middle mouse button for quick copy and paste.
3. Short-cuts in Vim to make life easier: Ctrl/Shift-left/right arrows to move between words quickly. Visual code, v+left/right/up/down arrows to select a part of contexts, or Shift-v to select the whole line, then d for cut or y for copy, finally p for paste.
4. Double and single quotes functions differently when doing expansions, considering the following. Single quotes are more powerful. It is always a good habit to avoid having spaces or special characters in filenames.
```
echo text ~/*.txt {a,b} $(echo foo) $((2+2)) $USER # All will be expanded.
echo "text ~/*.txt {a,b} $(echo foo) $((2+2)) $USER" # $(echo foo) $((2+2)) $USER will still be expanded.
echo 'text ~/*.txt {a,b} $(echo foo) $((2+2)) $USER' # None will be expanded.
```
Nevertheless, if we assign a double or single quoted string with `*` to a variable, we can expand it again using `$`, considering the following.
```
a='*.csv' # This is similar to a=*.csv or a="*.csv", and hence $a is exactly *.csv.
echo $a # *.csv will be expanded and printed.
echo "$a" # Double quotes do not work for $ and hence it first becomes "*.csv". However, double quotes do work for * and hence *.csv printed eventually.
echo '$a' # Single quotes do not work for $ and hence $a printed directly.
```
5. Following 4, read more about variables.
6. Use bc to do math calculation in Terminal including floating numbers.
```
echo "9.45 / 2.327" | bc
echo "9.45 / 2.327" | bc -l
```

Do in a later time: locals(), \*arg, \*\*kwarg, and etc. in [Python Tips](https://book.pythontips.com/en/latest/#); \_\_file\_\_, \_\_doc\_\_, \_self, and etc. in [Python module slides](https://github.com/FeiYao-Edinburgh/Shell-Python-Advanced/blob/master/Slides/Python%E7%BC%96%E7%A8%8B%E5%9F%BA%E7%A1%80%EF%BC%8820140317%EF%BC%89.pdf).

-Fei (17/9/2019 @Edinburgh)

