# juniper
Установка Ansible проста, так как все из коробки (для этой задачи мы использовали ubuntu server 16.04.03):

sudo apt-add-repository ppa:ansible/ansible
sudo apt-get update
sudo apt-get install ansible

Изменим настройки в /etc/ansible/ansible.cfg

#Каталог для ролей по умолчанию
roles_path = /etc/ansible/roles
#Проверка при подключении, можно и оставить, но предварительно к хостам придется подключится по SSH и подтвердить отпечаток.
host_key_checking = False
#Журнал
log_path = /var/log/ansible.log

Данные настройки сугубо личные для меня, у себя вы можете использовать свои.
Модуль для Juniper

Установим данный модуль и проверим его в списке:

sudo ansible-galaxy install Juniper.junos
ansible-galaxy list

Так же для использования модуля нам понадобиться nccclient

sudo apt-get install python-pip
pip install ncclient
