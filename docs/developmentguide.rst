.. _developmentguide:

Development Guide
=================

Please read our :ref:`Contributing guide lines <contributing>` first.

.. _requirements:

Requirements
------------

You can find any required library for this project in the *requirements.txt*:

.. literalinclude:: ../requirements.txt

You can install them by

.. code-block:: bash

    pip install -r requirements.txt --user
    pip install . --user

NOTE: Make sure to have also all the extensions listed in the `docs/conf.py`
that are required for the SDK Documentation.

.. _docs/conf.py: https://rawgit.com/hexonet/python-sdk/master/docs/conf.py

We suggest to use `Visual Studio Code`_ with installed plugins for Python
Development described here_. But if you prefer any other IDE / Editor, it
is fine.

.. _Visual Studio Code: https://code.visualstudio.com
.. _here: https://code.visualstudio.com/docs/languages/python

.. _testsnvalidation:

Run Tests and Code Validation
-----------------------------

If you open a Pull Request (PR), we will trigger automated tests and pep8 style
check in Travis CI. So nothing you have to worry about in your development.
You can open your PR and prefix its title with WIP "Work In Progress" to access
these checks in advance.

If there's anything breaking, be so kind to fix it. If you're not able to do it
- feel free to ask for help.

Try to auto-fix pep8 styling issues by

.. code-block:: bash

    # to autofix possible issues
    ./scripts/pep8fix.sh

    # to check for issues left
    ./scripts/pep8check.sh

    # run unit tests
    ./scripts/coverage.sh

Pull Request (PR) Procedure
---------------------------
* fork our project and create a new branch.
* clone it and check this branch out
* apply your desired changes / extensions
* commit and push it to remote. Please follow these format rules_.
  We suggest to use commitizen_.
* open a pull request (PR) - check results of Travis CI.
  There are possibly Code issues you can correct.

**We care then about the rest** - no need to worry about things like
building current realease and versioning.

**You can stop here.**

The below sections are just for our reference.
TIA for your PR and thus for your support of this project. As we have
further SDKs in other languages, it might take a bit of time to check
if we can role out that PR as we want to keep all our SDKs aligned.

.. _rules: https://github.com/angular/angular.js/blob/master/DEVELOPERS.md#-git-commit-guidelines)
.. _commitizen:  https://github.com/commitizen/cz-cli/blob/master/README.md

Versioning
----------

We use SemVer_ for versioning. For the versions available, see the
`tags on this repository`_. New version numbers will be set automatically
through npm module semantic-release which is part of our CI/CD.

.. _SemVer: http://semver.org/
.. _tags on this repository: https://github.com/hexonet/python-sdk/tags

Releasing
---------

Our Travis CI integration cares about checking the PR for issues. If all
looks fine, please care about rebasing and if applicable about squashing.
Now you can merge the PR into master branch. Travis CI and semantic-release
care about releasing and uploading. This also includes automatic update of
changelog and source code documentation.

Changes to the documentation will be auto-deployed by a webhook to
readthedocs.org_ and to `github pages`_.

.. _readthedocs.org: https://hexonet-python-sdk.readthedocs.io
.. _github pages: https://hexonet.github.io/python-sdk

The module can be accessed on the `PyPi (Live) Index`_ and the
`PyPi (Test) Index`_.

.. _PyPi (Live) Index: https://pypi.org/project/hexonet.apiconnector/
.. _PyPi (Test) Index: https://test.pypi.org/project/hexonet.apiconnector/

SDK Documentation
-----------------

Have an eye on the generated :ref:`api`.

If you want to generate it from scratch out of the sources, please use
the below script:

.. code-block:: bash

    ./scripts/generatedocs.sh

The generated files are then available in subfolder "docs/_build/html".
We regenerate the SDK Documentation whenever a new tag commit reaches
the master branch.
