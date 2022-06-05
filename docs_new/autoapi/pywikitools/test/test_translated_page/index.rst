:py:mod:`pywikitools.test.test_translated_page`
===============================================

.. py:module:: pywikitools.test.test_translated_page


Module Contents
---------------

Classes
~~~~~~~

.. autoapisummary::

   pywikitools.test.test_translated_page.TestTranslationUnit
   pywikitools.test.test_translated_page.TestTranslationSnippet
   pywikitools.test.test_translated_page.TestTranslatedPage




Attributes
~~~~~~~~~~

.. autoapisummary::

   pywikitools.test.test_translated_page.TEST_UNIT_WITH_LISTS
   pywikitools.test.test_translated_page.TEST_UNIT_WITH_LISTS_DE
   pywikitools.test.test_translated_page.TEST_UNIT_WITH_DEFINITION
   pywikitools.test.test_translated_page.TEST_UNIT_WITH_DEFINITION_DE_ERROR
   pywikitools.test.test_translated_page.TEST_UNIT_WITH_HEADLINE
   pywikitools.test.test_translated_page.TEST_UNIT_WITH_BR
   pywikitools.test.test_translated_page.LIST_TEST


.. py:data:: TEST_UNIT_WITH_LISTS
   :annotation: = Multiline-String

    .. raw:: html

        <details><summary>Show Value</summary>

    .. code-block:: text
        :linenos:

        Jesus would not...
        * <b>sell your data</b>
        * trick you into his business
        * give quick & dirty fixes
        Jesus would...
        # give everything away freely
        # train people & share his skills
        # care for people & treat them well


    .. raw:: html

        </details>

   

.. py:data:: TEST_UNIT_WITH_LISTS_DE
   :annotation: = Multiline-String

    .. raw:: html

        <details><summary>Show Value</summary>

    .. code-block:: text
        :linenos:

        Jesus würde nicht...
        * <b>deine Daten verkaufen</b>
        * dich in sein Geschäftsmodell reintricksen
        * keine "quick & dirty" Lösungen anbieten
        Jesus würde...
        # alles frei weitergeben
        # Menschen trainieren und sein Wissen teilen
        # sich um Menschen kümmern und sie gut behandeln


    .. raw:: html

        </details>

   

.. py:data:: TEST_UNIT_WITH_DEFINITION
   :annotation: = Multiline-String

    .. raw:: html

        <details><summary>Show Value</summary>

    .. code-block:: text
        :linenos:

        ;Forgiving myself
        :Sometimes we’re angry at ourselves or blame ourselves for something. God offers a way to forgive us and
        cleanse us through Jesus Christ. Forgiving myself means taking His offer and applying it to myself.
        ;“Forgiving” God
        :Sometimes we have negative thoughts about God or are even mad at Him. God doesn’t make mistakes,
        so in that sense we can’t forgive Him. But it is important that we let go of our frustrations and
        negative feelings towards Him.


    .. raw:: html

        </details>

   

.. py:data:: TEST_UNIT_WITH_DEFINITION_DE_ERROR
   :annotation: = Multiline-String

    .. raw:: html

        <details><summary>Show Value</summary>

    .. code-block:: text
        :linenos:

        ;Mir selbst vergeben
        :Es kann sein, dass wir wütend auf uns selbst sind und uns etwas vorwerfen.
        Gott bietet uns einen Weg an, wie er uns durch Jesus Christus vergeben und reinigen möchte.
        Mir selbst vergeben bedeutet, sein Angebot anzunehmen und es auf mich anzuwenden.
        Gott „vergeben“
        :Manchmal haben wir negative Gedanken über Gott oder sind zornig auf ihn.
        Gott macht keine Fehler und in dem Sinn können wir ihm nicht vergeben. Aber es ist wichtig,
        dass wir Enttäuschungen über ihn loslassen und uns von allen negativen Gefühlen ihm gegenüber trennen.


    .. raw:: html

        </details>

   

.. py:data:: TEST_UNIT_WITH_HEADLINE
   :annotation: = Multiline-String

    .. raw:: html

        <details><summary>Show Value</summary>

    .. code-block:: text
        :linenos:

        == Dealing with Money ==
        Money is a tool. With the same banknote I can bring blessing or harm.
        === Be fair ===
        With money comes temptation.


    .. raw:: html

        </details>

   

.. py:data:: TEST_UNIT_WITH_BR
   :annotation: = Multiline-String

    .. raw:: html

        <details><summary>Show Value</summary>

    .. code-block:: text
        :linenos:

        But God wants us to see clearly and know the truth.
        He wants to set us free from our distorted views and the negative consequences they have for us and other people.<br/>

        Jesus says in John 8:31-32: <i>“If you obey my teaching, you are really my disciples.
        Then you will know the truth. And the truth will set you free.”</i>

    .. raw:: html

        </details>

   

.. py:data:: LIST_TEST
   :annotation: = Multiline-String

    .. raw:: html

        <details><summary>Show Value</summary>

    .. code-block:: text
        :linenos:

        * soll er Gott um Vergebung bitten, dass er die Lüge geglaubt und mit ihr zusammengearbeitet hat,
        * die Lüge an Gott abgeben und
        * fragen, „Gott, was ist die Wahrheit stattdessen?“
        Lass denjenigen fragen, „Welche Lüge habe ich dadurch über mich gelernt?“ und fahre wie oben fort.


    .. raw:: html

        </details>

   

.. py:class:: TestTranslationUnit(methodName='runTest')

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

   .. py:method:: test_untranslated_unit(self)


   .. py:method:: test_read_and_write(self)


   .. py:method:: test_is_title(self)


   .. py:method:: test_split_into_snippets(self)


   .. py:method:: test_is_translation_well_structured(self)


   .. py:method:: test_iteration(self)


   .. py:method:: test_remove_links(self)


   .. py:method:: test_copy(self)


   .. py:method:: test_comparison(self)



.. py:class:: TestTranslationSnippet(methodName='runTest')

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

   .. py:method:: test_simple_functions(self)


   .. py:method:: test_str(self)



.. py:class:: TestTranslatedPage(methodName='runTest')

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

   .. py:method:: test_untranslated_page(self)


   .. py:method:: test_returning_empty_strings(self)


   .. py:method:: test_with_real_data(self)



