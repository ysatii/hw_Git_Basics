# Домашнее задание к занятию «Основы Git»


## Задание 1. Знакомимся с GitLab и Bitbucket 
<details>
<summary>Нажмите для просмотра просмотра задания</summary>

Из-за сложности доступа к Bitbucket в работе достаточно использовать два репозитория: GitHub и GitLab.

Иногда при работе с Git-репозиториями надо настроить свой локальный репозиторий так, чтобы можно было 
отправлять и принимать изменения из нескольких удалённых репозиториев. 

Это может понадобиться при работе над проектом с открытым исходным кодом, если автор проекта не даёт права на запись в основной репозиторий.

Также некоторые распределённые команды используют такой принцип работы, когда каждый разработчик имеет свой репозиторий, а в основной репозиторий пушатся только конечные результаты 
работы над задачами. 

### GitLab

Создадим аккаунт в GitLab, если у вас его ещё нет:

1. GitLab. Для [регистрации](https://gitlab.com/users/sign_up)  можно использовать аккаунт Google, GitHub и другие. 
1. После регистрации или авторизации в GitLab создайте новый проект, нажав на ссылку `Create a projet`. 
Желательно назвать также, как и в GitHub — `devops-netology` и `visibility level`, выбрать `Public`.
1. Галочку `Initialize repository with a README` лучше не ставить, чтобы не пришлось разрешать конфликты.
1. Если вы зарегистрировались при помощи аккаунта в другой системе и не указали пароль, то увидите сообщение:
`You won't be able to pull or push project code via HTTPS until you set a password on your account`. 
Тогда перейдите [по ссылке](https://gitlab.com/profile/password/edit) из этого сообщения и задайте пароль. 
Если вы уже умеете пользоваться SSH-ключами, то воспользуйтесь этой возможностью (подробнее про SSH мы поговорим в следующем учебном блоке).
1. Перейдите на страницу созданного вами репозитория, URL будет примерно такой:
https://gitlab.com/YOUR_LOGIN/devops-netology. Изучите предлагаемые варианты для начала работы в репозитории в секции
`Command line instructions`. 
1. Запомните вывод команды `git remote -v`.
1. Из-за того, что это будет наш дополнительный репозиторий, ни один вариант из перечисленных в инструкции (на странице 
вновь созданного репозитория) нам не подходит. Поэтому добавляем этот репозиторий, как дополнительный `remote`, к созданному
репозиторию в рамках предыдущего домашнего задания:
`git remote add gitlab https://gitlab.com/YOUR_LOGIN/devops-netology.git`.
1. Отправьте изменения в новый удалённый репозиторий `git push -u gitlab main`.
1. Обратите внимание, как изменился результат работы команды `git remote -v`.

#### Как изменить видимость репозитория в  GitLab — сделать его публичным 

* На верхней панели выберите «Меню» -> «Проекты» и найдите свой проект.
* На левой боковой панели выберите «Настройки» -> «Основные».
* Разверните раздел «Видимость» -> «Функции проекта» -> «Разрешения».
* Измените видимость проекта на Public.
* Нажмите «Сохранить изменения».

### Bitbucket* (задание со звёздочкой) 

Это самостоятельное задание, его выполнение необязательно.
____

Теперь необходимо проделать всё то же самое с [Bitbucket](https://bitbucket.org/). 

1. Обратите внимание, что репозиторий должен быть публичным — отключите галочку `private repository` при создании репозитория.
1. На вопрос `Include a README?` отвечайте отказом. 
1. В отличии от GitHub и GitLab в Bitbucket репозиторий должен принадлежать проекту, поэтому во время создания репозитория 
надо создать и проект, который можно назвать, например, `netology`.
1. Аналогично GitLab на странице вновь созданного проекта выберите `https`, чтобы получить ссылку, и добавьте этот репозиторий, как 
`git remote add bitbucket ...`.
1. Обратите внимание, как изменился результат работы команды `git remote -v`.

Если всё проделано правильно, то результат команды `git remote -v` должен быть следующий:

```bash
$ git remote -v
bitbucket https://andreyborue@bitbucket.org/andreyborue/devops-netology.git (fetch)
bitbucket https://andreyborue@bitbucket.org/andreyborue/devops-netology.git (push)
gitlab	  https://gitlab.com/andrey.borue/devops-netology.git (fetch)
gitlab	  https://gitlab.com/andrey.borue/devops-netology.git (push)
origin	  https://github.com/andrey-borue/devops-netology.git (fetch)
origin	  https://github.com/andrey-borue/devops-netology.git (push)
```

Дополнительно можете добавить удалённые репозитории по `ssh`, тогда результат будет примерно такой:

```bash
git remote -v
bitbucket	git@bitbucket.org:andreyborue/devops-netology.git (fetch)
bitbucket	git@bitbucket.org:andreyborue/devops-netology.git (push)
bitbucket-https	https://andreyborue@bitbucket.org/andreyborue/devops-netology.git (fetch)
bitbucket-https	https://andreyborue@bitbucket.org/andreyborue/devops-netology.git (push)
gitlab	git@gitlab.com:andrey.borue/devops-netology.git (fetch)
gitlab	git@gitlab.com:andrey.borue/devops-netology.git (push)
gitlab-https	https://gitlab.com/andrey.borue/devops-netology.git (fetch)
gitlab-https	https://gitlab.com/andrey.borue/devops-netology.git (push)
origin	git@github.com:andrey-borue/devops-netology.git (fetch)
origin	git@github.com:andrey-borue/devops-netology.git (push)
origin-https	https://github.com/andrey-borue/devops-netology.git (fetch)
origin-https	https://github.com/andrey-borue/devops-netology.git (push)
```

Выполните push локальной ветки `main` в новые репозитории. 

Подсказка: `git push -u gitlab main`. На этом этапе история коммитов во всех трёх репозиториях должна совпадать. 
</details>

## Решение 1. 
1. Регистрация в  GitLab. Используем логин и пароль  для авторизации
 ![Работа с гитом](https://github.com/ysatii/hw_Git_Basics/blob/main/img/image1.jpg)  

 

2. Создадим проект  
 ![Работа с гитом](https://github.com/ysatii/hw_Git_Basics/blob/main/img/image1_1.jpg)
3. Добавим ключи 
 ![Работа с гитом](https://github.com/ysatii/hw_Git_Basics/blob/main/img/image1_2.jpg)

 ![Работа с гитом](https://github.com/ysatii/hw_Git_Basics/blob/main/img/image1_3.jpg)
4. перйдем на страницу проекта 

 [Страница проекта](https://gitlab.com/yurii_melnik/devops-netology )

 ![Работа с гитом](https://github.com/ysatii/hw_Git_Basics/blob/main/img/image1_4.jpg)

 ![Работа с гитом](https://github.com/ysatii/hw_Git_Basics/blob/main/img/image1_5.jpg)

5. Скопируем проект на новый репозиторий
 
 командой 
 ```sh
 git remote add gitlab https://gitlab.com/yurii_melnik/devops-netology
```
Добавим новый репозиторий  

Командой  
 ```sh
 git remote -v
```
Выведем все репозитории 



 ![Работа с гитом](https://github.com/ysatii/hw_Git_Basics/blob/main/img/image1_7.jpg)
 ![Работа с гитом](https://github.com/ysatii/hw_Git_Basics/blob/main/img/image1_8.jpg)

 Командой  
 ```sh
 git push -u gitlab main
```
Отправим изминения в репозиторий

 ![Работа с гитом](https://github.com/ysatii/hw_Git_Basics/blob/main/img/image1_6.jpg)


## Задание 2. Теги

<details>
<summary>Нажмите для просмотра просмотра задания</summary>
Представьте ситуацию, когда в коде была обнаружена ошибка — надо вернуться на предыдущую версию кода,
исправить её и выложить исправленный код в продакшн. Мы никуда не будем выкладывать код, но пометим некоторые коммиты тегами и создадим от них ветки. 

1. Создайте легковестный тег `v0.0` на HEAD-коммите и запуште его во все три добавленных на предыдущем этапе `upstream`.
1. Аналогично создайте аннотированный тег `v0.1`.
1. Перейдите на страницу просмотра тегов в GitHab (и в других репозиториях) и посмотрите, чем отличаются созданные теги. 
    * в GitHub — https://github.com/YOUR_ACCOUNT/devops-netology/releases;
    * в GitLab — https://gitlab.com/YOUR_ACCOUNT/devops-netology/-/tags;
    * в Bitbucket — список тегов расположен в выпадающем меню веток на отдельной вкладке. 

</details>

## Решение 2.
1. Пометим тегами указатель ветки и выведем сисок коммитов  
 ![Работа с гитом](https://github.com/ysatii/hw_Git_Basics/blob/main/img/image2.jpg)  

2. Отправим изминения в репозиторий  
 ![Работа с гитом](https://github.com/ysatii/hw_Git_Basics/blob/main/img/image2_1.jpg)

3. Убедимся в наличии тегов  
 в GitHub — https://github.com/ysatii/devops-netology/releases;  
 ![Работа с гитом](https://github.com/ysatii/hw_Git_Basics/blob/main/img/image2_2.jpg)
 
 в GitLab — https://gitlab.com/yurii_melnik/devops-netology/-/tags;
 ![Работа с гитом](https://github.com/ysatii/hw_Git_Basics/blob/main/img/image2_3.jpg)

## Задание 3. Ветки 
<details>
<summary>Нажмите для просмотра просмотра задания</summary>

Давайте посмотрим, как будет выглядеть история коммитов при создании веток. 

1. Переключитесь обратно на ветку `main`, которая должна быть связана с веткой `main` репозитория на `github`.
1. Посмотрите лог коммитов и найдите хеш коммита с названием `Prepare to delete and move`, который был создан в пределах предыдущего домашнего задания. 
1. Выполните `git checkout` по хешу найденного коммита. 
1. Создайте новую ветку `fix`, базируясь на этом коммите `git switch -c fix`.
1. Отправьте новую ветку в репозиторий на GitHub `git push -u origin fix`.
1. Посмотрите, как визуально выглядит ваша схема коммитов: https://github.com/YOUR_ACCOUNT/devops-netology/network. 
1. Теперь измените содержание файла `README.md`, добавив новую строчку.
1. Отправьте изменения в репозиторий и посмотрите, как изменится схема на странице https://github.com/YOUR_ACCOUNT/devops-netology/network 
и как изменится вывод команды `git log`.
</details>

## Решение 3
1. Переключимся обратно на ветку **main**, которая должна быть связана с веткой **main** репозитория на **github**. 
 ![Работа с гитом](https://github.com/ysatii/hw_Git_Basics/blob/main/img/image3.jpg)
2. Посмотрим лог коммитов и найдем хеш коммита с названием **Prepare to delete and move**, который был создан в пределах предыдущего домашнего задания.   
Выполним **git checkout** по хешу найденного коммита. Создадим новую ветку fix, базируясь на этом коммите **git switch -c fix**. 
Отправим новую ветку в репозиторий на GitHub 
```sh
git push -u origin fix. 
```
3. Посмотрим, как визуально выглядит ваша схема коммитов  
 [схема коммитов](https://github.com/ysatii/devops-netology/network)

 ![Работа с гитом](https://github.com/ysatii/hw_Git_Basics/blob/main/img/image3_1.jpg)

4. Изменим содержание файла README.md, добавив новую строчку.
 ![Работа с гитом](https://github.com/ysatii/hw_Git_Basics/blob/main/img/image3_2.jpg)

5. Отправим изменения в репозиторий и посмотрите, как изменится схема на странице

 ![Работа с гитом](https://github.com/ysatii/hw_Git_Basics/blob/main/img/image3_3.jpg)

 ![Работа с гитом](https://github.com/ysatii/hw_Git_Basics/blob/main/img/image3_4.jpg)
  ![Работа с гитом](https://github.com/ysatii/hw_Git_Basics/blob/main/img/image3_5.jpg)
6. Как изменится вывод команды git log

 ![Работа с гитом](https://github.com/ysatii/hw_Git_Basics/blob/main/img/image3_6.jpg)

## Задание 4. Упрощаем себе жизнь
<details>
<summary>Нажмите для просмотра просмотра задания</summary>

Попробуем поработь с Git при помощи визуального редактора. 

1. В используемой IDE PyCharm откройте визуальный редактор работы с Git, находящийся в меню View -> Tool Windows -> Git.
1. Измените какой-нибудь файл, и он сразу появится на вкладке `Local Changes`, отсюда можно выполнить коммит, нажав на кнопку внизу этого диалога. 
1. Элементы управления для работы с Git будут выглядеть примерно так:

   ![Работа с гитом](img/ide-git-01.jpg)
   
1. Попробуйте выполнить пару коммитов, используя IDE. 

[По ссылке](https://www.jetbrains.com/help/pycharm/commit-and-push-changes.html) можно найти справочную информацию по визуальному интерфейсу. 

Если вверху экрана выбрать свою операционную систему, можно посмотреть горячие клавиши для работы с Git. 
Подробней о визуальном интерфейсе мы расскажем на одной из следующих лекций.

*В качестве результата работы по всем заданиям приложите ссылки на ваши репозитории в GitHub, GitLab и Bitbucket*.  
 
----

</details>