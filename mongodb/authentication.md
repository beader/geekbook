# Authentication

## Enable Authentication

With access control enabled, ensure you have a user with userAdmin or userAdminAnyDatabase role in the admin database.

### Procedures

1. Start MongoDB without access control.
2. Connect to the instance.
3. Create the user administrator.
```js
use admin
db.createUser(
  {
    user: "myUserAdmin",
    pwd: "abc123",
    roles: [ { role: "userAdminAnyDatabase", db: "admin" } ]
  }
)
```
4. Re-start the MongoDB instance with access control.
```js
mongod --auth --port xxx --dbpath xxx
```
5. Authenticate as the user administrator.
```js
mongo --port 27017 -u "myUserAdmin" -p "abc123" --authenticationDatabase "admin"
```
or in the mongo shell connected without authentication, switch to the authentication database, and use db.auth() method to authenticate:
```js
use admin
db.auth("myUserAdmin", "abc123" )
```
6. Create additional users as needed for your deployment.

## User Management Methods

- `db.auth()`	Authenticates a user to a database.
- `db.createUser()`	Creates a new user.
- `db.updateUser()`	Updates user data.
- `db.changeUserPassword()`	Changes an existing user’s password.
- `db.removeUser()`	Deprecated. Removes a user from a database.
- `db.dropAllUsers()`	Deletes all users associated with a database.
- `db.dropUser()`	Removes a single user.
- `db.grantRolesToUser()`	Grants a role and its privileges to a user.
- `db.revokeRolesFromUser()`	Removes a role from a user.
- `db.getUser()`	Returns information about the specified user.
- `db.getUsers()`	Returns information about all users associated with a database.

## Role Management Methods

- `db.createRole()`	Creates a role and specifies its privileges.
- `db.updateRole()`	Updates a user-defined role.
- `db.dropRole()`	Deletes a user-defined role.
- `db.dropAllRoles()`	Deletes all user-defined roles associated with a database.
- `db.grantPrivilegesToRole()`	Assigns privileges to a user-defined role.
- `db.revokePrivilegesFromRole()`	Removes the specified privileges from a user-defined role.
- `db.grantRolesToRole()`	Specifies roles from which a user-defined role inherits privileges.
- `db.revokeRolesFromRole()`	Removes inherited roles from a role.
- `db.getRole()`	Returns information for the specified role.
- `db.getRoles()`	Returns information for all the user-defined roles in a database.

## Built-In Roles

A role grants privileges to perform sets of actions on defined resources. A given role applies to the database on which it is defined and can grant access down to a collection level of granularity.

### Database User Roles

- `read` 
- `readWrite`

### Database Administration Roles

- `dbAdmin`
- `dbOwner` The database owner can perform any administrative action on the database.
- `userAdmin` Provides the ability to create and modify roles and users on the current database.

### Cluster Administration Roles

- `clusterAdmin`
- `clusterManager`
- `clusterMonitor`
- `hostManager`

### Backup and Restoration Roles

The admin database includes the following roles for backing up and restoring data:

- `backup`
- `restore`

### All-Database Roles

- `readAnyDatabase`
- `readWriteAnyDatabase`
- `userAdminAnyDatabase`

## References

- [mongoDB 3.0 安全权限访问控制](http://ibruce.info/2015/03/03/mongodb3-auth/)
- [User Management Methods](https://docs.mongodb.com/manual/reference/method/js-user-management/)
- [Role Management Methods](https://docs.mongodb.com/manual/reference/method/js-role-management/)
- [Built-In Roles](https://docs.mongodb.com/manual/reference/built-in-roles/#userAdminAnyDatabase)
- [Enable Authentication](https://docs.mongodb.com/manual/tutorial/enable-authentication/)
