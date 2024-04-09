# Создание контекстного меню для быcтрого теста

```c#
[ContextMenu("UseJump")]
public void Jump()
{
    if (isOnGround)
    {

        velocity = Mathf.Sqrt(jumpHeight * -2f * gravity);
    }
}
```
![image](https://github.com/Dyshakov/unity/assets/91851290/1dc57414-d52f-40c1-a3ad-0122c40a76b4)
