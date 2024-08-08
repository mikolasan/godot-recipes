# Runtime loading scenes

Create a level manager and add it to Autoloads

```gdscript
extends Node

var nodes = {}

func get_node_by_name(nodeName):
	if nodes.has(nodeName):
		return nodes[nodeName]

func add_shortcut(node, nodeName):
	nodes[nodeName] = node

func remove_shortcut(nodeName):
	nodes.erase(nodeName)

```

Then use it like this:

```gdscript
extends Node2D

# https://docs.godotengine.org/en/stable/classes/class_packedscene.html#description
var main_scene = load("res://Src/Scenes/Main.tscn").instance()
var bonus_scene = load("res://Src/Scenes/Bonus.tscn").instance()

func _ready():
    print("ready")
    LevelManager.add_shortcut($MainScene, "main") # "/root/Game/MainScene"
    LevelManager.add_shortcut($BonusScene, "bonus") # "/root/Game/BonusScene"
    LevelManager.add_shortcut($Help, "help")

func add_runtime_nodes():
    print("add_runtime_nodes")
    add_child_below_node($Background, main_scene, true)
    main_scene.set_name("MainScene")
    add_child_below_node(main_scene, bonus_scene, true)
    bonus_scene.set_name("BonusScene")
    bonus_scene.hide()

```
