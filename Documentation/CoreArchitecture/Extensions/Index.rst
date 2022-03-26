.. include:: /Includes.rst.txt


.. _extensions:

Extensions
----------

TYPO3 CMS is entirely built around the concept of extensions. The Core itself
- since version 7 - is entirely comprised of extensions, called "system extensions".
Some are required and will always be activated. Others can be activated
or deactivated at will.

Many more extensions - developed by the community - are available in the
`TYPO3 Extension Repository (TER) <https://typo3.org/extensions/repository/>`_.

Yet more extensions are not officially published and are available straight
from source code repositories like `GitHub <https://github.com/>`_.

It is also possible to set up TYPO3 CMS using Composer. This opens
the possibility of including any library published on
`Packagist <https://packagist.org/>`_.

The architecture of an extension is described in detail in the
:ref:`Core APIs Reference <t3coreapi:extension-architecture>`.


.. _extensions-package-manager:

Package Manager
^^^^^^^^^^^^^^^

Extensions are managed by a Package Manager. The two most visible parts of
this tool are the :code:`\TYPO3\CMS\Core\Package\PackageManager` PHP class
and the :file:`typo3conf/PackageStates.php` file.

The :file:`typo3conf/PackageStates.php` file contains a list of all available
packages and their status (active or inactive).

Here is an extract of this file:

.. code-block:: php

	<?php
	# PackageStates.php

	# This file is maintained by TYPO3's package management. Although you can edit it
	# manually, you should rather use the extension manager for maintaining packages.
	# This file will be regenerated automatically if it doesn't exist. Deleting this file
	# should, however, never become necessary if you use the package commands.

	return [
		'packages' => [
			'core' => [
				'manifestPath' => '',
				'composerName' => 'typo3/cms-core',
				'state' => 'active',
				'packagePath' => 'typo3/sysext/core/',
				'classesPath' => 'Classes/',
				'suggestions' => [],
			],
			'extbase' => [
				'manifestPath' => '',
				'composerName' => 'typo3/cms-extbase',
				'state' => 'active',
				'packagePath' => 'typo3/sysext/extbase/',
				'classesPath' => 'Classes/',
				'suggestions' => [],
			],
			...
		],
		'version' => 4,
	];

.. warning::

   You should not edit this file yourself, unless you know exactly what you are doing
   and you also know how to clear the cache manually.


.. _extensions-system-main:

Main system extensions
^^^^^^^^^^^^^^^^^^^^^^

This section describes the main system extensions, their use and
what main resources and libraries they contain. The system extensions
are located in directory :file:`typo3/sysext`.

core
  As its name implies, this extension is crucial to the working of TYPO3 CMS.
  It defines the main database tables (BE users, BE groups, pages and all the
  "sys\_*" tables. It also contains the default global configuration
  (in :file:`typo3/sysext/core/Configuration/DefaultConfiguration.php`). Last
  but not least, it delivers a huge number of base PHP classes, far too many
  to describe here.

  .. tip::

     A nice way to browse TYPO3 CMS Core classes is to use http://api.typo3.org/.

backend
  This system extension provides all that is necessary to run the TYPO3 CMS
  backend. This means quite a few PHP classes, but also a lot of Fluid templates.

  .. note::

     Most backend labels reside in system extension "lang".

frontend
  This system extension contains all the tools for performing rendering in
  the frontend, i.e. the actual web site. It is mostly comprised of PHP classes,
  in particular those in :file:`typo3/sysext/frontend/Classes/ContentObject`,
  which are use for rendering the various content objects (one class per object
  type, plus a number of base and utility classes).

extbase
  Extbase is a MVC framework (with the "View" part being actually system extension
  "fluid") originally derived from the `Flow framework <https://www.neos.io/>`_.
  Not all of the TYPO3 CMS backend is written in Extbase, but many modules are,
  with more being migrated to that framework with each new version.

  For extensions, Extbase is now the recommended way to go.

fluid
  Fluid is a templating engine complementary to Extbase. It forms the "View" part
  of the MVC framework. This system extension provides a number of base classes
  and many View Helpers (in :file:`typo3/sysext/fluid/Classes/ViewHelpers`), which
  extend the basic templating features of Fluid.

install
  This system extension is the package containing the TYPO3 CMS Install Tool.
