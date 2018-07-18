============
angular-libs
============

This `project <https://github.com/evannetwork/ui-angular-libs>`_ contains a collection of Angular core libraries. This project is deployed to the ens (likelly to the angular-core), so you can require angular libraries (etc...) directly into the frontend without building duplicated libraries into your dapps.

This project exports the following libraries for you:

- `@angular/animations <https://angular.io/api?query=animations>`_
- `@angular/common <https://angular.io/api?query=common>`_
- `@angular/common/locales/de <https://angular.io/api?query=common>`_
- `@angular/common/locales/en <https://angular.io/api?query=common>`_
- `@angular/common/locales/fr <https://angular.io/api?query=common>`_
- `@angular/core <https://angular.io/api?query=core>`_
- `@angular/forms <https://angular.io/api?query=forms>`_
- `@angular/http <https://angular.io/api?query=http>`_
- `@angular/platform-browser <https://angular.io/api?query=platform-browser>`_
- `@angular/platform-browser-dynamic <https://angular.io/api?query=platform-browser-dynamic>`_
- `@angular/platform-browser/animations <https://angular.io/api?query=platform-browser>`_
- `@angular/router <https://angular.io/api?query=router>`_
- `@ionic-native/camera <https://ionicframework.com/docs/native/camera/>`_
- `@ionic-native/file <https://ionicframework.com/docs/native/file/>`_
- `@ionic-native/file-path <https://ionicframework.com/docs/native/file-path>`_
- `@ionic-native/qr-scanner <https://ionicframework.com/docs/native/qr-scanner/>`_
- `@ionic-native/splash-screen <https://ionicframework.com/docs/native/splash-screen/>`_
- `@ionic-native/status-bar <https://ionicframework.com/docs/native/status-bar>`_
- `@ionic-native/transfer <https://ionicframework.com/docs/native/file-transfer>`_
- `@ngx-translate/core <https://github.com/ngx-translate/core>`_
- `@zxing/library <https://github.com/zxing-js/ngx-scanner>`_
- `@zxing/ngx-scanner <https://github.com/zxing-js/ngx-scanner>`_
- `ionic-angular <https://ionicframework.com/docs/>`_
- `ionic-tags-input <https://github.com/HsuanXyz/ionic-tags-input>`_
- `ng-circle-progress <https://github.com/bootsoon/ng-circle-progress>`_
- `rxjs/BehaviorSubject <https://angular.io/guide/rx-library>`_
- `rxjs/Observable <https://angular.io/guide/rx-library>`_
- `rxjs/Subscription <https://angular.io/guide/rx-library>`_

------------
Installation
------------

.. code-block:: sh

  npm i @evan.network/ui-angular-libs

-----
Usage
-----
- tsconfig.json

.. code-block:: typescript

  {
    "compilerOptions": {
      ...,
      "paths": {
        "angular-libs": [
          "../node_modules/@evan.network/ui-angular-core/dist/angularlibs.js"
        ]
      }
      ...
    }
  }

- typescript

.. code-block:: typescript

  ...
  import {
    NgModule, ErrorHandler, enableProdMode,   // @angular/core
    CommonModule, registerLocaleData,         // @angular/common
    RouterModule, Routes, RouteReuseStrategy, // @angular/router
    FormsModule,                              // @angular/forms
    IonicModule, IonicApp,                    // ionic-angular
    TranslateModule, TranslateService,        // @ngx-translate/core
    BrowserAnimationsModule,                  // @angular/platform-browser/animations'
    NgCircleProgressModule,                   // ng-circle-progress
    IonTagsInputModule,                       // ionic-tags-input
    ZXingScannerModule,                       // qr-code-scanner module
    Camera,                                   // @ionic-native/camera
    QRScanner,                                // @ionic-native/qr-scanner
    ...
  } from 'angular-libs';
  ...
