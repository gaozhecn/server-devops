```
web:
  image: daocloud.io/fy_sft/python-mysql-sample:master
  ports:
  - 8000:8000
  links:
  - mysql:mysql
  - redis:redis
  volumes:
  - /home/ubuntu/cms-test/cms:/tmp/
  command: /code/manage.py runserver 0.0.0.0:8000
mysql:
  image: daocloud.io/mysql:latest
  environment:
  - MYSQL_DATABASE=django
  - MYSQL_ROOT_PASSWORD=mysql
  volumes:
  - /home/ubuntu/cms-test/cms/mysql:/var/lib/mysql
  ports:
  - 3307:3306
redis:
  image: daocloud.io/redis:latest
  ports:
  - 6379:6379

```



