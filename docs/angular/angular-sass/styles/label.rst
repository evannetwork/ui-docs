===================
Round Status Labels
===================

.evan-label
===========
Shows an outline label. Add more style using the following classes: 

==============================  ================================================================================================
Class                           Description 
==============================  ================================================================================================
.label-rouded                   add border-radious to the label
.label-info                     add yellow color to the label
.label-success                  add green color to the label
.label-danger                   add red color to the label
==============================  ================================================================================================

-------
Example
-------

::

  <span class="evan-label label-rounded"
    [class.label-danger]="task.contractState != '7'"
    [class.label-success]="task.contractState == '7'">
    {{ (task.contractState == '7' ? '_digitaltwin.finished' : '_digitaltwin.rented') | translate }}
  </span>

------------
View Example
------------

.. image:: ../../../images/angular-sass/label-rounded.png
   :width: 200

.evan-circle
============
Shows an label as an round element.

-------
Example
-------

::

  <div class="evan-circle display-inline-block"
    [class.bg-success]="todo.solved">
    <ng-container *ngIf="!todo.loading">{{ i + 1 }}</ng-container>
    <ion-spinner color="primary" *ngIf="todo.loading" margin-right></ion-spinner>
  </div>

------------
View Example
------------

.. image:: ../../../images/angular-sass/label-round.png
   :width: 600