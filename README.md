# GDScript Language

### Check type

```gdscript
if typeof(data.selected_card.one_time_effect) == TYPE_OBJECT:
	pass
```

### Iterate over array

```gdscript
# no index
for item in array:
	pass

# with index
for i in range(array.size()):
	var item = array[i]
```

### Iterate over dictionary

```gdscript
# with keys
for key in dict:
	var value = dict[key]

# or
for key in dict.keys():
	var value = dict[key]

# no keys, only values
for value in dict.values():
	pass
```

### Multiline string

```gdscript
var stats = """
Move: {move}
Energy: {energy}
Skills: {skills}
Equipment: {equipment}
"""
```
