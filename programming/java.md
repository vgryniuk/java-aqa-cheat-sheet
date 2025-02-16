# Java Basics

### OOP Basics
В об'єкно орієнтованих мовах є 3 способи організації взаємодії між класами: **наслідування**, **агрегація** і **композиція**. 
* **Наслідування** - клас наслідник має всі поля і методи батьківського класу, і як правило додає якийсь новий функціонал. Наприклад Легковий автомобіль є наслідником Автомобіля.
* **Композиція** - клас контейнер містить в собі інший клас в якості поля, і клас вміст контейнера не може існувати окремо від самого контейнера. Вміст контейнера створюється в момент створення самого контейнера, і знищується разом з контейнером.
* **Агрегація** - клас контейнер містить в собі інший клас в якості поля, але вміст існує незалежно від контейнера. В момент створення контейнера вміст передається як параметр в конструктор.

Замість наслідування рекомендують використовувати композицію. Композиція забезпечує слабку зв'язність (наслідування це сильна зв'язність), і дозволяє більш гнучко створювати потрібні нам об'єкти. Композиція реалізується шляхом впровадження інтерфейсів між абстракціями верхнього та нижнього рівнів.

**Приклад**: ВУЗ (композиція) Факультет (агрегація) Студент.

---
### Абстрактні класи
**Абстрактний клас** - клас для якого не можливо створити екземпляр.
* Якщо в класі є хоча б один абстрактний метод, то цей клас повинен бути абстрактним.
* Абстрактний клас може містити, а може і не містити абстрактні методи.
* Абстрактний метод не може мати тіла.
* Дочірний клас повинен реалізувати всі абстрактні методи батьківського класу, або теж бути абстрактним.
* Абстрактний клас може містити поля, і вони не можуть бути абстрактними.
* Будь-який перевизначений метод може бути як абстрактним, так і не абстрактним.
* Для методів абстрактного класу неприпустиме поєднання: final abstract, private abstract, static abstract, оскільки ці модифікатори говорять що метод далі не наслідується.

---
### Інтерфейси
**Інтерфейс** – це конструкція мови програмування, яку часто порівнюють із контрактом. У цьому контракті зазначено, що клас зможе робити, тобто, які методи в ньому будуть присутні, якщо він імплементує цей інтерфейс. Коли клас імплементує якийсь інтерфейс, він зобов'язується забезпечити методи цього інтерфейсу тілами (перезаписати
абстрактні методи), інакше клас має стати абстрактним. Тобто якщо відомо, що клас імплементував якийсь інтерфейс, то цьому класі гарантовано будуть методи з інтерфейсу.
* Неможливо створити об'єкт інтерфейсу, оскільки це не клас. Звідси також слідує, що інтерфейс не має конструкторів.
* Інтерфейс не може бути final.
* Методи інтерфейсу не можуть бути final.
* Зі змінних в інтерфейсі можуть бути лише константи, які повинні бути в ньому ініціалізовані.
* Якщо клас, який імплементував інтерфейс не перевизначив його методи, то цей клас повинен бути абстрактним.
* Iнтерфейс може мати внутрішні класи, які за замовчувнням будуть статичні.
* Інтерфейс може мати дефолтні та статичні методи.
* Всі не дефолтні та не статичні методи за замовчуванням `public abstract`.
* Всі поля інтерфейсу за замовчуванням `public static final`.
---

### Модифікатор Static
**Static** - модифікатор, який застосовується до поля, метода, або внутнішнього класу, вказує на прив'язку суб'єкта до поточного класу.

**Статичні поля** - при позначенні змінної модофікатором `static`, ми вказуємо на те, що її значення відноситься до класу, і є спільним для всіх об'єктів класу.

**Статичні методи** - прив'язані до класу, а не до об'єкту. Щоб викликати статичний метод не обов'язково створювати екземпляр класу. Важливим нюансом є те, що статичний метод може звертатися лишень до статичних полів/методів.

**Статичні класи** - статичним класом може бути лише внутрішній клас. По суті, не відрізняється від будь якого іншого внутрішнього класу, за винятком того, що його об'єкт не містить посилання на об'єкт зовнішнього класу, який його створив. 

---
### Різниця між фреймворком та бібліотекою

**Бібліотека** - набір функцій, які ви можете викликати. Бібліотеки організовані в класи. Після виклику бібліотеки, виконується якась робота і контроль повертається до користувача.

**Фреймворк** - містить в собі деякий абстрактний дизайн і вбудовану поведінку. Щоб його використовувати, треба розмістити свій код в різних місцях фреймворку (через наслідування, або додавання своїх класів). Код фреймворку буде викликати ваш код.

Основна різниця між фреймворком та бібліотекою - інверсія управління.

---
### Iterator
**Iterator** - деяка сутність, здатна перебрати всі елементи колекції без вникання у її внутрішню структуру.
```
Iterator iterator = list.iterator();
while (iterator.hasNext()) {
    System.out.println(iterator.next());
}
```

---
### Compatator vs Сomparable
Compatator і Сomparable - інтерфейси, що імплементують методи для порівняння об'єктів одного типу. 

**Comparable** реалізує всього один метод `compareTo()`, який повертає нуль, якщо об'єкти рівні, додатнє число, якщо перший об'єкт більший за другий, та від'ємне якщо навпаки. Comparable використовується для порівняння об'єктів класу в рамках якого був реалізований.

**Comparator** імплементує кілька методів, ключовим серед яких є `compare()`. Comparator можна використовувати з різними класами і багатократно. Від дозволяє створювати об'єкти, що керуватимуть процесом порівняння, наприклад при сортуванні.

