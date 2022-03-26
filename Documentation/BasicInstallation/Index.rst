.. include:: /Includes.rst.txt


.. _installation:

A basic installation
--------------------

Since we are dealing with the core of TYPO3 CMS it might help us to make a
totally trimmed down installation of TYPO3 CMS with *only* the core
and the required system extensions (i.e. system extension which are always
installed and can not be removed).

The installation process is covered in the
:doc:`Installation and Upgrade Guide <t3install:Index>`.
You should perform the basic installation steps and **not** install
any distribution. This will give you the "lightest" possible version
of TYPO3 CMS.

Log into your basisc installation and  move to the **ADMIN TOOLS > Extensions**
module. You will see all extensions which are loaded by default.
The required extensions are not only loaded by default, but have no
"Activate/Deactivate" button.

.. figure:: ../Images/ExtensionsMinimalList.png
   :alt: The Extension Manager with a bare bones installation


The most important thing to note for now is that **everything** is an
extension in TYPO3 CMS. Even the most basic functions are packaged in a
system extension called "core".
