spirit.bob
==========

``spirit.bob`` provides several `mr.bob`_ template to generate packages for `it-spirit`_ projects.

To create a package like ``spirit.diazo.mytheme``::

    $ mrbob spirit.bob:diazo_theme

.. note::
    In contrast to other available ``mr.bob`` templates (e.g. `bobtemplates.plone`_), the packages created with ``spirit.bob`` create the package folder as well.


Available Templates
===================

The templates provided by ``spirit.bob`` are categorized as follows:

- Plone and Diazo Packages
- Zope Packages (planned)
- Pyramid Packages (planned)

Plone and Diazo Package Templates
---------------------------------

diazo_theme
    A installable diazo core or customer theme.
    Core themes are mainly used as a base for most customer themes.
    Customer themes can extend a core theme.


Options
=======

On creating a package you can choose from the following options. The default value is in [square brackets].

diazo_theme
-----------

Type of the Theme (core or customer) [customer]
    A customer theme can extend a core theme.
    Core themes will have the ``spirit.diazo`` namespace prefix, customer themes the ``customer.diazo`` namespace prefix.

Base theme to extend
    Add the package name of the core theme you want to extend.
    Leave empty if you don't want to extend.
    This options is only available for ``customer`` themes.

Repository type of the base theme to extend [git]
    Should be something like 'git', 'hg', 'svn'.
    Used for the mr.developer source section within the buildout.
    This option is only available if a base theme was provided.

Repository URL of the base theme to extend [https://github.com/it-spirit/spirit.diazo.base]
    The URL to the repo used for the mr.developer source section within the buildout.
    This option is only available if a base theme was provided.

Name of the Theme [Example Theme]
    Should be something like 'Example Theme'.

Package Name of the Theme [example]
    Should be something like 'example'.


Features
========

Package created with ``spirit.bob`` use the current best-practices when creating an addon.


Plone and Diazo Packages
------------------------

Buildout
    The packages are contained in a buildout that allow you to build Plone with the new package installed for testing-purposes.

Locales
    The packages register a directory for locales.

Profile
    The packages contain a `Generic Setup Profile`_ that installs a browserlayer.

Setuphandler
    The packages contain a `setuphandlers.py`_ where you can add code that is executed on installing the package.

Template-Overrides
    The packages register the folder ``template_overrides`` as a directory where you can drop template-overrides using `z3c.jbot`_.

Tests
    The packages come with a test setup and some `tests`_ for installing the package.
    They also contain a `robot-test`_ for browser testing.
    The buildouts also contains a config to allow testing the package on `travis`_.



Compatibility
=============

Addons created with ``spirit.bob`` are tested to work in Plone 4.3.x.
They should also work with other versions but that was not tested.


Installation
============

Use in a buildout
-----------------

::

    [buildout]
    parts += mrbob

    [mrbob]
    recipe = zc.recipe.egg
    eggs =
        mr.bob
        spirit.bob

If you want to use the latest development version from GitHub, add ``spirit.bob`` to your ``mr.developer`` source section::

    [buildout]
    extensions += mr.developer

    [sources]
    spirit.bob = git git://github.com/it-spirit/spirit.bob.git


This creates a mrbob-executeable in your bin-directory.
Call it from the ``src``-directory of your project like this.::

    $ ../bin/mrbob spirit.bob:diazo_theme


Installation in a virtualenv
----------------------------

You can also install ``spirit.bob`` in a virtualenv.::

    $ pip install spirit.bob

You can also install the latest version of ``spirit.bob`` directly from GitHub::

    $ pip install -e git://github.com/it-spirit/spirit.bob.git#egg=spirit.bob

Now you can use it like this::

    $ mrbob spirit.bob:diazo_theme


.. _`mr.bob`: http://mrbob.readthedocs.org/en/latest/
.. _`Generic Setup Profile`: http://docs.plone.org/develop/addons/components/genericsetup.html
.. _`it-spirit`: http://it-spir.it
.. _`robot-test`: http://docs.plone.org/external/plone.app.robotframework/docs/source/index.html
.. _`setuphandlers.py`: http://docs.plone.org/develop/addons/components/genericsetup.html?highlight=setuphandler#custom-installer-code-setuphandlers-py
.. _`tests`: http://docs.plone.org/external/plone.app.testing/docs/source/index.html
.. _`travis`: http://travis-ci.org/
.. _`z3c.jbot`: https://pypi.python.org/pypi/z3c.jbot
.. _`bobtemplates.plone`: https://github.com/plone/bobtemplates.plone
