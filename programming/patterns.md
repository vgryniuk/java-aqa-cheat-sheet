# Patterns
---
### Strategy
**Патерн стратегія** визначає сімейство алгоритмів, інкапсулює кожен з них і забезпечує їхню взаємозамінність. Дозволяє модифікувати алгоритми не залежно від їхнього використання з боку клієнта. Або по іншому: поведінка інкапсулюється в окремому наборі класів, який легко розширюється і змінюється навіть під час виконання.

**Приклад:** будь який набір класів зі складною ієрархією, та поведінкою яка іноді може бути суперечливою. Простіше тримати всю реалізацію назовні (качечки в ставку: жива, резинова, дерев'яна).

---
### Observer
**Патерн Спостерігач** - визначає відношення 'один-до-багатьох' між об'єктами таким чином, що при зміні стану обного об'єкта відбувається автоматичне сповіщення та оновлення усіх залежних об'єктів.

**Приклад:** реакція лістенерів на поведінку програми.

---
### Decorator
**Патерн Декоратор** - шаблон проєктування, призначений для динамічного підключення додаткових можливостей до об'єкта, загортаючи їх у корисні «обгортки».

**Недоліки** - додає до архітектурибагатодрібних класів, у яких важко розібратися по мірі зростання кількості.

**Приклад:** Розрахунок ціни при купівлі чого небудь з набором не обов'язкових додаткових опцій.

---
### Factory Method
**Фабричний метод** - визначає інтерфейс сворення об'єкта, але дозволяє підкласам обрати створюваний екземпляр. Основне завдання: переміщення створення екземплярів у підкласи.

### Abstract Factory
**Абстрактна фабрика** - надає інтерфейс для створення сімейств взаємопов'язаних обє'ктів без зазначення їх конкретних класів.

---
### Singleton
**Паттерн Одинак** - гарантує, що клас має лише один екземпляр, і надає глобальну точку доступу до цього екземпляра. Для реалізації обов'язково повинен бути приватний конструктор, і статичний метод у поєднанні зі статичною змінною.

**Переваги** - відтермінована реалізація. На відміну від глобальних змінних, не обов'язково створювати на початку виконання програми. Сінглтон може бути створений у будь який момент на вимогу.

**Недоліки** - можуть виникати проблеми при багатопоточності (падіння швидкості), і при роботі з класлоадерами (2
 екземпляри сінглтона).

---
### Command

**Паттерн команда** - відокремлює об'єкт що видає запити від об'єкта, що вміє ці запити виконувати. По іншому, інкапсулює запит у вигляді об'єкта, роблячи можливою параметризацію клієнтських об'єктів із іншими запитами, організацію черги або логування запитів ітд.

Механізм патерна складається з клієнта, ініціатора та одержувача (Клієнт -> ініціатор -> одержувач). Об'єкт команди інкапсулює одержувача з операцією, або набором операцій. Ініціатор викликає метод `execute()` об'єкта, що призводить до відповідних операцій з одержувачем.

Недоліки - класична реалізація призводить до появи багатьох проміжних класів, але використання лямбда виразів дозволяє їх успішно замінити.

---

Page Object
Builder