---
### Generic <T>
**Generic** (узагальнення) - це параметризовані типи. З їх допомогою можна оголошувати класи, інтерфейси та методи, де тип даних вказаний як параметр. Даний підхід до опису даних і алгоритмів дозволяє працювати з різними типами без зміни опису (алгоритмів і даних). Дозволяє виправити помилки пов'язані з неправильним приведенням типів ще на етапі компіляції. Generics використовуються на рівні компіляції, що означає, що вони не зберігаються у байт-коді (явище називається type erasure — стирання типів).

**Приклад без Geeric**
```
public class Main {
    public static void main(String[] args) {
        List list = new ArrayList(); // raw type
        list.add("Hello");
        list.add(123); // No error during compilation.

        String s = (String) list.get(0); // ОК
        String s2 = (String) list.get(1); // ClassCastException!
        System.out.println(s);
        System.out.println(s2); // ERROR!!!
    }
}
```

**приклад з Generic**
```
public class Main {
    public static void main(String[] args) {
        List<String> list = new ArrayList<>(); //Strictly defined type
        list.add("Hello");
        // list.add(123); // Error during compilation

        String s = list.get(0); // No need to cast types
    }
}
```
#### Wildcards <?>
**Wildcards <?>** використовуються для визначення узагальнених типів у сигнатурах методів, коли точний тип невідомий або має змінюватися в різних викликах. Wildcards <?> використовуються тільки у сигнатурах методів, але не можна створювати змінні або класи з <?>, оскільки <?> означає невідомий тип, і компілятор не може визначити, які операції дозволені з такою змінною.
```
List<?> list = new ArrayList<?>(); // ERROR: unable to create ArrayList<?>
```
Аналогічно зі створенням класу.

#### Коваріантність <? extends Type>
**Коваріантність <? extends Type>** означає, що ми можемо працювати з типами, які є підкласами певного класу. Тобто `List<? extends Animal>` може містити `List<Dog>`, `List<Cat>` тощо. `<? extends Type>` дозволяє читати елементи, але не дозволяє додавати жодного елементу окрім null, оскільки при додаванні може виникнути помилка приведення типів.

#### Контрваріантність <? super Type>
**Контрваріантність <? super Type>** означає, що ми можемо працювати з типами, які є суперкласами певного класу. Тобто `List<? super Integer>` може містити `List<Integer>`, `List<Number>`, `List<Object>`.`<? super Type>` дозволяє додавати елементи, але читати можна тільки як Object, оскільки компілятор не знає точний тип.

---
### Серіалізація
**Серіалізація** - збереження стану об'єкту, наприклад для передачі по мережі чи збереження з можливістю відтворити пізніше. При серіалізації зберігаєтся повний граф об'єкта, включно зі всіма об'єктами, на які він посилається. Для того щоб бути серіалізованим, об'єкт повинен імплементувати інтерфейс `Serializable`. Для коректної серіалізації, всі об'єктина які посилається об'єкт також повинні бути `Serializable`. 

Для того, щоб серіалізувати об'єкт, потрібно створити потік `FileOutputStream`,  з'єднати його з потоком `ObjectOutputStream` та викликати з нього метод `writeObject(object)`.

Якщо змінну не треба серіалізувти (наприклад щоб не зберігати пароль), її необхідно помітити як `transient`. При десеріалізації `transient` змінна отримає значення `null`.
```
class <CLASS_NAME> implements Serializable {transient String <VAR_NAME>}
```
Статичні змінні не серіалізуються.

---
### Exceptions

![Exception hierachy diagram](/images/ExceptionClassHierarchy.png "Exception hierachy diagram")

Обробка винятків дозволяє нам розмежовувати код на код, який повинен виконуватися при звичайному перебігу програми та код, який повинен виконуватися при появі винятків.

**Error** - це дуже серйозні помилки, які не можуть бути безпосередньо конрольовані програмою (ExceptionInInitializerError, StackOverflowError, NoClassDefFoundError OutOfMemoryError).

**RuntimeException (unchecked exceptions)** - Runtime виключення бувають у коді, в якому присутні помилки. Тобто, у виникненні цих винятків винен сам програміст. Компілятор не може перевірити можливість виникненя runtime виключеннь. Runtime винятки можна не оголошувати і не обробляти, але за бажанням можна зробити і те, й інше.

**IOException (checked exceptions)** - винятки вказують на частину коду, який знаходиться за межами безпосереднього контролю програми, і який може бути причиною викиду винятків. Вони зазвичай виникають при взаємодії програми із зовнішніми джерелами (робота з файлами, з БД, з мережею), через які можуть виникати проблеми. Компілятор завжди перевіряє можливість виникнення checked винятків. Checked винятки завжди повинні бути або оголошені та/або оброблені.

---
### String, StringBuffer, StringBuilder

|       | String | StringBuilder | StringBuffer |
| ----------- | ----------- | ----------- | ----------- |
| незмінність      | immutable       | mutable       | mutable       |
| розширюваність   | final        | final       | final       |
| потокобезпеіність   | Так, за рахунок незмінності.       | Ні.       | Так, за рахунок синхронізації.       |
| переваги      | За рахунок незмінності хеш код кешується, його не потрібно щоразу обчислювати. Це дає високу продуктивність при використанні в якості ключа Hash map. | Не забиває пам'ять сміттям.       | Не забиває пам'ять сміттям.       |
| недоліки      | В результаті операцій створюються нові екземпляри стрічок, а старі відкидаються. Це породжує велику кількість сміття в пам'яті.       | Потоконебезпечний.       | Синхронізовані методи повільніші за несинхронізовані. |
| коли використовувати   | При роботі зі стрічками, які рідко будуть модифікуватись.        | При роботі зі стрічками в однопоточному середовищі. | При роботі зі стрічками в багатопоточному середовищі.       |

---
