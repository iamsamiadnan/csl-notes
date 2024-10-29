![[Pasted image 20241029230521.png]]

## app.js

```js
// app.js
import PromptSync from "prompt-sync";
import { createAccount } from "./utils.js";
import CreateAccountPage from "./pages/CreateAccountPage.js";


do {
    console.clear();
    console.log();
    console.log(':: Banking Management System ::');
    console.log(':: Menu ::');
    console.log();
    console.log('1. Create Account');
    console.log();

    const prompt = PromptSync({sigint: true});
    const input = Number(prompt('Choose: '));

    switch (input) {
        case 1:
            CreateAccountPage();
            break;
        default:
            break;
    }
} while (true);
```

## pages/CreateAccountPage.js

```js
// pages/CreateAccountPage.js
import PromptSync from "prompt-sync";
import { createAccount } from "../utils.js";
import { users } from "../database.js";

function CreateAccountPage() {
    console.clear();
    console.log();
    console.log(':: Banking Management System ::');
    console.log(':: Create Account ::');
    console.log();

    const prompt = PromptSync({sigint: true});

    const firstName = prompt('First Name: ');
    const lastName = prompt('Last Name: ');
    const username = prompt('User Name: ');
    const password = prompt('Password: ');
    const email = prompt('Email: ');

    const user = {
        id: users.length + 1,
        firstName,
        lastName,
        username,
        password,
        email,
        created_at: new Date(),
    }

    //console.log(user);
    console.log();
    const response = createAccount(user, users);

    console.log(response.message);
    console.log();

    if(response.error) {
        console.log('Please Press Enter To Try Again!');
        prompt();
        CreateAccountPage();
        return; // must return other wise following message 'Please Press Enter To Return To Menu' will print twice
    }
    
    console.log('Please Press Enter To Return To Menu');
    prompt();
}

export default CreateAccountPage;
```

## database.js

```js
export const users = [];
```

