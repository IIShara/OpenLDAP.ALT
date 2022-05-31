# OpenLDAP.ALT
Настройка OpenLdap на ALT Linux

1. Настрока домена и пользователя
```
sudo vi /etc/openldap/slapd-hdb-db01.conf

database hdb
suffix "dc=stand,dc=ru" //Доменное имя
rootdn "cn=admin,dc=stand,dc=ru" // имя пользователя ldap
rootpw admin // пароль пользователя ldap
directory /var/lib/ldap/bases/stand.ru 

```
2. Создание директории
```
sudo mkdir /var/lib/ldap/bases/stand.ru
chown ldap:ldap /var/lib/ldap/bases/stand.ru

```
4. Настрока доступа к ldap
```
sudo vi /etc/sysconfig/ldap

########################################
# SLAPD Proccess options
########################################
# SLAPD URL list
#SLAPDURLLIST="ldap://localhost/"
#SLAPDURLLIST="'ldap://localhost/ ldaps:///'"
SLAPDURLLIST="'ldap:/// ldaps:///'"

#SLAPD_OPTIONS="-l DAEMON -s 6"
```

4. Настройка логов
```
sudo vim /etc/syslog.conf

local4.*                                                -/var/log/ldap/slapd.log
```
