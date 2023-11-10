Reto SQL
```sql
     CREATE DATABASE IF NOT EXISTS pruebas;
     USE pruebas;
     CREATE TABLE tblUsuarios (
          idx INT PRIMARY KEY AUTO_INCREMENT,
          usuario VARCHAR(20),
          nombre VARCHAR(20),
          sexo VARCHAR(1),
          nivel TINYINT,
          email VARCHAR(50),
          telefono VARCHAR(20),
          marca VARCHAR(20),
          compañia VARCHAR(20),
          saldo FLOAT,
          activo BOOLEAN
     );
     INSERT INTO tblUsuarios 
     VALUES 
     ('1','BRE2271','BRENDA','M','2','brenda@live.com','655-330-5736','SAMSUNG','IUSACELL','100','1'),
     ('2','OSC4677','OSCAR','H','3','oscar@gmail.com','655-143-4181','LG','TELCEL','0','1'),
     ('3','JOS7086','JOSE','H','3','francisco@gmail.com','655-143-3922','NOKIA','MOVISTAR','150','1'),
     ('4','LUI6115','LUIS','H','0','enrique@outlook.com','655-137-1279','SAMSUNG','TELCEL','50','1'),
     ('5','LUI7072','LUIS','H','1','luis@hotmail.com','655-100-8260','NOKIA','IUSACELL','50','0'),
     ('6','DAN2832','DANIEL','H','0','daniel@outlook.com','655-145-2586','SONY','UNEFON','100','1'),
     ('7','JAQ5351','JAQUELINE','M','0','jaqueline@outlook.com','655-330-5514','BLACKBERRY','AXEL','0','1'),
     ('8','ROM6520','ROMAN','H','2','roman@gmail.com','655-330-3263','LG','IUSACELL','50','1'),
     ('9','BLA9739','BLAS','H','0','blas@hotmail.com','655-330-3871','LG','UNEFON','100','1'),
     ('10','JES4752','JESSICA','M','1','jessica@hotmail.com','655-143-6861','SAMSUNG','TELCEL','500','1'),
     ('11','DIA6570','DIANA','M','1','diana@live.com','655-143-3952','SONY','UNEFON','100','0'),
     ('12','RIC8283','RICARDO','H','2','ricardo@hotmail.com','655-145-6049','MOTOROLA','IUSACELL','150','1'),
     ('13','VAL6882','VALENTINA','M','0','valentina@live.com','655-137-4253','BLACKBERRY','AT&T','50','0'),
     ('14','BRE8106','BRENDA','M','3','brenda2@gmail.com','655-100-1351','MOTOROLA','NEXTEL','150','1'),
     ('15','LUC4982','LUCIA','M','3','lucia@gmail.com','655-145-4992','BLACKBERRY','IUSACELL','0','1'),
     ('16','JUA2337','JUAN','H','0','juan@outlook.com','655-100-6517','SAMSUNG','AXEL','0','0'),
     ('17','ELP2984','ELPIDIO','H','1','elpidio@outlook.com','655-145-9938','MOTOROLA','MOVISTAR','500','1'),
     ('18','JES9640','JESSICA','M','3','jessica2@live.com','655-330-5143','SONY','IUSACELL','200','1'),
     ('19','LET4015','LETICIA','M','2','leticia@yahoo.com','655-143-4019','BLACKBERRY','UNEFON','100','1'),
     ('20','LUI1076','LUIS','H','3','luis2@live.com','655-100-5085','SONY','UNEFON','150','1'),
     ('21','HUG5441','HUGO','H','2','hugo@live.com','655-137-3935','MOTOROLA','AT&T','500','1');
   ```

### Bloque 1

##### Consultas

1. Listar los nombres de los usuarios

   ```sql
   SELECT nombre FROM tblUsuarios;
   ```
     | nombre    |
     |-----------|
     | BRENDA    |
     | OSCAR     |
     | JOSE      |
     | LUIS      |
     | LUIS      |
     | DANIEL    |
     | JAQUELINE |
     | ROMAN     |
     | BLAS      |
     | JESSICA   |
     | DIANA     |
     | RICARDO   |
     | VALENTINA |
     | BRENDA    |
     | LUCIA     |
     | JUAN      |
     | ELPIDIO   |
     | JESSICA   |
     | LETICIA   |
     | LUIS      |
     | HUGO      |


