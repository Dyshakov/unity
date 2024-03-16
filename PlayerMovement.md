# Движение персонажа
Для начала персонажу нужно добавить компонент `CharacterController`

```c#
public class PlayerMove : MonoBehaviour
{
    // Определяем переменную, которая будет хранить компонент управления персонажем
    private CharacterController controller;
    public float speed = 12f;
    void Start()
    {
    // Записываем компонент в переменную при старте игры
        controller = GetComponent<CharacterController>();
    }

    // Update is called once per frame
    void Update()
    {
        float x = Input.GetAxis("Horizontal");
        float z = Input.GetAxis("Vertical");
        Vector3 move = transform.right * x + transform.forward * z;

        controller.Move(move * speed * Time.deltaTime);


    }
}

```
