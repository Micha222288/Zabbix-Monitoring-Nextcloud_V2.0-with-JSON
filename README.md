# Zabbix-Monitoring-Nextcloud_V2.0-with-JSON

Description:

1.

curl -u CHANGEMEuser:CHANGEMEpassword -H 'OCS-APIRequest: true' https://nc.link.tld/ocs/v2.php/core/getapppassword

2.

EXTERNAL MONITORING WITH SSL change Timeout Value in ZBX Agent and Server both 10 till 30

UserParameter=nextcloud,curl -s -u CHANGEMEuser:CHANGEMEapp-passwd https://nc.link.tld/ocs/v2.php/apps/serverinfo/api/v1/info?format=json

######## OR ########

INTERNAL MONITORING LOCAL NO SSL more Performance

UserParameter=nextcloud,curl -s -k -u CHANGEMEuser:CHANGEMEapp-passwd https://127.0.0.1/ocs/v2.php/apps/serverinfo/api/v1/info?format=json

3-1.

Copy nextcloudv2.conf to /etc/zabbix/zabbix_agentd.conf.d
(SLL OR LOCAL depending on your monitoring)

3-2.

Add line to zabbix_agentd.conf

Include=/etc/zabbix/zabbix_agentd.conf.d/*.conf and restart Agent and Server

4.

Add 'nextcloudv2.xml' to Server templates

5.

You are ready to go. Wait at least 10 minutes or execute Item 'Nextcloud' of host.

6.

Check values in 'Latest Data' of zabbix host.

7.

If you see values - congratulations!

#####To be continued...#####
