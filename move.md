# Движение игрока

создадим скрипт "PlayerController"
```c#
transform.Translate(0, 0, 1);
// или
transform.Translate(Vector3.forward);
```
данный скрипт будет изменять позицию объекта по оси z каждую единицу времени. Скорость обновления координат зависит от количества кадров в секунду.
Если мы хотим, чтобы обновление позиции объекта было привязано не к fps а к времени. Нужно умножить вектор на `Time.deltaTime`
```c#
transform.Translate(Vector3.forward * Time.deltaTime);
// чтобы изменить скорость передвижения объекта необходимо умножить на скорость
transform.Translate(Vector3.forward * Time.deltaTime * 20);
```
