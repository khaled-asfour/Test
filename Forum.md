# SubFourms

## List SubFourm

```
GET /api/Subfourm
```

List All SubFourm

### Response:

```
200 ok
{
    "subfourm": [{
        "id","subforum-id"
        "name": "something",
        "description": "some Body text",
        "number_of_post" :100,
        "posts_date": "3 months"
    }]
}
```

## Display SubFourm

```
GET /api/SubFourm/{id}
```

Display SubFourm

### Response:

```
200 OK
{
    "id": ""
    "name": "something",
    "description": "some description text",
    "number_of_post":100,
    "posts_date": "3 months"
}
```

### Errors:

```
404 subfourm not found
{
    "id": "subfourm-id",
    "message": "there was no data found."
}
```

# Posts

## Create Post

```
POST /api/Posts [Auth]
```

Create a new post

### Request Body:

```
{
    "title": "something",
    "body": "some Body text",
    "subforumId": "id",
    "imageurl": "img.png"
}
```

### Response:

```
201
{
    "id": "post-id",
    "createdAt": "date"
    "title": "something",
    "body": "some Body text",
    "imageurl": "img.png"
    user object and subfourm object
}
```

### Errors:

```
400 Fields invalid
{
    "title": "required",
    "imageurl": "not vaild image"
}

404
{
    "subforumId": "unkown subforum"
}
```

## List Posts

```
GET /api/Posts [Auth]
```

List All Posts

### Query Parameters:

- `paginator`:object
- `items`: object

### Response:

```
200 ok
{
    "paginator": {
            "page":1,
            "max-post":10,
            "total":20
    },
    "items": [{
            "id": "post-id",
            "title": "something",
            "body": "some Body text",
            "imageurl": "img.png",
            "number_of_votes":"999",
            "createdAt": "2 hours",
            "score": "-1",
            "subfourm": {
                "id": "subfourm-id",
                "subforum_name": "technology"
            },
            "user": {
                 "id": "user-id"
                 "username": "jhon"
            }
    }]
}
```

### Errors:

```

```

## List Posts

```
GET /api/Posts
```

List All Post

### Query Parameters:

- `paginator`:object
- `items`: object

### Response:

```
200 ok
{
    "paginator": {
            "page":1,
            "max-post":10,
            "total":20
    },
    "items": [{
            "id": "post-id",
            "title": "something",
            "body": "some Body text",
            "imageurl": "img.png",
            "number_of_votes":"999",
            "createdAt": "2 hours",
            "subfourm": {
                "id": "subfourm-id",
                "subforum_name": "technology"
            },
            "user": {
                 "id": "user-id"
                 "username": "jhon"
            }
    }]
}
```

## My Posts

```
GET /api/Posts/MyPosts [Auth]
```

List All Post

### Query Parameters:

- `paginator`:object
- `items`: object

### Response:

```
200 ok
{
    "paginator": {
            "page":1,
            "max-post":10,
            "total":20
    },
    "items": [{
            "id": "post-id",
            "title": "something",
            "body": "some Body text",
            "imageurl": "img.png",
            "number_of_votes":"999",
            "createdAt": "2 hours",
            "score":"-1",
            "subfourm": {
                "id": "subfourm-id",
                "subforum_name": "technology"
            },
            "user": {
                 "id": "user-id"
                 "username": "jhon"
            }
    }]
}
```

## Display Post

```
GET /api/Posts/{id} [Auth]
```

Display a Post

### Query Parameters:

- `items`:object

### Response:

```
200 ok
 {
    "items": {
        "share_link": "www.xyz.com/posts/{id}",
        "id": "post-id",
        "createdAt": "2 hours",
        "number-of-votes":"123",
        "score":"1",
        "title": "post titile",
        "imageURL": "img.png"
        "subfourm": {
            "id": "subfourm-id",
            "subforum_name": "technology"
        },
        "user": {
            "id": "user-id",
            "userbname": "jhon"
        },
    },
}

```

### Errors:

