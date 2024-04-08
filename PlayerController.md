# Разделение кода в unity на примере скрипта `PlayerController`

Разные функции игрока должны разделяться на разные скрипты. Так к примеру, функции, отвечающие за передвижение, и функции, отвечающие за анимацию, должны быть разделены на разные скрипты.

![image](https://github.com/Dyshakov/unity/assets/91851290/7d63625d-f2a4-402e-b743-2df7980c09dc)

`PlayerScript` должен содержать ссылки на остальные скрипты игрока
```c#
PlayerInputScript inputScript;
PlayerCollisionScript colissionScript;
PlayerMovementScript MovementScript;
```

`PlayerInputScript`
```c#
bool _leftPressed;
bool _rightPressed;
bool _forwardPressed;
bool _ backwardPressed;
```

`PlayerMovementScript`
```c#

```
