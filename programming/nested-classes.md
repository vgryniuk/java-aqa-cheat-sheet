## Nested classes

**Nested classes** (вкладені класи) - класи, щоб виділяють деяку сутність, що нерозривно зв'язані з іншою сутністю. Внутрішній клас є сенс зробити, якщо він корисний тільки для одного класу. Розділяються на `Non static nested classes` (inner classes) (не статичні, внутрішні), та `Static nested classes` (статичні). В свою чергу `inner classes` діляться на власне `inner classes`, `method local inner classes`, та `anonymous inner classes`. 
  
Самі по собі вкладені класи не мають відношення до Java 1.8, але є логічним попередником лямбди, і основою для її розуміння.

---
### Inner Classes
**Внутрішній клас** - не статичний клас, що описаний в тілі іншого класу, є частковим випадком вкладеного класу. Створити об'єкт внутрішнього класу можна лише при наявності об'єкту зовнішнього класу. Внутрішній клас має доступ до полів і методів зовнішнього класу, але не навпаки.

**Обмеження внутрішніх класів:**
* не можуть мати статичних полів та методів
* в середині не може бути оголошений enum
* не можна повернути об'єкт внутнішнього класу зі статичного методу зовнішнього класу

**Переваги внутрішніх класів:**
* можна мати кілька реалізацій того самого абстрактного класу чи інтерфейсу в межах одного зовнішнього класу.
* дозволяє мати кілька об'єктів, кожен з яких володіє власним станом, і в той же час володіє станом зовнішнього класу.
* можна створити об'єкт внутрішнього класу, після створення об'єкту зовнішнього

Внутрішній клас можна наслідувати за межами зовнішнього, але потрібно вказати зовнішній клас, і конструктор повинен отримувати посилання на об'єкт зовнішнього класу.
 
---
### Static nested classes
**Статичний (вкладений клас)** - статичний клас оголошений в тілі іншого класу. Може існувати без зовнішнього класу, і має доступ лише до статичних полів зовнішнього класу. Корисний у випадку, коли зв'язок внутрішнього і зовнішнього класу не потрібен. Не має доступу до не статичних полів зовнішнього класу.

**Для чого використовують Статичні вкладені класи**
* щоб підкреслити, що зовнішній клас складається з більш мілких частин
* приховування частини логіки в середині класу

---
### Local inner classes
**Локальний внутрішній клас** -не статичний клас, що оголошується в середині блоку коду, і не є членом зовнішнього класу. Можна розглядати не як клас, а як локальну змінну типу Class. В загальному випадку локальний внутрішній клас може бути оголошений у більш вузьких блоках коду, ніж метод, наприклад тіло умовного оператора, цикли, блоки ініціалізації, try-catch.

Java не підтримує статичних локальних внутрішніх класів.

**Для чого потрібні локальні внутрішні класи**
* реалізація логіки з використанням об'єкту ксласу в тілі методу
* реалізація абстрактного класу або інтерфеййсу в тілі методу, з метою отримання посилання на об'єкт потрібного типу

**Особливості локальних внутрішніх класів**
* об'єкт локального внутрішнього класу не може створюватись за межами блоку коду в якому його було оголошено
* локальні внутрішні класи не можуть мати модифікаторів доступу
* локальні внутрішні класи не можуть бути статичними

Локальні внутрішні класи мають такі самі обмеження, як і звичайні внутрішні класи.

---
### Anonymous inner classes

 **Анонімний клас** - різновид внутрішніх класів, при створенні яких ім'я явно не задається. Використання обумовлено необхідністю однократного створення об'єкту, який реалізує абстрактний клас або інтерфейс. Анонімні класи можуть використовіватися як внутрішні, або як локальні внутрішні класи. 
 
 Анонімний клас з одним перевизначеним методом отримав розвиток у вигляді лямбди в java 1.8. Взагалі, анонімний клас може перевизначати більше ніж один метод. Різниця між лямбдою та анонімним класом - в тому, що у лямбді можна перевизначити тільки 1 метод, а в анонімному класі більше ніж 1.

**Обмеження анонімних класів**
* аноніминй клас не може мати конструктора, оскільки ім'я конструктора повинно співпадати з іменем класу, а анонімний клас імені не має. Проблема відсутності конструктора частково вирішується через не статичний блок ініціалізації.
* анонімний клас може реалізувати **тільки один** інтерфейс
* анонімний клас не може нічого наслідувати, і його самого теж не можна наслідувати
* анонімний клас не може визначати поля й методи, крім констант `static final`

---
