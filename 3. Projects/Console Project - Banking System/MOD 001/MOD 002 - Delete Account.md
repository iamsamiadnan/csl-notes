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

export function deleteAccount(id, _users) {
    if(!id) return { statusCode: 409, error: true, message: "Enter Valid ID." };
    
    let isUserExists = false;

    for (const idx in _users) {
        if (_users[idx].id === id) {
            isUserExists = !isUserExists;
            _users.splice(idx, 1);
            break;
        }
    }

    return isUserExists
        ? { statusCode: 200, error: false, message: 'The Account Is Deleted.' }
        : { statusCode: 409, error: true, message: "User Doesn't Exist" };
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