---
title: $allChannelsCount 
description: $allChannelsCount will return the amount of all cached channels of a given type.
id: allChannelsCount
---

`$allChannelsCount` will return the amount of all cached channels of a given type.

## Usage

```php
$allChannelsCount[type?]
```

## Parameters 


| Field | Type   | Description                 | Required |
| ----- | ------ | --------------------------- | -------- |
| type? | string | type you want the amount of | no       |

<details open>
  <summary><h3> Channel Types </h3></summary>

| Channel Type         |                    |
| -------------------- | ------------------ |
| Text Channel         | Text               |
| Voice Channel        | Voice              |
| Category             | Category           |
| Stage Channel        | Stage              |
| Private Thread       | PrivateThread      |
| Public Thread        | PublicThread       |
| Forum                | Forum              |
| Announcement Thread  | AnnouncementThread |
| Announcement Channel | Announcement       |
| Home                 | GuildDirectory     |
| NSFW Channel         | NSFW               |
| Direct Message       | DM                 |
| All Channel Types    | all                |

#### Note: all channel types are **case-sensitive**.

</details>

## Example

This will return the amount of Voice Channels in your guild:

```javascript
bot.command({
  name: 'allChannelsCount',
  code: `
  $allChannelsCount[Voice]
  `
});
```
