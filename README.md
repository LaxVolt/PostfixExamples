# PostfixExamples
Example Config Files for Postfix Email Relay

These are a sanatized set of files that will allow SMTP relay functionality to M365 tenants.  This is a semi-secure configuration (i.e. non-open relay)

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
