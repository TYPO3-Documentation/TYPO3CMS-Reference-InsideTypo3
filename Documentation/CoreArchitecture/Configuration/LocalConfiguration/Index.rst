.. include:: /Includes.rst.txt


.. _configuration-local-configuration:

The LocalConfiguration.php file
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The global configuration is stored in file :file:`typo3conf/LocalConfiguration.php`.

.. important::

   Since configuration settings can be manipulated from within the
   TYPO3 CMS backend, the :file:`typo3conf/LocalConfiguration.php`
   must be writable by the web server user.

The local configuration file is basically a long array which is simply returned
when the file is included. It represents the global TYPO3 CMS configuration.
This configuration can be modified/extended/overridden by extensions,
by setting configuration options inside an extension's
:file:`ext_localconf.php` file. See :ref:`Core APIs <t3coreapi:extension-files-locations>`
for more details about extension structure.

Here is the local configuration file after the :ref:`basic installation <installation>`:

.. code-block:: php

	<?php
	return [
		'BE' => [
			'debug' => true,
			'explicitADmode' => 'explicitAllow',
			'installToolPassword' => '$P$Cbp90UttdtIKELNrDGjy4tDxh3uu9D/',
			'loginSecurityLevel' => 'rsa',
		],
		'DB' => [
			'database' => 'empty_typo3',
			'host' => 'localhost',
			'password' => 'foo',
			'socket' => '',
			'username' => 'bar',
		],
		'EXT' => [
			'extConf' => [
				'css_styled_content' => 'a:1:{s:32:"loadContentElementWizardTsConfig";s:1:"1";}',
				'doc_tut_templating' => 'a:0:{}',
				'rsaauth' => 'a:1:{s:18:"temporaryDirectory";s:0:"";}',
				'saltedpasswords' => 'a:2:{s:3:"BE.";a:4:{s:21:"saltedPWHashingMethod";s:41:"TYPO3\\CMS\\Saltedpasswords\\Salt\\PhpassSalt";s:11:"forceSalted";i:0;s:15:"onlyAuthService";i:0;s:12:"updatePasswd";i:1;}s:3:"FE.";a:5:{s:7:"enabled";i:1;s:21:"saltedPWHashingMethod";s:41:"TYPO3\\CMS\\Saltedpasswords\\Salt\\PhpassSalt";s:11:"forceSalted";i:0;s:15:"onlyAuthService";i:0;s:12:"updatePasswd";i:1;}}',
				't3editor' => 'a:0:{}',
			],
		],
		'FE' => [
			'debug' => true,
			'loginSecurityLevel' => 'rsa',
		],
		'GFX' => [
			'colorspace' => 'RGB',
			'im' => 1,
			'im_mask_temp_ext_gif' => 1,
			'im_path' => '/usr/local/bin/',
			'im_path_lzw' => '/usr/local/bin/',
			'im_v5effects' => -1,
			'im_version_5' => 'gm',
			'image_processing' => 1,
			'jpg_quality' => '80',
		],
		'INSTALL' => [
			'wizardDone' => [
				'TYPO3\CMS\Install\Updates\AccessRightParametersUpdate' => 1,
				'TYPO3\CMS\Install\Updates\BackendUserStartModuleUpdate' => 1,
				'TYPO3\CMS\Install\Updates\Compatibility6ExtractionUpdate' => 1,
				'TYPO3\CMS\Install\Updates\ContentTypesToTextMediaUpdate' => 1,
				'TYPO3\CMS\Install\Updates\ExtensionManagerTables' => 1,
				'TYPO3\CMS\Install\Updates\FileListIsStartModuleUpdate' => 1,
				'TYPO3\CMS\Install\Updates\FilesReplacePermissionUpdate' => 1,
				'TYPO3\CMS\Install\Updates\LanguageIsoCodeUpdate' => 1,
				'TYPO3\CMS\Install\Updates\MediaceExtractionUpdate' => 1,
				'TYPO3\CMS\Install\Updates\MigrateMediaToAssetsForTextMediaCe' => 1,
				'TYPO3\CMS\Install\Updates\MigrateShortcutUrlsAgainUpdate' => 1,
				'TYPO3\CMS\Install\Updates\OpenidExtractionUpdate' => 1,
				'TYPO3\CMS\Install\Updates\PageShortcutParentUpdate' => 1,
				'TYPO3\CMS\Install\Updates\ProcessedFileChecksumUpdate' => 1,
				'TYPO3\CMS\Install\Updates\TableFlexFormToTtContentFieldsUpdate' => 1,
				'TYPO3\CMS\Install\Updates\WorkspacesNotificationSettingsUpdate' => 1,
				'TYPO3\CMS\Rtehtmlarea\Hook\Install\DeprecatedRteProperties' => 1,
				'TYPO3\CMS\Rtehtmlarea\Hook\Install\RteAcronymButtonRenamedToAbbreviation' => 1,
			],
		],
		'MAIL' => [
			'transport_sendmail_command' => '/usr/sbin/sendmail -t -i ',
		],
		'SYS' => [
			'caching' => [
				'cacheConfigurations' => [
					'extbase_object' => [
						'backend' => 'TYPO3\\CMS\\Core\\Cache\\Backend\\Typo3DatabaseBackend',
						'frontend' => 'TYPO3\\CMS\\Core\\Cache\\Frontend\\VariableFrontend',
						'groups' => [
							'system',
						],
						'options' => [
							'defaultLifetime' => 0,
						],
					],
				],
			],
			'clearCacheSystem' => true,
			'devIPmask' => '*',
			'displayErrors' => 1,
			'enableDeprecationLog' => 'file',
			'encryptionKey' => '0396e1b6b53bf48b0bfed9e97a62744158452dfb9b9909fe32d4b7a709816c9b4e94dcd69c011f989d322cb22309f2f2',
			'exceptionalErrors' => 28674,
			'isInitialDatabaseImportDone' => true,
			'isInitialInstallationInProgress' => false,
			'sitename' => 'New TYPO3 site',
			'sqlDebug' => 1,
			'systemLogLevel' => 0,
			't3lib_cs_convMethod' => 'mbstring',
			't3lib_cs_utils' => 'mbstring',
		],
	];

As you can see, the array is structured on two main levels. The first level
corresponds roughly to a category, the second one being properties, which
may themselves be arrays.

The configuration categories are:

BE
  Options related to the TYPO3 CMS backend

DB
  Database connection configuration

EXT
  Extension configuration options. The settings of each extension is stored as
  a serialized array.

FE
  Frontend-related options.

GFX
  Options related to image manipulation.

INSTALL
  The Install Tool does not have any options, but stores in the local configuration
  file the list of upgrade wizards that were already executed (to avoid presenting
  them to the user over and over again).

MAIL
  Options related to the sending of emails (transport, server, etc.).

SYS
  General options which may affect both the frontend and the backend.

Details on the various configuration-options can be found in the install-tool as well as the TYPO3-source at :file:`typo3/sysext/core/Configuration/DefaultConfiguration.php`. The documentation shown in the install-tool is automatically extracted from those comments of DefaultConfiguration.php.
