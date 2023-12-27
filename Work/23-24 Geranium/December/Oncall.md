


Previous:
[Incident-451747646 Details - IcM (microsofticm.com)](https://portal.microsofticm.com/imp/v3/incidents/details/451747646/home)

12/21

[Incident-451772444 Details - IcM (microsofticm.com)](https://portal.microsofticm.com/imp/v3/incidents/details/451772444/home)

Customer suddenly cannot connect to SQL database via Azure VM 

It's PE connection/proxy, nslookup (private ip resolution) and TCP-Connection both works fine 

CA-PA (VIP) mapping not updated after VIP changed (SQL migration)

Azure VM conected to SQL DB via Private endpoint on old control ring even SQL DB has been migrated to new one

There was CA-PA mappaing between private endpoint IP and SQL Gateway VIP.  When we investigate NMAgent logs, we only found below entry during that time.

According to SQL team, they migrated SQL dataslice to different control rings but the client still connected to old rings which resulted the failured