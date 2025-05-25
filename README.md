# ter-homeworks-01  
Moiseenko A.N.  

Чек-лист готовности к домашнему заданию  
1. Скачайте и установите Terraform версии >=1.8.4 . Приложите скриншот вывода команды terraform --version.
![image](https://github.com/user-attachments/assets/60bf2257-7bc4-4c63-9f26-016fc330a0e2)

2. Скачайте на свой ПК этот git-репозиторий. Исходный код для выполнения задания расположен в дире ктории 01/src.
![image](https://github.com/user-attachments/assets/0d39ee16-40d2-456e-bb98-8a1a9c47c98e)
  
3. Убедитесь, что в вашей ОС установлен docker.
![image](https://github.com/user-attachments/assets/9f769094-9a61-40fd-9a98-80d2e1666f77)


    Задание 1  
1. Перейдите в каталог src. Скачайте все необходимые зависимости, использованные в проекте.
![image](https://github.com/user-attachments/assets/97706206-af10-40f9-b6c8-f49c60f64c7a)
![image](https://github.com/user-attachments/assets/cb0b0cec-4048-446f-9050-f2ca6322bbd9)
  
3. Изучите файл .gitignore. В каком terraform-файле, согласно этому .gitignore, допустимо сохранить личную, секретную информацию?(логины,пароли,ключи,токены итд)
  
Ответ:  
Секретную информацию можно сохранить в файле personal.auto.tfvars  
   
5. Выполните код проекта. Найдите в state-файле секретное содержимое созданного ресурса random_password, пришлите в качестве ответа конкретный ключ и его значение.  
![image](https://github.com/user-attachments/assets/c5e04ea0-9bfc-4afd-88f5-904a1581e389)
![image](https://github.com/user-attachments/assets/d5d8b957-d554-458c-abcd-5dbc76453e0e)
Ответ:
 "result": "r870aNEav1lRDqm7"  
  
7. Раскомментируйте блок кода, примерно расположенный на строчках 29–42 файла main.tf. Выполните команду terraform validate. Объясните, в чём заключаются намеренно допущенные ошибки. Исправьте их.
![image](https://github.com/user-attachments/assets/87ca65aa-79a4-41c3-aeb6-7e47f4e4f507)  

Ответ:  
Первая ошибка - отсутствие имени у ресурса с типом "docker_image"  
  
Вторая ошибка - имя ресурса с типом "docker_container" начинается с цмфры "1nginx". Имя ресурса может начинаться либо с буквы либо со знака подчеркивания.  
  
Третья ошибка - в значении ключа "name" ресурса с типом "docker_container" "nginx" указан необъявленный ресур с типом "random_password" "random_string_FAKE". Правильно будет указать name  = "example_${random_password.random_string.result}"  
  



9. Выполните код. В качестве ответа приложите: исправленный фрагмент кода и вывод команды docker ps.  
10. Замените имя docker-контейнера в блоке кода на hello_world. Не перепутайте имя контейнера и имя образа. Мы всё ещё продолжаем использовать name = "nginx:latest". Выполните команду terraform apply -auto-approve. Объясните своими словами, в чём может быть опасность  
применения ключа -auto-approve. Догадайтесь или нагуглите зачем может пригодиться данный ключ? В качестве ответа дополнительно приложите вывод команды docker ps.  
11. Уничтожьте созданные ресурсы с помощью terraform. Убедитесь, что все ресурсы удалены. Приложите содержимое файла terraform.tfstate.  
12. Объясните, почему при этом не был удалён docker-образ nginx:latest. Ответ ОБЯЗАТЕЛЬНО НАЙДИТЕ В ПРЕДОСТАВЛЕННОМ КОДЕ, а затем ОБЯЗАТЕЛЬНО ПОДКРЕПИТЕ строчкой из документации terraform провайдера docker. (ищите в классификаторе resource docker_image )

```
nekiy kod
```





