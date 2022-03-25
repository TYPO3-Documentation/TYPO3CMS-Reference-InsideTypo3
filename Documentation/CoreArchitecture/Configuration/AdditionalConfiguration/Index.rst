.. include:: /Includes.rst.txt


.. _configuration-additional-configuration:

The AdditionalConfiguration.php file
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Although you can manually edit the :file:`typo3conf/LocalConfiguration.php`
file, it is limited in scope because the file is expected to return
a PHP array. Also the file is rewritten every time an option is
changed in the Install Tool or some other operation (like changing
an extension configuration in the Extension Manager). Thus custom
code cannot reside in that file.

Such code should be placed in the :file:`typo3conf/AdditionalConfiguration.php`
file. This file is never touched by TYPO3, so any code will be
left alone.

Furthermore this file is loaded **after** :file:`typo3conf/LocalConfiguration.php`,
which means it represents an opportunity to change global configuration
values programmatically if needed.

:file:`typo3conf/AdditionalConfiguration.php` is a plain PHP file.
There are no specific rules about what it may contain. However since
the code it contains is included on **every** request to TYPO3 CMS
- whether frontend or backend - you should avoid inserting code
which requires heavy duty processing.
