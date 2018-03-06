# alfa guides
Правила, инструкции и нотации по разработке

# Инструменты окружения разработчика

* rbenv - https://github.com/rbenv/rbenv (устанавливать только локально в домашний каталог)
* nvm - https://github.com/creationix/nvm (устанавливать только локально в домашний каталог)
* direnv - https://direnv.net (можно устанавливать системно через apt-ge)

# Правила работы с ветками в репозитории:

* (git flow) A successful Git branching model - http://nvie.com/posts/a-successful-git-branching-model/


# Замечания по ратое с кодом

## Строго:

* Не использовать относительные пути в импортах `import loadMessages from '../server/intl/loadMessages'`
* Стараться НЕ привязывать JS к классам и идентификаторам (использовать data или спец-атрибут)
* В package.json в dependencies лежать и dev зависимости и НЕ dev зависимости.

## Желательно:

*  Использовать константы для определения action-ов:
  src/verification/actions.js:    type: 'app/cards/INITIAL',
  src/verification/reducer.js:    case 'app/cards/INITIAL':


# Развертывание

* Отличное введение в docker - http://guides.hexlet.io/docker/
* Хорошое введение в capistrano - http://guides.beanstalkapp.com/deployments/deploy-with-capistrano.html


# Другие гайды

* hexlet - http://guides.hexlet.io


# Работа с git-ом

* Курс - https://ru.hexlet.io/courses/intro_to_git

В message комитов указываем номер задачи из Pivotal - `[(Finishes|Fixes|Delivers) #TRACKER_STORY_ID]`

# Прочее

* https://12factor.net/ru/

# Целевая ОС на серверах

* Ubuntu 16.04.3 LTS minimal


# Как делается релиз

1. Работаем в ветке develop.
2. Инкрементим версию релиза (composite.json)
3. Ветка develop выкатывается на staging
4. На staging проверяются все изменения которые выполнены по задачам вошедшим в develop
5. Если нужны правки - их делают в develop и переходят на пункт.
6. Если все OK - идем дальше.
7. Вливаем develop -> master.
8. Пушаем в master
9. Открываем консоль с логами nginx, php и cron
10. Выкатываем на боевой (bundle exec cap production deploy)
11. Смотрим в оба глаза на логи
12. Если все OK - ждем на релизе delivery

