# PostfixExamples
Example Config Files for Postfix Email Relay

These are a sanatized set of files that will allow SMTP relay functionality to M365 tenants.  This is a semi-secure configuration (i.e. non-open relay).  Additionally this relay was designed to be behind a firewall and no publicly accessible for inbound traffic.  

## Requirements
- Ability to create receive connector in M365
- Ability to send SMTP (Port 25) traffic outbound throught premise firewall
- Basic Linux Familiarity

## Prerequisites
- Linux Server with Postfix installed
- Port 25 open on linux server

## Contents
- main.cf
- local_domains
- open_access
- recipient_access
- restrict_senders
- transport

### File Functions
main.cf = primary configuration file for postfix, most changes are at the bottom of this config file but a few settings are inline you need to pay attention for.

local_domains = these are your email domains

open_access = list of ip based devices that can use the relay

restrict_senders = list of from addresses that can use the relay

transport = configuration that points to M365

recipient_access = not sure what this does as I did not use it

### Post configuration requirements.
After modifying the configuration files (all except "main.cf") you need to convert them to a db file.  This is achieved by the postmap command. 
Example: `postmap transport` or `postmap open_access`, etc

Then you need to restart the postfix server for those changes to take effect.
`postfix stop`, then `postfix reload`, then `postfix start`

### Helpful Postfix Commands

`postfix reload` = reload postfix

`postfix stop` = stop postfix

`postfix start` = start postfix

`postfix status` = see status of postfix

`postmap filename` = update file map after changes to file

`mailq` = view mail queue

`postqueue -p` = print/view mail queue

`postqueue -f` = flush/release mail queue

`tail -f /var/log/maillog | grep -B 2 -A 2 "emailaddress"` = search log for messages
