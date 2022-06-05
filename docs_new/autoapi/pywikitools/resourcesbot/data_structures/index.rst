:py:mod:`pywikitools.resourcesbot.data_structures`
==================================================

.. py:module:: pywikitools.resourcesbot.data_structures


Module Contents
---------------

Classes
~~~~~~~

.. autoapisummary::

   pywikitools.resourcesbot.data_structures.FileInfo
   pywikitools.resourcesbot.data_structures.WorksheetInfo
   pywikitools.resourcesbot.data_structures.LanguageInfo
   pywikitools.resourcesbot.data_structures.DataStructureEncoder



Functions
~~~~~~~~~

.. autoapisummary::

   pywikitools.resourcesbot.data_structures.json_decode



.. py:class:: FileInfo(file_type: str, url: str, timestamp: Union[datetime.datetime, str], translation_unit: Optional[int] = None)

   This class holds information on one file that is available on the website.

   .. note:: This class should not be modified after the creation.

   .. py:attribute:: __slots__
      :annotation: = ['file_type', 'url', 'timestamp', 'translation_unit']

      

   .. py:method:: get_file_name(self) -> str

      Return file name out of url


   .. py:method:: __str__(self)

      Return str(self).



.. py:class:: WorksheetInfo(page: str, language_code: str, title: str, progress: TranslationProgress, version: str, version_unit: Optional[int] = None)

   Holds information on one worksheet in one specific language
   Only for worksheets that are at least partially translated

   .. py:attribute:: __slots__
      :annotation: = ['page', 'language_code', 'title', 'progress', 'version', 'version_unit', '_files']

      

   .. py:method:: add_file_info(self, file_info: Optional[FileInfo] = None, file_type: Optional[str] = None, from_pywikibot: Optional[pywikibot.page.FileInfo] = None, unit: Optional[int] = None)

      Add information about another file associated with this worksheet.
      You can call the function in two different ways:
      - providing file_info
      - providing file_type and from_pywikibot (and potentially unit)
      This will log on errors but shouldn't raise exceptions


   .. py:method:: get_file_infos(self) -> Dict[str, FileInfo]

      Returns all available files associated with this worksheet


   .. py:method:: has_file_type(self, file_type: str) -> bool

      Does the worksheet have a file for download (e.g. "pdf")?


   .. py:method:: get_file_type_info(self, file_type: str) -> Optional[FileInfo]

      Returns FileInfo of specified type (e.g. "pdf"), None if not existing


   .. py:method:: is_incomplete(self) -> bool

      A translation is incomplete if most units are translated but at least one is not translated or fuzzy


   .. py:method:: __str__(self) -> str

      For debugging purposes: Format all data as a human-readable string



.. py:class:: LanguageInfo(language_code: str)

   Holds information on all available worksheets in one specific language

   .. py:attribute:: __slots__
      :annotation: = ['language_code', 'worksheets']

      

   .. py:method:: add_worksheet_info(self, name: str, worksheet_info: WorksheetInfo)


   .. py:method:: has_worksheet(self, name: str) -> bool


   .. py:method:: get_worksheet(self, name: str) -> Optional[WorksheetInfo]


   .. py:method:: worksheet_has_type(self, name: str, file_type: str) -> bool

      Convienence method combining LanguageInfo.has_worksheet() and WorksheetInfo.has_file_type()


   .. py:method:: compare(self, old) -> pywikitools.resourcesbot.changes.ChangeLog

      Compare ourselves to another (older) LanguageInfo object: have there been changes / updates?

      @return data structure with all changes


   .. py:method:: list_worksheets_with_missing_pdf(self) -> List[str]

      Returns a list of worksheets which are translated but are missing the PDF


   .. py:method:: list_incomplete_translations(self) -> List[WorksheetInfo]


   .. py:method:: count_finished_translations(self) -> int



.. py:function:: json_decode(data: Dict[str, Any])

   Deserializes a JSON-formatted string back into
   TranslationProgress / FileInfo / WorksheetInfo / LanguageInfo objects.
   @raises AssertionError if data is malformatted


.. py:class:: DataStructureEncoder(*, skipkeys=False, ensure_ascii=True, check_circular=True, allow_nan=True, sort_keys=False, indent=None, separators=None, default=None)

   Bases: :py:obj:`json.JSONEncoder`

   Serializes a LanguageInfo / WorksheetInfo / FileInfo / TranslationProgress object into a JSON string

   .. py:method:: default(self, obj)

      Implement this method in a subclass such that it returns
      a serializable object for ``o``, or calls the base implementation
      (to raise a ``TypeError``).

      For example, to support arbitrary iterators, you could
      implement default like this::

          def default(self, o):
              try:
                  iterable = iter(o)
              except TypeError:
                  pass
              else:
                  return list(iterable)
              # Let the base class default method raise the TypeError
              return JSONEncoder.default(self, o)




