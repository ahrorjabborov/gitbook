---
description: >-
  The AiKYNETIX Web API provides a comprehensive set of endpoints to manage user
  accounts and related administrative tasks.
---

# 👨‍💻 User Management

### <mark style="color:purple;">Creating a New User</mark>

Administrators can create a new user by submitting a minimal JSON payload. The required fields include the user's email and display name, while the phone number is optional.

```
POST /user-management/users/
```

#### Request Body Example

```
{
  "email": "user@gmail.com",
  "display_name": "User",
  "phone": "932323232"
}
```

#### Response

On success, a JSON object is returned containing the newly created user’s data:

```
{
  "userData": {
    "user_uid": "MYmC7MzsPBNU6uSQBnJ0",
    "email": "user@gmail.com",
    "display_name": "User",
    "phone": "932323232"
  }
}
```

***

### <mark style="color:orange;">Updating User Details</mark>

Update an existing user’s profile by sending a JSON payload with the user’s unique identifier along with any new or updated fields. Additional profile attributes such as physical metrics and preferences can be included.

#### Endpoint

```
PUT /user-management/users/
```

#### Request Body Example

```
curl -L \
  --request PUT \
  --url 'https://aikpy-nsz2.onrender.com/user-management/users/' \
  --header 'Authorization: API-KEY YOUR_API_TOKEN' \
  --header 'Content-Type: application/json' \
  --data '{
    "user_uid": "DSdmk3mKd9Dmsmsd",
    "display_name": "User1",
    "email": "User1@example.com",
    "height": 175,
    "weight": 68,
    "age": "23",
    "ycom": 0.95,
    "leg_length": 0.91,
    "shoeSize": "7",
    "brand": "Adidas",
    "shoeModel": "UltraBoost",
    "gender": "Female"
  }'
```

#### Response

A successful update returns a confirmation message:

```
{
  "message": "User information updated successfully."
}
```

***

### Retrieving Users

Administrators can retrieve a list of all users associated with their account. The API supports both simple and filtered retrieval, including pagination for large user bases.

#### List All Users

**Endpoint:**

```
GET /user-management/users/
```

#### Response Example:

```
{
  "users": [
    {
      "user_uid": "MYmC7MzsPBNU6uSQBnJ0",
      "email": "user@gmail.com",
      "display_name": "User",
      "phone": "932323232",
      "created_at": "2024-12-02T19:17:30.371Z",
      "age": "30",
      "weight": 79.8,
      "height": 177.8,
      "ycom": 1.01,
      "leg_length": 0.96,
      "shoeSize": "8",
      "brand": "Nike",
      "shoeModel": "Peak-smart"
    },
    {
      "user_uid": "CMQe1HuAg4uMXqHE6dVO",
      "email": "user1@example.com",
      "display_name": "User1",
      "phone": "8328889011",
      "created_at": "2024-08-16T00:29:21.349Z",
      "age": "22",
      "weight": 70,
      "height": 174,
      "ycom": 0.96,
      "leg_length": 0.91,
      "shoeSize": "6",
      "brand": "Fabletics",
      "shoeModel": "The Everyday Sneaker II"
    }
  ]
}
```

***

#### Filtering and Pagination

Use query parameters to filter the list of users or paginate results:

* **start\_after\_id**: UID after which to begin the list.
* **end\_before\_id**: UID before which to end the list.
* **limit**: Maximum number of users to return (default is 5).

**Endpoint:**

```
GET /user-management/users/filter/
```

#### Example Request:

```
GET /user-management/users/filter/?limit=10&activity=Running
```

**Response includes:**

* `query_count`: Total number of matching users.
* `users`: Array of user objects.
* `first_uid` and `last_uid`: UIDs for pagination.

***

### Retrieving Specific User Details

Retrieve detailed information for a specific user by providing their unique user UID.

#### Endpoint

```
GET /user-management/users/{user_uid}
```

#### Example Request

```
GET /user-management/users/CMQe1HuAg4uMXqHE6dVO
```

#### Example Response

```
{
  "user_uid": "CMQe1HuAg4uMXqHE6dVO",
  "email": "user1@example.com",
  "display_name": "User1",
  "phone": "8328889011",
  "created_at": "2024-08-16T00:29:21.349Z",
  "age": "22",
  "weight": 70,
  "height": 174,
  "ycom": 0.96,
  "leg_length": 0.91,
  "shoeSize": "6",
  "brand": "Fabletics",
  "shoeModel": "The Everyday Sneaker II",
  "gender": "Female"
}
```

***

### <mark style="color:red;">Deleting a User</mark>

Administrators can delete a user from their account by providing the user’s unique UID in the request body.

#### Endpoint

```
DELETE /user-management/users/
```

#### Request Body Example

```
{
  "user_uid": "MYmC7MzsPBNU6uSQBnJ0"
}
```

#### Response

A successful deletion returns a confirmation message:

```
{
  "message": "User with UID MYmC7MzsPBNU6uSQBnJ0 deleted from admin."
}
```

***

### Managing Sub-Admin Invitations and Assignments

Administrators can invite users to become sub-admins and manage sub-admin assignments.

#### List Invitations

**Endpoint:**

```
GET /admin-management/invitation/
```

Retrieve a list of pending invitations. Each invitation includes details such as the inviter’s information, invitee email, and invitation status.

#### Create an Invitation

**Endpoint:**

```
POST /admin-management/invitation/
```

Submit a JSON payload with the invitee’s email (and optionally a platform link):

```
{
  "user_email": "invitee@example.com",
  "platform_link": "https://yourplatform.com/welcome"
}
```

#### Remove an Invitation

**Endpoint:**

```
DELETE /admin-management/invitation/
```

Provide the `invite_token` in the request body to remove the invitation.

#### Sub-Admin Management

Administrators can also retrieve, add, or remove sub-admins using the following endpoints:

* **Retrieve, Add and Remove Sub-Admins:**

```
GET /admin-management/sub-admins/
POST /admin-management/sub-admins/
DELETE /admin-management/sub-admins/
```

***

### Retrieving Organization Status

Admins and sub-admins can retrieve organization status details including session count, user UID, role, payment type, and associated activities.

#### Endpoint

```
GET /user-management/organization-status/
```

#### Example Response

```
{
  "session_number": 50,
  "uid": "aB3xYz1PqW8LmTnK4R9VfJ0gHsCd",
  "role": "admin",
  "payment_type": "Enterprise",
  "activity": ["Running", "Weightlifting", "VerticalJump"],
  "companyName": "Apple",
  "name": "Username"
}
```

