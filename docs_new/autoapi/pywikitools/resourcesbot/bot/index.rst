:py:mod:`pywikitools.resourcesbot.bot`
======================================

.. py:module:: pywikitools.resourcesbot.bot


Module Contents
---------------

Classes
~~~~~~~

.. autoapisummary::

   pywikitools.resourcesbot.bot.ResourcesBot




.. py:class:: ResourcesBot(config: configparser.ConfigParser, limit_to_lang: Optional[str] = None, rewrite_all: bool = False, read_from_cache: bool = False)

   Contains all the logic of our bot

   .. py:method:: run(self)


   .. py:method:: get_english_version(self, page_source: str) -> Tuple[str, int]

      Extract version of an English worksheet
      @return Tuple of version string and the number of the translation unit where it is stored


   .. py:method:: _query_translated_file(self, worksheet: pywikitools.resourcesbot.data_structures.WorksheetInfo, english_file_info: pywikitools.resourcesbot.data_structures.FileInfo) -> None

      Query the name of the translated file and see if it is valid. If yes, go ahead and see if such a file exists


   .. py:method:: _add_file_type(self, worksheet: pywikitools.resourcesbot.data_structures.WorksheetInfo, file_type: str, file_name: str, unit: Optional[int] = None)

      Try to add details on this translated file to worksheet - warn if it doesn't exist.


   .. py:method:: _add_english_file_infos(self, page_source: str, worksheet: pywikitools.resourcesbot.data_structures.WorksheetInfo) -> None

      Finds out the names of the English downloadable files (originals)
      and adds them to worksheet


   .. py:method:: _query_translations(self, page: str)

      Go through one worksheet, check all existing translations and gather information into self._result
      @param: page: Name of the worksheet


   .. py:method:: _sync_and_compare(self, language_info: pywikitools.resourcesbot.data_structures.LanguageInfo) -> pywikitools.resourcesbot.changes.ChangeLog

      Synchronize our generated data on this language with our "database" and return the changes.

      The "database" is the JSON representation of LanguageInfo and is stored in a mediawiki page.

      @param lang language code
      @return comparison to what was previously stored in our database


   .. py:method:: _save_languages_list(self)

      Save a list of language codes of all our languages to the mediawiki server
      We want this list so that the bot can be run with --read-from-cache for all languages

      The list is stored to https://www.4training.net/4training:languages.json in alphabetical order


   .. py:method:: _save_number_of_languages(self)

      Count number of languages we have and save them to https://www.4training.net/MediaWiki:Numberoflanguages
      Language variants (any language code containing a "-") are not counted extra.
      TODO: Discuss how we want to count in some edge cases, e.g. count pt-br always extra as we have a
      separate page for Brazilian Portuguese?
      @param language_list: List of language codes



