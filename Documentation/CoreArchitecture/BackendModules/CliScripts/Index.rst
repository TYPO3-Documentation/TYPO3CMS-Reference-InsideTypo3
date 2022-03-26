.. include:: /Includes.rst.txt


.. _initialize-cli-mode:
.. _cli-mode:

TYPO3 CMS shell scripts (CLI mode)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Besides the backend, it is also possible to run some TYPO3 CMS
scripts from the command line. This makes it possible - for
example - to set up cronjobs. There are two ways to register
CLI scripts:

- using the :file:`cli_dispatch.phpsh` command-line dispatcher.

- creating an Extbase command controller.


.. _cli-mode-dispatcher:

The command-line dispatcher
"""""""""""""""""""""""""""

.. note::

   Although still common and not officially deprecated,
   this way of doing things is considered old style.
   Using Extbase command controllers is now recommended
   (although Extbase command controllers are called via
   the dispatched itself).

Any given script can be registered with the :file:`cli_dispatch.phpsh`
command-line dispatcher. Registration takes places in an extension's
:file:`ext_localconf.php` file (example taken from the "scheduler"
system extension):

.. code-block:: php

     // Register the Scheduler as a possible key for CLI calls
     $GLOBALS['TYPO3_CONF_VARS']['SC_OPTIONS']['GLOBAL']['cliKeys']['scheduler'] = array(
         function () {
             $schedulerCliController = \TYPO3\CMS\Core\Utility\GeneralUtility::makeInstance(\TYPO3\CMS\Scheduler\Controller\SchedulerCliController::class);
             $schedulerCliController->run();
         },
         '_CLI_scheduler'
     );

The last part of the declaration ("scheduler") is the key with which
the script can be called.

The registration takes a closure which instantiates the corresponding
class and calls the :code:`run()` method. The second argument is the
backend user that TYPO3 CMS should use when running that script
(here "_cli_scheduler"). If that user is not present in the system,
the script will fail. It will also fail if that user is "Admin".

The script should simply implement the :code:`run()` method and perform
its logic according to the arguments received on the command line.

The dispatcher is run by using:

.. code-block:: shell

     $ /path/to/php /path/to/webroot/typo3/cli_dispatch.phpsh

Calling the script without any argument will get you a list of available
keys:

.. code-block:: shell

     Oops, an error occurred: This script must have a command as first argument.

     Valid keys are:

       extbase
       lowlevel_admin
       lowlevel_cleaner
       lowlevel_refindex

Calling the script again with a key but no further arguments will trigger
the display of the script's help text.


.. _cli-mode-command-controllers:

Extbase command controllers
"""""""""""""""""""""""""""

First of all, the command controller must be registered in an extension's
:file:`ext_localconf.php` file (example taken from the "lang" system
extension):

.. code-block:: php

     // Register language update command controller
     $GLOBALS['TYPO3_CONF_VARS']['SC_OPTIONS']['extbase']['commandControllers'][] = \TYPO3\CMS\Lang\Command\LanguageCommandController::class;

The class itself must extend the :code:`\TYPO3\CMS\Extbase\Mvc\Controller\CommandController`
class. Each action that should be available from the command line must
be named following the pattern "[action name]Command". The PHPdoc information
is directly used as help text (description of the action, what arguments it
takes).

Here's an extract from the command controller class of the "lang"
extension:

.. code-block:: php

     /**
      * Language command controller updates translation packages
      */
     class LanguageCommandController extends \TYPO3\CMS\Extbase\Mvc\Controller\CommandController
     {
         ...

         /**
          * Update language file for each extension
          *
          * @param string $localesToUpdate Comma separated list of locales that needs to be updated
          * @return void
          */
         public function updateCommand($localesToUpdate = '')
         {
             ...
         }
     }

This command would be called by using:

.. code-block:: shell

     $ /path/to/php /path/to/webroot/typo3/cli_dispatch.phpsh extbase language:update fr

which would update translation packages for the French language.

The advantage of using Extbase command controllers are many:

- you benefit from the Extbase-way of doing things, where actions are automatically
  dispatched to the proper method

- display of help text is easy, since PHPdoc comments are used

- the base command controller gives you access to many useful tools, in particular
  for outputting to the terminal, thanks to the integration of the Symfony console.

