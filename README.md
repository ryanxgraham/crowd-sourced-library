# Crowd Sourced Library

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app), using the [Redux](https://redux.js.org/) and [Redux Toolkit](https://redux-toolkit.js.org/) template.

#### Inspiration

I almost never get my books back from people after lending one to them. I have bought Douglas Adam’s ```Long Dark Tea-Time of the Soul``` no fewer than six times because I lend it out, forget who I give it to and never see it again.  So with that in mind, I wanted a way to keep track of my collection of books.  Who has them, when did I lend it to them, etc.

#### Concept

A book exchange website, where users can upload the books they own to their profile.  Users can see each other's collections, and request to borrow a book from another user, or request that a book to be returned.  

#### Format

* A Library is a community of users who can see each other’s collections.
* A new user would create an account, and then be prompted to either create a new Library, join an existing one, or add books to their collection.  
* Each book available in the Library can be rated and reviewed by members.


## Tech Stack

* `Express`
* `Postgres`
* `GraphQL`
* `Hasura`
* `Apollo`
* `Heroku`
* `Google Books API`
* `React`
* `Redux`

## Spec

#### Landing Page

The `Landing Page` should include the following:
  - [ ] Login/Signup
  - [ ] List of features

#### Library

The `Library` page should include the following:
  - [ ] Owner
  - [ ] List of members
  - [ ] Featured book
  - [ ] Top 5 rated book
  - [ ] List of all books
    - [ ] Sortable by rating
    - [ ] Filterable by availablility (count flagged as available > 0)
  - [ ] A community message board

#### My Collection

The `My Collection` page should include the following:
  - [ ] Owned Books
  - [ ] A button to add books to your collection
  - [ ] An option to choose your favorite book
  - [ ] An option to rate books
  - [ ] Books you've borrowed & currently borrowing
  - [ ] Books you've lent & currently lending out
  - [ ] Requests from other users to borrow a book in your collection
  - [ ] An option to reccommend a book to another user

#### Other User's Pages

Other user's pages should include the following:
  - [ ] Owned Books, as well as an indication of availablility
  - [ ] Books they've borrowed and are currently borrowing
  - [ ] Books they've lent & currently lending out
  - [ ] Their Favorite book
  - [ ] An option to rate books
  - [ ] A button to request to borrow a book.

#### Google Books API interaction

The following parameters will be utilized in the Google Books Search:
  * `intitle=title` to specify the title.
  *  `inauthor=author` to specify an author.
  * `langRestrict=en` to default to english language books.  This can be changed by the user
  * `maxResults=5` to slim down the response to only likely candidates of book we intend to add.

Sample API request for _Terry Pratchett's_ book, _"Snuff"_:

   `
  https://www.googleapis.com/books/v1/volumes?q=intitle:snuff+inauthor:pratchett&maxResults=5&langRestrict=en&key=yourAPIKey
  `

Sample API Response:

```
{
  "kind": "books#volumes",
  "totalItems": 1,
  "items": [
    {
      "kind": "books#volume",
      "id": "0gUgmOyu0JEC",
      "etag": "thMbiEket+U",
      "selfLink": "https://www.googleapis.com/books/v1/volumes/0gUgmOyu0JEC",
      "volumeInfo": {
        "title": "Snuff",
        "authors": [
          "Terry Pratchett"
        ],
        "publisher": "Random House",
        "publishedDate": "2012",
        "description": "It is a truth universally acknowledged that a policeman taking a holiday would barely have had time to open his suitcase before he finds his first corpse. Commander Sam Vimes of the Ankh-Morpork City Watch is on holiday in the pleasant and innocent countryside, but not for him a mere body in the wardrobe. There are many, many bodies - and an ancient crime more terrible than murder. He is out of his jurisdiction, out of his depth, out of bacon sandwiches, occasionally snookered and out of his mind. But never out of guile. Where there is a crime there must be a finding, there must be a chase and there must be a punishment. They say that in the end all sins are forgiven. But not quite all... Winner of the Bollinger Everyman Wodehouse Prize for Comic Fiction",
        "industryIdentifiers": [
          {
            "type": "ISBN_13",
            "identifier": "9780552166751"
          },
          {
            "type": "ISBN_10",
            "identifier": "0552166758"
          }
        ],
        "readingModes": {
          "text": false,
          "image": false
        },
        "pageCount": 512,
        "printType": "BOOK",
        "categories": [
          "Discworld (Imaginary place)"
        ],
        "averageRating": 3.5,
        "ratingsCount": 87,
        "maturityRating": "NOT_MATURE",
        "allowAnonLogging": false,
        "contentVersion": "0.5.0.0.preview.0",
        "imageLinks": {
          "smallThumbnail": "http://books.google.com/books/content?id=0gUgmOyu0JEC&printsec=frontcover&img=1&zoom=5&source=gbs_api",
          "thumbnail": "http://books.google.com/books/content?id=0gUgmOyu0JEC&printsec=frontcover&img=1&zoom=1&source=gbs_api"
        },
        "language": "en",
        "previewLink": "http://books.google.com/books?id=0gUgmOyu0JEC&dq=intitle:snuff+inauthor:pratchett&hl=&cd=1&source=gbs_api",
        "infoLink": "http://books.google.com/books?id=0gUgmOyu0JEC&dq=intitle:snuff+inauthor:pratchett&hl=&source=gbs_api",
        "canonicalVolumeLink": "https://books.google.com/books/about/Snuff.html?hl=&id=0gUgmOyu0JEC"
      },
      "saleInfo": {
        "country": "US",
        "saleability": "NOT_FOR_SALE",
        "isEbook": false
      },
      "accessInfo": {
        "country": "US",
        "viewability": "NO_PAGES",
        "embeddable": false,
        "publicDomain": false,
        "textToSpeechPermission": "ALLOWED",
        "epub": {
          "isAvailable": false
        },
        "pdf": {
          "isAvailable": true
        },
        "webReaderLink": "http://play.google.com/books/reader?id=0gUgmOyu0JEC&hl=&printsec=frontcover&source=gbs_api",
        "accessViewStatus": "NONE",
        "quoteSharingAllowed": false
      },
      "searchInfo": {
        "textSnippet": "&quot;The 39th installment in the New York Times bestselling &quot;Discworld&quot; canon from Terry Pratchett, &quot;the purely funniest English writer since Wodehouse.&quot; (Washington Post Book World)&quot;-- Provided by publisher."
      }
    }
  ]
}
```

The user should see the author, title, a thumbnail of the image, and a button that says "add to my collection"

When a user adds a book to their collection we extract the following data from the response. In this case, `response.body.items[0]`

```  
  {
    id : string,
    volumeInfo.title : string,
    volumeInfo.subtitle : string,
    volumeInfo.authors[] : [string],
    volumeInfo.publishedDate : string,
    volumeInfo.Description : string,
    volumeInfo.imageLinks : {
      "smallThumbnail": string,
      "thumbnail": string
    },
    volumeInfo.averageRating: int
    volumeInfo.language: string
    volumeInfo.canonicalVolumeLink: string
  }

```

We will then add this info as a new `book` entry into the user's owned books.

### Schemas

`note: some of this is definitely psuedocode right now.`
![](/schema.png)

###### Book Schema

```
{
  book {
    id: uuid,
    googleVolumeId: test,
    title : text,
    subtitle : text,
    authors : text,
    publishedDate : text,
    description : text,
    smallThumbnail: text,
    thumbnail: text
    isAvailable: bool
    availableCopies: int
    totalCopies: int
  },

  bookOwners {
    ownerId: uuid -> user.id,
    bookId: uuid -> book.id
  }
}
```

###### User Schema

```
{
  user {
    id: uuid,
    userName: text,
    email: text,
    createdAt: timestamp,
    firstName: text,
    lastName: text
}
```

###### Library Schema

```
{
  lib {
    id: uuid,
    createdAt: timestamp,
    libName: text
  },

  libOwners {
    libId: uuid -> lib.id,
    ownerId: uuid -> user.id    
  },

  libMembers {
    libId: uuid -> lib.id,
    memberId: uuid -> user.id
  },

  libBooks {
    libId: uuid -> lib.id,
    bookId: uuid -> book.id
  }
}
```



## Author

* **Ryan Graham** - [Github](https://github.com/ryanxgraham)
