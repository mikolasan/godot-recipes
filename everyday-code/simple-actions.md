# Simple actions

### Random number

```gdscript
var rng = RandomNumberGenerator.new()
rng.randomize()
var r = rng.randf_range(0.0, 1.0)
var k = rng.randi_range(1, 4) / 5.0
```

### Float to string (display float in label)

```gdscript
var number: float = 42.0
$Label.text = number % "%.02f"
$Label.text = str(number).pad_decimals(2)
$Label.text = String.format("%.02f", number)
```

### Concatenate strings from an array:

```gdscript
var array = ["a", "b", "c"]
var result = PoolStringArray(array).join(", ")
```

### Find element in array (functional style)

```gdscript
func _find(arr: Array, f: FuncRef):
	for v in arr:
		if f.call_func(v):
			return true
	return false
	
func _lambda_player_in_room(a):
	return a.player_name != null

var player_in_room = _find(rooms, funcref(self, "_lambda_player_in_room"))
```
