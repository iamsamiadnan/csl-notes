```js
// update user object
// CreateAccountPage.js
// add balance: Number, transations: Array to user object
// ...

    const user = {
        id: users.length + 1,
        firstName,
        lastName,
        username,
        password,
        email,
        balance: 0,
        transactions: [],
        created_at: new Date(),
    }
    
```

```js
// DepositPage.js

import PromptSync from "prompt-sync";
import { users } from "../database.js";
import { createAccount, deposit } from "../utils.js";

function DepositPage() {
    console.clear();
    console.log(':: BANKING MANAGEMENT SYSTEM ::');
    console.log(':: MENU::');``
    console.log();
    
    const prompt = PromptSync({sigint: true});

    const id = Number(prompt('Enter ID: '));
    const amount = Number(prompt('Enter $: '));

    const result = deposit(id, users, amount);
    console.log(result.message);

    prompt('Press Enter To Continue ..');
}


export default DepositPage;
```

```js
// utils.js

// Deposit Func

export function deposit(id, _users, amount) {

    if(!id) return { statusCode: 409, error: true, message: "Enter Valid ID." };
    
    let isUserExists = false;

    for (const idx in _users) {
        if (_users[idx].id === id) {
            isUserExists = !isUserExists;
            // add amount
            _users[idx].balance = _users[idx].balance + amount;

            // add transaction
            _users[idx].transactions.push(
                JSON.stringify(
                    {
                        id: _users[idx].transactions.length + 1,
                        created_at: new Date(),
                        type: 'DEPOSIT',
                        amount,
                    }
                )
            );
            break;
        }
    }

    return isUserExists
        ? { statusCode: 200, error: false, message: `$${amount} Is Deposited!` }
        : { statusCode: 409, error: true, message: "User Doesn't Exist" };
}
```