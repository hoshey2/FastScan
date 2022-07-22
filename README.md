# FastScan
Qucik scanner I scripted using RustScan and Nmap

# use bash
! /bin/bash
# formatting
echo "Target IP x.x.x.x: "
# read input
read IP
# formatting
echo "Starting Rustscan on" $IP
# rustscan with timeout, ulimit, greppable, and url set. 
# Cut out the open ports only.
openports=$(rustscan -t 2000 --ulimit 2000 -g -a $IP | cut -f 2 -d '[' | cut -f 1 -d ']')
# formatting
echo "Starting Nmap on open ports:" $openports
# nmap the open ports with timing, all (OS detection, version detection, script scanning, and traceroute), reason, and no ping set.
nmap -p $openports -T4 -A --reason -Pn $IP
