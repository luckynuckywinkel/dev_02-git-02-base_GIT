# Домашнее задание к занятию «Основы Git», Лебедев А.И., fops-10


------

## Задание 1. Знакомимся с GitLab и Bitbucket 

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

### Решение:  

- Итак. Зарегистрируемся на gitlab и bitbucket, создадим там пустые репозитории, создадим ssh-ключ на нашей машине, добавим значение публичного ключа в ssh обеих платформ, добавим репозитории (https и ssh) при помощи git remote add и запушим в их ветку main все изменения, которые были сделаны нами в origin-репозитории на github.

![1](img/1.JPG)  

![2](img/2.JPG)   

![3](img/3.JPG)   

![4](img/4.JPG)   

![5](img/5.JPG)   

![6](img/6.JPG)   

![7](img/7.JPG)  

![8](img/8.JPG)   

- Хотел бы обратить внимание, что у bitbucker по дефолту существует ветка master. Т.к. пуш был в main, он создал новую ветку с таким названием. Не знаю, помешает ли это мне в дальнейшем, но пока оставил, как есть. 

---

## Задание 2. Теги

Представьте ситуацию, когда в коде была обнаружена ошибка — надо вернуться на предыдущую версию кода,
исправить её и выложить исправленный код в продакшн. Мы никуда не будем выкладывать код, но пометим некоторые коммиты тегами и создадим от них ветки. 

1. Создайте легковестный тег `v0.0` на HEAD-коммите и запуште его во все три добавленных на предыдущем этапе `upstream`.
1. Аналогично создайте аннотированный тег `v0.1`.
1. Перейдите на страницу просмотра тегов в GitHab (и в других репозиториях) и посмотрите, чем отличаются созданные теги. 
    * в GitHub — https://github.com/YOUR_ACCOUNT/devops-netology/releases;
    * в GitLab — https://gitlab.com/YOUR_ACCOUNT/devops-netology/-/tags;
    * в Bitbucket — список тегов расположен в выпадающем меню веток на отдельной вкладке.
  

- Создадим lightweight tag v0.0 на последнем коммите и запушим его во все удаленные (и origin).

![9](img/9.JPG)   

- Выше я ввел еще и хэш последнего коммита, но, судя по всему, можно было обойтись и без этого, т.к. мы тэгируем последний коммит. Теперь пушим.

```
root@git:/home/vagrant/devops_netology# git push --tags
Total 0 (delta 0), reused 0 (delta 0)
To bitbucket.org:luckynuckywinkel-1/devops_netology.git
 * [new tag]         v0.0 -> v0.0
```

- Видим, что таким образом он запушил тэг только в битбакер. Вероятно, от того, что последний апстрим (-u) был указан на него и работает он через ssh (поэтому и не спросил юзернэйм и пассворд) На оставшиеся пушим руками:

```
root@git:/home/vagrant/devops_netology# git push --tags gitlab
Username for 'https://gitlab.com': luckynuckywinkel
Password for 'https://luckynuckywinkel@gitlab.com':
Total 0 (delta 0), reused 0 (delta 0)
To https://gitlab.com/luckynuckywinkel/devops_netology.git
 * [new tag]         v0.0 -> v0.0
```

```
root@git:/home/vagrant/devops_netology# git push --tags origin
Username for 'https://github.com': luckynuckywinkel
Password for 'https://luckynuckywinkel@github.com':
Total 0 (delta 0), reused 0 (delta 0)
To https://github.com/luckynuckywinkel/devops_netology.git
 * [new tag]         v0.0 -> v0.0
```

- Создадим annotated tag и запушим его по аналогии с легковесным:

```
root@git:/home/vagrant/devops_netology# git tag -a v0.1 -m "This is a test of annotate commit"
```

![10](img/10.JPG)   

- Посмотрим, что там в вебе:

![11](img/11.JPG)   

![12](img/12.JPG)   

![13](img/13.JPG)   

- Замечу, что все платформы имеют разное отображение тэгов. В гитлабе, на мой взгляд, все нагляднее.

---

## Задание 3. Ветки 

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

### Решение:  

- Выполним все необходимые действия:

![14](img/14.JPG)   

![15](img/15.JPG)   

![16](img/16.JPG)  

![17](img/17.JPG)  

- Замечу одну интеерсную вещь. Коммит от которого пошла новая ветка, был сделан мною до доработки, когда файле README.md я не добавил полное описание каждой строчки *.gitignore. От этого, в ветке fix "потерялось" очень много текста. Не знаю, возможно, это даже нагляднее, а, возможно, повлияет на что-то в будущем.

## Задание 4. Упрощаем себе жизнь

Попробуем поработь с Git при помощи визуального редактора. 

1. В используемой IDE PyCharm откройте визуальный редактор работы с Git, находящийся в меню View -> Tool Windows -> Git.
1. Измените какой-нибудь файл, и он сразу появится на вкладке `Local Changes`, отсюда можно выполнить коммит, нажав на кнопку внизу этого диалога. 
1. Элементы управления для работы с Git будут выглядеть примерно так:

  
   
1. Попробуйте выполнить пару коммитов, используя IDE. 

[По ссылке](https://www.jetbrains.com/help/pycharm/commit-and-push-changes.html) можно найти справочную информацию по визуальному интерфейсу. 

Если вверху экрана выбрать свою операционную систему, можно посмотреть горячие клавиши для работы с Git. 
Подробней о визуальном интерфейсе мы расскажем на одной из следующих лекций.

*В качестве результата работы по всем заданиям приложите ссылки на ваши репозитории в GitHub, GitLab и Bitbucket*.    

### Решение:  

- Коллеги, честно говоря, наверное, не до конца разобрался. Функционал, вроде бы, работает, но не так всё визуально понятно, как у вас на картинках. У меня машина на windows. И в Vbox крутятся линуксовые виртуалки. Без графики. Поставил PyCharm прямо на Windows, смог вытянуть гит клоном репозиторий с гитхаба, добавил коммит в main-ветку. Графики. Красиво. Прикольно. Не очень привычно. Пушить не стал, пусть будет локально, ну его, к дьяволу.

![18](img/18.JPG)   

- Ссылки на созданные ресурсы:

<a href>https://gitlab.com/luckynuckywinkel/devops_netology</a>  

<a href>https://bitbucket.org/luckynuckywinkel-1/devops_netology/src/main/</a>  

- GitHub:

<a href>https://github.com/luckynuckywinkel/devops_netology</a>  

  
 
----

