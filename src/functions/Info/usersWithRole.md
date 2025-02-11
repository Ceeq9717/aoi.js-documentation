---
title: $usersWithRole 
description: $usersWithRole will return the users who have a specific role.
id: usersWithRole
---

`$usersWithRole` will return the users who have a specific role.

## Usage

```php
$usersWithRole[roleID;guildID?;option?;sep?]
```

## Parameters 


| Field     | Type    | Description                                        | Required |
|-----------|---------|----------------------------------------------------| :------: |
| roleID    | integer  | role ID                             | yes      |
| guildID?    | integer  | guild ID                             | no      |
| option?    | string  | how to return the users <br /> 1. **id** (default) <br /> 2. **mention**                             | no      |
| sep?    | string  | seperator to seperate multiple arguments                             | no      |


## Example

This will return the users of a specific role, make sure to replace roleID:

```javascript
bot.command({
  name: 'usersWithRole',
  code: `
  $usersWithRole[roleID;$guildID;id;, ]
  `
});
```
