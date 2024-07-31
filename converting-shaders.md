---
description: From GLSL to Godot shaders
---

# Converting shaders

{% embed url="https://docs.godotengine.org/en/3.5/tutorials/shaders/shader_reference/shading_language.html#built-in-functions" %}
Godot 3.5 documentation about shaders
{% endembed %}

### iResolution

`SCREEN_PIXEL_SIZE` is the inverse of `iResolution`

<pre><code><strong>iResolution.x == (1.0 / SCREEN_PIXEL_SIZE.x)
</strong></code></pre>

### UV

Usually on shader toy you will see UV from fragcoord

```
vaec uv = FRAGCOORD.xy * SCREEN_PIXEL_SIZE;
```

But in Godot if you want to make shader draw things in object coordinates, then just use

```
vec2 uv = UV;
```

### mat2

If you have an error message like

```
Invalid arguments for built-in function: mat2(float, float, float, float)
```

then replace the way 2D matrix is created. It must be 2 vectors of floats, but not 4 floats

```
mat2(a,b,c,d) => mat2(vec2(a,b), vec2(c,d))
```

### Helper functions

```
Unknown identifier in expression: SCREEN_PIXEL_SIZE
```

For example, `SCREEN_PIZEL_SIZE` only defined in main `fragment()`  function, pass it as argument to other functions.
