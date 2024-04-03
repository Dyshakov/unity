скрипт `InventoryItem.cs`
```c#
public class InventoryItem: MonoBehaviour
{
  [HideInInspector]public Item item;

  [Header("UI")]
  public Image image;

  private void Start()
  {
    InitialiseItem(item);
  }

  public void InitialiseItem(Item newITem)
  {
    item = newItem
    image.sprite = newItem.image
  }
}
```

скрипт `InventoryManager.cs`

```c#
public class InventoryManager: MonoBehaviour
{
  public InventorySlot[] inventorySlots
  public void AddItem(Item item)
  {
    
  }

  void SpawnItem(Item item, InventorySlot slot)
  {

  }
}
```
