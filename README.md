Setting up a new Repository
===============================
[![Build](https://github.com/edmundsj/template/actions/workflows/python-package-conda.yml/badge.svg)](https://github.com/edmundsj/template/actions/workflows/python-package-conda.yml) [![docs](https://github.com/edmundsj/template/actions/workflows/build-docs.yml/badge.svg)](https://github.com/edmundsj/template/actions/workflows/build-docs.yml )[![codecov](https://codecov.io/gh/edmundsj/template/branch/main/graph/badge.svg?token=7L4PK4K0P3)](https://codecov.io/gh/edmundsj/template)

This is a template repository for python projects which use sphinx for
documentation, github actions for building, pytest and codecov for test
coverage.


Getting Started
------------------
1. Clone this repository into your desired directory

    ```git clone https://github.com/edmundsj/template.git <DESIRED_DIRECTORY>```

2. Change the git hooks location:

    ```git config core.hooksPath .hooks```

3. Create a new repository on github
4. Change this repository's name with 

   ```git remote set-url origin <NEW_REPO_URL>```

5. Add this repositry to codecov: https://app.codecov.io/gh/edmundsj, and add
   the CODECOV_TOKEN secret to the github repository.
6. Push to the new repository 

    ```git push -u origin main```

7. Set github pages to use the ``docs/`` folder for github pages at the bottom
   of the "Settings" page
8. Create a status badge from the '... -> Create Status Badge' in the github actions area separately for docs and build, and paste them in the README, as well as from codecov.

Done! Your repository should be viewable on github pages: 
https://edmundsj.github.io/REPO_NAME/

Features
---------
- Github actions unit test integration via pytest
- Github actions package management with conda
- Github actions documentation build using sphinx and reST/markdown, with auto
self-push to repository after successful build
- Github pages documentation hosting/integration
- Local commits hooks run full test suite
- Coverage uploaded automatically to codecov after successful build
- [FUTURE] Auto-deploy to pyPi/testpyPi after successful build


Adding Additional Unit Tests
-------------------------------
- Any time you want to add additional unit tests just add them to those in the
``tests/`` directory and prepend with the name ``test``. These will be
automatically found by pytest and run during local commits and remote builds.


Writing the Documentation
------------------------------
- The documentation source is located in ``docs/source`` and is written in
restructured text (markdown is also available).

Building the Documentation
----------------------------
Simply run ``make html`` from the ``docs/`` directory. This will compile the
files in the ``source/`` directory, and place them in the main ``docs/``
directory where github pages can find them.

Writing Tests and Adding them to the Test Runner
---------------------------------------------------
The tests are run from github hooks prior to each commit and on the remote
server with the file located in ``test/fullRunner.py``. This is meant to be a
comprehensive set of unit tests, and any additional test files should be added
to that file.
