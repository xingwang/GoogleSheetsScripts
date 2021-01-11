# GoogleSheetsScripts
---
Quickly hacked together script to automatically insert a last updated date/time in the 5th column of a changed row with some minor checks.
```js
function onEdit() {
  var activeSheet = SpreadsheetApp.getActiveSheet();
  var activeCell = activeSheet.getActiveCell();
  if (['sheet1', 'sheet2', 'sheet3'].indexOf(activeSheet.getName().toLowerCase()) === -1 || activeCell.getColumn() > 4 || activeCell.getRow() < 2) return;
  var rowIndex = activeCell.getRowIndex();
  var dateColumn = activeSheet.getLastColumn();
  var dateCellToUpdate = activeSheet.getRange(rowIndex,dateColumn);
  var time = Utilities.formatDate(new Date(), "GMT", "MM/DD/YYYY HH:mm:ss");
  dateCellToUpdate.setValue(time);
}
```
