
```js
// app.js
import { isUserExists } from "./utils.js";
const accounts = [];


function createAccount(user) {
    const userExists  = isUserExists(user, accounts);
    //console.log(userExists);
    if(userExists === false) {
        accounts.push(user);
        return {statusCode: 200, error: false, message: 'User Created Successfully.'};
    }
    //accounts.push(user);

    return {statusCode: 409, error: true, message: 'User Already Exists.'};
}

const user1 = {
    id: 1,
    firstName: 'Adnan',
    lastName: 'Sami',
    created_at: new Date(),
    username: 'adnansami',
    password: '123456',
    email: 'adnansami@ymail.com',
}
const user2 = {
    id: 2,
    firstName: 'Rahim',
    lastName: 'Ullah',
    created_at: new Date(),
    username: 'rahimullah',
    password: '654321',
    email: 'rahimullah@ymail.com',
}

console.log(createAccount(user1));
console.log(createAccount(user1));
createAccount(user1);
createAccount(user1);
console.log(createAccount(user2));

// createAccount(user2);
// createAccount(user1);

console.log(accounts);

```

```js
// utils.js
export function isUserExists(_user, _accounts) {
    //console.log(_user, _accounts);   
    for(const account of _accounts) {
        if(account.username === _user.username) return true;
    }

    return false;
}
```

## Taking Input from CLI

```bash
npm i prompt-sync
```

https://github.com/heapwolf/prompt-sync 

[[MOD 001 - Create Account Page UI]]