2. Calcular el saldo máximo de los usuarios de sexo “Mujer”

     ```sql
     SELECT MAX(saldo) FROM tblUsuarios WHERE sexo='M';
     ```
     | MAX(saldo) |
     |------------|
     |        500 |

3. Listar nombre y teléfono de los usuarios con teléfono NOKIA, BLACKBERRY o SONY

     ```sql
      SELECT nombre, telefono FROM tblUsuarios WHERE marca='NOKIA' OR marca='BLACKBERRY' OR marca='SONY';
     ```
     | nombre    | telefono     |
     |-----------|--------------|
     | JOSE      | 655-143-3922 |
     | LUIS      | 655-100-8260 |
     | DANIEL    | 655-145-2586 |
     | JAQUELINE | 655-330-5514 |
     | DIANA     | 655-143-3952 |
     | VALENTINA | 655-137-4253 |
     | LUCIA     | 655-145-4992 |
     | JESSICA   | 655-330-5143 |
     | LETICIA   | 655-143-4019 |
     | LUIS      | 655-100-5085 |

4. Contar los usuarios sin saldo o inactivos

     ```sql
     SELECT COUNT(usuario) FROM tblUsuarios WHERE saldo=0 OR activo=0;
     ```
     | COUNT(usuario) |
     |----------------|
     |              7 |

5. Listar el login de los usuarios con nivel 1, 2 o 3

     ```sql
     SELECT usuario, email FROM tblUsuarios WHERE nivel=1 OR nivel=2 OR nivel=3;
     ```
     | usuario | email               |
     |---------|---------------------|
     | BRE2271 | brenda@live.com     |
     | OSC4677 | oscar@gmail.com     |
     | JOS7086 | francisco@gmail.com |
     | LUI7072 | luis@hotmail.com    |
     | ROM6520 | roman@gmail.com     |
     | JES4752 | jessica@hotmail.com |
     | DIA6570 | diana@live.com      |
     | RIC8283 | ricardo@hotmail.com |
     | BRE8106 | brenda2@gmail.com   |
     | LUC4982 | lucia@gmail.com     |
     | ELP2984 | elpidio@outlook.com |
     | JES9640 | jessica2@live.com   |
     | LET4015 | leticia@yahoo.com   |
     | LUI1076 | luis2@live.com      |
     | HUG5441 | hugo@live.com       |

6. Listar los números de teléfono con saldo menor o igual a 300

     ```sql
     SELECT telefono FROM tblUsuarios WHERE saldo<=300;
     ```
     | telefono     |
     |--------------|
     | 655-330-5736 |
     | 655-143-4181 |
     | 655-143-3922 |
     | 655-137-1279 |
     | 655-100-8260 |
     | 655-145-2586 |
     | 655-330-5514 |
     | 655-330-3263 |
     | 655-330-3871 |
     | 655-143-3952 |
     | 655-145-6049 |
     | 655-137-4253 |
     | 655-100-1351 |
     | 655-145-4992 |
     | 655-100-6517 |
     | 655-330-5143 |
     | 655-143-4019 |
     | 655-100-5085 |

7. Calcular la suma de los saldos de los usuarios de la compañia telefónica NEXTEL

     ```sql
     SELECT SUM(saldo) AS SumaSaldo FROM tblUsuarios WHERE compañia="NEXTEL";
     ```
     | SumaSaldo |
     |-----------|
     |       150 |


8. Contar el número de usuarios por compañía telefónica

     ```sql
     SELECT compañia,COUNT(compañia) AS Cantidad FROM tblUsuarios GROUP BY compañia;
     ```
     | compañia  | Cantidad |
     |-----------|----------|
     | IUSACELL  |        6 |
     | TELCEL    |        3 |
     | MOVISTAR  |        2 |
     | UNEFON    |        5 |
     | AXEL      |        2 |
     | AT&T      |        2 |
     | NEXTEL    |        1 |


9. Contar el número de usuarios por nivel

     ```sql
     SELECT nivel,COUNT(nivel) AS Cantidad FROM tblUsuarios GROUP BY nivel;
     ```
     | nivel | Cantidad |
     |-------|----------|
     |     2 |        5 |
     |     3 |        6 |
     |     0 |        6 |
     |     1 |        4 |

