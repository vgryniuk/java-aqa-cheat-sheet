# Stream API
---
**Stream API** - механізм обробки даних у функціональному стилі в java8. Дозволяє спростити обробку даних. Найчастіше застосовується для обробки колекцій та файлів, але може бути застосований до будь-якого джерела даних. Ключовим поняттям Stream API є потік **stream** - можливість почергового (або одночасного) отримання елемента даних для подальшої обробки. Stream є альтернативою до ітераторів (iterator). В той час, як ітератор є зовнішньою процедурою перебору даних в колекції, стрім є методом внутрішнього ітерування.

**Різниця між Stream та  Iterator**  Різниця між зовнішньою та внутрішньою ітерацією з точки зору реалізації є інтерфейси, що лежать в основі цих механізмів. Для зовнішньої реалізації використовують `Iterator<T>`, а для внутрішньої `Spliterator<T>`.

StreamAPI побудований на основі інтерфейсу `BaseStream<T, S extends BaseStream<T,S>>`, в ньому визначені методи для створення і роботи з потоками даних. Ці методи можна поділити на дві категорії:
* **Проміжні (intermediate)** - обробляють елементи що поступають, і повертають stream. Проміжних методів може бути кілька. Створюють послідовність операцій по якій обробляються дані. Умовно можна поділити по функціоналу на настіпні карегорії: фільтрація, зміна, впорядкування даних. 
* **Термінальні (terminal)** - обробляють елементи та завершують ланцюжок обробки стріма. Термінальний метод може бути лиш один. За функціональністю можна умовно розділити на: акумуляція даних, збереження даних, генерація результатів на основі даних.

Методи BaseStream: `void close()`, `boolean isParallel()`, `Iterator<T> iterator()` -  термінальний, `S (Stream) onClose()`, `S parallel()`, `S sequential()`, `Spliterator<T> spliterator()` - термінальний, `S unordered()`.

На основі `BaseStream` та його методів, створений `Stream<T>`.

**Як створити Stream**
* Collection - `stream()`, `parallelStream()`.
* Array - `Array.stream(Object[])`.
* Static methods - `IntStream.range(int, int)`, `StreamOf(Object[])`.
* File - `File.lines()`.
---
### Проміжні методи для фільтрацій даних
* `Stream<T> filter(Predicate<? Super T> predicate)`
* `Stream<T> distinct()` - повертає той самий потік без дублювання.
* `Stream<T> limit(long maxSize)` - повертає тільки перші n елементів.
* `Stream<T> skip(long n)` - пропускає перші n елементів.
* `default Stream<T> dropWhile(Predicate<? Super T> predicate)` - видаляє з потоку елементи, поки реалізація предикату повертає true. Як тільки предикат повертає false, поточний елемент і всі наступні залишаються.
* `default Stream<T> takeWhile(Predicate<? Super T> predicate)` - навпаки залишає в потоці елементи, поки реалізація предикату повертає true.

Проміжні методи можна застосовувати кілька разів підряд.
```
        List<Integer> list = Arrays.asList(1, 2, null, 4, 7, 8);
        List<Integer> newList = list.stream()
                .filter(Objects::nonNull)
                .filter(e -> e > 5)
                .collect(Collectors.toList());
```
---
### Проміжні методя для зміни потоку
Проміжні методя для зміни потоку призначені для генерації нового потоку на основі існуючого, злиття кількох потоків, або створення нового потоку.
* `<R> Stream<R> map(Function<? super T, ? extends R> mapper)` - зміна типу даних потоку на основі Function.
* `<R> Stream<R> flatMap(Function<? super T, ? extends R> mapper)` - створює окремий потік на основі кожного елементу даного потоку, і потім об'єднує всі потоки в один.
* `static <T> Stream<T> of(T t)` - потік з одного елементу.
* `static <T> Stream<T> of(T... values)` - потік з кількох елементів.
* ...

```
        List<String> l = List.of("Mercury", "Venus", "Earth" ,"Mars");
        Stream<Integer> s = l.stream().map(p -> p.length()); // Stream<String> -> Stream<Integer>
        s.forEach(System.out::println); // 7, 5, 5, 4
```
```
        String[] array = new String[] {"Mercury", "Earth" ,"Mars"};
        IntStream is = Arrays.stream(array).flatMapToInt(p -> p.codePoints());
        is.forEach(System.out::println); // 77, 101, 114, 99, 117, 114, 121, 69, 97...
```
---

