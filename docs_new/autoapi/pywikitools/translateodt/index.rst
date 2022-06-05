:py:mod:`pywikitools.translateodt`
==================================

.. py:module:: pywikitools.translateodt

.. autoapi-nested-parse::

   This script produces a translated ODT file for a given worksheet and a given language.
   It does so by:
   1. accessing the worksheet in the mediawiki system together with its translation
   2. downloading the English ODT file (the URL is found in the result of the first step)
   3. doing search and replace: For each translation unit
      - do some cleansing (removing links, unnecessary spaces)
      - split it up even further into small snippets (when the translation unit contains lists etc.)
      - search for each snippet and replace it by its translation
   4. saving the created ODT file

   It does quite some logging:
       - error level: serious issues where the script had to be aborted
       - warning level: these should be checked afterwards
       - info level: going along what the script does
       - debug level: extensive details for debugging

   Command line options:
       -h, --help: help message
       -l [debug, info, warning, error]: set loglevel
       --keep-english-file: don't delete the downloaded English ODT file after we're finished



Module Contents
---------------

Classes
~~~~~~~

.. autoapisummary::

   pywikitools.translateodt.TranslateOdtConfig
   pywikitools.translateodt.TranslateODT




Attributes
~~~~~~~~~~

.. autoapisummary::

   pywikitools.translateodt.SNIPPET_WARN_LENGTH
   pywikitools.translateodt.IGNORE_TEMPLATES
   pywikitools.translateodt.NO_ADD_ENGLISH_VERSION
   pywikitools.translateodt.log_levels


.. py:data:: SNIPPET_WARN_LENGTH
   :annotation: = 3

   

.. py:data:: IGNORE_TEMPLATES
   :annotation: = ['Template:DocDownload', 'Template:OdtDownload', 'Template:PdfDownload',...

   

.. py:data:: NO_ADD_ENGLISH_VERSION
   :annotation: = ['de', 'pt-br', 'cs', 'nl', 'fr', 'id', 'ro', 'es', 'sv', 'tr', 'tr-tanri']

   

.. py:class:: TranslateOdtConfig

   Contains configuration on how to process one worksheet:
   Which translation units should be ignored?
   Which translation units should be processed multiple times?

   It is read from a config file (see TranslateODT.read_worksheet_config()) of the following structure:
   [Ignore]
   # Don't process the following translation units
   Template:BibleReadingHints/18
   Template:BibleReadingHints/25

   [Multiple]
   # Process the following translation unit 5 times
   Template:BibleReadingHints/6 = 5

   .. py:attribute:: __slots__
      :annotation: = ['ignore', 'multiple']

      


.. py:class:: TranslateODT(*, keep_english_file: bool = False, config: Dict[str, Dict[str, str]] = {})

   .. py:method:: _is_search_and_replace_necessary(self, orig: str, trans: str) -> bool

      Checks if we need to do a search and replace or if there are other exceptions
      Logs warnings for certain circumstances
      @return true if we need to do search and replace


   .. py:method:: _process_snippet(self, orig: str, trans: str)

      Looks at one snippet, does some preparations and tries to do search and replace
      @param orig the original string (what to search for)
      @param trans the translated string (what we're going to replace it with)


   .. py:method:: _search_and_replace(self, translated_page: pywikitools.lang.translated_page.TranslatedPage)

      Go through the whole document, search for original text snippets and replace them
      with the translated text snippets


   .. py:method:: _fetch_english_file(self, odt_file: str) -> str

      Download the specified file from the mediawiki server
      @return full path of the downloaded file (empty string on error)


   .. py:method:: _get_odt_filename(self, translated_page: pywikitools.lang.translated_page.TranslatedPage) -> str

      Create filename from headline of translated page

      E.g. page "Hearing from God" -> "Hearing_from_God.odt"
      Compares it to the translated file name and gives a warning if it doesn't match


   .. py:method:: _cleanup_units(self, translated_page: pywikitools.lang.translated_page.TranslatedPage, config: TranslateOdtConfig) -> pywikitools.lang.translated_page.TranslatedPage

      Clean up translation units before we do search and replace:
      - filter out empty/irrelevant units
      - remove [[links]]
      - remove bold/italic/underline formatting from definition
      - replace '' / ''' with <i> / <b> in translation
      - check order of translation units and rearrange if necessary
      - process config: remove ignored units, replicate units that should be processed multiple times

      We can run into troubles if a we have a short translation snippet that is contained in another snippet
      -> search and replace will likely happen at the wrong place
      Let's loop through all units and in the case a snippet is contained in anoher one, we'll move the short
      translation unit to the end: We always try to match long search strings first

      @param config: Instructions on which units should be ignored and which should be processed multiple times
      @return a cleaned up copy TranslatedPage (as in-place manipulation isn't easily possible)


   .. py:method:: special_sort_units(self, units: List[pywikitools.lang.translated_page.TranslationUnit]) -> None

      Order the TranslationUnits in such a way that units with a short snippet
      (that is part of another one) are moved to the end of the list
      ["long", "A long sentence", "long sentence"] -> ["A long sentence", "long sentence", "long"]

      Then we first search and replace the long strings, avoiding replacing at the wrong places.
      This is not a "typical" ordering like ordering alphabetically. That's why we can't use Python's sort()
      method but really must compare each element with all other elements. This has O(n^2) complexity
      but for normal use-cases (less than 1000 translation units) that shouldn't be an issue

      If no snippet contains another one, nothing will be re-ordered
      @param units: The list of translation units will be re-ordered in-place


   .. py:method:: read_worksheet_config(self, worksheet: str) -> TranslateOdtConfig

      Read processing configuration for a specific worksheet from the MediaWiki system.
      The config is read from page [worksheet-name].config in the Project namespace
      (example: https://www.4training.net/4training:Bible_Reading_Hints.config ).
      If there is no such config, the two members of the data structure returned will both be empty


   .. py:method:: translate_odt(self, odt_path: str, translated_page: pywikitools.lang.translated_page.TranslatedPage, config: TranslateOdtConfig) -> None

      Open the specified ODT file and replace contents with translation
      @param odt_path: Path of the ODT file
      @param translated_page: Contains all translation units we'll do search&replace with
      Raises ConnectionError (coming from LibreOffice.open_file) if LibreOffice connection didn't work


   .. py:method:: translate_worksheet(self, worksheet: str, language_code: str) -> Optional[str]

      Create translated worksheet: Fetch information, download original ODT, process it, save translated ODT
      @param worksheet name of the worksheet (e.g. "Forgiving_Step_by_Step")
      @param language_code what language we should translate to (e.g. "de")
      @return file name of the created ODT file (or None in case of error)


   .. py:method:: _set_properties(self, page: pywikitools.lang.translated_page.TranslatedPage)

      Set the properties of the ODT file



.. py:data:: log_levels
   :annotation: :List[str] = ['debug', 'info', 'warning', 'error']

   

