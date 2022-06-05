:py:mod:`pywikitools.test.test_resourcesbot`
============================================

.. py:module:: pywikitools.test.test_resourcesbot

.. autoapi-nested-parse::

   Testing ResourcesBot

   Currently we have only little test coverage...
   TODO: Find ways to run meaningful tests that don't take too long...



Module Contents
---------------

Classes
~~~~~~~

.. autoapisummary::

   pywikitools.test.test_resourcesbot.TestResourcesBot




Attributes
~~~~~~~~~~

.. autoapisummary::

   pywikitools.test.test_resourcesbot.HEARING_FROM_GOD


.. py:data:: HEARING_FROM_GOD
   :annotation: = Multiline-String

    .. raw:: html

        <details><summary>Show Value</summary>

    .. code-block:: text
        :linenos:

        [...]
        <translate>This is the end of the mediawiki source of the Hearing from God worksheet...</translate>
        {{PdfDownload|<translate><!--T:52--> Hearing_from_God.pdf</translate>}}
        {{OdtDownload|<translate><!--T:53--> Hearing_from_God.odt</translate>}}
        {{Version|<translate><!--T:55--> 1.2</translate>}}


    .. raw:: html

        </details>

   

.. py:class:: TestResourcesBot(methodName='runTest')

   Bases: :py:obj:`unittest.TestCase`

   We mock pywikibot because otherwise we would need to provide a valid user-config.py (and because it saves time)

   .. py:method:: setUp(self)

      Hook method for setting up the test fixture before exercising it.


   .. py:method:: test_add_english_file_infos(self, mock_filepage)


   .. py:method:: test_add_file_type(self, mock_filepage, mock_os)


   .. py:method:: test_add_file_type_not_existing(self, mock_filepage)


   .. py:method:: test_add_file_type_exception(self, mock_filepage)


   .. py:method:: test_get_english_version(self)


   .. py:method:: test_run_with_cache(self, mock_consistency_check, mock_export_html, mock_export_repository, mock_write_list, mock_write_report, mock_pywikibot_page, mock_pywikibot_site)



