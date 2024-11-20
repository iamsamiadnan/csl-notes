
## Monolithic Architecture

A monolithic architecture is a traditional approach where the entire application—frontend, backend, and database—is tightly integrated into a single unit. All components are interconnected, often running as a single codebase.

## Headless CMS

A headless CMS is a content management system that provides a backend for managing content, with a RESTful or GraphQL API for delivering that content to any frontend (web, mobile, etc.).

```js

function getData() {
    fetch('https://BASE_URL/rest/v1/books', {
        method: 'GET',
        headers: {
            'apikey': 'API_KEY'
        }
    })
    .then((response) => response.json())
    .then((data) => {
        //console.log(data)
        setData(data)
    })
    .catch((error) => console.log(error))
}


function setData(books) {
    let lis = '';

    for(const book of books) {
        lis = lis + `<li id="${book.id}"><span>${book.title}</span> ${book.author}</li>`;
    }

    document.getElementById('ulList').innerHTML = lis;
}
```

https://postgrest.org/en/stable/references/api/tables_views.html 

https://github.com/orgs/supabase/discussions/860#discussioncomment-473516

https://supabase.com/docs/reference/javascript/select

https://supabase.com/docs/guides/database/postgres/row-level-security


```js
function postData() {
    fetch('https://BASE_URL/rest/v1/books', {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json',
            'apikey': 'API_KEY'
        },
        body: JSON.stringify({
            title: 'this is a title',
            author: 'Adnan Sami',
            isbn: '6091032333',
            category: 'Backed',
            publisher: 'CodeAcademy'
        }),
    })
    .then((response) => response.json())
    .then((data) => {
        console.log('BOOK DATA ', data);
    })
    .catch((error) => console.log(error));
}
```


jSY2drn9vGpQCOrb