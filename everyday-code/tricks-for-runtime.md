# Tricks for runtime

### Get window (viewport) size

```gdscript
var window_size = get_tree().get_root().size
```

### Close the app

```gdscript
get_tree().quit()
```

### Hide group of elements

```gdscript
get_tree().call_group_flags(SceneTree.GROUP_CALL_REALTIME, "StartupHide", "hide")
```

### Change label color (break current style)

```gdscript
label.add_color_override("font_color",
    Color("ffffff") if scale_value == (i+1) else Color("bdbdbd"))
```

### Update label size

```gdscript
hint.text = message
hint.rect_size.y = hint.get_line_height() * hint.get_line_count()
```

### Detect mouse click on Control

```gdscript
func on_gui_input(event):
    if event is InputEventMouseButton and event.pressed:
        pass
    if event is InputEventKey and event.scancode == KEY_SPACE:
        pass
```

### Load scene at runtime

```gdscript
# if the path is wrong or the scene can't be loaded
# the `preload` function will fail at compile time
var bingo_scene = preload("res://Scenes/Bingo.tscn")
var bingo = null

func _ready():
	bingo = bingo_scene.instance()
	bingo.position = Vector2(1021, 790)
	bingo.name = 'Bingo'
	add_child(bingo)
```

But in case that scene is optional, then use a `ResourceLoader`

```gdscript
var bingo_scene_path = "res://Scenes/Bingo.tscn"
var bingo_scene = null
var bingo = null

func _enter_tree():
	if ResourceLoader.exists(bingo_scene_path):
		bingo_scene = ResourceLoader.load(bingo_scene_path)

func _ready():
	if bingo_scene:
		bingo = bingo_scene.instance()
		bingo.name = 'Bingo'
		bingo.position = Vector2(1021, 790)
		add_child(bingo)
```

### Reassign resources in code

Load textures as resources. Drag and drop resources into the editor for the path

```gdscript
onready var training_texture: Texture = load("res://Assets/meter_training.png")
```

### Get local scene root



```gdscript
func get_local_scene_root(p_node : Node) -> Node:
    while(p_node and not p_node.filename):
        p_node = p_node.get_parent()

    return p_node as Node

```
