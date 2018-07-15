## Backend Action part

```
<?php

use Illuminate\Contracts\Encryption\DecryptException;

function action_in_controller(Request $request, $id){

	try {
	
		$decrypted_id = decrypt($id);
	
	} catch (DecryptException $e) {
    
		// Encryption failed. Probably some one was trying to figure out something and made a fake id

	}

}

?>
```

## Frontend UI part

```<a href="{{ route('users.edit', [ 'id' => encrypt($value->id) ]) }}">Edit User</a>```