10. Listar el login de los usuarios con nivel 2

      ```sql
      SELECT usuario,email FROM tblUsuarios WHERE nivel=2;
      ```
     | usuario | email               |
     |---------|---------------------|
     | BRE2271 | brenda@live.com     |
     | ROM6520 | roman@gmail.com     |
     | RIC8283 | ricardo@hotmail.com |
     | LET4015 | leticia@yahoo.com   |
     | HUG5441 | hugo@live.com       |

11. Mostrar el email de los usuarios que usan gmail

      ```sql
      SELECT email FROM tblUsuarios WHERE email LIKE '%@gmail.com';
      ```
     | email               |
     |---------------------|
     | oscar@gmail.com     |
     | francisco@gmail.com |
     | roman@gmail.com     |
     | brenda2@gmail.com   |
     | lucia@gmail.com     |

12. Listar nombre y teléfono de los usuarios con teléfono LG, SAMSUNG o MOTOROLA

      ```sql
      SELECT nombre,telefono FROM tblUsuarios WHERE marca='LG' OR marca='SAMSUNG' OR marca='MOTOROLA';
      ```
     | nombre  | telefono     |
     |---------|--------------|
     | BRENDA  | 655-330-5736 |
     | OSCAR   | 655-143-4181 |
     | LUIS    | 655-137-1279 |
     | ROMAN   | 655-330-3263 |
     | BLAS    | 655-330-3871 |
     | JESSICA | 655-143-6861 |
     | RICARDO | 655-145-6049 |
     | BRENDA  | 655-100-1351 |
     | JUAN    | 655-100-6517 |
     | ELPIDIO | 655-145-9938 |
     | HUGO    | 655-137-3935 |

------

### Bloque 2

##### Consultas

1. Listar nombre y teléfono de los usuarios con teléfono que no sea de la marca LG o SAMSUNG

     ```sql
     SELECT nombre,telefono FROM tblUsuarios WHERE marca!='LG' OR marca!='SAMSUNG';
     ```
     | nombre    | telefono     |
     |-----------|--------------|
     | BRENDA    | 655-330-5736 |
     | OSCAR     | 655-143-4181 |
     | JOSE      | 655-143-3922 |
     | LUIS      | 655-137-1279 |
     | LUIS      | 655-100-8260 |
     | DANIEL    | 655-145-2586 |
     | JAQUELINE | 655-330-5514 |
     | ROMAN     | 655-330-3263 |
     | BLAS      | 655-330-3871 |
     | JESSICA   | 655-143-6861 |
     | DIANA     | 655-143-3952 |
     | RICARDO   | 655-145-6049 |
     | VALENTINA | 655-137-4253 |
     | BRENDA    | 655-100-1351 |
     | LUCIA     | 655-145-4992 |
     | JUAN      | 655-100-6517 |
     | ELPIDIO   | 655-145-9938 |
     | JESSICA   | 655-330-5143 |
     | LETICIA   | 655-143-4019 |
     | LUIS      | 655-100-5085 |
     | HUGO      | 655-137-3935 |

2. Listar el login y teléfono de los usuarios con compañia telefónica IUSACELL

     ```sql
     SELECT usuario,email,telefono FROM tblUsuarios WHERE compañia='IUSACELL';
     ```
     | usuario | email               | telefono     |
     |---------|---------------------|--------------|
     | BRE2271 | brenda@live.com     | 655-330-5736 |
     | LUI7072 | luis@hotmail.com    | 655-100-8260 |
     | ROM6520 | roman@gmail.com     | 655-330-3263 |
     | RIC8283 | ricardo@hotmail.com | 655-145-6049 |
     | LUC4982 | lucia@gmail.com     | 655-145-4992 |
     | JES9640 | jessica2@live.com   | 655-330-5143 |

