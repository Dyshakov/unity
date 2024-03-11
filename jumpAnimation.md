# Воспроизведение анимации при прыжке
```c#
private Animator playerAnimator;

void Start()
{
  playerAnimator = GetComponent<Animator>();
}

void Update()
{
  if (Input.GetKeyDown(KeyCode.Space) && isOnGround)
  {
    playerAnimator.SetTrigger("Jump_trig);
  }
}
```
