# Проверка находится ли объект в зоне видимости другого объета
```c#
public float attackRange = 5f;
public LayerMask whatIsPlayer;
bool playerInAttackRange;

void Update()
{
  // Если игрок находится в сфере радиусом 5, то переменная принимает значение true 
  playerInAttackRange = Physics.CheckSphere(transform.position, attackRange, whatIsPlayer);
}
```
