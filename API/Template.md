# Template
This is an API template. It is not a real API in the game engine.

##### Inherits from: `SomeClass`

## Fields

| Field         | Type          | Description  |
| --------------|:-------------:| ------------ |
| className | `String` | The className of the object |
| Name | `String` | The name of the object |

## Instantiation
Every object has a constructor. The constructor is called via the `Class` object

##### Example:
```lua
local Class = require(game.ReplicatedStorage.Classes.Class);

local Template = Class.new('Template', param1, param2, ...);
```

#### Parameters

| Parameter | Type | Description  |
| --------------|:-------------:| ------------ |
| className | `String` | The className of the object |
| Name `optional` | `String` | The name of the object |

##### Here's a template for what this might look like:

```lua
local Template = Class.new('Template', {className}, {optional name});
```

##### Examples for what it might actually look like:

```lua
local Template = Class.new('Template', 'SomeClassName');

local Template = Class.new('Template', 'SomeClassName', 'SomeName');
```

## Events

### Event name
What is it for? When does it fire?

#### Returns

| Type | Description  |
| ------------- | ------------ |
| `Integer` | Some Integer |
| `String` | Some String |

## Methods

### Method name
What does it do?

#### Parameters

| Parameter | Type | Description |
| --------------|:-------------:| ------------ |
| Name | `String` | The name |
| LastName `optional` | `String` | The last name |

#### Returns

| Type | Description  |
| ------------- | ------------ |
| `Integer` | Some Integer |
| `String` | Some String |
