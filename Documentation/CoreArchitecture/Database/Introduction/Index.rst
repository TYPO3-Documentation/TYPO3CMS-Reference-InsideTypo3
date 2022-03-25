
.. include:: /Includes.rst.txt


.. _database-introduction:

Introduction
^^^^^^^^^^^^

TYPO3 CMS relies on storing its data in a Relational database management
system (RDBMS). The Doctrine dbal component is used to enable connecting to
different database management systems. Most used is still MySQL, but thanks
to Doctrine others like MariaDB, Postgres, Oracle and SQLServer are also an
option.

During the install progress you can select the corresponding DBMS.

.. note::
   At the time of writing the installation process does not fully work for
   SQL Server, the connection settings have to be manually configured in that case.
