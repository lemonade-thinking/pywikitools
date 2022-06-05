:py:mod:`pywikitools.generateodtbot`
====================================

.. py:module:: pywikitools.generateodtbot

.. autoapi-nested-parse::

   Bot that is generating translated odt files:
       - calls translateodt.py (which does the actual work)
       - calls dropboxupload.py for uploading the result to the dropbox
       - sends notification to the mediawiki user who requested the action together with log output (only warning level)
       - sends notification to admin with log output (both warning and debug level)



Module Contents
---------------


Functions
~~~~~~~~~

.. autoapisummary::

   pywikitools.generateodtbot.usage
   pywikitools.generateodtbot.notify_user



Attributes
~~~~~~~~~~

.. autoapisummary::

   pywikitools.generateodtbot.CONNECT_TRIES
   pywikitools.generateodtbot.LOCKFILENAME
   pywikitools.generateodtbot.global_site
   pywikitools.generateodtbot.config
   pywikitools.generateodtbot.logger
   pywikitools.generateodtbot.fformatter
   pywikitools.generateodtbot.log_path
   pywikitools.generateodtbot.fh
   pywikitools.generateodtbot.fh_debug
   pywikitools.generateodtbot.sformatter
   pywikitools.generateodtbot.stream
   pywikitools.generateodtbot.sh
   pywikitools.generateodtbot.stream_debug
   pywikitools.generateodtbot.sh_debug
   pywikitools.generateodtbot.worksheet
   pywikitools.generateodtbot.languagecode
   pywikitools.generateodtbot.username
   pywikitools.generateodtbot.base_path
   pywikitools.generateodtbot.f
   pywikitools.generateodtbot.retries
   pywikitools.generateodtbot.got_lock
   pywikitools.generateodtbot.got_lock
   pywikitools.generateodtbot.filename


.. py:data:: CONNECT_TRIES
   :annotation: = 10

   

.. py:data:: LOCKFILENAME
   :annotation: = generateodtbot.lock

   

.. py:data:: global_site
   

   

.. py:data:: config
   

   

.. py:data:: logger
   

   

.. py:data:: fformatter
   

   

.. py:data:: log_path
   

   

.. py:data:: fh
   

   

.. py:data:: fh_debug
   

   

.. py:data:: sformatter
   

   

.. py:data:: stream
   

   

.. py:data:: sh
   

   

.. py:data:: stream_debug
   

   

.. py:data:: sh_debug
   

   

.. py:function:: usage()


.. py:function:: notify_user(username: str, worksheet: str, languagecode: str, admin: bool)


.. py:data:: worksheet
   

   

.. py:data:: languagecode
   

   

.. py:data:: username
   

   

.. py:data:: base_path
   

   

.. py:data:: f
   

   

.. py:data:: retries
   :annotation: = 0

   

.. py:data:: got_lock
   :annotation: = False

   

.. py:data:: got_lock
   :annotation: = True

   

.. py:data:: filename
   

   