3. Listar el login y teléfono de los usuarios con compañia telefónica que no sea TELCEL

     ```sql
     SELECT usuario,email,telefono FROM tblUsuarios WHERE compañia!='TELCEL';
     ```
     | usuario | email                 | telefono     |
     |---------|-----------------------|--------------|
     | BRE2271 | brenda@live.com       | 655-330-5736 |
     | JOS7086 | francisco@gmail.com   | 655-143-3922 |
     | LUI7072 | luis@hotmail.com      | 655-100-8260 |
     | DAN2832 | daniel@outlook.com    | 655-145-2586 |
     | JAQ5351 | jaqueline@outlook.com | 655-330-5514 |
     | ROM6520 | roman@gmail.com       | 655-330-3263 |
     | BLA9739 | blas@hotmail.com      | 655-330-3871 |
     | DIA6570 | diana@live.com        | 655-143-3952 |
     | RIC8283 | ricardo@hotmail.com   | 655-145-6049 |
     | VAL6882 | valentina@live.com    | 655-137-4253 |
     | BRE8106 | brenda2@gmail.com     | 655-100-1351 |
     | LUC4982 | lucia@gmail.com       | 655-145-4992 |
     | JUA2337 | juan@outlook.com      | 655-100-6517 |
     | ELP2984 | elpidio@outlook.com   | 655-145-9938 |
     | JES9640 | jessica2@live.com     | 655-330-5143 |
     | LET4015 | leticia@yahoo.com     | 655-143-4019 |
     | LUI1076 | luis2@live.com        | 655-100-5085 |
     | HUG5441 | hugo@live.com         | 655-137-3935 |
4. Calcular el saldo promedio de los usuarios que tienen teléfono marca NOKIA

     ```sql
     SELECT AVG(saldo) AS SaldoPromedio FROM tblUsuarios WHERE marca='NOKIA';
     ```
     | SaldoPromedio |
     |---------------|
     |           100 |

5. Listar el login y teléfono de los usuarios con compañia telefónica IUSACELL o AXEL

     ```sql
     SELECT usuario,email,telefono FROM tblUsuarios WHERE compañia='IUSACELL' OR compañia='AXEL';
     ```
     | usuario | email                 | telefono     |
     |---------|-----------------------|--------------|
     | BRE2271 | brenda@live.com       | 655-330-5736 |
     | LUI7072 | luis@hotmail.com      | 655-100-8260 |
     | JAQ5351 | jaqueline@outlook.com | 655-330-5514 |
     | ROM6520 | roman@gmail.com       | 655-330-3263 |
     | RIC8283 | ricardo@hotmail.com   | 655-145-6049 |
     | LUC4982 | lucia@gmail.com       | 655-145-4992 |
     | JUA2337 | juan@outlook.com      | 655-100-6517 |
     | JES9640 | jessica2@live.com     | 655-330-5143 |

6. Mostrar el email de los usuarios que no usan yahoo

     ```sql
     SELECT email FROM tblUsuarios WHERE email NOT LIKE '%@yahoo.com'
     ```
     | email                 |
     |-----------------------|
     | brenda@live.com       |
     | oscar@gmail.com       |
     | francisco@gmail.com   |
     | enrique@outlook.com   |
     | luis@hotmail.com      |
     | daniel@outlook.com    |
     | jaqueline@outlook.com |
     | roman@gmail.com       |
     | blas@hotmail.com      |
     | jessica@hotmail.com   |
     | diana@live.com        |
     | ricardo@hotmail.com   |
     | valentina@live.com    |
     | brenda2@gmail.com     |
     | lucia@gmail.com       |
     | juan@outlook.com      |
     | elpidio@outlook.com   |
     | jessica2@live.com     |
     | luis2@live.com        |
     | hugo@live.com         |

7. Listar el login y teléfono de los usuarios con compañia telefónica que no sea TELCEL o IUSACELL

     ```sql
     SELECT usuario,email,telefono FROM tblUsuarios WHERE compañia!='IUSACELL' AND compañia!='TELCEL';
     ```
     | usuario | email                 | telefono     |
     |---------|-----------------------|--------------|
     | JOS7086 | francisco@gmail.com   | 655-143-3922 |
     | DAN2832 | daniel@outlook.com    | 655-145-2586 |
     | JAQ5351 | jaqueline@outlook.com | 655-330-5514 |
     | BLA9739 | blas@hotmail.com      | 655-330-3871 |
     | DIA6570 | diana@live.com        | 655-143-3952 |
     | VAL6882 | valentina@live.com    | 655-137-4253 |
     | BRE8106 | brenda2@gmail.com     | 655-100-1351 |
     | JUA2337 | juan@outlook.com      | 655-100-6517 |
     | ELP2984 | elpidio@outlook.com   | 655-145-9938 |
     | LET4015 | leticia@yahoo.com     | 655-143-4019 |
     | LUI1076 | luis2@live.com        | 655-100-5085 |
     | HUG5441 | hugo@live.com         | 655-137-3935 |


