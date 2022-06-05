:py:mod:`correct_bot`
=====================

.. py:module:: correct_bot

.. autoapi-nested-parse::

   Bot that replaces common typos for different languages.

   All correction rules for different languages are in the correctors/ folder in separate classes.

   Run with dummy page:
       python3 correct_bot.py Test de
       python3 correct_bot.py CorrectTestpage fr

   TODO: Not yet operational



Module Contents
---------------

Classes
~~~~~~~

.. autoapisummary::

   correct_bot.CorrectBot



Functions
~~~~~~~~~

.. autoapisummary::

   correct_bot.parse_arguments



Attributes
~~~~~~~~~~

.. autoapisummary::

   correct_bot.args


.. py:class:: CorrectBot(fortraininglib: pywikitools.fortraininglib.ForTrainingLib, simulate: bool = False)

   Main class for doing corrections

   .. py:method:: _load_corrector(self, language_code: str) -> Callable

      Load the corrector class for the specified language and return it.

      Raises ImportError if corrector class can't be found


   .. py:method:: check_unit(self, corrector: pywikitools.correctbot.correctors.base.CorrectorBase, unit: pywikitools.lang.translated_page.TranslationUnit) -> Optional[pywikitools.correctbot.correctors.base.CorrectionResult]

      Check one specific translation unit: Run the right correction rules on it.
      For this we analyze: Is it a title, a file name or a "normal" translation unit?


   .. py:method:: check_page(self, page: str, language_code: str) -> bool

      Check one specific page and store the results in this class

      This does not write anything back to the server. Changes can be read with
      get_stats(), get_correction_counter() and get_diff()
      @returns True on success, False if an error occurred


   .. py:method:: get_stats(self) -> str

      Return a summary: which correction rules could be applied (in the last run)?


   .. py:method:: get_correction_counter(self) -> int

      How many corrections did we do (in the last run)?


   .. py:method:: get_diff(self) -> str

      Print a diff of the corrections (made in the last run)


   .. py:method:: run(self, page: str, language_code: str)

      Correct the translation of a page.
      TODO write it back to the system if we're not in simulation mode



.. py:function:: parse_arguments() -> argparse.Namespace

   Parses the arguments given from outside


.. py:data:: args
   

   

