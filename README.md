
Список протестированного оборудования

# Juniper: SRX100
# JunOS: 12.1x46

**модули:http://docs.ansible.com/ansible/latest/modules/list_of_network_modules.html#junos **

Установка Ansible проста, так как все из коробки:

*sudo apt-add-repository ppa:ansible/ansible
*sudo apt-get update
*sudo apt-get install ansible

Изменим настройки в /etc/ansible/ansible.cfg

#Каталог для ролей по умолчанию
*roles_path = /etc/ansible/roles
#Проверка при подключении, можно и оставить, но предварительно к хостам придется подключится по SSH и подтвердить отпечаток.
*host_key_checking = False
#Журнал
*log_path = /var/log/ansible.log

**Модуль для Juniper**

Установим данный модуль и проверим его в списке:

*sudo ansible-galaxy install Juniper.junos
*ansible-galaxy list

Так же для использования модуля нам понадобиться nccclient

*sudo apt-get install python-pip
*pip install ncclient


Для авторизации на устройствах хотелось бы сразу настроить авторизацию по ключу. Генерируем для удобства под root ключ RSA После копируем его в предварительно созданный /etc/ansible/.ssh для удобства использования.

*ssh-keygen -t rsa
*cp /root/.ssh/id_rsa.pub /etc/ansible/.ssh/ansible.pub
*cp /root/.ssh/id_rsa /etc/ansible/.ssh/ansible

По итогу на целевых устройствах необходимо было бы завести вручную пользователя с публичным ключом:

*set system login user ansible class super-user authentication ssh-rsa "<SSH-key>"
