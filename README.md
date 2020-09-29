# Отчёт о тестировании приложения "Credit Card Number Validator"

## Проверка валидности кредитных карт.

### Подставить в `String number` номер кредитной карты банка.


```
public class Main {
  public static void main(String[] args) {
    // TODO: подставлять номер карты нужно сюда между двойными кавычками, без пробелов
    String number = "5351719427810741";
    System.out.println(String.format("Result is %s", isValidCardNumber(number) ? "OK" : "FAIL"));
  }

  public static boolean isValidCardNumber(String number) {
    if (number == null) {
      return false;
    }

    if (number.length() != 16) {
      return false;
    }

    long result = 0;
    for (int i = 0; i < number.length(); i++) {
      int digit;
      try {
        digit = Integer.parseInt(number.charAt(i) + "");
      } catch (NumberFormatException e) {
        return false;
      }

      if (i % 2 == 0) {
        digit *= 2;
        if (digit > 9) {
          digit -= 9;
        }
      }
      result += digit;
    }

    return (result != 0) && (result % 10 == 0);
  }
}
```

## В результате тестирования выявлены следующие дефекты: 
* [American Express (AMEX) FAIL](https://github.com/BulygaDenis/javaHW1.2/issues/1);
* [Diners Club - Carte Blanche FAIL](https://github.com/BulygaDenis/javaHW1.2/issues/2).
* [Diners Club - International FAIL](https://github.com/BulygaDenis/javaHW1.2/issues/3)

## Документация:
[Установить IntelliJ IDEA согласно Руководство по установке IntelliJ IDEA](https://github.com/netology-code/javaqa-homeworks/blob/master/intro/idea.md)


## Результаты

1. 11\3 (Ok\Fail)
2. [Issues](https://github.com/BulygaDenis/javaHW1.2/issues)



## Окружение:

Win 10 x 64
openjdk version "11.0.8" 2020-07-14
OpenJDK Runtime Environment AdoptOpenJDK (build 11.0.8+10)
OpenJDK 64-Bit Server VM AdoptOpenJDK (build 11.0.8+10, mixed mode)



