:py:mod:`pywikitools.test.test_data_structures`
===============================================

.. py:module:: pywikitools.test.test_data_structures

.. autoapi-nested-parse::

   Test the different classes and functions of resourcesbot
   Currently the different helper classes are tested well,
   the ResourcesBot class itself isn't tested yet.

   Run tests:
       python3 test_resourcesbot.py



Module Contents
---------------

Classes
~~~~~~~

.. autoapisummary::

   pywikitools.test.test_data_structures.TestTranslationProgress
   pywikitools.test.test_data_structures.TestPdfMetadataSummary
   pywikitools.test.test_data_structures.TestFileInfo
   pywikitools.test.test_data_structures.TestWorksheetInfo
   pywikitools.test.test_data_structures.TestLanguageInfo
   pywikitools.test.test_data_structures.TestLanguageInfoComparison




Attributes
~~~~~~~~~~

.. autoapisummary::

   pywikitools.test.test_data_structures.TEST_TIME
   pywikitools.test.test_data_structures.TEST_URL
   pywikitools.test.test_data_structures.TEST_URL2
   pywikitools.test.test_data_structures.TEST_PROGRESS
   pywikitools.test.test_data_structures.TEST_PROGRESS2
   pywikitools.test.test_data_structures.TEST_PROGRESS3
   pywikitools.test.test_data_structures.TEST_EN_NAME
   pywikitools.test.test_data_structures.TEST_LANG
   pywikitools.test.test_data_structures.TEST_LANG_NAME
   pywikitools.test.test_data_structures.TEST_TITLE
   pywikitools.test.test_data_structures.TEST_VERSION


.. py:data:: TEST_TIME
   :annotation: :str = 2018-12-20T12:58:57+00:00

   

.. py:data:: TEST_URL
   :annotation: :str = https://www.4training.net/mediawiki/images/7/70/Gottes_Reden_wahrnehmen.pdf

   

.. py:data:: TEST_URL2
   :annotation: :str = https://www.4training.net/mediawiki/images/1/15/Gottes_Reden_wahrnehmen.pdf

   

.. py:data:: TEST_PROGRESS
   :annotation: :dict

   

.. py:data:: TEST_PROGRESS2
   :annotation: :dict

   

.. py:data:: TEST_PROGRESS3
   :annotation: :dict

   

.. py:data:: TEST_EN_NAME
   :annotation: :str = Hearing_from_God

   

.. py:data:: TEST_LANG
   :annotation: :str = de

   

.. py:data:: TEST_LANG_NAME
   :annotation: :str = German

   

.. py:data:: TEST_TITLE
   :annotation: :str = Gottes Reden wahrnehmen

   

.. py:data:: TEST_VERSION
   :annotation: :str = 1.2

   

.. py:class:: TestTranslationProgress(methodName='runTest')

   Bases: :py:obj:`unittest.TestCase`

   A class whose instances are single test cases.

   By default, the test code itself should be placed in a method named
   'runTest'.

   If the fixture may be used for many test cases, create as
   many test methods as are needed. When instantiating such a TestCase
   subclass, specify in the constructor arguments the name of the test method
   that the instance is to execute.

   Test authors should subclass TestCase for their own tests. Construction
   and deconstruction of the test's environment ('fixture') can be
   implemented by overriding the 'setUp' and 'tearDown' methods respectively.

   If it is necessary to override the __init__ method, the base class
   __init__ method must always be called. It is important that subclasses
   should not change the signature of their __init__ method, since instances
   of the classes are instantiated automatically by parts of the framework
   in order to be run.

   When subclassing TestCase, you can set these attributes:
   * failureException: determines which exception will be raised when
       the instance's assertion methods fail; test methods raising this
       exception will be deemed to have 'failed' rather than 'errored'.
   * longMessage: determines whether long messages (including repr of
       objects used in assert methods) will be printed on failure in *addition*
       to any explicit message passed.
   * maxDiff: sets the maximum length of a diff in failure messages
       by assert methods using difflib. It is looked up as an instance
       attribute so can be configured by individual tests if required.

   .. py:method:: test_everything(self)



.. py:class:: TestPdfMetadataSummary(methodName='runTest')

   Bases: :py:obj:`unittest.TestCase`

   A class whose instances are single test cases.

   By default, the test code itself should be placed in a method named
   'runTest'.

   If the fixture may be used for many test cases, create as
   many test methods as are needed. When instantiating such a TestCase
   subclass, specify in the constructor arguments the name of the test method
   that the instance is to execute.

   Test authors should subclass TestCase for their own tests. Construction
   and deconstruction of the test's environment ('fixture') can be
   implemented by overriding the 'setUp' and 'tearDown' methods respectively.

   If it is necessary to override the __init__ method, the base class
   __init__ method must always be called. It is important that subclasses
   should not change the signature of their __init__ method, since instances
   of the classes are instantiated automatically by parts of the framework
   in order to be run.

   When subclassing TestCase, you can set these attributes:
   * failureException: determines which exception will be raised when
       the instance's assertion methods fail; test methods raising this
       exception will be deemed to have 'failed' rather than 'errored'.
   * longMessage: determines whether long messages (including repr of
       objects used in assert methods) will be printed on failure in *addition*
       to any explicit message passed.
   * maxDiff: sets the maximum length of a diff in failure messages
       by assert methods using difflib. It is looked up as an instance
       attribute so can be configured by individual tests if required.

   .. py:method:: test_serialization(self)



