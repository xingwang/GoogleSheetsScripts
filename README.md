# GoogleSheetsScripts
---
Quickly hacked together script to automatically insert a last updated date/time in the 5th column of a changed row with some minor checks.
```js
function onEdit(e) {
  var sh = SpreadsheetApp.getActiveSheet();
  var r = sh.getActiveCell();
  var blah = sh.getName().toLowerCase();
  if (['sheet1', 'sheet2', 'sheet3'].indexOf(sh.getName().toLowerCase()) === -1 || r.getColumn() > 4 || r.getRow() < 2) return;
  var time = Utilities.formatDate(new Date(), "GMT", "MM/DD/YYYY HH:mm:ss");
  var actSht = e.source.getActiveSheet();
  var actRng = e.source.getActiveRange();
  var index = actRng.getRowIndex();
  var dateCol = actSht.getLastColumn();
  var lastCell = actSht.getRange(index,dateCol);
  lastCell.setValue(time);
}
```
