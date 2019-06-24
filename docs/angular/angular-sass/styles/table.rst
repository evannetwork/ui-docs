======
Tables
======

Tables are simply and dont need any classes. Only for a responsive design, you should wrap your table within a ".table-responsive" class, to handle small screen overflow.

-------
Example
-------

- Reference Implementation: `Logging DApp <https://github.com/evannetwork/ui-core-dapps/blob/develop/dapps/logging/src/components/logging/logging.html>`_

::

  <div class="evan-content">
    <h2 class="content-header m-t-0 display-inline-block">{{ 'logging' | translate }}</h2>
    <ion-icon class="clickable" margin-left name="funnel" (click)="toggleFilters()"></ion-icon>
    
    <div margin-bottom>{{ '_logging.click-to-log' | translate }}</div>
    <div class="table-responsive">
      <table class="table table-hover">
        <thead>
          <tr>
            <th>{{ '_logging.timestamp' | translate }}</th>
            <th>{{ '_logging.level' | translate }}</th>
            <th>{{ '_logging.message' | translate }}</th>
          </tr>
        </thead>
        <tbody>
          <tr *ngFor="let log of logs"
            [ngClass]="'level-' + log.level"
            (click)="logSingleLog(log)">
            <td>{{ log.timestamp | date:'long':'':translateService.translate.currentLang }}</td>
            <td>{{ log.level }}</td>
            <td>{{ log.message }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>

------------
View Example
------------

.. image:: ../../images/angular-sass/table.png
   :width: 600
