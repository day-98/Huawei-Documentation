###**Objetive**
Configure the SNMP agent with authentication and encryption (v3), read/write communities (v2c), and a trap destination host.

### **Tasks**
**Log in to the switch**

**Enter System Mode**

`system-view`

**Create SNMPv3 User Groups**

   `snmp-agent group v3 <group> noauth`

**Configure SNMP MIB Views**

   `snmp-agent group v3 <group> privacy read-view iso-view write-view iso-view notify-view iso-view`

   `snmp-agent mib-view private include mgmt`

   `snmp-agent mib-view iso-view include iso`

   `snmp-agent mib-view public_view include internet`

**Configure TRAP destination**

   `snmp-agent target-host trap-hostname eSight address <IP> udp-port 162 trap-paramsname <user>`

**Configure Securityname**

   `snmp-agent target-host trap-paramsname <user> v3 securityname <pass> noauthnopriv`

**Configure SNMPv3 User**

   `snmp-agent usm-user version v3 <user>`

**Assign user to group**

   `snmp-agent usm-user version v3 <user> group <group>`

**Configure authentication to user**

    `snmp-agent usm-user version v3 <user> authentication-mode sha2-256 <passw>`

**Configure encryption to user**

    `snmp-agent usm-user version v3 <user> privacy-mode aes128 <passw>`

**Configure Source Interface**

    `snmp-agent protocol source-interface all`
    `snmp-agent protocol source-interface <interface>`

**Enable Trap functionality**

    `snmp-agent trap enable`

### Check configurations

`display snmp-agent community`

 `display snmp-agent group`

 `display snmp-agent usm-user`

 `display snmp-agent target-host`

 `display snmp-agent mib-view`
