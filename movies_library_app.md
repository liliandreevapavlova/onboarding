# Movies Library Application

## 1. Assignment Goals

The goal of this assignment is to simulate work on a real project.

Another goal is to get experience creating a project from scratch.

## 2. Assignment Description

To complete this assignment, you will have to setup a project. Create a responsive layout using HTML & CSS.

- General Requirements:
  - Separated components
  - Navigation between pages
  - Responsive layout
  - Use of semantic HTML
  
- Authentication of user
	In order for the authentication to work Firebase should be added to the project. 
    More information on how to add it can be found here: https://firebase.google.com/docs/auth/web/password-auth 
	Depending on the framework there may be differences in the way it is implemented, please make sure to use the proper implementation depending on the framework. 
    The variables that you would need are the following:
    
```html 
<!-- The core Firebase JS SDK is always required and must be listed first -->
<script src="https://www.gstatic.com/firebasejs/8.2.9/firebase-app.js"></script>

<!-- TODO: Add SDKs for Firebase products that you want to use
     https://firebase.google.com/docs/web/setup#available-libraries -->
<script src="https://www.gstatic.com/firebasejs/8.2.9/firebase-analytics.js"></script>

<script>
  // Your web app's Firebase configuration
  // For Firebase JS SDK v7.20.0 and later, measurementId is optional
  var firebaseConfig = {
    apiKey: "AIzaSyB_SfeLENmQKY3stWWPQNVE5F64MBMXWqU",
    authDomain: "book-library-9bca1.firebaseapp.com",
    databaseURL: "https://book-library-9bca1.firebaseio.com",
    projectId: "book-library-9bca1",
    storageBucket: "book-library-9bca1.appspot.com",
    messagingSenderId: "529107128033",
    appId: "1:529107128033:web:83cd6b8ca8ab0691bfb1a0",
    measurementId: "G-FQQMFQKXLM"
  };
  // Initialize Firebase
  firebase.initializeApp(firebaseConfig);
  firebase.analytics();
</script>
```

- Connect your application with TMDb's API 
```
movieDbBaseUrl: 'https://api.themoviedb.org/3',
movieDbApiKey: '519e9b151c1dc701bf50e6824fbe3409'
```

