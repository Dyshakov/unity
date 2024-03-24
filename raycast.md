```c#
 RaycastHit hit;
 Ray ray;
 float rayDistance = 5;
 void Start()
 {
     
 }

 // Update is called once per frame
 void Update()
 {
     //создаем новый луч. начальная точка - позиция камеры. направление - вперед
     ray = new Ray(gameObject.transform.position, transform.forward);
     Debug.DrawRay(gameObject.transform.position, transform.forward * rayDistance, Color.red);
     if(Physics.Raycast(ray, out hit))
     {
         //если луч пересекается с каким то объектом, то его имя выводится в консоль
         Debug.Log(hit.collider.gameObject.name);
         
     }
 }
```
