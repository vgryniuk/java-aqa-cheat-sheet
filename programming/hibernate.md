# Hibernate
---
**Hibernate** - фркймворк який використовується для отримання (створення, видалення, зміни, збереження) java  об'єктів з бази даних. В порівнянні з JDBC сильно спрощує роботу з БД. Багато роблти виконує "під капотом". По суті є надбудовою на д JDBC.
 
##### Плюси
 * ORM (Object Relation Mapping).
 * Зменшує кількість коду при роботі.
 
Конфігурація зв'язку між класом та таблицею відбувається за допомогою:
 * **XML-файлу** (старий, громіздкий спосіб).
 * **Java аннотацій** 
 
Hibernate використовує концепцію **Entity class** - клас, що відображає інформацію таблиці в базі даних за допомогою анотацій. Entity клас повинен бути помічений анотаціями `@Entity`, `@Column` та `@Table` (де відбувається прив'язка до таблиці з ДБ).
  
Щоб працювати з БД потрібно створити сесію, користуючись `SessionFactory
`. В межах сесій, кожна операція відбувається в межах транзакції. Кожну транзакцію потрібно відкривати та закривати. 