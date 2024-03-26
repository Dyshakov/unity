# прыжок с помощью CharacterController
для начала определим необходимые переменные
```c#
private CharacterController controller;
public float gravity = -9.99f;
public float jumpHeight = 3f;
public LayerMask whatIsGround;
public float velocity;
public bool isOnGround;

 void Start()
 {
     controller = GetComponent<CharacterController>();
 }
```

```c#
// Проверка находится ли игрок на земле
isOnGround = Physics.Raycast(transform.position, -transform.up, 3f, whatIsGround);

if(Input.GetKeyDown(KeyCode.Space) && isOnGround)
{
    velocity = Mathf.Sqrt(jumpHeight * -2f * gravity);
}
else if (isOnGround) 
{
    velocity = 0;
}

if (!isOnGround)
{
    velocity += gravity * Time.deltaTime;
}


controller.Move(Vector3.up * velocity * Time.deltaTime);
```
