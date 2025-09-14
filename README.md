# AirBnB Clone — The Console

## Project description

This project is the first step in building a full AirBnB clone. We  will create a Python command-line interpreter (console) to manage project objects (User, Place, State, City, Amenity, Review, etc.) and implement a simple file-based storage engine. The interpreter will let you create, show, update, destroy, and list objects as well as serialize/deserialize them to JSON.


---

## Contents

* `console.py` — entry point for the command interpreter
* `models/` — package containing all model classes and `base_model.py`
* `models/engine/file_storage.py` — file storage engine (JSON file)
* `tests/` — unit tests organized to mirror `models/` structure
* `README.md` — this file
* `AUTHORS` — contributors list

---

## Requirements

* Ubuntu 20.04 LTS (the automatic tests run here)
* Python 3.8.x (3.8.5 recommended)
* pycodestyle 2.7.\* for style checks

All scripts must be executable and start with the shebang `#!/usr/bin/python3`.

---

## What you'll learn

* Create a Python package
* Implement a command interpreter using the `cmd` module
* Serialize/deserialize objects to/from JSON
* Work with `uuid` and `datetime`
* Use `*args` and `**kwargs` correctly
* Write unit tests with `unittest`

---

## How to start the console

Make sure `console.py` is executable (`chmod +x console.py`) and run:

```bash
./console.py
```

You should see the `(hbnb)` prompt. The console also supports non-interactive mode. For example:

```bash
echo "help" | ./console.py
```

or

```bash
cat test_help | ./console.py
```

---

## Basic commands (must be implemented)

The required commands (and examples of usage):

* `create <ClassName>`

  * Creates a new instance of `ClassName`, saves it (to file storage) and prints the new instance `id`.
  * Example: `create User`

* `show <ClassName> <id>`

  * Prints the string representation of an instance based on the class name and `id`.
  * Example: `show User 1234-1234-1234`

* `destroy <ClassName> <id>`

  * Deletes an instance based on the class name and `id` (from storage).
  * Example: `destroy User 1234-1234-1234`

* `all [<ClassName>]`

  * Prints all string representations of all instances, optionally filtered by `ClassName`.
  * Example: `all` or `all User`

* `update <ClassName> <id> <attribute_name> "<attribute_value>"`

  * Updates an instance by adding or updating an attribute
  * Example: `update User 1234-1234-1234 email "a@b.com"`

* `count <ClassName>`

  * Retrieves the number of instances of a given class.
  * Example: `count User`

Also support advanced command syntax: `ClassName.command(args)` such as `User.all()` or `User.count()`.

---

## Storage flow

Instances should follow this serialization/deserialization flow:

```
Instance <-> Dictionary <-> JSON string <-> File
```

Implement `BaseModel` to handle common functionality: `id` (UUID), `created_at`, `updated_at`, `to_dict()`, and `save()`.

---

## Project structure (recommended)

```
alu-AirBnB_clone/
├─ console.py
├─ models/
│  ├─ __init__.py
│  ├─ base_model.py
│  ├─ user.py
│  ├─ place.py
│  ├─ state.py
│  ├─ city.py
│  ├─ amenity.py
│  ├─ review.py
│  └─ engine/
│     └─ file_storage.py
├─ tests/
│  ├─ test_models/
│  │  ├─ test_base_model.py
│  │  └─ test_user.py
│  └─ test_console.py
├─ AUTHORS
└─ README.md
```

---

## Running unit tests

Unit tests are required and must use `unittest`. From the project root run:

```bash
python3 -m unittest discover tests
```

To test a single file:

```bash
python3 -m unittest tests/test_models/test_base_model.py
```

All tests must pass in both interactive and non-interactive modes.

---

## Styling & Documentation rules

* Follow `pycodestyle` (2.7.\*)
* All modules, classes and functions must include docstrings with descriptive sentences
* Files must end with a newline

---

## Examples (interactive session)

*(Short examples — full examples are in the tests and project rubric)*

```
$ ./console.py
(hbnb) create BaseModel
e4b2f6b2-1dcd-4f6a-bf2b-7a6c2a3d2f3a
(hbnb) show BaseModel e4b2f6b2-1dcd-4f6a-bf2b-7a6c2a3d2f3a
[BaseModel] (e4b2f6b2-1dcd-4f6a-bf2b-7a6c2a3d2f3a) {'id': 'e4b2f6b2-1dcd-4f6a-bf2b-7a6c2a3d2f3a', 'created_at': '2020-01-01T12:00:00.000000', ...}
(hbnb) update BaseModel e4b2f6b2-1dcd-4f6a-bf2b-7a6c2a3d2f3a name "My model"
(hbnb) all BaseModel
["[BaseModel] (e4b2f6b2-1dcd-4f6a-bf2b-7a6c2a3d2f3a) {...}"]
(hbnb) quit
$
```

---

## Submission checklist

* [ ] Repository named `alu-AirBnB_clone`
* [ ] `README.md` and `AUTHORS` at repo root
* [ ] `console.py` executable and functional
* [ ] `models/` package with required classes
* [ ] `file_storage.py` engine implemented
* [ ] Unit tests in `tests/` that mirror project structure
* [ ] All tests pass with `python3 -m unittest discover tests`
