Revision Log
============

pypi version 1.47 (in-work)
---------------------------
- added new function: ``db.nr('table1')`` returns the contents of named range "table1"
- added new function: ``db.ws('Sheet1').range('A1:C3')`` that returns the contents of a range
  it also has the ability to return the formulas of the range
- updated ``db.ws('Sheet1').row()`` and ``db.ws('Sheet1').col()`` to take in a new argument ``formual``
  that returns the formulas of a row or col


pypi version 1.46
------------------
- bug fix: added ability to input an empty string into the cell update functions
  (previously entering val='') threw and error

pypi version 1.45
-----------------
- added support for cell values that have multiple formats within a single cell.
  previous versions did not support this functionality since it is logged differently in sharedString.xml
- added support for updating formulas and viewing them:

    - view formula: ``db.ws('Sheet1').address('A1', formula=True)``
    - edit formula: ``db.ws('Sheet1').update_address('A1', val='=A1+10')``

- updated the following function arguments to drive commonality:

    - was: ``readxl(fn, sheetnames)`` new: ``readxl(fn, ws)``
    - was: ``writexl(db, path)`` new: ``writexl(db, fn)``
    - was: ``db.ws(sheetname)`` new: ``db.ws(ws)``
    - was: ``db.add_ws(sheetname, data)`` new: ``db.add_ws(ws, data)``

- added new feature to be able to read-in NamedRanges, store it in the Database, update it, remove it,
  and write it. NamedRanges were integrated with existing function to handle semi-structured-data

    - ``db.add_nr(name'range1', ws='sheet1', address='A1:C2')``
    - ``db.remove_nr(name='range1')``
    - ``db.nr_names``

- add feature to remove worksheet: ``db.remove_ws(ws='Sheet1')``
- add feature to rename worksheet: ``db.rename_ws(old='sh1', new='sh2')``
- added a cleanup function upon writing to delete _pylightxl_ temp folder in case an error left them
- added feature to write to file that is open by excel by appending a "new_" tag to the file name and
  a warning message that file is opened by excel so a file was saved as "new_" + filename

pypi version 1.44
-----------------
- bug fix: accounted for num2letter roll-over issue
- new feature: added a pylightxl native function for handling semi-structured data

pypi version 1.43
-----------------
- bug fix: accounted for reading error'ed out cell "#N/A"
- bug fix: accounted for bool TRUE/FALSE cell values not registering on readxl
- bug fix: accounted for edge case that was prematurely splitting cell tags <c r /> by formula closing
  bracket <f />
- bug fix: accounted for cell address roll-over

pypi version 1.42
-----------------
- added support for pathlib file reading
- bug fix: previous version did not handle merged cells properly
- bug fix: database updates did not update maxcol maxrow if new data addition was larger than the initial
  dataset
- bug fix: writexl that use linefeeds did not read in properly into readxl (fixed regex)
- bug fix: writexl filepath issues

pypi version 1.41
-------------------
- new-feature: write new excel file from pylightxl.Database
- new-feature: write to existing excel file from pylightxl.Database
- new-feature: db.update_index(row, col, val) for user defined cell values
- new-feature: db.update_address(address, val) for user defined cell values
- bug fix for reading user defined sheets
- bug fix for mis-alignment of reading user defined sheets and xml files

pypi version 1.3
----------------
- new-feature: add the ability to call rows/cols via key-value ex: ``db.ws('Sheet1').keycol('my column header')``
  will return the entire column that has 'my column header' in row 1

- fixed-bug: fixed leading/trailing spaced cell text values that are marked ``<t xml:space="preserve">`` in the
  sharedString.xml

pypi version 1.2
----------------
- fixed-bug: fixed Sheet number to custom Sheet name matching for 10+ sheets that were previously only sorting alphabetical
  which resulted with sorting: Sheet1, Sheet10, Sheet11, Sheet2... and so on.

pypi version 1.1
----------------
- initial release
