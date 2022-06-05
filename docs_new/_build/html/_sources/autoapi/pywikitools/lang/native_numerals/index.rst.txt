:py:mod:`pywikitools.lang.native_numerals`
==========================================

.. py:module:: pywikitools.lang.native_numerals


Module Contents
---------------

Classes
~~~~~~~

.. autoapisummary::

   pywikitools.lang.native_numerals.NativeNumerals



Functions
~~~~~~~~~

.. autoapisummary::

   pywikitools.lang.native_numerals.native_to_standard_numeral



.. py:class:: NativeNumerals

   .. py:attribute:: hindi
      :annotation: :Dict[str, str]

      

   .. py:attribute:: kannada
      :annotation: :Dict[str, str]

      

   .. py:attribute:: tamil
      :annotation: :Dict[str, str]

      

   .. py:attribute:: languages
      :annotation: :Dict[str, Dict]

      


.. py:function:: native_to_standard_numeral(language_code: str, native_text: str) -> str

   Replace native numerals in a str with standard numerals.

   @param language_code Selects which languages numerals are to be replaced
   @param native_text Text in which native numerals are to be replaced
   @return str with native numerals replaced by standard numerals


