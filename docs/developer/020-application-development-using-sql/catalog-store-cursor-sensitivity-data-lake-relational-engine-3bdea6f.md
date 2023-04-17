<!-- loio3bdea6fd6c5f1014a0c5c3cc8d0d9477 -->

# Catalog Store Cursor Sensitivity Data Lake Relational Engine

Cursors are classified by their sensitivity to changes in the underlying data. In other words, cursor sensitivity is defined by the changes that are visible.

Insensitive cursors
:   The result set is fixed when the cursor is opened. No changes to the underlying data are visible.

Sensitive cursors
:   The result set can change after the cursor is opened. All changes to the underlying data are visible.

Asensitive cursors
:   Changes may be reflected in the membership, order, or values of the result set seen through the cursor, or may not be reflected at all.

Value-sensitive cursors
:   Changes to the order or values of the underlying data are visible. The membership of the result set is fixed when the cursor is opened.

The differing requirements on cursors place different constraints on execution and therefore affect performance.

