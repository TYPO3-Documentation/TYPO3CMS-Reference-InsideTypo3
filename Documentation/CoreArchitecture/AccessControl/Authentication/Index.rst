.. include:: ../../../Includes.txt


.. _authentication:

Authentication
^^^^^^^^^^^^^^

Authentication in TYPO3 CMS is done via the :doc:`services API <t3services:Index>`.
This makes it very flexible. It is easy to add new authentication services
via extensions.

Services get executed in order of priority. Services with higher
priority get executed first, which means it is easy to control
the order in which services get executed. By default, TYPO3 CMS
provides a basic authentication service and two improved ones,
which are installed by default: "saltedpasswords" and "rsaauth".

Alternative services are available in the TYPO3 Extension Repository.
It is thus possible to find solutions for using LDAP as an
authentication server, for example.

You can check which authentication services are installed
using the **SYSTEM > Reports** module, in the *Installed Services*
view:

.. figure:: ../../../Images/AccessInstalledAuthServices.png
   :alt: All installed authentication services and their priority

