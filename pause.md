# Создание паузы
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.SceneManagement;

public class PauseManager : MonoBehaviour
{
    public bool isPause;
    public GameObject pauseGameMenu;
    void Start()
    {
        isPause = false;
    }

    // Update is called once per frame
    void Update()
    {
        if(Input.GetKeyDown(KeyCode.Escape))
        {
            if (!isPause)
            {
                Pause();
            }
            else
            {
                ResumeGame();
            }
        }
    }

    void Pause()
    {
        pauseGameMenu.SetActive(true);
        isPause = true;
        Time.timeScale = 0.0f; ;
    }

    void ResumeGame()
    {
        isPause = false;
        pauseGameMenu.SetActive(false);
        Time.timeScale = 1.0f;
    }


}

```
