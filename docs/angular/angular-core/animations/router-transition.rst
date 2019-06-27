=================
router transition
=================

.. list-table:: 
   :widths: auto
   :stub-columns: 1

   * - Source
     - `router-transition <https://github.com/evannetwork/ui-angular-core/blob/develop/src/animations/router-transition.ts>`__

createRouterTransition
======================
.. code-block:: typescript

  createRouterTransition(animationDefinitions)

Create a transition for several an router-outlet to get swiping animations between routing changes.

-------
Returns
-------

`AnimationDefinition``: The animation definitions

-------
Example
-------
Slide two components to the left / right.

- component.ts

.. code-block:: typescript

  @Component({
    ...
    animations: [
      createRouterTransition([
        new AnimationDefinition('component1', '=>', 'component2', 'right'),
        new AnimationDefinition('component2', '=>', 'component1', 'left'),
      ])
    ]
  })
  

- component.html

:: 

  <div evan-content [@routerTransition]="o?.activatedRouteData?.state">
    <router-outlet #o="outlet"></router-outlet>
  </div>




--------------------------------------------------------------------------------

.. _angular_core_AnimationDefinition_AnimationDefinition:

AnimationDefinition
================================================================================

.. code-block:: typescript
  
  new AnimationDefinition(from, direction, to, type)

Defines an AnimationDefinition that specifies the transition that should be build.

----------
Parameters
----------

#. ``from`` - ``string``: forward, backward
#. ``direction`` - ``strin``: from state
#. ``to`` - ``string``: =>, <=, <=>
#. ``type`` - ``string``: to state

-------
Example
-------

.. code-block:: typescript

  new AnimationDefinition('component1', '=>', 'component2', 'right')


--------------------------------------------------------------------------------

.. _angular_core_router_transitions_getSideSlideAnimation:

getSideSlideAnimation
================================================================================

.. code-block:: typescript

  getSideSlideAnimation(translateEnter, translateEnterTo, translateLeave, translateLeaveTo, translateDirection);

Generates an slide animation for angular animate.

----------
Parameters
----------

#. ``translateEnter`` - ``number``:  From translateDirection on enter
#. ``translateEnterTo`` - ``number``: To translateDirection on enter
#. ``translateLeave`` - ``number``:  From translateDirection on leave
#. ``translateLeaveTo`` - ``number``: To translateDirection on leave
#. ``translateDirection`` - ``number``: translateX / translateY

-------
Returns
-------

``Array<any>`` : The side slide animation.

-------
Example
-------

.. code-block:: typescript

  up: function (from: string, to: string, direction: string): AnimationEntryMetadata {
    return transition(`${from} ${direction} ${to}`, getSideSlideAnimation(
      100, 0,
      0, -100,
      'translateY'
    ));
  },


--------------------------------------------------------------------------------

.. _angular_core_router_transition_animations_up:

animations.up
================================================================================

.. code-block:: typescript

  animations.up(from, to, direction);

Generate up animation (from bottom to top)

**cannot directly used within component animations, only used for animation building**

----------
Parameters
----------

#. ``from`` - ``string``: forward, backward
#. ``to`` - ``string``: =>, <=, <=>
#. ``direction`` - ``strin``: from state

-------
Returns
-------

``AnimationEntryMetadata`` : Transition including it's slideanimation

--------------------------------------------------------------------------------

.. _angular_core_router_transition_animations_down:

animations.down
================================================================================

.. code-block:: typescript

  animations.down(from, to, direction);

Generate down animation (from top to bottom)

**cannot directly used within component animations, only used for animation building**

----------
Parameters
----------

#. ``from`` - ``string``: forward, backward
#. ``to`` - ``string``: =>, <=, <=>
#. ``direction`` - ``strin``: from state

-------
Returns
-------

``AnimationEntryMetadata`` : Transition including it's slideanimation

--------------------------------------------------------------------------------

.. _angular_core_router_transition_animations_right:

animations.right
================================================================================

.. code-block:: typescript

  animations.right(from, to, direction);

Generate right animation (from left to right)

**cannot directly used within component animations, only used for animation building**

----------
Parameters
----------

#. ``from`` - ``string``: forward, backward
#. ``to`` - ``string``: =>, <=, <=>
#. ``direction`` - ``strin``: from state

-------
Returns
-------

``AnimationEntryMetadata`` : Transition including it's slideanimation



--------------------------------------------------------------------------------

.. _angular_core_router_transition_animations_left:

animations.left
================================================================================

.. code-block:: typescript

  animations.left(from, to, direction);

Generate left animation (from right to left)

**cannot directly used within component animations, only used for animation building**

----------
Parameters
----------

#. ``from`` - ``string``: forward, backward
#. ``to`` - ``string``: =>, <=, <=>
#. ``direction`` - ``strin``: from state

-------
Returns
-------

``AnimationEntryMetadata`` : Transition including it's slideanimation





