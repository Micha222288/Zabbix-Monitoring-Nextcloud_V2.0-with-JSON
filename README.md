###### Zabbix-Monitoring-Nextcloud_V2.0-with-JSON
---------------------------------------------------------

DESCRIPTION:
------------

-----------------------------------------------------------------------------------------------------------------------------------------------
### 1. Get your APPPASSWORD ###
---------------------------------------------------------
(Executed following command >> BEFORE >> change YOURADMINUSER and YOURADMINPASSWORD)

curl -u YOURADMINUSER:YOURADMINPASSWORD -H 'OCS-APIRequest: true' https://YOUR.NEXTCLOUD-URL.TLD/ocs/v2.php/core/getapppassword

-----------------------------------------------------------------------------------------------------------------------------------------------
### 2. EXTERNAL MONITORING WITH SSL
---------------------------------------------------------

(change Timeout Value in ZBX Agent and Server both 10 till 30 - depending on your performnce)

-----------------------------------------------------------------------------------------------------------------------------------------------
### 3-1 Copy (*.conf)
---------------------------------------------------------

Copy nextcloudv2.conf to /etc/zabbix/zabbix_agentd.conf.d
(SLL OR LOCAL depending on your monitoring)

a) EXRTERNAL MONITORING WITH SSL (nextcloudv2_ssl.conf)
# (Change in file before copying all capital written words) #
UserParameter=nextcloud,curl -s -u YOURADMINUSER:APPPASSWORD https://YOUR.NEXTCLOUD-URL.TLD/ocs/v2.php/apps/serverinfo/api/v1/info?format=json

###### OR ######

b) INTERNAL MONITORING LOCAL NO SSL - faster Performance (nextcloudv2_local.conf)
# (Change in file before copying all capital written words) #
UserParameter=nextcloud,curl -s -k -u YOURADMINUSER:APPPASSWORD https://127.0.0.1/ocs/v2.php/apps/serverinfo/api/v1/info?format=json

-----------------------------------------------------------------------------------------------------------------------------------------------
### 3-2 Add line to zabbix_agentd.conf
---------------------------------------------------------
Include=/etc/zabbix/zabbix_agentd.conf.d/*.conf

After this restart your ZBX Server

-----------------------------------------------------------------------------------------------------------------------------------------------
### 4. Add 'zbx_nextcloud2-0_V1-1-0_Beta-xml' to Server templates
---------------------------------------------------------

-----------------------------------------------------------------------------------------------------------------------------------------------
### 5. You are ready to go. Wait at least 10 minutes or execute Item 'Nextcloud' of host.
---------------------------------------------------------

-----------------------------------------------------------------------------------------------------------------------------------------------
### 6. Check values in 'Latest Data' of zabbix host.
---------------------------------------------------------

-----------------------------------------------------------------------------------------------------------------------------------------------
### 7. If you see values - congratulations!
---------------------------------------------------------

-----------------------------------------------------------------------------------------------------------------------------------------------
###### Release Notes/Updates: ######
-----------------------------------------------------------------------------------------------------------------------------------------------
## 04.08.2021
New Template uploaded Release 1.0.3
with bugfixes for items and triggers

## 26.09.2021
New Template uploaded Release 1.1.0-Beta
added all possible values as item which are printed in API url.
Also added Excel File show the ZBX-key-build.
Preparing for final Template 1.2.0 now.
