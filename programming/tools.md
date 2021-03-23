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

#Selenide vs Selenium

#Lombok