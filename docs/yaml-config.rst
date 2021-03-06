Read the Docs YAML Config
=========================

Read the Docs now has support for configuring builds with a YAML file.
The file, `readthedocs.yml`, must be in the root directory of your project.

.. warning:: This feature is in a beta state.
             Please file an `issue`_ if you find anything wrong.

Supported Settings
------------------

formats
~~~~~~~

* Default: ``htmlzip``, ``pdf``, ``epub``
* Options: ``htmlzip``, ``pdf``, ``epub``, ``none``

The formats of your documentation you want to be built.
Choose ``none`` to build none of the formats.

.. note:: We will always build an HTML & JSON version of your documentation.
		  These are used for web serving & search indexing, respectively.

.. code-block:: yaml

    # Don't build any extra formats
    formats:
        - none

.. code-block:: yaml

    # Build PDF & ePub
    formats:
        - epub
        - pdf

requirements_file
~~~~~~~~~~~~~~~~~

* Default: `None`
* Type: Path (specified from the root of the project)

The path to your Pip requirements file.

.. code-block:: yaml

	requirements_file: requirements/docs.txt


conda
~~~~~

The ``conda`` block allows for configuring our support for Conda.

conda.file
``````````

* Default: `None`
* Type: Path (specified from the root of the project)

The file option specified the Conda `environment file`_ to use.


.. code-block:: yaml

	conda:
	    file: environment.yml

.. note:: Conda is only supported via the YAML file.

python
~~~~~~

The ``python`` block allows you to configure aspects of the Python executable
used for building documentation.

python.version
``````````````

* Default: ``2``
* Options: ``2``, ``3``

The version of Python to use when building your documentation.

.. code-block:: yaml

	python:
	   version: 3

python.setup_py_install
```````````````````````

* Default: `False`
* Type: Boolean

When true, install your project into the Virtualenv with
``python setup.py install`` when building documentation.

.. code-block:: yaml

	python:
	   setup_py_install: true

python.pip_install
``````````````````

* Default: `False`
* Type: Boolean

When true, install your project into the Virtualenv with pip when building
documentation.

.. code-block:: yaml

    python:
       pip_install: true

.. To implement..

	type
	~~~~

    * Default: ``sphinx``
    * Options: ``sphinx``, ``mkdocs``

    The ``type`` block allows you to configure the build tool used for building
    your documentation.

	.. code-block:: yaml

		type: sphinx

	conf_file
	~~~~~~~~~

    * Default: `None`
    * Type: Path (specified from the root of the project)

    The path to a specific Sphinx ``conf.py`` file. If none is found, we will
    choose one.

	.. code-block:: yaml

		conf_file: project2/docs/conf.py


.. _issue: https://github.com/rtfd/readthedocs.org/issues
.. _environment file: http://conda.pydata.org/docs/using/envs.html#share-an-environment