8. Listar el login y teléfono de los usuarios con compañia telefónica UNEFON

     ```sql
     SELECT usuario,email,telefono FROM tblUsuarios WHERE compañia='UNEFON';
     ```
     | usuario | email              | telefono     |
     |---------|--------------------|--------------|
     | DAN2832 | daniel@outlook.com | 655-145-2586 |
     | BLA9739 | blas@hotmail.com   | 655-330-3871 |
     | DIA6570 | diana@live.com     | 655-143-3952 |
     | LET4015 | leticia@yahoo.com  | 655-143-4019 |
     | LUI1076 | luis2@live.com     | 655-100-5085 |

9. Listar las diferentes marcas de celular en orden alfabético descendentemente

     ```sql
     SELECT DISTINCT marca FROM tblUsuarios ORDER BY marca DESC;
     ```
     | marca      |
     |------------|
     | SONY       |
     | SAMSUNG    |
     | NOKIA      |
     | MOTOROLA   |
     | LG         |
     | BLACKBERRY |

10. Listar las diferentes compañias en orden alfabético aleatorio

      ```sql
      SELECT DISTINCT marca FROM tblUsuarios ORDER BY RAND();
      ```
     | marca      |
     |------------|
     | NOKIA      |
     | SAMSUNG    |
     | MOTOROLA   |
     | BLACKBERRY |
     | LG         |
     | SONY       |

11. Listar el login de los usuarios con nivel 0 o 2

      ```sql
      SELECT usuario,email FROM tblUsuarios WHERE nivel=0 OR nivel=2;
      ```
     | usuario | email                 |
     |---------|-----------------------|
     | BRE2271 | brenda@live.com       |
     | LUI6115 | enrique@outlook.com   |
     | DAN2832 | daniel@outlook.com    |
     | JAQ5351 | jaqueline@outlook.com |
     | ROM6520 | roman@gmail.com       |
     | BLA9739 | blas@hotmail.com      |
     | RIC8283 | ricardo@hotmail.com   |
     | VAL6882 | valentina@live.com    |
     | JUA2337 | juan@outlook.com      |
     | LET4015 | leticia@yahoo.com     |
     | HUG5441 | hugo@live.com         |

12. Calcular el saldo promedio de los usuarios que tienen teléfono marca LG

      ```sql
      SELECT AVG(saldo) AS SaldoPromedio FROM tblUsuarios WHERE marca='LG';
      ```
     | SaldoPromedio |
     |---------------|
     |            50 |

------

### Bloque 3

##### Consultas

1. Listar el login de los usuarios con nivel 1 o 3

     ```sql
     SELECT usuario,email FROM tblUsuarios WHERE nivel=1 OR nivel=3;
     ```
     | usuario | email               |
     |---------|---------------------|
     | OSC4677 | oscar@gmail.com     |
     | JOS7086 | francisco@gmail.com |
     | LUI7072 | luis@hotmail.com    |
     | JES4752 | jessica@hotmail.com |
     | DIA6570 | diana@live.com      |
     | BRE8106 | brenda2@gmail.com   |
     | LUC4982 | lucia@gmail.com     |
     | ELP2984 | elpidio@outlook.com |
     | JES9640 | jessica2@live.com   |
     | LUI1076 | luis2@live.com      |

2. Listar nombre y teléfono de los usuarios con teléfono que no sea de la marca BLACKBERRY

     ```sql
     SELECT nombre,telefono FROM tblUsuarios WHERE marca!='BLACKBERRY';
     ```
     | nombre  | telefono     |
     |---------|--------------|
     | BRENDA  | 655-330-5736 |
     | OSCAR   | 655-143-4181 |
     | JOSE    | 655-143-3922 |
     | LUIS    | 655-137-1279 |
     | LUIS    | 655-100-8260 |
     | DANIEL  | 655-145-2586 |
     | ROMAN   | 655-330-3263 |
     | BLAS    | 655-330-3871 |
     | JESSICA | 655-143-6861 |
     | DIANA   | 655-143-3952 |
     | RICARDO | 655-145-6049 |
     | BRENDA  | 655-100-1351 |
     | JUAN    | 655-100-6517 |
     | ELPIDIO | 655-145-9938 |
     | JESSICA | 655-330-5143 |
     | LUIS    | 655-100-5085 |
     | HUGO    | 655-137-3935 |

