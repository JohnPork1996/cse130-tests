# Assignment 2 Resources

This directory contains resources for assignment 2:

* `bin/` A directory containing a library of helper functions.

* `test_scripts/` A directory containing test scripts for evaluating your
  assignment.

* `Makefile` A Makefile for building your program and all of its dependencies.

* `httpserver.c` A starter code template that you can use for your assignment.

* `debug.h` Templates for printing formatted debug messages.

* `load_repo.sh` A script that can be used to load your asgn2 for testing.

* `protocol.h` A set of regex patterns that can be used for parsing HTTP requests.

* `test_repo.sh` A script that can be used to test your repository.

In the instructions that follow, `{path_to_asgn2_dir}` is the path to
your `asgn2` directory.

Finally, our tests require that you have another package in your
system, named `net-tools`.  To install it, run:

```
sudo apt install net-tools
```

## Using these Resources

1. Copy the tests and helper functions to your repository using the supplied `load_repo.sh`
   script:

```
./load_repo.sh {path_to_asgn2_dir} {bin_type}
```

where `{path_to_asgn2_dir}` is the path to your asgn2 directory.

and `{bin_type}` will be one of [`x86-64` or `arm64`]

2. Go to your `asgn2` directory:

```
cd {path_to_asgn2_dir}
```

3. Make your httpserver binary:

```
make
````

4. execute `test_repo.sh`:

```
./test_repo.sh
```

This command will print out each test and whether it passed or failed.
If the test passed, you will see a message saying "SUCCESS"; if it
fails you will see a message saying "FAILURE".

You can count the number of correct tests by executing:

```
./test_repo.sh | grep "SUCCESS" | wc -l
```

If the output is 14, then you've passed all of our public tests. Note that there are several additional hidden tests that will be run for your final submission along with the public tests. The autograder will give you a one-sentence description of what each test does along with indicators if they passed or not. You are recommended to reuse and modify the public tests to look for edge cases that may be tested as part of the hidden tests.

You can execute each
test individually as well.  For example, to execute the test
`test_scripts/test_xxx.sh`, run:

```
./test_scripts/test_xxx.sh
```

Make sure that you comment out the line `cleanup $new_files` at the bottom of
the test script that you are running in order to see the output files that are
generated.

### Using the Helper Functions:

You can use the header file, `asgn2_helper_funcs.h`, in the same way
that you would use any other header.  You can use the static library,
`asgn2_helper_funcs.a`, like you would an object file.  That is, when
you build your final executable you will include it in the command
line.  For example, to to build your program, `httpserver`, using your
`httpserver.c` file and the `asgn2_helper_funcs.a` library, you would
execute:

```
clang -o httpserver httpserver.c asgn2_helper_funcs.a
```

### Using the Starter Code:

You can use the code that we have provided in `httpserver.c`. This program consists of a simple main function that creates a listener socket and accepts connections on the port provided. It then calls an empty function called `handle_connection` with the connection fd created by the socket accept function. The `handle_connection` function simply closes the `connfd` and returns immediately.
<br>
<br>
If you decide to use this code then you will need to add to the `handle_connection` function and create other functions that your server will use.
<br>
<br>
We intend for this code to serve as a good entry point into this assignment and show you that modularization is a good idea. Functions should not contain a lot of code, and if you find yourself writing code that is repeated or extensive then you should break it out into more functions. We also suggest that you split your code among multiple files. There is no limit to the number of `.c` and `.h` files that you can have in your repo. Doing this will make debugging significantly easier.
