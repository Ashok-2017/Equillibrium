# Equillibrium
#!/bin/bash
$1=HOST
$2=PORT
check=$(curl -s -w "%{http_code}\n" -L "${1}:{2}/" -o /dev/null)

if [[ ${check} == 200 || ${check} == 403 ]]
then
    echo "Service is online"
    if [ -f "/usr/local/var/run/nginx.pid" ]
    then
         echo "Nginx is running"
         status=124
         exit ${status}
    else
        echo " we need to restart the service"
        sudo service nginx start
        staus=125
        exit ${status} 
else
    echo "Service is offline"
    exit 1
fi    
