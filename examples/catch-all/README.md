# Catch All Example

Demonstrates the use of the `catch_all` option, which will allows any command
to receive an arbitrary list of arguments.

This example was generated with:

```bash
$ bashly init
# ... now edit src/bashly.yml to match the example ...
$ bashly generate
```

-----

## `bashly.yml`

````yaml
name: download
help: Catch All Example
version: 0.1.0

# Enable catch_all for the root command
catch_all: true

args:
- name: message
  required: true
  help: Message

flags:
- long: --debug
  short: -d
````



## Output

### `$ ./download`

````shell
missing required argument: MESSAGE
usage: download MESSAGE [OPTIONS] [--] [...]


````

### `$ ./download -h`

````shell
download - Catch All Example

Usage:
  download MESSAGE [OPTIONS] [--] [...]
  download --help | -h
  download --version | -v

Options:
  --debug, -d


  --help, -h
    Show this help

  --version, -v
    Show version number

Arguments:
  MESSAGE
    Message



````

### `$ ./download something`

````shell
# This file is located at 'src/root_command.sh'.
# It contains the implementation for the 'download' command.
# The code you write here will be wrapped by a function named 'download_command()'.
# Feel free to edit this file; your changes will persist when regenerating.
args:
- ${args[message]} = something


````

### `$ ./download something with --additional args`

````shell
# This file is located at 'src/root_command.sh'.
# It contains the implementation for the 'download' command.
# The code you write here will be wrapped by a function named 'download_command()'.
# Feel free to edit this file; your changes will persist when regenerating.
args:
- ${args[message]} = something

other_args:
- ${other_args[*]} = with --additional args
- ${other_args[0]} = with
- ${other_args[1]} = --additional
- ${other_args[2]} = args


````

### `$ ./download something --debug -- also pass --debug to catch_all`

````shell
# This file is located at 'src/root_command.sh'.
# It contains the implementation for the 'download' command.
# The code you write here will be wrapped by a function named 'download_command()'.
# Feel free to edit this file; your changes will persist when regenerating.
args:
- ${args[--debug]} = 1
- ${args[message]} = something

other_args:
- ${other_args[*]} = also pass --debug to catch_all
- ${other_args[0]} = also
- ${other_args[1]} = pass
- ${other_args[2]} = --debug
- ${other_args[3]} = to
- ${other_args[4]} = catch_all


````



