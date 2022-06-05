:py:mod:`pywikitools.resourcesbot.changes`
==========================================

.. py:module:: pywikitools.resourcesbot.changes

.. autoapi-nested-parse::

   Contains the classes ChangeType, ChangeItem and ChangeLog that describe the list of changes on the 4training.net website
   since the last run of the resourcesbot.



Module Contents
---------------

Classes
~~~~~~~

.. autoapisummary::

   pywikitools.resourcesbot.changes.ChangeType
   pywikitools.resourcesbot.changes.ChangeItem
   pywikitools.resourcesbot.changes.ChangeLog




.. py:class:: ChangeType

   Bases: :py:obj:`enum.Enum`

   The different types of changes that can happen.
   Normally there wouldn't be any deletions

   .. py:attribute:: NEW_WORKSHEET
      :annotation: = new worksheet

      

   .. py:attribute:: NEW_PDF
      :annotation: = new PDF

      

   .. py:attribute:: NEW_ODT
      :annotation: = new ODT

      

   .. py:attribute:: UPDATED_WORKSHEET
      :annotation: = updated worksheet

      

   .. py:attribute:: UPDATED_PDF
      :annotation: = updated PDF

      

   .. py:attribute:: UPDATED_ODT
      :annotation: = updated ODT

      

   .. py:attribute:: DELETED_WORKSHEET
      :annotation: = deleted worksheet

      

   .. py:attribute:: DELETED_PDF
      :annotation: = deleted PDF

      

   .. py:attribute:: DELETED_ODT
      :annotation: = deleted ODT

      


.. py:class:: ChangeItem(worksheet: str, change_type: ChangeType)

   Holds the details of one change
   This shouldn't be modified after creation (is there a way to enforce that?)

   .. py:attribute:: __slots__
      :annotation: = ['worksheet', 'change_type']

      

   .. py:method:: __str__(self) -> str

      Return str(self).


   .. py:method:: __eq__(self, other) -> bool

      Return self==value.


   .. py:method:: __hash__(self) -> int

      Return hash(self).



.. py:class:: ChangeLog

   Holds all changes that happened in one language since the last resourcesbot run

   .. py:attribute:: __slots__
      :annotation: = ['_changes', '_iterate_pos']

      

   .. py:method:: add_change(self, worksheet: str, change_type: ChangeType)


   .. py:method:: is_empty(self)


   .. py:method:: count_changes(self) -> int


   .. py:method:: __str__(self) -> str

      Return str(self).


   .. py:method:: __iter__(self)

      Make this class iterable in a simple way (not suitable for concurrency!)


   .. py:method:: __next__(self) -> ChangeItem

      Return a next ChangeItem



