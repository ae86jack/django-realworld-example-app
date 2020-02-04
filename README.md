### 项目简介

把[django-realworld-example-app](https://github.com/gothinkster/django-realworld-example-app)整个服务进行docker化. 

### 项目启动

docker-compose启动, 包括前后端, 数据库等:
```bash
docker-compose up
```

在启动服务后, 创建表:
```bash
docker-compose exec backend python manage.py migrate
```

### 代码修改
相对原项目做了以下修改:
- 把conduit/settings.py里的DEBUG, SECRET_KEY, DATABASES改成环境变量.  
- requirements.txt新增
    * psycopg2-binary==2.8.3
    * gunicorn==19.9.0
    
### 服务简介

- frontend, 前端项目: http://localhost
- db, Postgresql数据库, 初始化时新建数据库`conduit`, 当前设置用户名为`postgres`, 密码为`pwd`
- pgadmin, PostgreSQL的Web管理界面: http://localhost:5050, 当前设置用户名为`admin`, 密码为`pwd`. 连接数据库, `Host name/address`设为`db`, `Port`为`5432`, `Username`为`postgres`, `Password`为`pwd`
- backend, 后端项目: http://localhost/api/
- proxy, 反向代理、负载均衡, [traefik](https://docs.traefik.io/), Dashboard界面: http://localhost:8090/dashboard