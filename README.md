# Equillibrium
#!/bin/bash
check=$(curl -s -w "%{http_code}\n" -L "${HOST}:{PORT}/" -o /dev/null)

if [[ ${check} == 200 || ${check} == 403 ]]
then
    echo "Service is online"
    exit 0
else
    echo "Service is offline"
    exit 1
fi    
