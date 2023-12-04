# Java and AQA Tools

## JUnit VS TestNG
В загальному TestNG створювався для більш високорівневого тестування. Майже всі основні фічі TestNG i JUnit
 дублюються. На мою думку TestNG має трохи більш лаконічний синтаксис.

#### Hooks
| level | JUnit | TestNG |
| --- | --- | --- |
| class | @BeforeEach | @BeforeClass |
| method | @BeforeAll | @BeforeMethod |
| suite | --- | @BeforeSuite |
| group | --- | @BeforeGroup |
| test | --- | @BeforeTest |

#### Test dependencies
В TestNG, якщо перший метод не пройдений, то всі наступні будуть помічені як пропущені, а не як зафейлені, на відміну від JUnit.

#### Test order
| JUnit | TestNG |
| --- | --- |
| @FixMethodOrder(MethodSorters.NAME__ASCENDING) | @Test(priority = 1) |

#### Test parametrization
| JUnit | TestNG |
| --- | --- |
| @ValueSource | @DataProvider |
| @MethodSource | @Parameters({...}) via testng.xml|
| @CsvSource |  |

#### Test Ignore
| JUnit | TestNG |
| --- | --- |
| @Ignore | @Test(enabled=false) |
---

# Selenide vs Selenium vs Playwright

| Feature                       | Selenium                                   | Selenide                                      | Playwright                                   |
|-------------------------------|--------------------------------------------|-----------------------------------------------|----------------------------------------------|
| **Language Support**          | Java, Python, C#, Ruby, etc.               | Java, Kotlin, Groovy, Scala                   | JavaScript, TypeScript                       |
| **API Style**                 | Object-oriented                            | Fluent                                        | Object-oriented                              |
| **Browser Support**           | Chrome, Firefox, Safari, Edge, etc.        | Chrome, Firefox, Edge, Safari                 | Chromium-based, Firefox, WebKit              |
| **Locator Strategy**          | Various (ID, Name, XPath, CSS, etc.)       | CSS, XPath                                    | CSS, XPath, text, accessibility, etc.        |
| **Wait Mechanism**            | Explicit and Implicit Waits                 | Fluent Waits                                  | Auto-waits (auto-waiting for elements)      |
| **Parallel Testing**          | Requires additional setup for parallel execution | Built-in support for parallel execution | Built-in support for parallel execution     |
| **Headless Mode**             | Supported                                   | Supported                                     | Supported                                    |
| **Installation**              | Requires additional setup (drivers, etc.)  | Simplified setup                              | Simplified setup                             |
| **Community Support**         | Large community and resources               | Active community and growing                  | Growing community support                    |
| **Popularity**                | Widely used in industry                     | Increasing adoption                           | Rapidly gaining popularity                   |
| **Speed of Execution**        | Moderately fast                             | Fast                                          | Very fast                                    |
| **Multiple Browser Tabs**     | Can manage but requires more manual handling | Limited support                     | Native support for managing multiple tabs    |
| **Test Recordings**           | Usually requires separate plugins/tools    | Not available                                | Native support for test recordings          |
| **Built-in Network Control**  | Limited control over network traffic        | Limited control                              | Native support for network traffic control  |
| **Built-in Reporting**        | Requires additional plugins/integration    | Limited support                              | Native support for reporting                |
| **API Testing**               | Can be integrated with additional tools    | Limited support                              | Limited native support for API testing      |

# Lombok