3. Listar el login de los usuarios con nivel 3

     ```sql
     SELECT usuario,email FROM tblUsuarios WHERE nivel=3;
     ```
     | usuario | email               |
     |---------|---------------------|
     | OSC4677 | oscar@gmail.com     |
     | JOS7086 | francisco@gmail.com |
     | BRE8106 | brenda2@gmail.com   |
     | LUC4982 | lucia@gmail.com     |
     | JES9640 | jessica2@live.com   |
     | LUI1076 | luis2@live.com      |

4. Listar el login de los usuarios con nivel 0

     ```sql
     SELECT usuario,email FROM tblUsuarios WHERE nivel=0;
     ```
     | usuario | email                 |
     |---------|-----------------------|
     | LUI6115 | enrique@outlook.com   |
     | DAN2832 | daniel@outlook.com    |
     | JAQ5351 | jaqueline@outlook.com |
     | BLA9739 | blas@hotmail.com      |
     | VAL6882 | valentina@live.com    |
     | JUA2337 | juan@outlook.com      |

5. Listar el login de los usuarios con nivel 1

     ```sql
     SELECT usuario,email FROM tblUsuarios WHERE nivel=1;
     ```
     | usuario | email               |
     |---------|---------------------|
     | LUI7072 | luis@hotmail.com    |
     | JES4752 | jessica@hotmail.com |
     | DIA6570 | diana@live.com      |
     | ELP2984 | elpidio@outlook.com |

6. Contar el número de usuarios por sexo

     ```sql
     SELECT sexo,COUNT(sexo) AS Cantidad FROM tblUsuarios GROUP BY sexo;
     ```
     | sexo | Cantidad |
     |------|----------|
     | M    |        9 |
     | H    |       12 |

7. Listar el login y teléfono de los usuarios con compañia telefónica AT&T

     ```sql
     SELECT usuario,email,telefono FROM tblUsuarios WHERE compañia!='At&t';
     ```
     | usuario | email                 | telefono     |
     |---------|-----------------------|--------------|
     | BRE2271 | brenda@live.com       | 655-330-5736 |
     | OSC4677 | oscar@gmail.com       | 655-143-4181 |
     | JOS7086 | francisco@gmail.com   | 655-143-3922 |
     | LUI6115 | enrique@outlook.com   | 655-137-1279 |
     | LUI7072 | luis@hotmail.com      | 655-100-8260 |
     | DAN2832 | daniel@outlook.com    | 655-145-2586 |
     | JAQ5351 | jaqueline@outlook.com | 655-330-5514 |
     | ROM6520 | roman@gmail.com       | 655-330-3263 |
     | BLA9739 | blas@hotmail.com      | 655-330-3871 |
     | JES4752 | jessica@hotmail.com   | 655-143-6861 |
     | DIA6570 | diana@live.com        | 655-143-3952 |
     | RIC8283 | ricardo@hotmail.com   | 655-145-6049 |
     | BRE8106 | brenda2@gmail.com     | 655-100-1351 |
     | LUC4982 | lucia@gmail.com       | 655-145-4992 |
     | JUA2337 | juan@outlook.com      | 655-100-6517 |
     | ELP2984 | elpidio@outlook.com   | 655-145-9938 |
     | JES9640 | jessica2@live.com     | 655-330-5143 |
     | LET4015 | leticia@yahoo.com     | 655-143-4019 |
     | LUI1076 | luis2@live.com        | 655-100-5085 |

8. Listar las diferentes compañias en orden alfabético descendentemente

     ```sql
     SELECT DISTINCT compañia FROM tblUsuarios ORDER BY compañia DESC;
     ```
     | compañia  |
     |-----------|
     | UNEFON    |
     | TELCEL    |
     | NEXTEL    |
     | MOVISTAR  |
     | IUSACELL  |
     | AXEL      |
     | AT&T      |
9. Listar el logn de los usuarios inactivos

     ```sql
     SELECT usuario,email FROM tblUsuarios WHERE activo=0;
     ```
     | usuario | email              |
     |---------|--------------------|
     | LUI7072 | luis@hotmail.com   |
     | DIA6570 | diana@live.com     |
     | VAL6882 | valentina@live.com |
     | JUA2337 | juan@outlook.com   |

