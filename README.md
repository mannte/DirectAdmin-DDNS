# Dynamic DNS for Directadmin
Want to attach your home server to a subdomain but don't know how?
Use this simple PHP script with a cronjob to dynamically update your DNS records!

## Setup
ssh to your home server and make sure deps are installed, such as `php php-curl`.

```
# git clone https://github.com/brechtwyns/DirectAdmin-DDNS /opt/dyndns
# vi /opt/dyndns/credentials.json
# cat /opt/dyndns/credentials.json
{
	"username": "directAdminUsername",
	"password": "directAdminPassword_or_Login_key",
	"hostname": "webXXXX.zxcs.nl",
	"domain": "mydomain.nl",
	"ArecordName": "ArecordName"
}
# whereis php # <php location>, usually /usr/bin/php
# crontab -e
* * * * * <php location> /opt/dyndns/dyndns.php
```
For the ArecordName do not forget to add a . to the end of you domain (e.g. mydomain.nl.) if you want to update the full domain. If you want to edit a subdomain this is not needed, e.g. if you want to create/update smarthome.mydomain.nl, use only smarthome (without a dot at the end and without mydomain).
If you are using 2-factor authentication or for better security, you set a Login Key via the DirectAdmin Home page (so not under Password).

## Sources
* Based on [this forum post](https://www.vimexx.nl/forum/14-tutorials/588-dyndns-mogelijk-via-directadmin-api-bij-vimexx?page=1#post-2323).
* Shamelessly mirroring [httpsocket.php](https://files.directadmin.com/services/all/httpsocket/)
* [DirectAdmin Docs] (https://docs.directadmin.com/changelog/version-1.24.2.html#api-for-user-and-admin-level-dns-administration)
