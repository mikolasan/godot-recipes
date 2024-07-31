---
description: Shuffle algorithm
---

# Fisher-Yates algorithm

```gdscript
var rng = RandomNumberGenerator.new()

func _ready():
	rng.randomize()

func shuffle(array: Array):
	var length = array.size()
	while length > 0:
		length = length - 1
		var i = rng.randi_range(0, length)
		var temp = array[i]
		array[i] = array[length]
		array[length] = temp
	return array
```
