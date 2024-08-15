# Вызов скрипта откуда угодно
Созаем canvas и создаем ему новый скрипт `InteractionText.cs`<br>
![image](https://github.com/user-attachments/assets/0d3bf8cb-f9ce-4ab3-98df-36de8fe081f2)
![image](https://github.com/user-attachments/assets/0058c77c-4ccc-4d00-9cfe-9d4b65423c96)



Синглтон позволяет создать класс к которому можно обращаться откуда угодно
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using TMPro;

public class InteractionText : MonoBehaviour
{
    // Создаем статическую переменную которая будет хранить экземпляр данного класса
    public static InteractionText instance;

    void Awake()
    {
        instance = this;
    }

    [SerializeField] TMP_Text interactionText;

    public void EnableInteractionText(string text)
    {
        interactionText.text = text + " (F)";
        interactionText.gameObject.SetActive(true);
    }

    public void DisableInteractionText()
    {
        interactionText.gameObject.SetActive(false);
    }
}
```

Вызов функции из скрипта камеры `Interactive.cs`<br>
![image](https://github.com/user-attachments/assets/5cda1935-5b35-4243-8dd3-e4cd8b6265b8)


```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

interface IInteractable
{
    public void Interact(); 
}

public class Interactive : MonoBehaviour
{
    [SerializeField] float distance;
    [SerializeField] LayerMask playerLayerMask; 

    void Update()
    {
        Ray r = new Ray(transform.position, transform.forward);
        
        if (Physics.Raycast(r, out RaycastHit hitInfo, distance, ~playerLayerMask))
        {
            if (hitInfo.collider.TryGetComponent(out IInteractable interactObj))
            {
                InteractionText.instance.EnableInteractionText("loot item");
                if (Input.GetKeyDown(KeyCode.E))
                {
                    interactObj.Interact();
                }   
            }
            else
            {
                InteractionText.instance.DisableInteractionText();
            }
        }
        else
        {
            InteractionText.instance.DisableInteractionText();
        }
    }
}
```
