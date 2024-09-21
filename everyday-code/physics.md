# Physics

This is how you stop the rigid body

```gdscript
linear_velocity = Vector3.ZERO
```

In case you want to use `look_at` but also apply lerp to it (the example is limited to work only in the XZ plane)

```gdscript
func angle_to_another_position(from: Vector3, to: Vector3) -> float:
	var forward = to - from
	var up = Vector3.UP
	var v_z = forward.normalized()
	var v_x = up.cross(v_z)
	v_x = v_x.normalized()
	var v_y = v_z.cross(v_x)
	var b: Basis = Basis(v_x, v_y, v_z)
	var rotate_y = b.get_euler().y
	return rotate_y
```
