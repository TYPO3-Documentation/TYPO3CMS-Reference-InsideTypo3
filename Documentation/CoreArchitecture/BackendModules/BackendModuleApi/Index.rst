.. include:: ../../../Includes.txt


.. _backend-modules-api:

Backend Module API
^^^^^^^^^^^^^^^^^^


.. _backend-modules-api-registration:

Registering new modules
"""""""""""""""""""""""

Modules added by extensions are registered in the :file:`ext_tables.php`
using the following API:

.. code-block:: php

   if (TYPO3_MODE === 'BE') {
       // Module System > Backend Users
       \TYPO3\CMS\Extbase\Utility\ExtensionUtility::registerModule(
           'TYPO3.CMS.Beuser',
           'system',
           'tx_Beuser',
           'top',
           array(
               'BackendUser' => 'index, addToCompareList, removeFromCompareList, compare, online, terminateBackendUserSession',
               'BackendUserGroup' => 'index'
           ),
           array(
               'access' => 'admin',
               'icon' => 'EXT:beuser/Resources/Public/Icons/module-beuser.svg',
               'labels' => 'LLL:EXT:beuser/Resources/Private/Language/locallang_mod.xlf'
           )
       );
   }

Here the module is declared as being a submodule of main module "system"
and it should be placed at the "top" of that main module, if possible
(if several modules are declared at the same position, the last one wins).

The last array contains important information: the module is accessible
only to "Admin" users. It also contains pointers to its icon and the
language file containing its title and description, for building the
module menu and for the display of information in the **About Modules**
module (found in the main help menu in the top bar).


.. _backend-modules-api-tbemodules:

$TBE\_MODULES
"""""""""""""

When modules are registered, they get added to a global array called
:code:`$GLOBALS['TBE_MODULES']`. It contains the list of all registered
modules, their configuration and the configuration of any existing
navigation component (the components which may be loaded into the
navigation frame).

:code:`$GLOBALS['TBE_MODULES']` can be explored using the
**SYSTEM > Configuration** module.

.. figure:: ../../../Images/BackendModulesConfiguration.png
   :alt: Exploring the TBE_MODULES array using the Configuration module


The list of modules is parsed by the class :code:`\TYPO3\CMS\Backend\Module\ModuleLoader`.
