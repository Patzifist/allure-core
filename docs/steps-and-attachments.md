## Steps And Attachments

Allure умеет разбивать тесты на степы и сохранять аттачи в процессе выполнения тестов.
Стоит заметить, что степы могут быть вложенными и содержать в себе аттачменты.

### Steps

Спепы - это некоторые действия из которых состоит сценарий теста. Это просто обычные методы.
Их можно переиспользовать в различных тестовых сценариях. Они могут быть параметризованными,
могут выполнять какие-то действия, выполнять проверки, могут состоять из других степов и делать
аттачменты.
    Для того, чтобы метод стал степом, достаточно проаннотировать его аннотацией @Step.
У степа есть имя. По умолчанию это имя метода, приведенное в более читабельный формат с помощью
следующего преобразования:

``` java
public static String humanizeCamelCase(String camelCaseString) {
    return camelCaseString.replaceAll(
            String.format("%s|%s|%s",
                    "(?<=[A-Z])(?=[A-Z][a-z])",
                    "(?<=[^A-Z])(?=[A-Z])",
                    "(?<=[A-Za-z])(?=[^A-Za-z])"
            ),
            " "
    );
}

```


Также есть возможность перегрузить имя степа:

```java
@Step("Open '{0}' page.")
public void openPageByAddress(String pageAddress) {
     ...
 }
```

В имени степа можно использовать параметры метода. Все {i} будет замененны на i-й аргумент,
а все {method} на имя метода.


### Attachments
