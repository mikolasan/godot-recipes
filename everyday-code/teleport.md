---
description: Get access to nodes anywhere in the project
---

# Teleport

First, we define a global object, Teleport that will allow us get reference to other nodes registered with it.

**Teleport.gd**

```gdscript
extends Node

var nodes = {}

func get(node_name: String) -> Node:
	var config = nodes[node_name]
	return config.root.get_node(config.path)

func add(root: Node, exports: Dictionary) -> void:
	for node_name in exports:
		if nodes.has(node_name):
			push_error("Teleport already has node with name '" + node_name + "', skipping...")
			continue
		var node_path = exports[node_name]
		nodes[node_name] = {
			root = root,
			path = node_path,
		}
```

Then we create a dynamic way to have exports in a node. This is a SmartNode2D class&#x20;

**SmartNode2D.gd**

```gdscript
tool
extends Node2D

var exports = {}

func _get(property):
	if exports.has(property):
		return exports[property]

func _set(property, value):
	if exports.has(property):
		exports[property] = value
		return true

func _get_property_list():
	var list = [{
		name = "Exports",
		type = TYPE_NIL,
		usage = PROPERTY_USAGE_CATEGORY | PROPERTY_USAGE_SCRIPT_VARIABLE
	}]
	for var_name in exports.keys():
		list.append({
			"hint": PROPERTY_HINT_NONE,
			"usage": PROPERTY_USAGE_DEFAULT,
			"name": var_name,
			"type": TYPE_NODE_PATH
		})
	return list

func _ready():
	Teleport.add(self, exports)
```

### Example

Declare, set nodes in UI

```gdscript
tool
extends "res://Src/SmartNode2D.gd"

func _init():
    exports = {
        top_screen = "", # "TopScreen",
        progressives = "", # "TopScreen/Progressives",
    }
```

Then use them

```gdscript
onready var top_screen = Teleport.get("top_screen")
onready var progressives = Teleport.get("progressives")
```
