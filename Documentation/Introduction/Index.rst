.. include:: ../Includes.txt



.. _introduction:

Introduction
============


.. _overview:

Overview
--------

For most people TYPO3 is equivalent to a CMS providing a backend for
management of the content and a frontend engine for website display.
However TYPO3s core is natively designed to be a general purpose
framework for management of database content. The core of TYPO3 CMS
delivers a set of principles for storage of this content, user access
management, editing of the content, uploading and managing files etc.
Many of these principles are expressed as an API (Application
Programming Interface) for use in *extensions* which ultimately
add most of the real functionality.

.. figure:: ../Images/Typo3CmsStructure.png
   :alt: The TYPO3 CMS code architecture


So the  *core* is the skeleton and  *extensions* are the muscles,
fibers and skin making a full bodied CMS. In this document I cut to
the bone and provide a detailed look at the core of TYPO3 CMS including
the API available to the outside. This is supposed to be the final
technical reference apart from source code itself which is - of course
- the ultimate documentation.

This manual is a complement to :doc:`Core APIs <t3api:Index>`.


.. _audience:

Intended audience
-----------------

This document is intended to be a reference for experienced TYPO3 CMS
developers. For intermediates it will help you to become experienced!
But the document presumes that you are well familiar with TYPO3 and
the concepts herein. Further it will presume knowledge in the
technical end; PHP, MySQL, Unix etc.

The goal is to take you "under the hood" of TYPO3 CMS. To make the
principles and opportunities clear and less mysterious. To educate you
to help continue the development of TYPO3 along the already
established lines so we will have a consistent CMS application in a
future as well. And hopefully my teaching on the deep technical level
will enable you to educate others higher up in the "hierarchy". Please
consider that as well!


.. _what-s-new:

What's new
----------

This version has been fully updated for TYPO3 CMS 7. This manual had not been
updated in a very long time, which means it is impossible to list
all changes. Let's just consider it a clean slate for now.


.. _feedback:

How to contribute
-----------------

If you find a bug in this manual, please be so kind as to check the
online version on http://docs.typo3.org/typo3cms/InsideTypo3Reference/.
From there you can hit the "Edit me on GitHub" button in the top right corner
and submit a pull request via GitHub. Alternatively you can just `file an issue
using the bug tracker <https://github.com/TYPO3-Documentation/TYPO3CMS-Reference-InsideTypo3/issues>`__.

Maintaining high quality documentation requires time and effort
and the TYPO3 Documentation Team always appreciates support.
If you want to support us, please join the slack channel `typo3-documentation
<https://typo3.slack.com/messages/C028JEPJL>`__. Visit https://forger.typo3.org/slack to gain
access to Slack.
Have a look at the contribution page for more information: https://docs.typo3.org/Contribute/Index.html
And finally, as a last resort, you can get in touch with the documentation team `by mail <documentation@typo3.org>`_.



.. _credits:

Credits
-------

This manual was originally written by Kasper Skårhøj. It was further
maintained, refreshed and expanded by François Suter.
