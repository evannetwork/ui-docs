===================
ListPagingComponent
===================

Simple helper for list paging. It offers the handling of basic paging parameters (offsett, totalSize) and shows a button, when the user can page to the next page. The whole logic how to load and display data is yours.

------
Inputs
------

#. ``offset`` - ``number``: offset to load the data from (start at index 0, 10, 33, ...)
#. ``totalSize`` - ``number``: page size to split the loaded bunches in
#. ``loadMore`` - ``Function``: function that is called to load more data

-----
Usage
-----
Reference Implementation: `contract list entries component <https://github.com/evannetwork/angular-core/tree/develop/src/components/contract-listentries>`_

- html

::

  <list-paging *ngIf="!loading" #listPaging
    [offset]="listEntries.length"
    [totalSize]="listEntryCount"
    [loadMore]="loadMore.bind(this)">
  </list-paging>