```
404 post not found
{
    "id": "post-id",
    "message": "there was no data found."
}
```

## Delete Post

```
DELETE /api/Posts/{id} [Auth]
```

Delete Post

### Response:

```
204
{
}
```

### Errors:

```
404 post not found
{
   "id": "post-id",
   "message": "post not found"
}
```

# Votes

## Create Comment Vote

```
POST /api/Votes [Auth]
```

Create a new comment vote

### Request Body:

```
{
    "score": 1,
    "commentId": "comment-id",
}
```

### Response:

```
201 {
        "id": "vote-id",
        "score": 1,
        "commentId": "comment-id"
    }
```

### Errors:

```
404 Comment  not found
{
   "id": "post-id",
   "message": "post not found"
}
```

## Create Post Vote

```
POST /api/Votes [Auth]
```

Create a new post vote

### Request Body:

```
{
    "score": 1,
    "postId": "post-id"
}
```

### Response:

```
201 created
{
    "id": "vote-id",
    "score": 1,
    "postId": "post-id"
}
```

### Errors:

```
404 post not found
{
   "id": "post-id",
   "message": "post not found"
}
```

## Create Reply Vote

```
POST /api/Votes [Auth]
```

Create a new reply vote

### Request Body:

```
{
    "score": 1,
    "replyId": "reply-id"
}
```

### Response:

```
201 created
{
    "id": "vote-id",
    "score": 1,
    "replyId": "reply-id"
}
```

### Errors:

```
404 reply not found
{
   "id": "reply-id",
   "message": "reply not found"
}
```

## Delete Comment Vote

```

DELETE /api/votes/{id}

```

Delete comment vote

### Response:

```
204 no content
{
}
```

### Errors:

```
404 comment not found
{
   "id": "comment-id",
   "message": "comment not found"
}
```

## Delete Reply Vote

```

DELETE /api/votes/{id}

```

Delete reply vote

### Response:

```
204 no content
{
}
```

### Errors:

```
404 reply not found
{
   "id": "reply-id",
   "message": "reply not found"
}
```

## Delete Post Vote

```

DELETE /api/votes/{id}

```

Delete post vote

### Response:

```
204 no content
{
}
```

### Errors:

```
404 post not found
{
   "id": "post-id",
   "message": "post not found"
}
```

# Comments

## Create Comment

```

POST /api/Comments [Auth]

```

Create a new comment

### Request Body:

```
{
    "comment_text": "comment to a post",
    "postId": "post-id"
}
```

### Response:

```
201 created
{
    "id": "comment-id",
    "comment_text": "comment to a post",
    "postId": "post-id"
}
```

### Errors:

```
400 bad requset
{
   "id": "comment-id",
   "message": "comment text can not be empty."
}
404 post not found
{
   "id": "post-id",
   "message": "there was no data found."
}
```

## Delete Comment

```

DELETE /api/Comments/{id} [Auth]

```

Delete a comment

### Response:

```
204 no content
{
}
```

### Errors:

```
404 comment not found
{
   "id": "comment-id",
   "message": "there was no data found."
}
```

## List Comments

```

GET /api/Comments [Auth]

```

list all comments

### Query Parameters:

- `paginator`:object
- `items`: object
- `postId`:string

### Request

```
{
    "postId":"post-id"
}
```

### Response:

```

200 ok
 {
    "paginator": {
        "page":1,
        "max-post":10,
        "total":20
    },
    "items": [{
        "id": "comment-id"
        "createdAt": "2 hours",
        "number-of-votes":"123",
        "score":"1",
        "comment_text": "comeeeeeeeeent sfha",
        "reply_link": "www.xyz.com/reply",
        "subfourm": {
            "id": "subfourm-id",
            "subforum_name": "technology"
        },
        "replies": [{
            "user": {
                "id": "user-id"
                "username": "jhon"
            },
                "createdAt": "2 hours",
                "number-of-votes": "999",
                "score": "-1",
                "commentId": "comment-id"
        }],
    }]
}
```

