# Instrucciones para la creacion de la base de datos correspondiente a este ejercicio

1. Instalar MySQL Server
    - `sudo apt install mysql-server`
2. Entrar a MySQL
    - `sudo mysql`
3. Crear una nueva base de datos
    - `create databases codigoIoT;`
4. Seleccionar la base de datos creada
    - `use codigoIoT;`
5. Crear una nueva tabla que contenga los campos deseados
    - id, fecha, nombre, temperatura, humedad
    - `create table clima (id INT (6) UNSIGNED AUTO_INCREMENT PRIMARY KEY, fecha TIMESTAMP DEFAULT CURRENT_TIMESTAMP, nombre CHAR (248) NOT NULL, temperatura FLOAT (4,2), humedad INT (3));`
6. Crear un nuevo usuario para ser usado con NodeRed
    - `CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'password';`
    - `CREATE USER 'hugohugo'@'localhost' IDENTIFIED BY '1234';`
    - `GRANT ALL PRIVILEGES ON *.* TO 'hugohugo'@'localhost';`



## Notas

- Puedes consultar todas las bases de datos con el comando `show databases;`
- Puedes consultar las tablas en el interior de una base de datos selecccionada con el comando `show tables;`
- Puedes consultar la forma de la tabla con el comando `describe clima;`
- Para agregar información a la base de datos con NodeRed se requiere poner en un nodo Function la siguiente información

`msg.topic = "INSERT INTO clima (`nombre`,`temperatura`,`humedad`) VALUES ('Hugo'," + global.get ("tempAPI")+ "," + global.get ("humAPI") + ");";`

`return msg;`

- Puedes consultar todos los datos de una tabla con el siguiente comando `SELECT * FROM clima;`