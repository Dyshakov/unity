#Реализация отдачи с возвращением прицела в центр

```c#
    private Vector3 currentRotation;
    private Vector3 targetRotation;

    [SerializeField] private float recoilX;
    [SerializeField] private float recoilY;
    [SerializeField] private float recoilZ;

    [SerializeField] private float snappiness;
    [SerializeField] private float returnSpeed;

   void Update()
    {
        float mouseX = Input.GetAxis("Mouse X") * mouseSens * Time.deltaTime;
        float mouseY = Input.GetAxis("Mouse Y") * mouseSens * Time.deltaTime;

        xRotation -= mouseY;
        yRotation -= mouseX;

        targetRotation = Vector3.Lerp(targetRotation, Vector3.zero, returnSpeed * Time.deltaTime);
        currentRotation = Vector3.Slerp(currentRotation, targetRotation, snappiness * Time.fixedDeltaTime);

        // Рассчитываем конечные углы с учетом отдачи
        float finalXRotation = xRotation + currentRotation.x;
        float finalYRotation = yRotation + currentRotation.y;


        transform.position = character.transform.position + offset;
        transform.localRotation = Quaternion.Euler(finalXRotation, -finalYRotation, 0);
    }

    public void Recoil()
    {
        targetRotation += new Vector3(recoilX, Random.Range(-recoilY, recoilY), Random.Range(-recoilZ, recoilZ));
    }
```

функцию `Recoil()` нужно вызывать из скрипта оружия при выстреле
