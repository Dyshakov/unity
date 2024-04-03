# Открытие инвентаря
скрипт `InventoryManager` empty объекта `InventoryManager`

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class InventoryManager : MonoBehaviour
{
    GameObject MainInventoryGroup;    // Переменная для хранения панели инвентаря
    void Start()
    {
        MainInventoryGroup = GameObject.Find("MainInventoryGroup");  // Присваеваем переменной объект панели
        MainInventoryGroup.SetActive(false);                         // Скрываем инвентарь в начале игры
    }

    // Update is called once per frame
    void Update()
    {
        // При нажатии на `I` открываем инвентарь
        if(Input.GetKeyDown(KeyCode.I))
        {
            OpenInventory();
        }
    }

    // Открытие инвентаря
    void OpenInventory()
    {
        MainInventoryGroup.SetActive(!MainInventoryGroup.active);
    }
}

```
