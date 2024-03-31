Для начало необходимо создать пустой объект `camTarget`, который будет целью для камеры. Затем нужно создать для него скрипт `camTargetController`.
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class canTargetController : MonoBehaviour
{
    GameObject player;
    public float xRotation = 0;
    public float yRotation = 0;
    public Vector3 offset;
    void Start()
    {
        player = GameObject.Find("Player");
    }

    // Update is called once per frame
    void Update()
    {
        float mouseX = Input.GetAxis("Mouse X") * 200 * Time.deltaTime;
        float mouseY = Input.GetAxis("Mouse Y") * 200 * Time.deltaTime;


        xRotation -= mouseY;

        yRotation -= mouseX;
        transform.position = player.transform.position + offset;
        transform.localRotation = Quaternion.Euler(xRotation, -yRotation, 0);
    }
}

```
Теперь перейдем к скрипту самой камеры
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class camera : MonoBehaviour
{
    public GameObject character;
    public GameObject characterSpin;
    public Vector3 offset;
    public float mouseSens = 200f;
    
    Ray ray;
    public float xRotation = 0;
    public float yRotation = 0;
    public RaycastHit hit;
    public GameObject camTarget;
    public bool isFirstView;
    void Start()
    {
        isFirstView = true;
    }

    // Update is called once per frame
    void Update()
    {
        ray = new Ray(transform.position, transform.forward);
        float mouseX = Input.GetAxis("Mouse X") * mouseSens * Time.deltaTime;
        float mouseY = Input.GetAxis("Mouse Y") * mouseSens * Time.deltaTime;

        xRotation -= mouseY;
        //xRotation = Mathf.Clamp(xRotation, -360, 360);

        yRotation -= mouseX;
        //yRotation = Mathf.Clamp(yRotation, -360, 360);

        
        if (Physics.Raycast(ray, out hit))
        {
            Debug.DrawRay(transform.position, hit.point);
        }

        if (isFirstView)
        {
            transform.position = character.transform.position + offset;
            transform.localRotation = Quaternion.Euler(xRotation, -yRotation, 0);

        }
        else
        {
            //transform.position = Vector3.Lerp(transform.position, camTarget.transform.position, .02f);
            transform.rotation = Quaternion.Lerp(transform.rotation, camTarget.transform.rotation, .01f);
            //transform.localRotation = Quaternion.Euler(-mouseY, mouseX, 0);
        }


        character.transform.rotation = Quaternion.Euler(0, transform.eulerAngles.y, 0);

       
        characterSpin.transform.rotation = Quaternion.Euler(transform.eulerAngles.x, transform.eulerAngles.y, 0);

        if (Input.GetKeyDown(KeyCode.V))
        {
            PersonView();
        }
    }


    void PersonView()
    {
        if(isFirstView)
        {
            ChangeLayer(character.transform, "Default");
            isFirstView = false;
            transform.SetParent(camTarget.transform, true);
            transform.localPosition = new Vector3(0, 2, -6);
        }
        else
        {
            ChangeLayer(character.transform, "whatIsPlayer");
            isFirstView = true;
            transform.SetParent(null, true);
        }
    }

    void ChangeLayer(Transform trans, string layerMaskName)
    {
        trans.gameObject.layer = LayerMask.NameToLayer(layerMaskName);
        foreach (Transform child in trans)
        {
            ChangeLayer(child, layerMaskName);
        }
    }
}

```
