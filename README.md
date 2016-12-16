# Azure Site Recovery Lab

This site is for the purpose of tracking my progress in building a suitable lab for testing Azure Site Recovery (ASR).

Both groups will be on one Azure subscription. One resource group will function as the "on-prem" site, and one resource group will function as the failover resource group meant to be in Azure containing the Azure Recovery Vault.

# On-Premise Group
RESOURCE GROUP = SouthCentral
REGION = South Central US 
VNET = southvnet / 172.16.0.0/16
 - DNS IP = 172.16.1.4
SUBNET = onprem 172.16.1.0/24
DOMAIN CONTROLLER = SouthDC 
 - DNS IP = static private ip 172.16.1.4
 - NETBIOS DOMAIN NAME = anniesasr
FILE SERVER = south-file-svr 
 - FILE TO FAILOVER - C:\Users\Annie\hello.txt
 - joined to anniesasr.priv
CONFIGURATION SERVER = ConfigServer / 
 - joined to anniesasr.priv
 - MySQL Root Password = Administrat0r!
 - Vault ID Passphrase = Administrat0r!!!
VIRTUAL NETWORK GATEWAY = GatewayToSouthRG
 - VPN

# Failover Group
RESOURCE GROUP = West
REGION = West Central US
VNET = westvnet / 192.168.0.0/16
SUBNET = west-failover 192.168.1.0/24
DOMAIN CONTROLLER = WestDC / DNS = static private ip 192.168.1.4
 - add to domain - anniesasr.priv
GRS STORAGE = failoverstoragewest
ASRRootCert =  installed
ASRRSV