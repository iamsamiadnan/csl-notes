```js
// Delete Account Page .js

import PromptSync from "prompt-sync";
import { accounts } from "../database.js";
import { deleteAccount } from "../utils.js";

function DeleteAccountPage() {
    console.clear();
    console.log(':: BANKING MANAGEMENT SYSTEM ::');
    console.log(':: MENU::');
    console.log();
    
    const prompt = PromptSync({sigint: true});

    const id = Number(prompt('Enter ID: '));

    if(!id) return;

    const result = deleteAccount(id, accounts);;
    console.log(result.message);

    prompt('Press Enter To Continue ..');
}

export default DeleteAccountPage;

```

```js
// utils .js

function isUserExistsById(id, _users) {
    for(const user of _users) { // account = user
        if(user.id === id) return user;
    }

    return null;
}

// Delete Account
export function deleteAccount(id, _users) {
    const userExists = isUserExistsById(id, _users);

    if(userExists) {
       const index = userExists.id - 1;
        _users.splice(index, 1)
        return {statusCode: 200, error: false, message: 'The Account Is Deleted.'}
    }

    return {statusCode: 409, error: true, message: 'User Doesn\'t Exists'};

}
```

```js
// app .js
switch (option) {
	case 1:
		CreateAccountPage();
		break;
	case 2:
		ShowUsersPage();
		break;
	case 3:
		DeleteAccountPage();
		break;
	default:
		break;
}
```