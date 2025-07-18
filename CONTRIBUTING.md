Contributing to SKADA
=====================


First off, thank you for considering contributing to SKADA.

How to contribute
-----------------

The preferred workflow for contributing to SKADA is to fork the
[main repository](https://github.com/scikit-adaptation/skada) on
GitHub, clone, and develop on a branch. Steps:

1. Fork the [project repository](https://github.com/scikit-adaptation/skada)
   by clicking on the 'Fork' button near the top right of the page. This creates
   a copy of the code under your GitHub user account. For more details on
   how to fork a repository see [this guide](https://help.github.com/articles/fork-a-repo/).

2. Clone your fork of the SKADA repo from your GitHub account to your local disk:

   ```bash
   $ git clone git@github.com:YourLogin/SKADA.git
   $ cd SKADA
   ```

2. Install pre-commit hooks to ensure that your code is properly formatted:

   ```bash
   $ pip install pre-commit
   $ pre-commit install
   ```

   This will install the pre-commit hooks that will run on every commit. If the hooks fail, the commit will be aborted.

3. Install the dependencies:

   ```bash
   $ pip install -e .
   ```
To install an optional dependency (see pyproject.toml), swap the previous command with ```pip install -e ."[dependency_name]"```.

4. Create a ``feature`` branch to hold your development changes:

   ```bash
   $ git checkout -b my-feature
   ```

   Always use a ``feature`` branch. It's good practice to never work on the ``main`` branch!

5. Develop the feature on your feature branch. Add changed files using ``git add`` and then ``git commit`` files:

   ```bash
   $ git add modified_files
   $ git commit
   ```

   to record your changes in Git, then push the changes to your GitHub account with:

   ```bash
   $ git push -u origin my-feature
   ```

6. Follow [these instructions](https://help.github.com/articles/creating-a-pull-request-from-a-fork)
to create a pull request from your fork. This will send an email to the committers.

(If any of the above seems like magic to you, please look up the
[Git documentation](https://git-scm.com/documentation) on the web, or ask a friend or another contributor for help.)

Pull Request Checklist
----------------------

We recommended that your contribution complies with the
following rules before you submit a pull request:

-  Follow the PEP8 Guidelines which should be handled automatically by pre-commit.

-  If your pull request addresses an issue, please use the pull request title
   to describe the issue and mention the issue number in the pull request description. This will make sure a link back to the original issue is
   created.

-  All public methods should have informative docstrings with sample
   usage presented as doctests when appropriate.

-  Please prefix the title of your pull request with `[MRG]` (Ready for
   Merge), if the contribution is complete and ready for a detailed review.
   Two core developers will review your code and change the prefix of the pull
   request to `[MRG + 1]` and `[MRG + 2]` on approval, making it eligible
   for merging. An incomplete contribution -- where you expect to do more work before
   receiving a full review -- should be prefixed `[WIP]` (to indicate a work
   in progress) and changed to `[MRG]` when it matures. WIPs may be useful
   to: indicate you are working on something to avoid duplicated work,
   request broad review of functionality or API, or seek collaborators.
   WIPs often benefit from the inclusion of a
   [task list](https://github.com/blog/1375-task-lists-in-gfm-issues-pulls-comments)
   in the PR description.


-  When adding additional functionality, provide at least one
   example script in the ``examples/`` folder. Have a look at other
   examples for reference. Examples should demonstrate why the new
   functionality is useful in practice and, if possible, compare it
   to other methods available in SKADA.

-  Documentation and high-coverage tests are necessary for enhancements to be
   accepted. Bug-fixes or new features should be provided with
   [non-regression tests](https://en.wikipedia.org/wiki/Non-regression_testing).
   These tests verify the correct behavior of the fix or feature. In this
   manner, further modifications on the code base are granted to be consistent
   with the desired behavior.
   For the Bug-fixes case, at the time of the PR, this tests should fail for
   the code base in main and pass for the PR code.

-  At least one paragraph of narrative documentation with links to
   references in the literature (with PDF links when possible) and
   the example.

You can also check for common programming errors with the following
tools:

- All lint checks pass. You can run the following command to check:

  ```bash
  $ pre-commit run --all-files
  ```

  This will run the pre-commit checks on all files in the repository.

- All tests pass. You can run the following command to check:

  ```bash
   $ pytest skada
  ```

Bonus points for contributions that include a performance analysis with
a benchmark script and profiling output (please report on the mailing
list or on the GitHub issue).

Filing bugs
-----------
We use Github issues to track all bugs and feature requests; feel free to
open an issue if you have found a bug or wish to see a feature implemented.

It is recommended to check that your issue complies with the
following rules before submitting:

-  Verify that your issue is not being currently addressed by other
   [issues](https://github.com/scikit-adaptation/skada/issues?q=)
   or [pull requests](https://github.com/scikit-adaptation/skada/pulls?q=).

-  Please ensure all code snippets and error messages are formatted in
   appropriate code blocks.
   See [Creating and highlighting code blocks](https://help.github.com/articles/creating-and-highlighting-code-blocks).

-  Please include your operating system type and version number, as well
   as your Python, SKADA, numpy, and scipy versions. This information
   can be found by running the following code snippet:

  ```python
  import platform; print(platform.platform())
  import sys; print("Python", sys.version)
  import numpy; print("NumPy", numpy.__version__)
  import scipy; print("SciPy", scipy.__version__)
  import ot; print("SKADA", ot.__version__)
  ```

-  Please be specific about what estimators and/or functions are involved
   and the shape of the data, as appropriate; please include a
   [reproducible](http://stackoverflow.com/help/mcve) code snippet
   or link to a [gist](https://gist.github.com). If an exception is raised,
   please provide the traceback.

New contributor tips
--------------------

A great way to start contributing to SKADA is to pick an item
from the list of [Good first issues](https://github.com/scikit-adaptation/skada/issues?q=is%3Aissue+is%3Aopen+label%3A%22good+first+issue%22)
in the issue tracker. Resolving these issues allow you to start
contributing to the project without much prior knowledge. Your
assistance in this area will be greatly appreciated by the more
experienced developers as it helps free up their time to concentrate on
other issues.

Documentation
-------------

We are glad to accept any sort of documentation: function docstrings,
reStructuredText documents (like this one), tutorials, and Markdown etc.
reStructuredText documents live in the source code repository under the
doc/ directory.

You can edit the documentation using any text editor and then generate
the HTML output by typing ``make html`` from the ``docs/`` directory.
Alternatively, ``make`` can be used to quickly generate the
documentation without the example gallery with `make html-noplot`. The resulting HTML files will
be placed in `docs/build/html/` and are viewable in a web browser.

For building the documentation, you will need
[sphinx](http://sphinx.pocoo.org/),
[matplotlib](http://matplotlib.org/), and
[pillow](http://pillow.readthedocs.io/en/latest/).

When you are writing documentation, it is important to keep a good
compromise between mathematical and algorithmic details, and give
intuition to the reader on what the algorithm does. It is best to always
start with a small paragraph with a hand-waving explanation of what the
method does to the data and a figure (coming from an example)
illustrating it.


This Contribution guide is strongly inspired by the one of the [POT](https://pythonot.github.io/) and [scikit-learn](https://github.com/scikit-learn/scikit-learn) teams.
