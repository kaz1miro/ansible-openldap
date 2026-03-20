# DevOps-Ansible Solution

## Описание
Автоматизированная установка и настройка OpenLDAP

Что реализует Playbook:
- преконфигурация LDAP до установки 
- установка OpenLDAP 
- создание базовой структуры, пользователей и групп

Playbook выполняется идемпотентно 

## Структура файлов 
```
-playbook.yml
-inventory.ini
-files/
  /-base.ldif
  /-user1.ldif
  /-user2.ldif
  /-dev.ldif
  /-admin.ldif
```

## Инструкция по запуску 
1. клонировать репозиторий 
```
git clone https://github.com/kaz1miro/ansible-openldap
```
2. зайти в папку репозитория 
3. выполнить
```
ansible-playbook -i inventory.ini playbook.yml -K
```
4. ввести пароль пользователя с sudo правами

## Поверка
Выполните
```
ldapsearch -x -LLL -H ldap://localhost -b dc=example,dc=com
```
и посмотрите структуру LDAP

## Примечание

Желатаельно запускать на чистой системе или сделать 
```
sudo apt purge slapd -y
sudo rm -rf /etc/ldap/slapd.d
sudo rm -rf /var/lib/ldap
```
