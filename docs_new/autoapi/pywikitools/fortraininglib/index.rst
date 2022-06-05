:py:mod:`pywikitools.fortraininglib`
====================================

.. py:module:: pywikitools.fortraininglib

.. autoapi-nested-parse::

   4training.net library

   Contains common functions, many of wrapping API calls
   We didn't name this 4traininglib.py because starting a python file name with a number causes problems



Module Contents
---------------

Classes
~~~~~~~

.. autoapisummary::

   pywikitools.fortraininglib.ForTrainingLib




Attributes
~~~~~~~~~~

.. autoapisummary::

   pywikitools.fortraininglib.RTL_LANGUAGES


.. py:data:: RTL_LANGUAGES
   :annotation: = ['ar', 'fa', 'ckb', 'ar-urdun', 'ps', 'ur']

   

.. py:class:: ForTrainingLib(base_url: str, api_path: str = '/mediawiki/api.php')

   .. py:attribute:: TIMEOUT
      :annotation: :int = 30

      

   .. py:attribute:: CONNECT_RETRIES
      :annotation: :int = 3

      

   .. py:method:: _get(self, params: Dict[str, str]) -> Any

      Wrapper around requests.get to handle timeouts and other issues
      @return JSON (as from response.json()) or {} in case of an error


   .. py:method:: get_worksheet_list(self) -> List[str]

      Returns the list of all worksheets. For now hard-coded as this doesn't change very often. Could be changed to
      retrieve that information from the backend.
      @param: -
      @return: worksheet_list (list): List of all worksheets.


   .. py:method:: get_file_types(self) -> List[str]

      Returns the supported file types.
      @param: -
      @return: file_types (list): list of supported file types


   .. py:method:: get_language_direction(self, language_code: str) -> str

      Returns language direction 'rtl' or 'ltr'

      This is hard-coded here to save time.
      See tools/check_language_directions.py for checking this for correctness
      by requesting language directions from the mediawiki API.


   .. py:method:: get_language_name(self, language_code: str, translate_to: Optional[str] = None) -> Optional[str]

      Returns the name of a language as either the autonym or translated into another language
      This function is calling the mediawiki {{#language:}} parser function and does no additional checks
      See https://www.mediawiki.org/wiki/Help:Magic_words#Miscellaneous
      .. rubric:: Examples

      get_language_name('de') = 'Deutsch'
      get_language_name('de','en') = 'German'
      get_language_name('nonsense') = 'nonsense' FYI

      @param language_code: identifies the language we're interested in
      @param translate_to: optional target language the language name should be translated into (None returns autonym)
      @return Language name if successful
      @return None in case of error (also logs a warning)


   .. py:method:: get_file_url(self, filename: str) -> Optional[str]

      Return the full URL of the requested file

      @return string with the URL or None in case of an error


   .. py:method:: get_page_source(self, page: str, revision_id: Optional[int] = None) -> Optional[str]

      Return the wikitext (source) of a page.
      @param revision_id Specify this to retrieve an older revision (default: retrieve current revision)
      @return None on error


   .. py:method:: get_page_html(self, page: str) -> Optional[str]

      Return the HTML representation of a page
      @return None on error


   .. py:method:: get_translated_title(self, page: str, language_code: str, revision_id: Optional[int] = None) -> Optional[str]

      Returns the translated title of a worksheet
      @return None on error


   .. py:method:: get_translated_unit(self, page: str, language_code: str, identifier: int, revision_id: Optional[int] = None) -> Optional[str]

      Returns the translation of one translation unit of a page into a given language

      This is comparable to e.g. https://www.4training.net/Translations:Hearing_from_God/2/de
      but returns wikitext, not HTML

      @param identifier: number of the translation unit (mediawiki internal)
      (use get_translated_title() for getting the "Page display title" translation unit)
      @param revision_id: Specify this to retrieve an older revision (default: retrieve current revision)
      (similar to https://www.4training.net/mediawiki/index.php?title=Translations:Hearing_from_God/2/de&oldid=26928 )
      @return the translated string or None if translation doesn't exist


   .. py:method:: get_pdf_name(self, page: str, language_code: str) -> Optional[str]

      returns the name of the PDF associated with that worksheet translated into a specific language
      @return None in case we didn't find it


   .. py:method:: get_version(self, page: str, language_code: str) -> Optional[str]

      Returns the version of the page in the specified language
      @return None in case we didn't find it


   .. py:method:: list_page_translations(self, page: str, include_unfinished=False) -> Dict[str, pywikitools.resourcesbot.data_structures.TranslationProgress]

      Returns all the existing translations of a page
      @param page the worksheet name
      @param include_unfinished whether unfinished translations should also be included

      Example: https://www.4training.net/mediawiki/api.php?action=query&meta=messagegroupstats&mgsgroup=page-Church
      @return a dictionary of language codes -> TranslationProgress objects
              In case no other translation exists the result will be {'en': progress object}
              In case of an error the map will be empty {}
              if you're not interested in the unfinished translations, you're probably only interested in the keys


   .. py:method:: list_page_templates(self, page: str) -> List[str]

      Returns list of templates that are transcluded by a given page
      Strips potential language code at the end of a template (returns 'Template:Italic', not 'Template:Italic/en')
      See also https://translatewiki.net/w/api.php?action=help&modules=query%2Btemplates
      Example: https://www.4training.net/mediawiki/api.php?action=query&format=json&titles=Polish&prop=templates
      @return empty list in case of an error


   .. py:method:: get_translation_units(self, page: str, language_code: str, limit: int = 500) -> Optional[pywikitools.lang.translated_page.TranslatedPage]

      Get the translation units of a page translated into the language identified by language_code
      Example: https://www.4training.net/mediawiki/api.php?action=query&format=json&list=messagecollection&mcgroup=page-Forgiving_Step_by_Step&mclanguage=de  # noqa: E501
      @param limit: Maximum number of translation units to return (default limit in API is also 500)
      @return None in case of an error


   .. py:method:: title_to_message(self, title: str) -> str

      Converts a mediawiki title to its corresponding system message
      .. rubric:: Examples

      Prayer -> sidebar-prayer
      Forgiving_Step_by_Step -> sidebar-forgivingstepbystep
      The_Three-Thirds_Process -> sidebar-thethreethirdsprocess
      God's_Story_(five_fingers) -> sidebar-godsstory-fivefingers


   .. py:method:: expand_template(self, raw_template: str) -> str

      TODO more documentation
      https://www.4training.net/mediawiki/api.php?action=expandtemplates&text={{CC0Notice/de|1.3}}&prop=wikitext&format=json


   .. py:method:: get_cc0_notice(self, version: str, language_code: str) -> str

      Returns the translated CC0 notice (https://www.4training.net/Template:CC0Notice)
      @param version Version number to put in
      @param language_code Which language to translate it
      @return The translated notice (for footers in worksheets)
      @return string with a TODO in case the translation doesn't exist


   .. py:method:: mark_for_translation(self, title: str, user_name: str, password: str)

      Mark a page for translation

      Unfortunately this functionality is not exposed in the API yet. (See https://phabricator.wikimedia.org/T235397)
      Also pywikibot doesn't support calling anything outside the API
      So we need to log in on our own and call Special:PageTranslation in the necessary way:
      1. GET https://www.4training.net/mediawiki/index.php?title=Special:PageTranslation&target=Afrikaans&do=mark
      2. scrape the answer: we need the content of the hidden input fields
      3. POST https://www.4training.net/Special:PageTranslation (with some data)
      @param title The title of the page that should be marked for translation
      @todo currently it's always marking the page for translation, even if there are no changes -> add check
      @todo better error handling, return if we were successful
      @todo add timeout=TIMEOUT and handle timeouts correctly