10. Listar los números de teléfono sin saldo

      ```sql
      SELECT telefono FROM tblUsuarios WHERE saldo=0;
      ```
     | telefono     |
     |--------------|
     | 655-143-4181 |
     | 655-330-5514 |
     | 655-145-4992 |
     | 655-100-6517 |

11. Calcular el saldo mínimo de los usuarios de sexo “Hombre”

      ```sql
      SELECT MIN(saldo) FROM tblUsuarios WHERE sexo='H';
      ```
     | MIN(saldo) |
     |------------|
     |          0 |

12. Listar los números de teléfono con saldo mayor a 300

      ```sql
      SELECT telefono FROM tblUsuarios WHERE saldo>300;
      ```
     | telefono     |
     |--------------|
     | 655-143-6861 |
     | 655-145-9938 |
     | 655-137-3935 |

------

### Bloque 4

##### Consultas

1. Contar el número de usuarios por marca de teléfono

     ```sql
     SELECT marca,COUNT(marca) AS Cantidad FROM tblUsuarios GROUP BY marca;
     ```
     | marca      | Cantidad |
     |------------|----------|
     | SAMSUNG    |        4 |
     | LG         |        3 |
     | NOKIA      |        2 |
     | SONY       |        4 |
     | BLACKBERRY |        4 |
     | MOTOROLA   |        4 |

2. Listar nombre y teléfono de los usuarios con teléfono que no sea de la marca LG

     ```sql
     SELECT nombre,telefono FROM tblUsuarios WHERE marca!='LG';
     ```
     | nombre    | telefono     |
     |-----------|--------------|
     | BRENDA    | 655-330-5736 |
     | JOSE      | 655-143-3922 |
     | LUIS      | 655-137-1279 |
     | LUIS      | 655-100-8260 |
     | DANIEL    | 655-145-2586 |
     | JAQUELINE | 655-330-5514 |
     | JESSICA   | 655-143-6861 |
     | DIANA     | 655-143-3952 |
     | RICARDO   | 655-145-6049 |
     | VALENTINA | 655-137-4253 |
     | BRENDA    | 655-100-1351 |
     | LUCIA     | 655-145-4992 |
     | JUAN      | 655-100-6517 |
     | ELPIDIO   | 655-145-9938 |
     | JESSICA   | 655-330-5143 |
     | LETICIA   | 655-143-4019 |
     | LUIS      | 655-100-5085 |
     | HUGO      | 655-137-3935 |

3. Listar las diferentes compañias en orden alfabético ascendentemente

     ```sql
     SELECT DISTINCT compañia FROM tblUsuarios ORDER BY compañia ASC;
     ```
     | compañia  |
     |-----------|
     | AT&T      |
     | AXEL      |
     | IUSACELL  |
     | MOVISTAR  |
     | NEXTEL    |
     | TELCEL    |
     | UNEFON    |
4. Calcular la suma de los saldos de los usuarios de la compañia telefónica UNEFON

     ```sql
     SELECT SUM(saldo) FROM tblUsuarios WHERE compañia='UNEFON';
     ```
     | SUM(saldo) |
     |------------|
     |        550 |

5. Mostrar el email de los usuarios que usan hotmail

     ```sql
     SELECT email FROM tblUsuarios WHERE email LIKE '%@hotmail.com'
     ```
     | email               |
     |---------------------|
     | luis@hotmail.com    |
     | blas@hotmail.com    |
     | jessica@hotmail.com |
     | ricardo@hotmail.com |

6. Listar los nombres de los usuarios sin saldo o inactivos

     ```sql
     SELECT nombre FROM tblUsuarios WHERE saldo=0 OR activo=0;
     ```
     | nombre    |
     |-----------|
     | OSCAR     |
     | LUIS      |
     | JAQUELINE |
     | DIANA     |
     | VALENTINA |
     | LUCIA     |
     | JUAN      |
