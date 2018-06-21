=================
EvanSlidesService
=================

Ionic Slide helper service to work around Ionic bugs.




--------------------------------------------------------------------------------

.. _document_afterViewInit:

afterViewInit
================================================================================

.. code-block:: typescript

  slidesService.afterViewInit(slide: Slides);

Use this function within your component to lock slides after ngAfterViewInit to prevent weird slide behavior.

----------
Parameters
----------

#. ``slide`` - ``Slides``: Tslides object to lock

-------
Example
-------

.. code-block:: typescript

  slidesService.afterViewInit(this.slidesComponent);




--------------------------------------------------------------------------------

.. _document_goToSlide:

goToSlide
================================================================================

.. code-block:: typescript

  slidesService.goToSlide(slide, index);

Navigate to a specific slide using locked slides.

----------
Parameters
----------

#. ``slide`` - ``Slide``: slides to slide
#. ``index`` - ``number``: index of slide to slide to


-------
Example
-------

.. code-block:: typescript

  slidesService.goToSlide(this.slidesComponent, 5),