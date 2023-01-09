# SXP_personality Extension with gltf-transform to use it

# Description

This extension allows users to assign personality attributes to a glTF node appended to a file. The attributes include `agent`, `spellName`, `host`, `personality` and `defaultMessage`. Currently this extension is only compatible with MagickML but will be adjusted to be interoperable with others as more options are available.

Usage: 
1) `npm install`
2) `node script.js someobject.glb tubby complexQuery https://localhost:8001 'nya nya!'`

# Extension Name

SXP_personality

# Extension Type

Node extension

# Properties

- `agent` (string) - The name of the agent assigned to the node.
- `spellName` (string) - The name of the spell assigned to the node.
- `host` (string) - The host URL for the node.
- `personality` (string) - Typically a long prompt describing the character and their backstory.
- `defaultMessage` (string) - The default message for the node.

# JSON Schema

The following JSON schema defines the extension properties:
```json
{
  "definitions": {
    "SXP_personality": {
      "type": "object",
      "properties": {
        "agent": { "type": "string" },
        "spellName": { "type": "string" },
        "host": { "type": "string" },
        "personality": { "type": "string" },
        "defaultMessage": { "type": "string" }
      }
    }
  },
  "type": "object",
  "properties": {
    "extensions": {
      "type": "object",
      "properties": {
        "SXP_personality": { "$ref": "#/definitions/SXP_personality" }
      }
    }
  }
}
```
# Example

Here is an example of how the extension can be used in a glTF file:
```json
{
  "nodes": [
    {
      "name": "TubbyPet",
      "extensions": {
        "SXP_personality": {
          "agent": "tubby",
          "spellName": "complexQuery",
          "host": "https://localhost:8001",
          "personality": "#agent is cheery.",
          "defaultMessage": "nya nya!"
        }
      }
    }
  ],
  "extensionsUsed": [ "SXP_personality" ]
}
```