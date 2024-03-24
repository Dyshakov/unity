# Удаление всех вхождений заданного элемента в массив

Дан массив `int[] nums = {1, 2, 4, 2, 6, 2, 4};` необходимо удалить все двойки из него

```c#
int[] nums = {1, 2, 4, 2, 6, 2, 4};
        
        int count = 0;
        int val = 2;
        for(int i = 0; i < nums.Length; i++)
        {
            if(nums[i] != val)
            {
                nums[count] = nums[i];
                count++;
            }
        }
        
        Array.Resize(ref nums, count);
```
