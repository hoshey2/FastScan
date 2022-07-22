#! /bin/bash
echo "Target IP x.x.x.x: "
read IP
echo "Starting Rustscan on" $IP
openports=$(rustscan -t 2000 --ulimit 2000 -g -a $IP | cut -f 2 -d '[' | cut -f 1 -d ']')
echo "Starting Nmap on open ports:" $openports
nmap -p $openports -T4 -A --reason -Pn $IP
