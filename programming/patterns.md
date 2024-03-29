# Patterns
---
### Strategy
![Strategy diagram](/images/strategy.png "Strategy diagram")

**Патерн стратегія** поведінковий патерн проектування, який визначає сімейство схожих алгоритмів і інкапсулює кожен з них у власному класі. Алгоритми можна заміняти один на інший прямо під час виконання програми. Патерн відділяє алгоритми від клієнтського коду, що їх використовує. Або по іншому: поведінка інкапсулюється в окремому наборі класів, який легко розширюється і змінюється навіть під час виконання. 

**Приклад:** програма навігатора, яка рахує маршрут окремо для авто, велосипеда та пішохода.

---
### Observer
**Патерн Спостерігач** - визначає відношення 'один-до-багатьох' між об'єктами таким чином, що при зміні стану обного об'єкта (subject) відбувається автоматичне сповіщення та оновлення усіх залежних об'єктів (observer). При чому суб'єкт нічого не знає про спостерігачів.

Патерн Спостерігач пропонує зберігати всередині об’єкта видавця (subject) список посилань на об’єкти підписників (observer). Причому видавець не повинен вести список підписки самостійно. Він повинен надати методи, за допомогою яких підписники могли б додавати або прибирати себе зі списку.

#### Listener
**Патерн Listener** - виконує практично туж саму функцію, що й Observer, за винятком того, що суб'єкт знає список спостерігачів, і повідомляє їх про зміни стану.

**Приклад:** Як Listener так і Observer використовують у т.зв *event-driven programming*, коли події, які генерує користувач змінюють стан програми, наприклад при імплементації графічних інтерфейсів.

**Простіший приклад:** Youtube присилає користувачу повідомлення, що з'явилось нове відео на каналі на який користувач підписаний.

---
### Decorator
**Патерн Декоратор** - шаблон проєктування, призначений для динамічного підключення додаткових можливостей до об'єкта, загортаючи їх у корисні «обгортки». В Java декоратор використовується щоб розширити поведінку класу без зміни самого класу, чи створення підкласів.

**Недоліки** - додає до архітектури багато дрібних класів, у яких важко розібратися по мірі зростання кількості.

**Приклад:** Розрахунок ціни при купівлі піци з набором додаткових наповнювачів.

---
### Factory Method
![Factory method diagram](/images/factory.png "Factory method diagram")

**Фабричний метод** - визначає інтерфейс сворення об'єкта, але дозволяє підкласам обрати створюваний екземпляр. Основне завдання: переміщення створення екземплярів у підкласи. Суть патерна в тому, що клас який викликає створення об'єкта не знає деталей реалізації самого створення, а часто й не знає наперед який саме тип об'єкта потрібно створити.

Патерн Фабричний метод дозволяє відмовитись від безпосереднього створення об’єктів за допомогою оператора new, замінивши його викликом фабричного методу.

Якщо ви маєте ієрархію продуктів і створюючий інтерфейс, який перевизначається в підкласах, то перед вами патерн Фабричний метод.

[Пояснення фабричного методу з кодом](https://www.baeldung.com/java-factory-pattern)

### Abstract Factory
**Абстрактна фабрика** - надає інтерфейс для створення сімейств взаємопов'язаних обє'ктів без зазначення їх конкретних класів.

---
### Singleton
**Паттерн Одинак** - гарантує, що клас має лише один екземпляр, і надає глобальну точку доступу до цього екземпляра. Для реалізації обов'язково повинен бути приватний конструктор, і статичний метод у поєднанні зі статичною змінною.

**Переваги** - відтермінована реалізація. На відміну від глобальних змінних, не обов'язково створювати на початку виконання програми. Сінглтон може бути створений у будь який момент на вимогу.

**Недоліки** - можуть виникати проблеми при багатопоточності (падіння швидкості), і при роботі з класлоадерами (2
 екземпляри сінглтона).

---
### Builder
**Будівельник** - породжуючий патерн проектування, що дає змогу створювати складні об’єкти крок за кроком. Будівельник дає можливість використовувати один і той самий код будівництва для отримання різних об’єктів. Його зручно використовувати, якщо треба ініціалізувати багаторізних полів.

---
### Command

**Паттерн команда** - відокремлює об'єкт що видає запити від об'єкта, що вміє ці запити виконувати. По іншому, інкапсулює запит у вигляді об'єкта, роблячи можливою параметризацію клієнтських об'єктів із іншими запитами, організацію черги або логування запитів ітд.

Механізм патерна складається з клієнта, ініціатора та одержувача (Клієнт -> ініціатор -> одержувач). Об'єкт команди інкапсулює одержувача з операцією, або набором операцій. Ініціатор викликає метод `execute()` об'єкта, що призводить до відповідних операцій з одержувачем.

Недоліки - класична реалізація призводить до появи багатьох проміжних класів, але використання лямбда виразів дозволяє їх успішно замінити.

---
### Adapter

**Адаптер** - перетворює інтерфейс одного класу на інший інтерфейс, на який розрахований клієнт. Адаптер забезпечує спільну роботу класів з несумісними інтерфейсами. З точки зору реалізації, це виглядає як пакування об'єкта, що володіє несумісним інтерфейсом, в обє'кт що реалізує необхідний інтерфейс.

Існує два види адаптерів: адаптери об'єктів та адаптери класів. В контексті java можна говорити лише про адаптери об'єктів. Для адаптерів класів потрібне множинне наслідування, що не реалізоване в java.

---
### Facade

**Фасад** - надає уніфікований інтерфейс доступу до групи інтерфейсів підсистеми. Фасад визначає високорівнений інтерфейс, що спрощує роботу з підсистемою. Простими словами - змінює інтерфейс заради його спрощення. Реалізується через клас, що спрощує та уніфікує низку інших класів.

---
### Template

**Патерн Шаборнний метод** - задає основу алгоритму в методі, залишаючи визначення деяких кроків реалізації підкласам. Дозволяє підкласам перевизначати деякі частини алгоритму без зміни його структури. Підходить для створення інфраструктур, які керують загальним ходом виконання завдання, але при цьому дають можливість користувачу вибирати, що відбувається на кожному кроці алгоритму.

Може мати наступні типи методів:
* final - підкласи не можуть модифікувати методи
* abstract - підкласи зобов'язані імплементувати метод на свій лад
* interceptor
 - пусті методи, через які реалізується необов'язкова частина алгоритму. Підкласи мржуть їх перевизначати, а можуть і ні

---
### Composite
**Композит / Компонувальник** - поєднує об'єкти у деревоподібні структури для репрезентації ієрархії "частина - ціле". Компонувальник дозволяє клієнтам ставитися до окремих об'єктів і композитів однаково.


---
### State

**Патерн Стан** - дозволяє об'єкту мати багато варіантів поведінки залежно від його внутрішнього стану. Може розглядатися як заміна численних умовних конструкцій `if else` у коді контексту на об'єкти в яких інкапсульована поведінка. Для зміни поведінки досить вибрати інший об'єкт стану. Виглядає ніби об'єкт змінює свій клас. Інкапсуляція кожного стану в окремому класі локалізує й полегшує можливі зміни. Клас Стану може бути як абстрактним так і інтерфейсом, залежно від того, чи є загальна функціональність.

Недоліки - збільшує кількість класів у проекті.

---

Page Object
Builder
