# Песочница для ДЗ Отуса/Express42

Виртуальная машина для экспериментов по домашним заданиям курса "DevOps практики и инструменты"
Песочница будет пополняться инструментами по мере прохождения курса

## Операционная система

CentOs 7

## Установленные инструменты

- ansible (последняя версия на момент запуска)
- packer    v.1.4.0
- terraform v.0.11.13 

## Передаваемые параметны

- каталог, который будет монтироваться к каталогу гостевой машины /home/vagrant/otus
- публичные и закрытые ключи для работы с виртуальными машинами
- файл-ключ для сервисной учетной записи Google Compute Provider

## Предварительные настройки

Желательно установить плагин для автоматической установке VirtualBox Guest Additions

<code>vagrant plugin install vagrant-vbguest</code>

## Запуск ВМ 

<code>vagrant up</code>

## Остановка ВМ 

<code>vagrant halt</code>

## Удаление ВМ 

<code>vagrant destroy</code>

## Войти в ВМ

<code>vagrant ssh</code>

## Синхроннизация папок

<code>vagrant rsync-auto</code>