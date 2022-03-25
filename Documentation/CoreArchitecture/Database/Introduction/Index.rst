
.. include:: /Includes.rst.txt


.. _database-introduction:

Introduction
^^^^^^^^^^^^

TYPO3 CMS relies on storing its data in a Relational database management
system (RDBMS). It works out of the box with MySQL. It is known to work
fine with MySQL forks like MariaDB, although they are not officially
supported.

The :code:`\TYPO3\CMS\Core\Database\DatabaseConnection` functions
as a database abstraction layer, handling all calls to the database.
It can be overridden to work with another RDBMS. The "dbal" system
extension does just this, providing support for Microsoft SQL Server,
Oracle and PostgreSQL. It may work with other RDBMS, but without
official support.

Activating "dbal" does cause a performance penalty, due to query
interpretation and table mapping overhead.