API documentation: [https://developers.themoviedb.org/]  
NOTE: The Movie Library application will not have design. Please use available sites as reference like IMDB or TMDB for example. Use all your knowledge on CSS flexbox and responsive design acquired up until now. **Do not copy/paste any of the code from this sites.** Implement it alone.

## 2.1. The Movie Library Application Overview

The Movie Library application gives you the chance to find and display information about your favorite movies.

## 2.2. The Movie Library Application Specifications
- All users (registered and not registered) have access to public home page with a list of the current popular movies.
- Each movie on the home screen is represented by a poster image, title, release date and average vote.
- Each user has access to every movie detailed page
- Each movie on his detailed page is represented by three sections:
  - Overview section containing a poster image, title, release date, genres, runtime, average vote, tagline and overview
  - Top Cast section - first 10 cast members represented by profile image, name and character
  - Reviews - each review is represented by author and content
  - Bonus section: Recommendations section - list of recommended movies for a movie represented by a poster image, title, release date and average vote
- Each user can sign up in the application giving e-mail and password.
- Each user can sign in in the application using e-mail and password.

Additional tasks:
- After sign in each user has access to his favorite movie page with a list with all liked movies.
- Each user can add movie to his favorite list

## 2.3. Tasks

### Setup

- Story 1: Setup a project

### Layout

- Story 1: Prepare the layout with header and main section. The navigation should contain your application logo, navigation, sign in button or user button depending on the current user status (logged in or not).

### Home page

- Story 1: Create public home page with a list of the current popular movies on TMDb. This list updates daily.
Each movie on the home screen is represented by a poster image, title, release date and average vote (in percentage).
```
https://developers.themoviedb.org/3/movies/get-popular-movies
```

NOTE: To get the poster image you should use poster_path, baseUrl and posterSize:
```javascript
let baseUrl = "https://image.tmdb.org/t/p/";
let availablePosterSizes": [
  "w92",
  "w154",
  "w185",
  "w342",
  "w500",
  "w780",
  "original"
];
let defaultPosterSize = "v500";
let movie = {
  "poster_path": "/e1mjopzAS2KNsvpbpahQ1a6SkSn.jpg",
  "adult": false,
  "overview": "From DC Comics comes the Suicide Squad, an antihero team of incarcerated supervillains who act as deniable assets for the United States government, undertaking high-risk black ops missions in exchange for commuted prison sentences.",
  "release_date": "2016-08-03",
  "genre_ids": [
    14,
    28,
    80
  ],
  "id": 297761,
  "original_title": "Suicide Squad",
  "original_language": "en",
  "title": "Suicide Squad",
  "backdrop_path": "/ndlQ2Cuc3cjTL7lTynw6I4boP4S.jpg",
  "popularity": 48.261451,
  "vote_count": 1466,
  "video": false,
  "vote_average": 5.91
};

let imageUrl = `${baseUrl}${defaultPosterSize}${movie.poster_path}`

Eg. 
<img src=`${baseUrl}${defaultPosterSize}${movie.poster_path}` />
<img src="https://image.tmdb.org/t/p/w500/e1mjopzAS2KNsvpbpahQ1a6SkSn.jpg" />
```

- Story 2: Add "Load more Movies" button. On click get the next 20 popular movies and display them.

*Hint:* Use the page query param.

- Story 3: Navigate from the movie card to the movie's detailed page.


### Sign in page

- Story 1: The User can sign in into the Movie Library application with his e-mail and password.
  For now I need to be able to sign in with:

```
E-mail: admin@admin.com
Password: admin123
```

**Method**
POST

**Route**
accounts:signInWithPassword

**Query String**
key: string _required_

**Request Body**
Object {
email: string _required_
password: string _required_
}

**Response**
Error:
```json
error: {
  code: 400
  errors: [
    0: {
      domain: "global"
      message: "EMAIL_NOT_FOUND"
      reason: "invalid"
    }
  ]
  message: "EMAIL_NOT_FOUND"
}
```
Success:
```json
displayName: ""
email: "admin@admin.com"
idToken: `eyJhbGciOiJSUzI1NiIsImtpZCI6IjBwUjNXdyJ9.eyJpc3MiOiJodHRwczovL2lkZW50aXR5dG9vbGtpdC5nb29nbGUuY29tLyIsImF1ZCI6InByYWN0Y2Utb24tZm9jdXMiLCJpYXQiOjE1ODgxNTQwMDYsImV4cCI6MTU4OTM2MzYwNiwidXNlcl9pZCI6ImpBd3hjZnFJTFpPWlplU2p2aGNwaHNQODhjdzEiLCJlbWFpbCI6ImFkbWluQGFkbWluLmNvbSIsInNpZ25faW5fcHJvdmlkZXIiOiJwYXNzd29yZCIsInZlcmlmaWVkIjpmYWxzZX0.G40t_Gi3UXAT6l3K3URS6IB6lYKiVMz2Talc2pF1dP35nFjto1FEQEYqXDQ_QKe9EnxrRxRh_yiAxcWHxJG4pyf00kM2PbtaARmXDL5zsZI6KwIlj3thxeqrwRVZdEnZTIXI-hnLeUAFCdFL40bscZX0ZevLUO-CUzFqFUPRsEPqyFQqZTKRuiOm2YFMtXLVUBkhk8howOxpJRL4jmnvzC48w0v8dVbx4bneWSOyVOe2lWOMrj9J5NvonYIiaWbnSAamDrXosVkOvpJh5z6CBiIMWmZFom_CNuolkqcnRZFi2ux488qiY2I_DpG9HEl5IBtI484y8aZNq-hD3z1qxg`
kind: "identitytoolkit#VerifyPasswordResponse"
localId: "jAwxcfqILZOZZeSjvhcphsP88cw1"
registered: true
```

Eg.

`${authApiUrl}accounts:signInWithPassword?key=${firebaseApiKey}`


### Sign up page
- Story 1: Create Authentication guard - if the user is signed in you should redirect directly to home page if he tries to access **sign in** and **sign up** routes

- Story 2: The User can sign up into the Movie Library application providing his **e-mail** and **password**. The form should also have **confirmation password** field.

NOTE: You should have validations for:
- Required fields (both)
- The email must be valid
- The password must be atleast 6 symbols
- The passwords must match

**Method**
POST

**Route**
accounts:signUp

**Query String**
key: string _required_

**Request Body**
Object {
email: string _required_
password: string _required_
}

**Response**
Error:
```json
error: {
  code: 400
  errors: [
    0: {
      domain: "global"
      message: errorType
      reason: "invalid"
    }
  ]
  message: errorType
}

```
Success:
```json
displayName: ""
email: "test@test.com"
idToken: `eyJhbGciOiJSUzI1NiIsImtpZCI6IjBwUjNXdyJ9.eyJpc3MiOiJodHRwczovL2lkZW50aXR5dG9vbGtpdC5nb29nbGUuY29tLyIsImF1ZCI6InByYWN0Y2Utb24tZm9jdXMiLCJpYXQiOjE1ODgxNTQwMDYsImV4cCI6MTU4OTM2MzYwNiwidXNlcl9pZCI6ImpBd3hjZnFJTFpPWlplU2p2aGNwaHNQODhjdzEiLCJlbWFpbCI6ImFkbWluQGFkbWluLmNvbSIsInNpZ25faW5fcHJvdmlkZXIiOiJwYXNzd29yZCIsInZlcmlmaWVkIjpmYWxzZX0.G40t_Gi3UXAT6l3K3URS6IB6lYKiVMz2Talc2pF1dP35nFjto1FEQEYqXDQ_QKe9EnxrRxRh_yiAxcWHxJG4pyf00kM2PbtaARmXDL5zsZI6KwIlj3thxeqrwRVZdEnZTIXI-hnLeUAFCdFL40bscZX0ZevLUO-CUzFqFUPRsEPqyFQqZTKRuiOm2YFMtXLVUBkhk8howOxpJRL4jmnvzC48w0v8dVbx4bneWSOyVOe2lWOMrj9J5NvonYIiaWbnSAamDrXosVkOvpJh5z6CBiIMWmZFom_CNuolkqcnRZFi2ux488qiY2I_DpG9HEl5IBtI484y8aZNq-hD3z1qxg`
kind: "identitytoolkit#VerifyPasswordResponse"
localId: "jAwxcfqILZOZZeSjvhcphsP88cw1"
registered: true
```

Eg.

`${authApiUrl}accounts:signUp?key=${firebaseApiKey}`


### Movie detailed page

Create a movie detailed page. Each movie on his detailed page is represented by three sections:

- Story 1: Overview section
  - Poster image
  - Title
  - Release date - The release date should be in format DD/MM/YYYY
  ```json
  Eg. "release_date": "2019-09-17" --> 17/09/2019
  ```
  - Genres - If there is more then one genre, they should be listed separated by ","
  - Runtime - The runtime should be in format HH:MM
  ```json
  Eg. "runtime": 123 --> 2h 3m
  ```
  - Average vote - The avarage vote should be formatted in percentage
  ```json
  Eg. "vote_average": 6 --> 60%
  ```
  - Tagline
  - Overview
  
Get the information for **the overview section** for each movie from the TMDb's server.
  ```
  https://developers.themoviedb.org/3/movies/get-movie-details
  ```

- Story 2: Top Cast section
  - List the first 10 cast members.
  - Each cast member is represented by profile image, name and character
  - If the list of cast members has more than 10 members show "See Full Cast Members" button which navigates to "Movie Cast Page"
  
Get the information for **the Top Cast section** for each movie from the TMDb's server.
```
https://developers.themoviedb.org/3/movies/get-movie-credits
```

**NOTE**: To get the profile image you should use baseUrl, size and profile_path. (same as poster image)

- Story 3: Reviews
  - List only the first 3 reviews.
  - Each review is represented by author and content.
  - If the list of reviews has more than 3 reviews show "Read All Reviews" button which navigates to "Movie Reviews Page"
  - If the movie doesn't have any reviews display: "This movie doesn't have any reviews"
  
Get the information for **the Reviews** for each movie from the TMDb's server.
```
https://developers.themoviedb.org/3/movies/get-movie-reviews
```

**NOTE**: Some of the reviews may have really long content. Think how to represent it best.

- BONUS STORY: Recommendations section 
  - List of recommended movies for a movie represented by a poster image, title, release date (DD/MM/YYYY) and average vote (in percentage)
  
Get the information for **Recommendations section** for each movie from the TMDb's server.
```
https://developers.themoviedb.org/3/movies/get-movie-recommendations
```

### Movie Cast Page

- Story 4: List the full cast members. Each cast member is represented by profile image, name and character.
```
https://developers.themoviedb.org/3/movies/get-movie-credits
```

### Movie Reviews Page

- Story 5: List the full reviews. Each review is represented by author and content. (use movieReviews.json)
```
https://developers.themoviedb.org/3/movies/get-movie-reviews
```


The API KEY and the BASE URL for **Favorites** Feature
```json
const API_KEY = 'AIzaSyD15XONBwSn_kgvyJ7OE46Zt_CZ7_Yl6nM';
const BASE_URL = 'https://practce-on-focus.firebaseio.com';
```

### Favorites - Additional task
- Story 1: The signed in user must be able to access his "Favorites" collection page. The link to "Favorites" should be displayed in the navigation bar only if the user is **signed in**. If the **not signed in** user tries to access "Favorites" page redirect to **Sign in**.
The page contains all movies liked by the user. If the user doesn't have favorites movies show coresponding message.

**Method**
GET

**Route**
`/favorites/${localId}.json`

**Query String**
key: string _required_

**Request Body**

Eg.
${BASE_URL}/favorites/${localId}.json?key=${API_KEY}

- Story 2: The signed in user must be able to add movie to his "Favorites" collection. The movie can be add from the main home screen or from the movie's detailed page. If the **not signed in** user tries to add a movie to his "Favorites" redirect to **Sign in**.

**Method**
PUT

**Route**
`/favorites/${localId}/${movie.id}.json`

**Query String**
key: string _required_

**Request Body**
The entire movie Object

Eg.
${BASE_URL}/favorites/${localId}/${movie.id}.json?key=${API_KEY}

- Story 3: The signed in user must be able to remove movie to his "Favorites" collection. The movie can be removed from the main home screen or from the movie's detailed page.

**Method**
DELETE

**Route**
`/favorites/${localId}/${movie.id}.json`

**Query String**
key: string _required_

Eg.
${BASE_URL}/favorites/${localId}/${movie.id}.json?key=${API_KEY}

- Story 4: The signed in user must be able to add/edit **personal note** to his favorites movies. The personal note to his favorite movie must be displayed in the movie's **Detailed paeg**.

**Method**
PATCH

**Route**
`/favorites/${localId}/${movie.id}.json`

**Query String**
key: string _required_

**Request Body**
Objects {
  personalNote: *string*
}

Eg.
${BASE_URL}/favorites/${localId}/${movie.id}.json?key=${API_KEY}

- If you have additional time you can implement Redux store. Please discuss with mentor: Add favorites list to the Redux store. Update the information in store when adding/removing from favorites. Connect the store with **the Favorites Components**. 


## 3. Assignment Grading

Writing quality code that builds without warnings or errors, and then testing the resulting application and iterating until it functions properly is the goal.
