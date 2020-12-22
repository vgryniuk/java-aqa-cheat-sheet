Основи ООп
Класи
Абстрактні класи
Інтерфейси
static

override / overload

Collections

Compatator vs comparable

iterator

generic

exceptions

#### Серіалізація
Серіалізація - збереження стану об'єкту, наприклад для передачі по мережі чи збереження з можливістю відтворити пізніше. При серіалізації зберігаєтся повний граф об'єкта, включно зі всіма об'єктами, на які він посилається. Для того щоб бути серіалізованим, об'єкт повинен імплементувати інтерфейс `Serializable`. Для коректної серіалізації, всі об'єктина які посилається об'єкт також повинні бути `Serializable`. 

Для того, щоб серіалізувати об'єкт, потрібно створити потік `FileOutputStream
`,  з'єднати його з потоком `ObjectOutputStream` та викликати з нього метод `writeObject(object)`.

Якщо змінну не треба серіалізувти (наприклад щоб не зберігати пароль), її необхідно помітити як `transient
`. При десеріалізації `transient` змінна отримає значення `null`.
```
class <CLASS_NAME> implements Serializable {transient String <VAR_NAME>}
```
Статичні змінні не серіалізуються.


Patterns
Singletone
Factory
Page Object
Builder



java 8
default functions
default interfaces
stream API
Optionals