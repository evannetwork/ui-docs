======================
EvanTranslationService
======================

I18N utility functions. Make it possible to share i18n through all applications. The I18N service uses `ngx translate <https://github.com/ngx-translate/core>`_ to handle translations in services and templates.


#. ``monthShortNames`` - ``Array<string>``: array of the 12 translated short names of the months

--------------------------------------------------------------------------------

.. _document_setLanguage:

setLanguage
================================================================================

.. code-block:: typescript

  translateService.setLanguage(language);

Set to the translation service the default language to en and the language to use.

----------
Parameters
----------

#. ``language`` - ``string``: Language to use (en, fr, it, ...)

-------
Example
-------

.. code-block:: typescript

  this.translateService.setLanguage('en')




--------------------------------------------------------------------------------

.. _document_reloadTranslations:

reloadTranslations
================================================================================

.. code-block:: typescript

  translateService.reloadTranslations();

Reload all translations for the current language (triggers ui recalculation, if the ApplicationRef change detection is enabled)

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  translateService.reloadTranslations();


  
  
--------------------------------------------------------------------------------

.. _document_setMultipleLanguageTranslations:

setMultipleLanguageTranslations
================================================================================

.. code-block:: typescript

  translateService.setMultipleLanguageTranslations(translations);

Set translations for multiple languages

----------
Parameters
----------

#. ``translations`` - ``any``: Translations objects wrapped by language keys { en : { 'hello' : 'Hello' }, de : { 'hello' : 'Hallo' } }

-------
Example
-------

.. code-block:: typescript

  this.translateService.setMultipleLanguageTranslations({
    en : { 'hello' : 'Hello' },
    de : { 'hello' : 'Hallo' }
  });




--------------------------------------------------------------------------------

.. _document_setTranslation:

setTranslation
================================================================================

.. code-block:: typescript

  initializedModule.setTranslation(language, translations, disableEvent);

Adds translations to the shared translate service

----------
Parameters
----------

#. ``language`` - ``string``: Language to set translations for
#. ``translations`` - ``any``: Translations to add.
#. ``disableEvent`` - ``boolean``: dont trigger translation update event

-------
Example
-------

.. code-block:: typescript

  this.translateservice.setTranslation('en', {
    'key1': 'translated 1',
    'key2': 'translated 2'
  })




--------------------------------------------------------------------------------

.. _document_setTranslationToCurrentLanguage:

setTranslationToCurrentLanguage
================================================================================

.. code-block:: typescript

  translateService.setTranslationToCurrentLanguage(translations);

Adds translations to the current language service

----------
Parameters
----------

#. ``translations`` - ``any``: Translations to add.

-------
Example
-------

.. code-block:: typescript

  this.translateservice.setTranslationToCurrentLanguage({
    'key1': 'translated 1',
    'key2': 'translated 2'
  })




--------------------------------------------------------------------------------

.. _document_instant:

instant
================================================================================

.. code-block:: typescript

  translateService.instant(key, options);

Returns an translated key instant, synchroniously

----------
Parameters
----------

#. ``key`` - ``string|any``: Key to translate or an object that contains key and translateOptions params
#. ``options`` - ``any``: translation options

-------
Returns
-------

``Promise`` returns ``void``: resolved when done

-------
Example
-------

.. code-block:: typescript

  translateService.instant('key1', { param1: '...' })




--------------------------------------------------------------------------------

.. _document_getTranslatedDescription:

getTranslatedDescription
================================================================================

.. code-block:: typescript

  translateService.getTranslatedDescription(dapp);

Use I18N object from DApp and add an translated property to the DApp, where translations for the current language are saved.

----------
Parameters
----------

#. ``dapp`` - ``any``: The options used for calling

-------
Returns
-------

``any``: The translated dapp description.

-------
Example
-------

Usage: have a look into the description service, `getDescription function <../services/bcc/description.html#getdescription>`_

--------------------------------------------------------------------------------

addSingleTranslation
================================================================================

.. code-block:: typescript

  translateService.addSingleTranslation(arguments);

Adds a single translation to the current language.

----------
Parameters
----------

#. ``key`` - ``string``: key to add
#. ``translation`` - ``string``: value for the key

-------
Example
-------

.. code-block:: typescript

  this.translateservice.addSingleTranslation('key1', 'translated 1')




--------------------------------------------------------------------------------

.. _document_getCurrentLang:

getCurrentLang
================================================================================

.. code-block:: typescript

  translateServic.getCurrentLang();

Returns the current language.

-------
Returns
-------

``string``: The current language key

-------
Example
-------

.. code-block:: typescript

  this.translateservice.getCurrentLang()




--------------------------------------------------------------------------------

.. _document_watchTranslationUpdate:

watchTranslationUpdate
================================================================================

.. code-block:: typescript

  translateService.watchTranslationUpdate(callback);

Adds a translation update watcher.

**Don't forget to unsubscribe on component destroy**.

----------
Parameters
----------

#. ``callback`` - ``Function``: function that is called, when translations were added

-------
Returns
-------

``Function``: call to unsubscribe

-------
Example
-------

.. code-block:: typescript

  const clearFunc = this.translateservice.watchTranslationUpdate(() => {
    console.log('translations added!')
  }))

  ngOnDestroy() {
    clearFunc
  }

