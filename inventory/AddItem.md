# Добавление предмета в инвентарь
Скрипт `InventoryManager`
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class InventoryManager : MonoBehaviour
{
    public inventorySlot[] inventorySlots;
    public GameObject inventoryItemPrefab;

    public void AddItem(Item item)
    {
        // Ищем пустой слот
        for (int i = 0; i < inventorySlots.Length; i++)
        {
            inventorySlot slot = inventorySlots[i];
            InventoryItem itemInSlot = slot.GetComponentInChildren<InventoryItem>();
            if (itemInSlot == null)
            {
                SpawnNewItem(item, slot);
                return;
            }
        }
    }

    public void SpawnNewItem(Item item, inventorySlot slot)
    {
        GameObject newItemGo = Instantiate(inventoryItemPrefab, slot.transform);
        InventoryItem inventoryItem = newItemGo.GetComponent<InventoryItem>();
        inventoryItem.InitialiseItem(item);
    }
}

```
![image](https://github.com/Dyshakov/unity/assets/91851290/7441a886-d569-40e5-aa21-5046c4de19d0)

Скрипт `InventoryItem`
```c#
using System.Collections;
using System.Collections.Generic;
using Unity.VisualScripting;
using UnityEngine;
using UnityEngine.EventSystems;
using UnityEngine.UI;

public class InventoryItem : MonoBehaviour, IBeginDragHandler, IEndDragHandler, IDragHandler
{
    [Header("UI")]
    public Image image;

    [HideInInspector] public Item item;

    public void InitialiseItem(Item newItem)
    {
        item = newItem;
        image.sprite = newItem.image;
    }
}
```

![image](https://github.com/Dyshakov/unity/assets/91851290/9cdff188-ce16-466d-a9a4-974d303f4ef3)


