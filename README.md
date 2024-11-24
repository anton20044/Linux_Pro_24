Лабораторная работа №24 по курсу Linux Pro.

Задание:

1) взять стенд https://github.com/erlong15/vagrant-bind
2) добавить еще один сервер client2
3) завести в зоне dns.lab имена web1 - смотрит на клиент1 web2 смотрит на клиент2
4) завести еще одну зону newdns.lab, завести в ней запись www - смотрит на обоих клиентов
5) настроить split-dns: клиент1 - видит обе зоны, но в зоне dns.lab только web1, клиент2 видит только dns.lab
6) настроить все без выключения selinux*

Решение:

- Добавлен сервер client2
- В зоне dns.lab заведены А записи: web1 и web2 (см "web1 from client" и "web2 from client"). Для проверки использовались команды dig @192.168.56.10 web1.dns.lab и dig @192.168.56.11 web2.dns.lab
- Добавлена зона newdns.lab, в зоне добавлено две записи www, которые смотрят на оба клиента
- Настроен split-dns:
 а) клиент1 видит обе зона, но в зоне dns.lab только web1 (см "web.dns.lab from client", "web1.dns.lab from client", "www.newdns.lab from client")
 б) клиент2 видит только dns.lab (см "web1.dns.lab from client2", "web2.dns.lab from client2", "www.newdns.lab from client2")
- На DNS серверах включен SELinux, т.к. используется стандартный 53 порт, то дополнительное конфигурирование не потребовалось

Разворачивание ВМ и их настройка с помощью vagrant и ansible.