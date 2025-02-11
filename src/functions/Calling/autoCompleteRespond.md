---
title: $autoCompleteRespond 
description: $autoCompleteRespond is used to auto-complete slash options.
id: autoCompleteRespond
---

`$autoCompleteRespond` is used to auto-complete slash options.

## Usage

```php
$autoCompleteRespond[json]
```
```php
$autoCompleteRespond[OptionName;OptionReply;...]
```

## Parameters 

| Field     | Type    | Description                                        | Required |
|-----------|---------|----------------------------------------------------| :------: |
| OptionName     | string  | name of the auto-complete option                                          | yes      |
| OptionReply    | string  | the reply that will be sent if the auto-complete option was selected      | yes      |


## Examples

Create the slash-commands: (please note that you require the `bot.onInteractionCreate()` callback in your main file)
```javascript
bot.command({
  name: 'createSlashCommand',
  code: `
  $createApplicationCommand[global;example;Awesome example interaction command with auto-complete!;true;slash;[{
  "name": "option", // slash command name
  "description": "test", // slash command description
  "required": false, // true or false, depending on if its required or not
  "type": 3, // string type
  "autocomplete": true // enable auto complete for the slash command
}]
  `
});
```
Interaction Command:
```javascript
bot.command({
  name: "test",
  prototype: "slash",
  code: `
  $if[$isAutocomplete==true]
  $autoCompleteRespond[First option;You selected the first option, therefore I'm responding with this!;Second option;You selected the first second, therefore I'm responding with this!]
  $else
  $interactionReply[$slashOption[option];;;;everyone]
  $endif
  `
});
```

### Advanced Example

Create the slash-commands: (please note that you require the `bot.onInteractionCreate()` callback in your main file)

```javascript
bot.command({
  name: 'createSlashCommand',
  code: `
  $createApplicationCommand[global;example;Awesome example interaction command with auto-complete!;true;slash;[{
  "name": "option", // slash command name
  "description": "test", // slash command description
  "required": false, // true or false, depending on if its required or not
  "type": 3, // string type
  "autocomplete": true // enable auto complete for the slash command
}, {
  "name": "anotheroption", // slash command name
  "description": "test", // slash command description
  "required": false, // true or false, depending on if its required or not
  "type": 3, // string type
}]
  `
});
```

Interaction Command:

```javascript
bot.command({
  name: "test",
  prototype: "slash",
  $if: "old",
  code: `
  $if[$isAutocomplete==true]
  $autoCompleteRespond[[{ 
    "name" : "First Option",
    "value" : "You selected the first option, therefore I\'m responding with this!"
  }, {
    "name" : "Second Option",
    "value" : "You selected the second option, therefore I\'m responding with this!"
  }]]
  $else
  $interactionReply[$slashOption[option] - autocomplete #SEMI# $slashOption[anotheroption] - no autocomplete;;;;everyone]
  $endif
  `
});
```
