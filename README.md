# flask-sqlacodegen

GitHub page: [flask-sqlacodegen](https://github.com/pwall27/flask-sqlacodegen)

This is a fork of a fork. The original fork is of [sqlacodegen](https://pypi.python.org/pypi/sqlacodegen) by Alex Gronholm. The fork this repo is directly from is [flask-sqlacodegen](https://github.com/pythrick/flask-sqlacodegen) by Patrick Rodrigues, and is based off the original at version 1.1.6.

I created this fork because even though the tag v1.1.6.1 claims to include the bugfix mentioned below, it did not work when I cloned/installed this tagged version. The master repo contains the fix, so I forked Patrick Rodrigues' repo and made a new version tag of 1.1.6.2. This effectively freezes this project at this version, which suits my purposes.

## Install

The best way I found to install this is using the following verbatim
```
git clone -b 'v1.1.6.2' --single-branch --depth 1 https://github.com/jjsayleraxio/flask-sqlacodegen.git
cd flask-sqlacodegen/
python setup.py install
```

---

What's different (taken from flask-sqlacodegen v1.1.6.1):

* Bugfix for "TypeError: unsupported operand type(s) for +: 'NoneType' and 'str'"
* Support for Flask-SQLAlchemy syntax using `--flask` option.
* Defaults to generating backrefs in relationships. `--nobackref` still included as option in case backrefs are not wanted. 
* Naming of backrefs is class name in snake_case (as opposed to CamelCase) and is pluralized if it's Many-to-One or Many-to-Many using [inflect](https://pypi.python.org/pypi/inflect).
* Primary joins are explicit.
* If column has a server_default set it to `FetchValue()` instead of trying to determine what that value is. Original code did not set the right server defaults in my setup.
* `--ignore-cols` ignores special columns when generating association tables. Original code requires all columns to be foreign keys in order to generate association table. Example: `--ignore-cols id,inserted,updated`.
* Uses the command `flask-sqlacodegen` instead of `sqlacodegen`.
