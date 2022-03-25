.. include:: ../../Includes.txt


.. _workspaces:

Versioning and Workspaces
-------------------------

TYPO3 CMS provides a feature called "workspaces", whereby changes
can be made to the content of the web site without affecting the
currently visible (live) version. Changes can be previewed and
go through an approval process before publishing.

The technical background and a practical user guide to this feature
are provided in the :doc:`"workspaces" system extension manual <workspaces:Index>`.

All the information necessary for making any database table
compatible with workspaces is described in the
TCA reference (in the :ref:`description of the "ctrl" section <t3tca:ctrl>`
and in the :ref:`description of the "versioningWS" property <t3tca:ctrl-reference-versioningws>`).

Developers will find information about making their extension
support workspaces in :ref:`TYPO3 Core API <t3api:workspaces>`.
