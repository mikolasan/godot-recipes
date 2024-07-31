# Observer

### Repository

[https://github.com/didier-v/GodotNotificationCenter](https://github.com/didier-v/GodotNotificationCenter)

### Code

The following thing lives in the global space and delivers messages from senders to observers.

```gdscript
extends Node

var notifications

func _ready():
	notifications = {};

func post_notification(notificationName,notificationData):
	if notifications.has(notificationName):
		var currentObservers=notifications[notificationName].observers
		for i in currentObservers:
			var anObserver =  currentObservers[i]
			if anObserver.object.has_method(anObserver.action):
				anObserver.object.call(anObserver.action,anObserver.object,notificationName,notificationData)

func add_observer(observer,notificationName,action):
	if not notifications.has(notificationName):
		notifications[notificationName]={
			"observers":{}
		}
	var currentObservers=notifications[notificationName].observers
	currentObservers[observer.get_instance_id()]={
		"object":observer,
		"action":action
	}

func remove_observer(observer, notificationName):
	if notifications.has(notificationName):
		var currentObservers=notifications[notificationName].observers
		if currentObservers.has(observer.get_instance_id()):
			currentObservers.erase(observer.get_instance_id())

```

### Usage

From the place where observer (or several of them) is accessible with `get_node` add it to `NotificationCenter`:

```gdscript
func _ready():
	NotificationCenter.add_observer($State, "state", "led_status")
```

Add action to the observer meaning you need function with a specific name and specific interface

```gdscript
func led_status(observer, notification_name, notification_data):
	# do your thing with `notification_data`
```

Now from any other place (node, scene) you can send data to the observers and trigger the action with:

```gdscript
NotificationCenter.post_notification("led_status", "scatter")
```
