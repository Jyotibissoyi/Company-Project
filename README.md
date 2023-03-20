# Company-Project

#  About
Run a SaaS Platform that enables user to make their communities and add members to it.

Each user, can create a community and (automatically) gets assigned the Community Admin role. They can add other users to the community who get assigned the Community Member role.

To restrict access, you need to develop a Scope-based Authorization system,

where any User who has signed up and create a Community
must have a Role (ex: Community Admin, Community Member)
to perform any actions on the resources (eg: member, community)

------------------------------<>-------------------------------------

In this project we use dependencies #ExpressJS #  Mongoose # Nodemon # dotenv And for Store data we use # MongoDB. Before going to start this project install all dependencies by using command ---> npm i 

START COMMAND ---> #npm start   // By using this command we start our server.

All the handler part present in controller were I CRUD perform operations or create, delete and get api's. In this project client can create a task and store inside Database(MongoDB). And fetch Data whenever required. I use mongoose for creating Schema which present in Model Folder.

Here I perform create and get operation for create community, get task and also use status code for response.

This project is running on PORT 3001 And cluster link also mentioned and I use #dotenv npm package for port number and cluster link.

#QUESTION-

Roles
List of roles:

Community Admin

can view all members
can add new members
can remove members
Community Member

can view all members
Community Moderator

can view all members
can remove members
Problem Statement
You need to build the APIs that adheres to above user stories.
The Role names are strict.
The API URLs and Response Structure is fixed.
The field attributes and table names are strict as well.
Addition of field for storing IDs when using NoSQL is allowed.
Validations for each API must be carried out.
Tech Stack
Language: Node v14+
Database: Postgres / MySQL / MongoDB
ORM: Sequelize / Prisma / Mongoose / MongoDB Native Driver
Library: @theinternetfolks/snowflake to generate unique IDs instead of autoincrement, UUID or MongoDB ObjectID
You are free to choose any database and ORM that goes with it for your use.

Make sure to see all the examples including Success and Error example, by going to any "Example Request" and selecting from the dropdown on the right.

Please read the FAQ section at the end for more clarifications.

User (user)
Key	Kind	Notes
id	string (snowflake)	primary key
name	varchar(64)	default: null
email	varchar(128)	unique
password	varchar(64)	-
created_at	datetime	-
Community (community)
Key	Kind	Notes
id	string (snowflake)	primary key
name	varchar(128)	-
slug	varchar(255)	unique
owner	string (snowflake)	ref: > user.id, relationship: m2o
created_at	datetime	-
updated_at	datetime	-
Role (role)
Key	Kind	Notes
id	string (snowflake)	primary key
name	varchar(64)	unique
created_at	datetime	-
updated_at	datetime	-
Member (member)
Key	Kind	Notes
id	string (snowflake)	primary key
community	string (snowflake)	ref: > community.id
user	string (snowflake)	ref: > user.id
role	string (snowflake)	ref: > role.id
created_at	datetime	-
Note:
Snowflake IDs are just string. Think of them just like UUID. Use our library to generate unique Snowflake IDs . It works exactly like generating UUIDs.

API Endpoints
Role
Name	URL
Create	POST /v1/role
Get All	GET /v1/role
User
Name	URL
Sign Up	POST /v1/auth/signup
Sign in	POST /v1/auth/signin
Get Me	GET /v1/auth/me
Community
Name	URL	Role
Create	POST /v1/community	-
Get All	GET /v1/community	-
Get All Members	GET /v1/community/:id/members	Community Admin / Community Moderator / Community Member
Get My Owned Community	GET /v1/community/me/owner	-
Get My Joined Community	GET /v1/community/me/member	-
Member
Name	URL	Role
Add Member	POST /v1/member	Community Admin
Remove Member	DELETE /v1/member/:id	Community Admin / Community Moderator

Output
You need to provide code that can run these APIs.

Use this link to submit the Assignment - http://bit.ly/tif-swe-002-round-2-form

Checklist before submission -

I have read the description for each API and adhered to the response structure.
I have used a database for storing data.
I have connected the database to the application using an ORM.
I have the URL for GitLab / GitHub Repository, accessible to public.
I have deployed the code, and the URL is publicly accessible. (optional)