7. Listar el login y teléfono de los usuarios con compañia telefónicaIUSACELL o TELCEL

     ```sql
     SELECT usuario,email,telefono FROM tblUsuarios WHERE compañia='IUSACELL' OR compañia='TELCEL';
     ```
     | usuario | email               | telefono     |
     |---------|---------------------|--------------|
     | BRE2271 | brenda@live.com     | 655-330-5736 |
     | OSC4677 | oscar@gmail.com     | 655-143-4181 |
     | LUI6115 | enrique@outlook.com | 655-137-1279 |
     | LUI7072 | luis@hotmail.com    | 655-100-8260 |
     | ROM6520 | roman@gmail.com     | 655-330-3263 |
     | JES4752 | jessica@hotmail.com | 655-143-6861 |
     | RIC8283 | ricardo@hotmail.com | 655-145-6049 |
     | LUC4982 | lucia@gmail.com     | 655-145-4992 |
     | JES9640 | jessica2@live.com   | 655-330-5143 |

8. Listar las diferentes marcas de celular en orden alfabético ascendentemente

     ```sql
     SELECT DISTINCT marca FROM tblUsuarios ORDER BY marca ASC;
     ```
     | marca      |
     |------------|
     | BLACKBERRY |
     | LG         |
     | MOTOROLA   |
     | NOKIA      |
     | SAMSUNG    |
     | SONY       |

9. Listar las diferentes marcas de celular en orden alfabético aleatorio

     ```sql
     SELECT marca FROM tblUsuarios GROUP BY marca ORDER BY RAND();
     ```
     | marca      |
     |------------|
     | SAMSUNG    |
     | MOTOROLA   |
     | BLACKBERRY |
     | LG         |
     | NOKIA      |
     | SONY       |

10. Listar el login y teléfono de los usuarios con compañia telefónica IUSACELL o UNEFON

      ```sql
      SELECT usuario,email,telefono FROM tblUsuarios WHERE compañia='IUSACELL' OR compañia='UNEFON';
      ```
     | usuario | email               | telefono     |
     |---------|---------------------|--------------|
     | BRE2271 | brenda@live.com     | 655-330-5736 |
     | LUI7072 | luis@hotmail.com    | 655-100-8260 |
     | DAN2832 | daniel@outlook.com  | 655-145-2586 |
     | ROM6520 | roman@gmail.com     | 655-330-3263 |
     | BLA9739 | blas@hotmail.com    | 655-330-3871 |
     | DIA6570 | diana@live.com      | 655-143-3952 |
     | RIC8283 | ricardo@hotmail.com | 655-145-6049 |
     | LUC4982 | lucia@gmail.com     | 655-145-4992 |
     | JES9640 | jessica2@live.com   | 655-330-5143 |
     | LET4015 | leticia@yahoo.com   | 655-143-4019 |
     | LUI1076 | luis2@live.com      | 655-100-5085 |

11. Listar nombre y teléfono de los usuarios con teléfono que no sea de la marca MOTOROLA o NOKIA

      ```sql
      SELECT usuario,email,telefono FROM tblUsuarios WHERE marca!='MOTOROLA' AND marca!='NOKIA';
      ```
     | usuario | email                 | telefono     |
     |---------|-----------------------|--------------|
     | BRE2271 | brenda@live.com       | 655-330-5736 |
     | OSC4677 | oscar@gmail.com       | 655-143-4181 |
     | LUI6115 | enrique@outlook.com   | 655-137-1279 |
     | DAN2832 | daniel@outlook.com    | 655-145-2586 |
     | JAQ5351 | jaqueline@outlook.com | 655-330-5514 |
     | ROM6520 | roman@gmail.com       | 655-330-3263 |
     | BLA9739 | blas@hotmail.com      | 655-330-3871 |
     | JES4752 | jessica@hotmail.com   | 655-143-6861 |
     | DIA6570 | diana@live.com        | 655-143-3952 |
     | VAL6882 | valentina@live.com    | 655-137-4253 |
     | LUC4982 | lucia@gmail.com       | 655-145-4992 |
     | JUA2337 | juan@outlook.com      | 655-100-6517 |
     | JES9640 | jessica2@live.com     | 655-330-5143 |
     | LET4015 | leticia@yahoo.com     | 655-143-4019 |
     | LUI1076 | luis2@live.com        | 655-100-5085 |

12. Calcular la suma de los saldos de los usuarios de la compañia telefónica TELCEL

      ```sql
      SELECT SUM(saldo) FROM tblUsuarios WHERE compañoa='TELCEL';
      ```
     | SUM(saldo) |
     |------------|
     |        550 |
