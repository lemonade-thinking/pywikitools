:py:mod:`pywikitools.resourcesbot.write_lists`
==============================================

.. py:module:: pywikitools.resourcesbot.write_lists


Module Contents
---------------

Classes
~~~~~~~

.. autoapisummary::

   pywikitools.resourcesbot.write_lists.WriteList




.. py:class:: WriteList(fortraininglib: pywikitools.fortraininglib.ForTrainingLib, site: pywikibot.site.APISite, user_name: str, password: str, force_rewrite: bool = False)

   Bases: :py:obj:`pywikitools.resourcesbot.post_processing.LanguagePostProcessor`

   Write/update the list of available training resources for languages.

   We only show worksheets that have a PDF file (to ensure good quality)

   This class can be re-used to call run() several times

   .. py:method:: needs_rewrite(self, language_info: pywikitools.resourcesbot.data_structures.LanguageInfo, change_log: pywikitools.resourcesbot.changes.ChangeLog) -> bool

      Determine whether the list of available training resources needs to be rewritten.


   .. py:method:: _create_file_mediawiki(self, file_info: Optional[pywikitools.resourcesbot.data_structures.FileInfo]) -> str

      Return string with mediawiki code to display a downloadable file

      Example: [[File:pdficon_small.png|link={{filepath:Gebet.pdf}}]]
      @return empty string if file_info is None


   .. py:method:: create_mediawiki(self, language_info: pywikitools.resourcesbot.data_structures.LanguageInfo) -> str

      Create the mediawiki string for the list of available training resources

      Output should look like the following line:
      * [[God's_Story_(five_fingers)/de|{{int:sidebar-godsstory-fivefingers}}]]           [[File:pdficon_small.png|link={{filepath:Gottes_Geschichte_(fünf_Finger).pdf}}]]           [[File:printpdficon_small.png|link={{filepath:Gottes_Geschichte_(fünf_Finger).pdf}}]]           [[File:odticon_small.png|link={{filepath:Gottes_Geschichte_(fünf_Finger).odt}}]]


   .. py:method:: _find_resources_list(self, page_content: str, language: str) -> Tuple[int, int]

      Find the exact positions of the existing list of available training resources in the page
      @param page_content: mediawiki "source" of the language info page that we're searching through
      @param language: The language name (as in LanguageInfo.english_name)
      @return Tuple of start and end position. (0, 0) indicates we couldn't find it


   .. py:method:: run(self, language_info: pywikitools.resourcesbot.data_structures.LanguageInfo, change_log: pywikitools.resourcesbot.changes.ChangeLog) -> None

      Entry point