.. py:class:: TestFileInfo(methodName='runTest')

   Bases: :py:obj:`unittest.TestCase`

   A class whose instances are single test cases.

   By default, the test code itself should be placed in a method named
   'runTest'.

   If the fixture may be used for many test cases, create as
   many test methods as are needed. When instantiating such a TestCase
   subclass, specify in the constructor arguments the name of the test method
   that the instance is to execute.

   Test authors should subclass TestCase for their own tests. Construction
   and deconstruction of the test's environment ('fixture') can be
   implemented by overriding the 'setUp' and 'tearDown' methods respectively.

   If it is necessary to override the __init__ method, the base class
   __init__ method must always be called. It is important that subclasses
   should not change the signature of their __init__ method, since instances
   of the classes are instantiated automatically by parts of the framework
   in order to be run.

   When subclassing TestCase, you can set these attributes:
   * failureException: determines which exception will be raised when
       the instance's assertion methods fail; test methods raising this
       exception will be deemed to have 'failed' rather than 'errored'.
   * longMessage: determines whether long messages (including repr of
       objects used in assert methods) will be printed on failure in *addition*
       to any explicit message passed.
   * maxDiff: sets the maximum length of a diff in failure messages
       by assert methods using difflib. It is looked up as an instance
       attribute so can be configured by individual tests if required.

   .. py:method:: test_basic(self)


   .. py:method:: test_get_file_name(self)


   .. py:method:: test_with_invalid_timestamp(self)


   .. py:method:: test_serialization(self)


   .. py:method:: test_str(self)



.. py:class:: TestWorksheetInfo(methodName='runTest')

   Bases: :py:obj:`unittest.TestCase`

   A class whose instances are single test cases.

   By default, the test code itself should be placed in a method named
   'runTest'.

   If the fixture may be used for many test cases, create as
   many test methods as are needed. When instantiating such a TestCase
   subclass, specify in the constructor arguments the name of the test method
   that the instance is to execute.

   Test authors should subclass TestCase for their own tests. Construction
   and deconstruction of the test's environment ('fixture') can be
   implemented by overriding the 'setUp' and 'tearDown' methods respectively.

   If it is necessary to override the __init__ method, the base class
   __init__ method must always be called. It is important that subclasses
   should not change the signature of their __init__ method, since instances
   of the classes are instantiated automatically by parts of the framework
   in order to be run.

   When subclassing TestCase, you can set these attributes:
   * failureException: determines which exception will be raised when
       the instance's assertion methods fail; test methods raising this
       exception will be deemed to have 'failed' rather than 'errored'.
   * longMessage: determines whether long messages (including repr of
       objects used in assert methods) will be printed on failure in *addition*
       to any explicit message passed.
   * maxDiff: sets the maximum length of a diff in failure messages
       by assert methods using difflib. It is looked up as an instance
       attribute so can be configured by individual tests if required.

   .. py:method:: setUp(self)

      Hook method for setting up the test fixture before exercising it.


   .. py:method:: test_add_file_info(self)


   .. py:method:: test_add_file_info_errors(self)


   .. py:method:: test_get_file_infos(self)


   .. py:method:: test_is_incomplete(self)


   .. py:method:: test_serialization(self)


   .. py:method:: test_to_str(self)


   .. py:method:: test_has_same_version(self)



.. py:class:: TestLanguageInfo(methodName='runTest')

   Bases: :py:obj:`unittest.TestCase`

   A class whose instances are single test cases.

   By default, the test code itself should be placed in a method named
   'runTest'.

   If the fixture may be used for many test cases, create as
   many test methods as are needed. When instantiating such a TestCase
   subclass, specify in the constructor arguments the name of the test method
   that the instance is to execute.

   Test authors should subclass TestCase for their own tests. Construction
   and deconstruction of the test's environment ('fixture') can be
   implemented by overriding the 'setUp' and 'tearDown' methods respectively.

   If it is necessary to override the __init__ method, the base class
   __init__ method must always be called. It is important that subclasses
   should not change the signature of their __init__ method, since instances
   of the classes are instantiated automatically by parts of the framework
   in order to be run.

   When subclassing TestCase, you can set these attributes:
   * failureException: determines which exception will be raised when
       the instance's assertion methods fail; test methods raising this
       exception will be deemed to have 'failed' rather than 'errored'.
   * longMessage: determines whether long messages (including repr of
       objects used in assert methods) will be printed on failure in *addition*
       to any explicit message passed.
   * maxDiff: sets the maximum length of a diff in failure messages
       by assert methods using difflib. It is looked up as an instance
       attribute so can be configured by individual tests if required.

   .. py:method:: setUp(self)

      Hook method for setting up the test fixture before exercising it.


   .. py:method:: test_basic_functionality(self)


   .. py:method:: test_worksheet_has_type(self)


   .. py:method:: test_serialization(self)

      Testing the import/export functionality into JSON representation
      First encode LanguageInfo object into JSON,
      then decode from this JSON representation and check that the result is the same again


   .. py:method:: test_basic_comparison(self)



.. py:class:: TestLanguageInfoComparison(methodName='runTest')

   Bases: :py:obj:`unittest.TestCase`

   Testing all the different possible outcomes of comparing two LanguageInfo objects

   .. py:method:: setUp(self)

      Hook method for setting up the test fixture before exercising it.


   .. py:method:: test_added_files(self)


   .. py:method:: test_deleted_files(self)


   .. py:method:: test_deleted_worksheet(self)


   .. py:method:: test_new_worksheet(self)


   .. py:method:: test_updated_files(self)


   .. py:method:: test_updated_worksheet(self)



