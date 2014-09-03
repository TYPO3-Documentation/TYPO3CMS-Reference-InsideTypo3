.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../../Includes.txt


How to acquire labels from the $GLOBALS['LANG'] object
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The previous section described the storage structure for translations:
"locallang" files and $LOCAL\_LANG arrays. But how are these values
practically used?

Basically there are two approaches:

- Call $GLOBALS['LANG']->getLL(' *label\_key* ')

- Call $GLOBALS['LANG']->sL('LLL:[file-reference of locallang file]:[key-name]')

These are described below.


$GLOBALS['LANG']->getLL()
"""""""""""""""""""""""""

This approach will simply return a label from the globally defined
$LOCAL\_LANG array. So prior to calling this function you must have
included a locallang file (and possibly sub-file) in the global scope
of the script.

There is a sister function, $GLOBALS['LANG']->getLLL(' *label\_key* ',
$LOCAL\_LANG), which allows you to do the same thing, but pass along
the $LOCAL\_LANG array to use (instead of the global array).

Requires a locallang file to be manually included prior to use. See
below.


$GLOBALS['LANG']->sL()
""""""""""""""""""""""

This approach lets you get a label by a reference to the file where it
exists and its label key: $GLOBALS['LANG']->sL('LLL:[file-reference of locallang
file]:[key-name]'). That mode is initiated by a triple L (LLL:) prefix
of the string.

The file-reference is a "locallang"-file in XML format (or in the old and
deprecated PHP format).

If  *not* a "LLL:" string is prefixed then the input is exploded by a
vertical bar (\|) and each part is perceived as the label for the
corresponding language in the TYPO3\_languages constant. However this
concept is  **deprecated** since it's impossible to maintain
efficiently.  *Always* use the "LLL:" references to proper locallang
files. (See discussion of "language-split" syntax above).

$GLOBALS['LANG']->sL() requires no manual inclusion of a locallang file since
that is done automatically. Typically used in table and field name
labels in $TCA or in modules where a single value from the core
locallang file is needed.

(See the example in the previous section '"language-split" syntax'
in addition)


Including locallang files in modules
""""""""""""""""""""""""""""""""""""

If you are using $GLOBALS['LANG']->getLL() for fetching labels in your modules
(this is recommended) then you must make sure to include the locallang
file with the labels during the initialization of your module. However
you should not just include the file - rather use the API-function
$GLOBALS['LANG']->includeLLFile() designed for that. There are three reasons for
this:

- If the locallang.xml file is split into a main- and sub-file that
  is automatically handled by that function.

- If any 'XLLFile' is configured to override the values in the default
  locallang file, that file will be included and the values merged onto
  the default array.

- The file-reference is a "locallang"-file in either PHP or XML format.
  It is not important to know in this case! Using the ".php" or ".xml"
  file ending will not matter as long as the file exists. TYPO3 will
  look for both file extensions and use the one it finds.

Example from the "setup" module (red line includes locallang for that
module)::

   require ($BACK_PATH . 'init.php');
   require ($BACK_PATH . 'template.php');
   $GLOBALS['LANG']->includeLLFile('EXT:setup/mod/locallang.xml');

This function call will load the $LOCAL\_LANG array from
'EXT:setup/mod/locallang.xml' into the global memory space and thus
make it available to $GLOBALS['LANG']->getLL(). If 'EXT:setup/mod/locallang.xml'
does not exist but 'EXT:setup/mod/locallang.php' does, then the latter
is parsed, loaded and everything is the same for TYPO3. Although you
should use XML format and the correct file extension in the file reference
(using ".xml" when the locallang file is actually a "locallang-XML"
format file).

If you wish to not load the $LOCAL\_LANG array into global space, but
rather have it returned in a variable, just set the second optional
argument true like this:

$myLocalLang = $GLOBALS['LANG']->includeLLFile('EXT:setup/mod/locallang.xml', FALSE);

