```c#
public class InventoryItem : MonoBehaviour, IBeginDragHandler, IDragHandler, IEndDragHandler
{
  public Image image;

  [HideInInspector] public Transform parentAfterDrag;
  public void OnBeginDrag(PointerEventData eventData)
  {
    image.raycastTarget = false;
    parentAfterDrag = transform.parent;
    transform.SetParent(transform.root);
  }

  public void OnDrag(PointerEventData eventData)
  {
    transform.position = Input.mousePosition;
  }

  public void OnEndDrag(PointerEventData eventData)
  {
    image.raycastTarget = true;
    transform.SetParent[parentAfterDrag);
  }

}
```

```c#
  public class InventorySlot : MonoBehaviour, IDropHandler
  {
    public void OnDrop(PointerEventData eventData)
    {
      if (transform.childCount == 0)
      {
        InventoryItem inventoryItem = eventData.pointerDrag.GetComponent<InventoryItem>();
        inventoryItem.parentAfterDrag = transform;
      }
    }
  }
```
