# Synology_dashboard_grafana
A grafana dashboard for monitoring Synology NAS. I ran into some trouble setting it up, thats why I created this fork. Please see the additional steps required for setup below.

Dependencies
InfluxDB as the time-series database
Telegraf as the collector

Quick Start
- Enable SNMP on your Synology NAS
- Merge input_syno_telegraf.conf with your local Telegraf instance configuration (or create a new instance) or put it into the telegraf.d subdir
- Edit the SNMP 'public' string as appropriate --> this is the community string you gave during enabling SNMP on your Synology device
- Edit the 'agents' list to include all of your monitored NAS
- If you do not already have an InfluxDB output configured in your Telegraf instance:
- Merge the included output_influxdb_telegraf.conf  with your local Telegraf instance configuration:
- Edit the URL to your new InfluxDB instance
- Edit the username and password for this InfluxDB instance as appropriate
- setup snmp on your telegraf box if not already done: apt-get install snmpd snmp snmp-mibs-downloader
- place for Synology mibs: https://global.download.synology.com/download/Document/MIBGuide/Synology_MIB_File.zip
- download the required mibs files from Synology and put them into the following dir /usr/share/snmp/mibs (thanks for the input from this repo: https://github.com/alhazmy13/Synology-NAS-monitoring)
- Restart Telegraf (set up logging in /var/log/telegraf if not already done and monitor any errors in parsing)

