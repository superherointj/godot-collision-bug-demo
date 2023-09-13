# Godot Collision Issue Demo

When two `CharacterBody2D` collide using `move_and_slide`, both get stuck.

## Screenshots from demo

![Screenshot - Picture Start](/screenshots/picture-start.png "Screenshot - Picture Start")

![Screenshot - Picture Locked](/screenshots/picture-locked.png "Screenshot - Picture Locked")

## Code used

Box A:

```
extends CharacterBody2D

var speed = 40.0
var vec = Vector2.ZERO

func _input(_event):
	vec = Input.get_vector("ui_left", "ui_right", "ui_up", "ui_down")

func _physics_process(delta):
	velocity.x = vec.x * speed
	velocity.y = vec.y * speed
	move_and_slide()
```


Box B:
```
extends CharacterBody2D

func _physics_process(delta):
	move_and_slide()
```

## Resolution

[Codimon](https://discord.com/channels/212250894228652034/735042396277964870/1151484226651291728) hinted that CharacterBody Motion Mode was set to Grounded (while it should have been `floating``). Issue is now solved.