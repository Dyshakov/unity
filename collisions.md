Чтобы определять когда происходит столкновение объектов, для начала нужно добавить компонент collider и rigidbody объекту и поставить галочку isTrigger.
Дальше в скрипте
```c#
private void OnTriggerEnter(Collider other)
{
    Destroy(gameObject);
    Destroy(other.gameObject);
}

```
  
