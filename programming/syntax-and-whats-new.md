# Syntax and What's new
---
## Java 5
### Variable Arguments (Varargs)
Метод, що може використовувати змінну кількість аргументів одного типу.
```
static void m(int... a) {
    System.out.println("Number of arguments: " + a.length);
    for (int i : a) {
        System.out.println(i + " ");
        }
}
```
---

## Java 8
### Ternary operator
```
variable = (condition) ? expressionTrue : expressionFalse;
```
---

## Java 9
### Immutable List Static Factory Methods
**` List.of()`** - статичний фабричний метод для зручного створення незмінних списків, з наступними ключовими особливостями:

* елементи не можна додавати, видаляти чи змінювати.
* елементи списку не можуть бути `null`. Спроба додати до списку `null` викличе `NullPointerException`.
* список може бути серіалізований, якщо всі елементи серіалізуються.

Більш широка реалізіція створення списку `Arrays.asList();`.
...
