# Crowd Sourced Library
This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app), using the [Redux](https://redux.js.org/) and [Redux Toolkit](https://redux-toolkit.js.org/) template.
### Inspiration

I almost never get my books back from people after lending one to them. I have bought Douglas Adam’s ```Long Dark Tea-Time of the Soul``` no fewer than six times because I lend it out, forget who I give it to and never see it again.  So with that in mind, I wanted a way to keep track of my collection of books.  Who has them, when did I lend it to them, etc.

### Concept

A book exchange website, where users can upload the books they own to their profile.  Users can see each other's collections, and request to borrow a book from another user, or request that a book to be returned.  

### Format

* A Library is a community of users who can see each other’s collections.
* A new user would create an account, and then be prompted to either create a new Library, join an existing one, or add books to their collection.  
* Each book available in the Library can be rated and reviewed by members, and members can give borrowers a rating based on the condition of the book upon return.

## Tech Stack

### Backend

* ```Express```
* ```Postgres```
* ```GraphQL```
* ```Google Books API```

### Frontend

* ```React```
* ```Redux```

### Schema
```
{
  "user" {
    "userId": "int"
    "userInfo" {
      "username": "string",
      "name" {
        "first": "string",
        "last": "string"
      }
      "location" {
        "city": "string",
        "state": string
       }
      "contact" {
        "phone":"555-555-5555",
        "email":"user@email.com"
      }
    }
    "libraries" {
      "libId1",
      "libId2",
      ...
    }
    "ownedBooks" {
      "bookId1" {
        "checkedOut":"bool",
        "borrower":"userId"
      },
      ...
    },
    "borrowedBooks" {
     "userId1" {
       "bookId" {
         "owner":"userId"
       }
     }
    }
  }
},
  "library" {
    "libId": "int"
    "owner" {
      userId
    },
    "members" {
      userId,
      ...
    },
    "books" {
      bookId,
      ...
    }
  }
}
```
## Author

* **Ryan Graham** - [Github](https://github.com/ryanxgraham)
