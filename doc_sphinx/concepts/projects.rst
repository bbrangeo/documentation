.. index::
   single: execution
   single: context
   single: projects
   module: core

==========
Projects
==========

Concept
=========

A project is a place where IFC files and documents are stored. IFC files and documents can be uploaded and organized, checkplans are defined.

A project is attached to a cloud and a cloud can host an infinite number of projects.

A project member can see all other members, and admin member can add a user to the project.

References
================

* GET ``/user/projects``
* GET ``/cloud/{cloud_pk}/project``
* POST ``/cloud/{cloud_pk}/project``
