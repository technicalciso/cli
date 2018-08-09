# nextstrain-cli

This is the Nextstrain command-line tool.  It aims to provide access to
Nextstrain components in a local environment with a minimum of fuss.

You can use it to run a pathogen build which makes use of components like
[sacra][], [fauna][], and [augur][] or view the results of such a build in our
standard viewer, [auspice][].


[sacra]: https://github.com/nextstrain/sacra
[fauna]: https://github.com/nextstrain/fauna
[augur]: https://github.com/nextstrain/augur
[auspice]: https://github.com/nextstrain/auspice


## Usage

This package provides a `nextstrain` program which provides access to a few
commands.  If you've installed this package (`nextstrain-cli`), you can just
run `nextstrain`.  Otherwise, you can run `./bin/nextstrain` from a copy of the
source code.

```
usage: nextstrain [-h] {build,view,deploy,shell,update,check-setup,version} ...

Nextstrain command-line tool

optional arguments:
  -h, --help            show this help message and exit

commands:
  {build,view,deploy,shell,update,check-setup,version}
    build               Run pathogen build
    view                View pathogen build
    deploy              Deploy pathogen build
    shell               Start a new shell in the build environment
    update              Updates your local image copy
    check-setup         Tests your local setup
    version             Show version information
```

For more information on a specific command, you can run it with the `--help`
option, for example, `nextstrain build --help`.


## Installation

This tool is written in Python 3 and requires at least Python 3.5.  You may
install it with pip (or pip3) like so:

    pip install nextstrain-cli

or from a git clone or copy of the source code:

    pip install .

If your system has both Python 2 and Python 3 installed side-by-side, you may
need to use pip3 instead of pip (which often defaults to pip2).

This tool also currently requires [Docker][].  You can download and install the
[Docker Community Edition (CE)][] for your platform for free.  After doing so,
run `nextstrain check-setup` to ensure it works.


[Docker]: https://docker.com
[Docker Community Edition (CE)]: https://www.docker.com/community-edition#download


## Development

Development of `nextstrain-cli` happens at <https://github.com/nextstrain/cli>.

We currently target compatibility with Python 3.5 and higher.  This may be
increased to 3.6 in the future.

Versions for this project follow the [Semantic Versioning rules][].

### Running with local changes

From within a clone of the git repository you can run `./bin/nextstrain` to
test your local changes without installing them.  (Note that `./bin/nextstrain`
is not the script that gets installed by pip as `nextstrain`; that script is
generated by the `entry_points` configuration in `setup.py`.)

### Releasing

New releases are made frequently and tagged in git using a [_signed_ tag][].
The source and wheel (binary) distributions are uploaded to [the nextstrain-cli
project on PyPi](https://pypi.org/project/nextstrain-cli).

There is a `./devel/release` script which will prepare a new release from your
local repository.  It ends with instructions for you on how to push the release
commit/tag and how to upload the built distributions to PyPi.  You'll need [a
PyPi account][] and [twine][] installed.

### Type annotations and static analysis

Our goal is to gradually add [type annotations][] to our code so that we can
catch errors earlier and be explicit about the interfaces expected and
provided.  Annotation pairs well with the functional approach taken by the
package.

During development you can run static type checks using [mypy][]:

    mypy nextstrain

There are also many [editor integrations for mypy][].


[Semantic Versioning rules]: https://semver.org
[_signed_ tag]: https://git-scm.com/book/en/v2/Git-Tools-Signing-Your-Work
[PyPi account]: https://pypi.org/account/register/
[twine]: https://pypi.org/project/twine
[type annotations]: https://www.python.org/dev/peps/pep-0484/
[mypy]: http://mypy-lang.org/
[editor integrations for mypy]: https://github.com/python/mypy#ide--linter-integrations
