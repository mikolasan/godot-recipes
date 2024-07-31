# Web export

### Serve files of HTML5 export

{% hint style="warning" %}
Outdated. Now you need to serve with special headers from the server
{% endhint %}

Python 3:

```bash
python -m http.server
```

## HTML5 on iOS

1. Export type: Regular. Because threads don't work in WASM (\[github issue about it]\([https://github.com/godotengine/godot/issues/86090](https://github.com/godotengine/godot/issues/86090)), \[many other tickets lead to this but I don't see a resolution]\([https://github.com/godotengine/godot/issues/26554](https://github.com/godotengine/godot/issues/26554)), or one \[can return]\([https://github.com/godotengine/godot/issues/26554](https://github.com/godotengine/godot/issues/26554)) \[asmjs back]\([https://github.com/godotengine/godot/pull/31383](https://github.com/godotengine/godot/pull/31383)) using \[this patch]\([https://patch-diff.githubusercontent.com/raw/godotengine/godot/pull/31383.patch](https://patch-diff.githubusercontent.com/raw/godotengine/godot/pull/31383.patch))
