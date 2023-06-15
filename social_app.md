# Social application

### 1. Assignment Goals

The goal of this project is to show all accumulated knowledge in the last month.

Technologies:
- SCRUM
- GIT
- HTML & CSS
- JavaScript

#### 2. Assignment Description

- General Requirements:
  - Create beautiful and responsive UI
  - Use semantic HTML
  - Use modules to split your application logic
  - Create several modules and use them in the routing
  - Use guards to prevent the user to access the routes
  - All of the data should be loaded from a web server
  - Each form should have validations and error handling
  - Your project should pass the default linting configuration without any errors
  - Your application should compile, work and produce an adequate result
  - Use Bitbucket and take advantage of the branches for writing your features.
  - Code Quality:
    - Meaningful methods and variable names;
    - Following JavaScripts code style guides and formatting;
    - Over/under used methods, classes, variables, data structures or code comments;
    - Adequate code reuse.
  - Unit test a few components and services

#### 2.1. The Social Application Overview

Your task is to create a Social Application. The App allows the users to upload photos to your service and share them as public for everyone or private only for their followers. Users should be able to review their posts, to delete them or change their privacy, to update their profile or request delete of the account. They can also view, comment and like posts shared by others. They should be able to review their followers and the people they follow and the posts they liked. They could receive notifications if someone followed them or liked their post.

For an example of such application, look at Instagram ;)

#### 2.2. The Social Application Specifications

**Public Part**
The public part of your projects should be visible without authentication.

- Application **MUST** have public Homepage
  - Not registered user can review only the public posts shared by others.
- Application **MUST** have Register functionality
  - The User **MUST** fill username, e-mail, password and repeat password fields.
  - All sign up fields **SHOULD** have data validation
- Application **MUST** have Login functionality
  - The User **MUST** be able to sign in with username and password.

As for authenticated users:

- Application **MUST** have Logout functionality
  - The User **MUST** be able to logout.
  - The User **COULD** be able to logout and afterwards when he/she try to login, a default user should be stored in the browser. The application should ask only for password ( the username should be prefilled ). **You can checkout Instagram/Facebook for reference.**

**Private part**
Registered users **MUST** have private area in the web application accessible after successful login, where they could see all posts created by them, all posts public and private created by the people they follow, a list of all followers and the people they follow, all liked posts and notifications.

- The user **MUST** be presented with an UI which allows him to create a post and enter the required post information and then “CREATE” the post. The newly created post is added to his profile page.
- Each user **MUST** add title, description, photo, status (private or public) and **COULD** add location to the post. Each post is created with additional information for id, author, date, likes and comments.
- The user **MUST** be able to review all posts created by him, post comments and likes and **SHOULD** be able to delete and change the status of the posts. - photo shouldn’t be deleted
- The user **MUST** be able to change his profile picture and **SHOULD** request delete of the account.
- The user **COULD** receive notification when someone followed him or liked his post.
- The user **MUST** be able to view other users’ profiles, information and public posts. The user **MUST** be able to follow them and after that see all posts - public and private.
- The User **MUST** be able to like and comment other’s posts.
- The User **SHOULD** search other users by their username.
- The User **SHOULD** be able to see a list of all followers and the people they follow - unfollow people
- The User **COULD** change the app theme from light to dark and reverse.

#### 3. Assignment Grading

In all of the assignments, writing quality code that builds without warnings or errors, and then testing the resulting application and iterating until it functions properly is the goal.

Here are the most common reasons assignments receive low points:

- Project does not build.
- One or more items in the Required Tasks section was not satisfied.
- A fundamental concept was not understood.
- Project does not build without warnings.
- Code is visually sloppy and hard to read (e.g. indentation is not consistent, etc.).
- Your solution is difficult (or impossible) for someone reading the code to
  understand due to lack of comments, poor variable/method names, poor solution
  structure, long methods, etc.
- Assignment is not submitted as per Assignment Submission section below.


#### 4. Social App API 
```
BASE_URL = "https://social-app.scalefocus.academy"
```

#### 4.1. Sign in

**Method**
POST

**Route**
/auth/login

**Request Body**
```
Object {
  username: string  _required_
  password: string  _required_
}
```

#### 4.2. Sign up

**Method**
`POST`

**Route**
`/auth/register`

**Request Body**
```
Object {
  username: string  _required_
  email: string  _required_
  password: string  _required_
}
```

#### 4.3 Logout

**Method**
`DELETE`

**Route**
`/auth/logout`

#### 4.4 Get public posts 

**Method**
`GET`

**Route**
`/posts`

**Query String**
```
take: number _required_ - How many posts to request from the base
skip: number _required_ - The index from which to start taking the posts
public: boolean - Public or private posts
```

#### 4.5 Get private posts

**Method**
`GET`

**Route**
`/posts/dashboard`

**Query String**
```
take: number _required_ - How many posts to request from the base
skip: number _required_ - The index from which to start taking the posts
```

#### 4.6 Create Single Post

**Method**
`POST`

**Route**
`/posts`

**Request Body**
```
Object {
  description: string  _required_
  public: boolean  _required_
  image: file  _required_
  location: string _required_
}
```

#### 4.7 Get single post

**Method**
`GET`

**Route**
`/posts/{id}`

#### 4.8 Edit single post status

**Method**
`PUT`

**Route**
`/posts/{id}/status`

```
Object {
  public: boolean  _required_
}
```

#### 4.9 Delete post

**Method**
`DELETE`

**Route**
`/posts/{id}`

#### 4.10 Comment post

**Method**
`POST`

**Route**
`/comments/{postId}`

**Request Body**
```
Object {
  content: string  _required_
}
```

#### 4.11 Edit comment

**Method**
`PATCH`

**Route**
`/comments/{commentId}`

**Request Body**
```
Object {
  content: string  _required_
  id: number (comment id) _required_
}
```

#### 4.12 Delete comment

**Method**
`DELETE`

**Route**
`/comments/{commentId}`

#### 4.13 Get single comment

**Method**
`GET`

**Route**
`/comments/{commentId}`

#### 4.14 Like post

**Method**
`POST`

**Route**
`posts/{postId}/votes`

**Request Body**
```
Object {}   
```

#### 4.15 Dislike post

**Method**
`DELETE`

**Route**
`posts/{postId}/votes`

#### 4.16 Get users

**Method**
`GET`

**Route**
`/users`

#### 4.17 Get user

**Method**
`GET`

**Route**
`/users/{userId}`

#### 4.18 Get user's posts

**Method**
`GET`

**Route**
`/users/{userId}/posts`

#### 4.19 Get user's following

**Method**
`GET`

**Route**
`/users/{userId}/following`

#### 4.20 Get user's followers

**Method**
`GET`

**Route**
`/users/{userId}/followers`

#### 4.21 Follow user

**Method**
`PUT`

**Route**
`/users/{userId}/followers`

**Request Body**
```
Object {}   
```

#### 4.22 Unfollow user

**Method**
`DELETE`

**Route**
`/users/{userId}/followers`

#### 4.23 Delete user

**Method**
`DELETE`

**Route**
`/users/{userId}`

#### 4.24 Change avatar

**Method**
`PUT`

**Route**
`/users/avatar`

**Request Body**
```
FormData {
    avatar: _required_  
}
```

#### 4.25 Get notifications

**Method**
`GET`

**Route**
`/notifications/likes`


#### 5. Assignment Grading

Writing quality code that builds without warnings or errors, and then testing the resulting application and iterating until it functions properly is the goal.
