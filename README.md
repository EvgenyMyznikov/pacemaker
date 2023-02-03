# Домашнее задание к занятию 10.3 «Pacemaker» - Evgeny Myznikov

### Задание 1
Согласно официальной документации, Pacemaker — это менеджер ресурсов кластера со следующими основными возможностями:
Обнаружение и восстановление сбоев на уровне узлов и сервисов;
Независимость от подсистемы хранения: общий диск не требуется;
Независимость от типов ресурсов: все что может быть заскриптовано, может быть кластеризовано;
Поддержка STONITH (изоляция отказавшего узла , чтобы он не вызывал нарушения работы компьютерного кластера. STONITH изолирует неисправные узлы, перезагружая или отключая неисправный узел. Конфликт между несколькими узлами, подверженный ошибкам, в кластере может привести к катастрофическим последствиям, например, если оба узла попытаются выполнить запись в общий ресурс хранилища. STONITH обеспечивает эффективную, хотя и радикальную защиту от этих проблем);
Поддержка кластеров любого размера;
Поддержка и кворумных и ресурсозависимых кластеров;
Поддержка практически любой избыточной конфигурации;
Автоматическая репликация конфига на все узлы кластера;
Возможность задания порядка запуска ресурсов, а также их совместимости на одном узле;
Поддержка расширенных типов ресурсов: клонов (запущен на множестве узлов) и с дополнительными состояниями (master/slave и т.п.);
Единый кластерный шелл (crm), унифицированный, скриптующийся.
Проект кроме собственно своих демонов, поддерживающих конфиг кластера и указанный выше шелл, также использует сторонние, тот же heartbeat и corosync (рекомендуется использовать corosync). В общем-то он поддерживает скрипты от heartbeat, поэтому проблем возникнуть не должно.

### Задание 2
Corosync - программный продукт, позволяющий реализовать кластер серверов. Его основное назначение — знать и передавать состояние всех участников кластера.
В основе работы заложены следующие функции: 
Отслеживание состояния приложений;
Оповещение приложений о смене активной ноды кластера;
Отправка одинаковых сообщений процессам на всех узлах кластера;
Предоставление доступа к общей базе данных с конфигурацией и статистикой;
Отправка уведомлений о ее изменениях;
Пример реализации кластера — Corosync + Stonith + Pacemaker (вместо Corosync может использовать Heartbeat).

### Задание 3
![master conf](https://github.com/EvgenyMyznikov/pacemaker/blob/main/img/corosync.conf2023-02-03.png?raw=true) 
![host1 conf](https://github.com/EvgenyMyznikov/pacemaker/blob/main/img/corosync.conf-host1-2023-02-03.png?raw=true)
![master status](https://github.com/EvgenyMyznikov/pacemaker/blob/main/img/pcs_status_master.png?raw=true)
![host1 status](https://github.com/EvgenyMyznikov/pacemaker/blob/main/img/pcs_status_host1.png?raw=true)
