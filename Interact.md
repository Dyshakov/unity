# Взаимодействие игрока с объектами
Данная механика поможет реализовать взаимодействие игрока с разными объектами. Например: открытие дверей, подбор предметов, сесть в машину, открыть ящик.

Для начала создадим скрипт `Interactive.cs` и назначим его камере.
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

// Интерфейс, который позволяет взаимодействовать с объектами которые имеют метод Interact
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
                if (Input.GetKeyDown(KeyCode.E))
                {
                    interactObj.Interact();
                } 
            }
        }
    }
}
```

## Теперь создадим объект с которым хотим взаимодействовать

Допустим это будет куб со скриптом `test.cs` 
![image](https://github.com/user-attachments/assets/2b524b97-95ce-435a-b3eb-f26ff21b947f)
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class test : MonoBehaviour, IInteractable
{
    public void Interact()
    {
        Debug.Log("interact");
    }
}
```