### Errors:

```
404 post not found
{
    "postId":"post-id",
    message:"post not found",
}
```

# Replies

## Create Reply

```
POST /api/Replies [Auth]
```

Create a new reply

### Request Body:

```
{
    "reply_text": "reply to a post",
    "commentId": "comment-Id"
}
```

### Response:

```
201 created
{
    "id": "reply-id",
    "reply_text": "reply to a post",
    "commentId": "coment-Id"
}
```

### Errors:

```
400 bad requset
{
   "id": "reply-id",
   "message": "reply text can not be empty."
}

404 comment not found
{
   "id": "comment-id",
   "message": "there was no data found."
}
```

## Delete reply

```
DELETE /api/Replies/{id} [Auth]
```

delete a reply

### Response:

```
204 no content
{
}
```

### Errors:

```
404 reply not found
{
   "id": "reply-id",
   "message": "there was no data found."
}
```

# Users

## Create User

```
POST /api/Auth/Register
```

Create a new user

### Request Body:

```
{
    "email": "test@test.com",
    "username": "test-username",
    "password": "TheUser@1"
}
```

### Response:

```
201 created
{
}
```

### Errors:

```
400 Fields invalid
 {
    "email": "existing email",
    "username": "existing username",
    "password": "unvalidate password"
}
```

## Login User

```
POST /api/connect/token
```

login user

### Request Body:

```
{
    "email": "email@email.com",
    "password": "password"
}
```

### Response:

```
202 Accepted
{
    "access_token":"jwt_token"
}

```

### Errors:

```

Field invalid

400
{
    "email": "required",
    "username": "exist username"
}

403
{
    "password": "wrong password"
}

404
{
    "email": "existing email",
    "password": "unvalidate password"
}

```

## Send Code Password

```

POST /api/Auth/ResetPassword/SendCode

```

reset user password

### Request Body:

```
{
    "email": "test@test.com"
}
```

### Response:

```

200 oK
{
}

```

### Errors:

```
404 email not found
{
    "email": " email dosen't exist"
}
```

## Valid Code Password

```

POST /api/Auth/ResetPassword/VerfiyCode

```

reset user password

### Request Body:

```
{
    "email": "test@test.com",
    "code": "dasf"
}
```

### Response:

```

200 oK
{
    "valid":"true"
}

```

### Errors:

```
404 token not active {
    "message": "This password reset token is invalid."
}
```

## Change User Password

```

POST /api/Auth/ResetPassword/ChangePassword

```

reset user password

### Request Body:

```
{
    "email": "test@test.com",
    "password": "seceret",
    "code": "code"
}
```

### Response:

```

200 oK
{
}

```

### Errors:

```
404 email not found {
    "email": " email dosen't exist"
}
```

# Profiles

## Display User Profile

```
GET /api/Profiles/MyProfile/{id} [Auth]
```

Display an user profile

### Query Parameters:

- `user`:object

### Response:

```
200 ok
 {
    "user": {
        "id": "user-id",
        "userbname": "jhon"
    },
}

```

### Errors:

```

404 post not found
{
    "id": "user-id",
    "message": "there was no data found."
}
```

## Edit User Profile

```
PUT /api/Profiles/MyProfile/{id} [Auth]
```

edit an user profile

### Request Body:

```
{
    "username": "username",
    "password": "password"
}
```

### Response:

```
200 ok
{

}

```

### Errors:

```
400 username not valid
{
    "username": "sgeorige",
    "message": "is already taken"
}
404 post not found
{
    "id": "user-id",
    "message": "there was no data found."
}
```

## Change Password User Profile

```
PUT /api/Profiles/ /{id} [Auth]
```

edit an user profile

### Request Body:

```
{
    "current_password": "oldseceret",
    "new_password": "newsecret"
}
```

### Response:

```
200 ok
{
}

```

### Errors:

```
400 username not valid
{
    "password": "password not valid",
}
404 post not found
{
    "id": "user-id",
    "message": "there was no data found."
}
```
