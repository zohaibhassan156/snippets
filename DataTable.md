DataTable manipulation examples:

```
var myDataTableInstance = new DataTable({options});

$('table').on('click', 'tr', function(){

	// here 'this' will be the row which we have clicked
	// we can easily pass it to table's instance variable in row method as a parameter to get datatable's data row.
	// note html table is 1 thing, datatable maintains its own set of rows/columns internally so we need to modify through that.
	// do like this for clicking on a row

	myDataTableInstance.row(this).remove().draw();

	// Other ways of doing row selection:
	// https://datatables.net/examples/api/select_single_row.html

	// now write your own logic for selecting row where delete button was clicked

	// For updating cell/column values after they are updated use this api:
	// https://datatables.net/reference/api/row().data()
	
});
```