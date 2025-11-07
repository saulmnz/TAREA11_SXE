# EXTENSIONES ÚTILES PARA GESTIONAR DOCKER 🐳 :

- **Varias extensiones necesarias ya vienen instaladas por defecto ( Como YAML o EnvFiles ) con el ide escogido, Pycharm. 🦦**

> **1. La propia extensión de docker. ( Ya viene instalada, quizás haya que realizar un update del pluggin ) 🎳**

![IMG](img/1.png)

> **2. Un Pluggin que nos ayude a gestionar bases de datos 🧟**

![IMG](img/3.png)

# ARCHIVO DE CONFIGURACIÓN DOCKER COMPOSE 🐙

```yaml
services:
  db:
    image: postgres:17
    container_name: odoo18_db
    environment:
      - POSTGRES_DB=postgres
      - POSTGRES_USER=odoo
      - POSTGRES_PASSWORD=odoo
    volumes:
      - postgres_data:/var/lib/postgresql/data
    restart: unless-stopped

  web:
    image: odoo:18.0
    container_name: odoo18_app
    depends_on:
      - db
    ports:
      - "8069:8069"
    environment:
      - HOST=db
      - USER=odoo
      - PASSWORD=odoo
      - ODOO_MASTER_PASSWD=odoo
    volumes:
      - web_data:/var/lib/odoo
      - ./addons:/mnt/extra-addons
    restart: unless-stopped

  pgadmin:
    image: dpage/pgadmin4
    container_name: pgadmin4_odoo18
    depends_on:
      - db
    ports:
      - "5050:80"
    environment:
      - PGADMIN_DEFAULT_EMAIL=admin@example.com
      - PGADMIN_DEFAULT_PASSWORD=admin
    volumes:
      - pgadmin_data:/var/lib/pgadmin
    restart: unless-stopped
volumes:
  postgres_data:
  web_data:
  pgadmin_data:
```

---

# CAPTURA DE PANTALLA CONFORME TODO FUNCIONA CORRECTAMENTE 🦔

> **ODOO 🐇**
![img](img/4.png)

> **PGADMIN INSTALACION BASE DE DATOS PARA ODOO EN PGADMIN 🐘**
![img](img/5.png)
![img](img/6.png)
![img](img/9.png)
![img](img/10.png)

---
 
# EXPLORAR ODOO CON DATOS DEMO

> **CARGAMOS DATOS DE DEMOSTRACIÓN PARA MOSTRAR LA INSTALACIÓN DE MÓDULOS BÁSICOS 🤖**
![img](img/17.png)
![img](img/11.png)
![img](img/12.png)
![img](img/13.png)
![img](img/14.png)


> **INSPECCIONAMOS LA BASE DE DATOS A TRAVÉS DE PgAdmin 🫧**

> ![img](img/15.png)
> ![img](img/16.png)