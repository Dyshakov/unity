# Движение камеры
```c#
public class MouseLook : MonoBehaviour
{
    public float mouseSens = 100f;
    public Transform playerBody;
    float xRotation = 0f;
    float yRotation = 0f;

    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        float mouseX = Input.GetAxis("Mouse X") * mouseSens * Time.deltaTime;
        float mouseY = Input.GetAxis("Mouse Y") * mouseSens * Time.deltaTime;

        xRotation -= mouseY;
        yRotation -= mouseX;

        transform.localRotation = Quaternion.Euler(xRotation, -yRotation, 0f);
        playerBody.Rotate(Vector3.up * mouseX);

    }
}
```
