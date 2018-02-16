# Protocol Buffers - Usage and example code

This tutorial comes from [Protocol Buffers Website](https://developers.google.com/protocol-buffers/)

This directory contains example code that uses Protocol Buffers to manage an
address book. Two programs are provided for each supported language. The
add_person example adds a new person to an address book, prompting the user to
input the person's information. The list_people example lists people already in
the address book. The examples use the exact same format in all three languages,
so you can, for example, use add_person_java to create an address book and then
use list_people_python to read it.

These examples are part of the Protocol Buffers tutorial, located at:
  https://developers.google.com/protocol-buffers/docs/tutorials

## Running protobuf on BU remote.cs machines

We'll be using Protocol Buffers 3.5.1. It is already installed in my home
directory. This installation includes the protocol compiler (the protoc binary)
and the protobuf runtime for the 3 languages that we use - C++, Java and Python.

_Note: Please read the Protocol Buffers tutorial on above link to get better idea._

Similar to Apache Thrift, you need to specify environment variables at compile and runtime.
* Protobuf binary:
```bash
export PATH=/home/vchaska1/protobuf/bin:$PATH
```
The protocol compiler (protoc) binary is present at this location. It is required to
generate code from .proto files.

* Protobuf package configuration file:
```bash
export PKG_CONFIG_PATH=/home/vchaska1/protobuf/lib/pkgconfig
```


### C++

First, add the C++ runtime libraries to LD_LIBRARY_PATH variable.
```bash
export LD_LIBRARY_PATH=/home/vchaska1/protobuf/lib
```

Then run "make cpp" in this directory to build the C++ example. It
will create two executables: add_person_cpp and list_people_cpp. These programs
simply take an address book file as their parameter. The add_person_cpp
programs will create the file if it doesn't already exist.

To run the examples:

    $ ./add_person_cpp addressbook.data
    $ ./list_people_cpp addressbook.data

### Python (Incomplete)

Add the following two lines at the beginning of your Python code.
```python
import sys
sys.path.append('/home/phao3/protobuf/protobuf-3.4.0/python')
```

Make sure to add these lines before any protobuf related imports.

Then run "make python" to build two executables (shell scripts actually):
add_person_python and list_people_python. They work the same way as the
C++ executables.

To run the examples:

    $ ./add_person_python addressbook.data
    $ ./list_people_python addressbook.data

### Java

Set the following CLASSPATH environment variable for runtime protobuf class
discovery:
```bash
export CLASSPATH=/home/vchaska1/protobuf/protobuf-java-3.5.1.jar
```

Then run "make java". This will create the add_person_java/list_people_java
executables (shell scripts) and can be used to create/display an address book
data file.

To run the examples:

    $ ./add_person_java addressbook.data
    $ ./list_people_java addressbook.data


Observe that the C++, Python, and Java examples in this directory run in a
similar way and can view/modify files created by other languages and vice
versa.
