docker volume create my-vol
docker volume ls
docker run  -d -p 9001:80 -v my-vol:/usr/local/apache2/htdocs/  --name con03 httpd
sudo find / -iname my-vol

sudo su -
 
ls /var/lib/docker/volumes/my-vol
 
ls /var/lib/docker/volumes/my-vol/_data/

echo "Added 2nd line in webserver" >> /var/lib/docker/volumes/my-vol/_data/index.html

cat /var/lib/docker/volumes/my-vol/_data/index.html
 
/var/lib/docker/volumes/my-vol/_data/index.html




docker exec con03 ls /usr/local/apache2/htdocs/
docker exec -it con03 /bin/bash
 -- once logged in
 cd htdocs/
cat index.html
echo "3rd line added in ws" > index.html
 
-- check the web page

exit from the container

docker run  -d -p 9002:80 -v my-vol:/usr/local/apache2/htdocs/:ro  --name con04 httpd
docker exec -it con04 /bin/bash
    cd htdocs/
    echo "4th line added in ws" > index.html