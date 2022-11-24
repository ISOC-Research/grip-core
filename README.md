# GRIP Core Python Package

## Installation

These instructions are specific for an install on FreeBSD

First of all, you need to install PostgreSQL, librrdkafka and cmake:

```
pkg install databases/postgresql15-server
pkg install net/librdkafka
pkg install devel/cmake
pkg install lang/gcc
pkg install math/openblas
```

cmake is needed for installing *py-ninja*, which is a dependency of *scipy* to install later.  GCC is installed because the fortran compiler is needed for the meson build system.

Then create a virtualenv:

```shell
python3 -m venv ./venv
```

Activate it:

```
source ./venv/bin/activate
```

Install the base libraries.  Defining the include and library paths for confluent-kafka is mandatory, as the pip install looks for _librdkafka_ in the wrong place. 

```
setenv C_INCLUDE_PATH /usr/local/include/
setenv LIBRARY_PATH /usr/local/lib/
pip3 install confluent-kafka
```

Then the rest

```
pip3 install scipy
pip3 install -r requirements.pip3.txt
python3 setup.py install
```



