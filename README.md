## Дипломный проект к профессии "Тестировщик"
## "Автоматизация тестирования комплексного веб-сервиса "Путешествие дня", взаимодействующего с СУБД и API Банка"     
***
### Документация
#### [План автоматизации](https://github.com/AlexanderKachalov/diplom/blob/master/docs/Plan.md)   
#### [Отчет о проведенном тестировании](https://github.com/AlexanderKachalov/diplom/blob/master/docs/Report.md)   
#### [Отчёт о проведённой автоматизации](https://github.com/AlexanderKachalov/diplom/blob/master/docs/Summary.md)   
***  

### Процедура запуска авто-тестов
---   
#### Перед запуском авто-тестов:  
* устанавливаем на ПК программную платформу **Node** и устанавливаем и запускаем инструмент виртуализации **Docker**   
---  
#### Программное окружение   
1. macOS Mojave v.10.14.6   
2. Браузер Google Chrome v.81.0.4044.129    
---
### Запуск автотестов
  1. Запускаем мультиконтейнерное приложение Docker командой ```docker-compose up -d```         
#### Для работы с MySQL  
  2. Запускаем веб-сервис командой ```java -jar aqa-shop.jar --spring.profiles.active=mysql```   
   * страница веб-сервиса находится по адресу ```http://localhost:8080```   
  3. Запускаем симулятор банковских сервисов:      
   * переходим в каталог gate-simulator командой ```cd gate-simulator```  
   * запускаем симулятор сервисов командой ```npm start```   
  4. Запускаем авто-тесты в каталоге diplom командой ```./gradlew clean test allureReport```   
  5. Формируем отчет Gradle командой ```./gradlew allureServe```   
### Для работы с PostgreSQL
  2. Запускаем веб-сервис командой ```java -jar aqa-shop.jar --spring.profiles.active=postgresql```    
    * страница веб-сервиса находится по адресу ```http://localhost:8080```   
  3. Запускаем симулятор банковских сервисов:
   * переходим в каталог gate-simulator командой ```cd gate-simulator```  
   * запускаем симулятор сервисов командой ```npm start```   
  4. Запускаем авто-тесты в каталоге diplom командой ```./gradlew clean test -DurlDb=jdbc:postgresql://localhost:5432/app allureReport```      
  5. Формируем отчет Gradle командой ```./gradlew allureServe```   
  
