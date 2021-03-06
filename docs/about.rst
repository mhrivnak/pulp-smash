About
=====

Location: :doc:`/index` → :doc:`/about`

Why does Pulp Smash exist? What are its goals, and what does it *not* do?

.. contents::
    :local:

Why Pulp Smash?
---------------

Pulp Smash exists to make testing Pulp easy. [1]_

Scope and Limitations
---------------------

Portability
~~~~~~~~~~~

Pulp Smash should be usable in any environment that supports:

* one of the Python versions listed in ``.travis.yml``,
* the dependencies listed in ``setup.py``,
* a \*nix-like shell,
* `GNU Make`_ (or a compatible clone),
* and the `XDG Base Directory Specification`_.

This level of portability [2]_ allows Pulp Smash to be accessible [3]_.

Provisioning
~~~~~~~~~~~~

Pulp Smash is not concerned with provisioning systems. Users must bring their
own systems.

Destructiveness
~~~~~~~~~~~~~~~

Should Pulp Smash record all changes it makes to a remote system and revert them
when testing is complete, or should systems be treated as throw-away? In other
words, should the systems under test be treated like pets or cattle? [4]_ This
has yet to be decided.

Contributing
------------

Contributions are encouraged. The easiest way to contribute is to submit a pull
request on GitHub, but patches are welcome no matter how they arrive.

You can create a development environment and verify its sanity like so::

    python -m virtualenv env  # Optional. Install separately on Python <= 3.2
    source env/bin/activate
    git clone https://github.com/PulpQE/pulp-smash.git
    cd pulp-smash
    pip install -r requirements.txt -r requirements-dev.txt
    make lint
    make test
    make docs-html

Please adhere to the following guidelines:

* Pull requests should not fail the Travis build. You can verify your change by
  executing the script steps listed in ``.travis.yml``. (``make lint``, ``make
  test``, etc.)
* Adhere to typical commit guidelines:

    * Commits should be small and coherent. One commit should address one issue.
      Ask yourself: "can I revert this commit?"
    * Commits should have `good commit messages`_.
    * `Rebasing`_ is encouraged. Rebasing produces a much nicer commit history
      than merging.

* If adding a new test for Pulp, please run the test and include the test output
  in the commit message.
* When in doubt, ask on IRC. Join the #pulp channel on `freenode`_.

.. [1] See: http://www.ichimonji10.name/blog/9/
.. [2] Portable software cannot make assumptions about its environment. It
    cannot reference ``/etc/pki/tls/certs/ca-bundle.crt``  or call ``yum``.
    Instead, it must use standardized mechanisms for interacting with its
    environment. This separation of concerns should lead to an application with
    fewer responsibilities. Fewer responsibilities means fewer bugs and more
    focused developers.
.. [3] An inaccessible project is a dead project. Labeling a project "open
    source" and licensing it under a suitable terms does not change that fact.
    People have better things to do than bang their head against a wall.
.. [4] The "pets vs cattle" analogy is widely attributed to Bill Baker of
    Microsoft.

.. _GNU Make: https://www.gnu.org/software/make/
.. _Rebasing: http://www.git-scm.com/book/en/v2/Git-Branching-Rebasing
.. _XDG Base Directory Specification: http://standards.freedesktop.org/basedir-spec/basedir-spec-latest.html
.. _freenode: https://freenode.net/
.. _good commit messages: http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html
