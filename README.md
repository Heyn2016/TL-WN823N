# TL-WN823N
Chipset: Realtek-RTL8192EU  

# Support Toradex iMX6Q
1. Linux 3.14.52  
2. GCC Linaro GCC 5.2-2015.11-2  

# Installing and Using

1. Installing <*.ko>:  
    $ insmod /lib/modules/3.14.52/kernel/net/wireless/cfg80211.ko  
    $ insmod /lib/modules/3.14.52/kernel/drivers/net/wireless/rtlwifi/rtl8192eu/8192eu.ko  

2. Then enable the Wi-Fi technology layer:  
    $ connmanctl enable wifi  

3. And scan for available networks:  
    $ connmanctl scan wifi  

4. Now show what the above actually found:  
    $ connmanctl services  
        *AR Wired            { ethernet_00142d486cef_cable }  
        <SSID>               { wifi_<HASH>_managed_psk }  

    $ vi /var/lib/connman/<SSID>-psk.config  
    [service_wifi_<HASH>_managed_psk]  
    Type = wifi  
    Name = <SSID>  
    Passphrase = <PASSPHRASE>  

5. Last but not least attempt to connect:  
    $ connmanctl connect wifi_<HASH>_managed_psk  


