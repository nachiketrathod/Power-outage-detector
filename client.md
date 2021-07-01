#!/bin/bash


while :
do
        curl --connect-timeout 10 --retry 2 --retry-delay 5 -L "http://x.x.x.x:xxxx/ping"
        sleep 30
        read -t 0.1 -n 1 k
        [[ "$k" == "s" ]] && break
done