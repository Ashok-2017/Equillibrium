# Equillibrium
#!/bin/bash
$1=HOST
$2=PORT
check=$(curl -s -w "%{http_code}\n" -L "${1}:{2}/" -o /dev/null)

if [[ ${check} == 200 || ${check} == 403 ]]
then
    echo "Service is online"
    exit 0
else
    echo "Service is offline"
    exit 1
fi    
