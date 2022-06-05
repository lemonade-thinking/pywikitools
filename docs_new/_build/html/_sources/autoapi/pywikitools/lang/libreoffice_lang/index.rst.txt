:py:mod:`pywikitools.lang.libreoffice_lang`
===========================================

.. py:module:: pywikitools.lang.libreoffice_lang


Module Contents
---------------

Classes
~~~~~~~

.. autoapisummary::

   pywikitools.lang.libreoffice_lang.FontType
   pywikitools.lang.libreoffice_lang.Lang




Attributes
~~~~~~~~~~

.. autoapisummary::

   pywikitools.lang.libreoffice_lang.LANG_LOCALE


.. py:class:: FontType

   Bases: :py:obj:`enum.Enum`

   LibreOffice has three different font categories

   .. py:attribute:: FONT_STANDARD
      :annotation: = 1

      

   .. py:attribute:: FONT_ASIAN
      :annotation: = 2

      

   .. py:attribute:: FONT_CTL
      :annotation: = 3

      


.. py:class:: Lang(language_code: str, country_code: str, font_type: FontType = FontType.FONT_STANDARD, custom_font: Optional[str] = None)

   Defining the parameters of a language for LibreOffice
   When editing styles we need to know which of the three FontTypes a language belongs to.
   The Locale struct has the following parameters: "ISO language code","ISO country code", "variant (browser specific)"
   See also https://www.openoffice.org/api/docs/common/ref/com/sun/star/lang/Locale.html
   Currently there is no need for the variant and we always set it as an empty string

   .. py:attribute:: __slots__
      :annotation: = ['language_code', 'country_code', 'font_type', '_custom_font']

      

   .. py:method:: __str__(self)

      Return str(self).


   .. py:method:: is_standard(self) -> bool


   .. py:method:: is_asian(self) -> bool


   .. py:method:: is_complex(self) -> bool


   .. py:method:: has_custom_font(self) -> bool


   .. py:method:: get_custom_font(self) -> str

      Returns empty string if there was no custom font defined


   .. py:method:: to_locale(self) -> com.sun.star.lang.Locale

      Return a LibreOffice Locale object



.. py:data:: LANG_LOCALE
   :annotation: :Final[Dict[str, Lang]]

   

