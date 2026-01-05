***Que es una base de datos***
Una base de datos es un sistema organizado para almacenar, gestionar y recuperar información de forma eficiente. Hablamos de una base de datos relacional cuando organiza la información en tablas con filas y columnas.

***Lenguaje SQL**
Para interactuar con esta base de datos usamos un lenguaje especifico SQL (Structured Query Lenguage) Esto nos permitira realizar operaciones como:

- Consultar datos
- Insertar nueva información
- Actualizar registros existentes
- Eliminar datos innecesarios
- Crear o modificar la estructura de las tablas

#### **Los 3 mundos de las bases de datos**
Para trabajar correctamente con bases de datos, es fundamental saber distinguir entre tres ámbitos o "mundos" que permiten transformar la realidad en un sistema estructurado

1. **Mundo real**
	Incluye todas las **personas, objetos, lugares o hechos reales** que nos interesan. 
		**En una biblioteca, el mundo real incluye** los libros físicos, las personas que van a la biblioteca, los bibliotecarios, los prestamos de libros que se realizan.... 
2. **Mundo conceptual**
	Es el conjunto de información o conocimiento que tenemos gracias a la observación de la parte del mundo real que nos interesa. 
		Es cómo **entendemos y organizamos la información** sobre esa realidad. Del ejemplo anterior de la biblioteca, el mundo conceptual seria: 
			Un libro tiene titulo, autor, ISBN, editorial.
			Un usuario tiene nombre, apellidos, correo, teléfono, DNI 
			Un usuario puede pedir prestado varios libros
			Un libro puede estar prestado o disponible
3. **Mundo de las representaciones**
	Es la **forma en la que el mundo conceptual se guarda en el ordenador**. En esta parte es en la que se ve las tablas, campos y registros. Por ejemplo una tabla llamada clientes, otra tabla llamada productos. Los datos se guardan en filas y columnas.

#### **Modelo de las bases de datos**
Para representar la información del **mundo conceptual** en el **mundo de las representaciones**, se utilizan distintos **modelos de bases de datos**. Un modelo define **cómo se organizan los datos** y **cómo se relacionan entre ellos**.

1. ***Modelo jerárquico***
	El modelo jerárquico organiza la información en una **estructura de árbol invertido**. Cada elemento tiene **un solo padre**, pero puede tener **varios hijos**. Existe un elemento principal llamado **raíz**, y los elementos finales se llaman **hojas**.

Es sencillo, pero **poco flexible**, ya que un elemento no puede depender de más de un padre.

```
Biblioteca
 ├── Sección: Novela
 │    ├── Libro: Don Quijote
 │    └── Libro: La sombra del viento
 └── Sección: Ciencia
      ├── Libro: Breve historia del tiempo
      └── Libro: El gen egoísta
```

2. ***Modelo en red***
	El modelo en red es similar al jerárquico, pero **más flexible**. Permite que un elemento tenga **más de un padre**, lo que facilita representar relaciones más complejas.

```
Sección: Historia ──┐
                    ├── Libro: Los pilares de la Tierra
                    │
Sección: Novela ────┘
```

3. ***Modelo relacional***
	El **modelo relacional** representa los datos mediante **tablas**, con **filas y columnas**. Cada **tabla** representa una entidad. Las **relaciones** se hacen mediante **claves** (DNI, ISBN)
###### Tabla `Libros`

|ISBN|Título|Autor|Editorial|Estado|
|---|---|---|---|---|
|123|Don Quijote|Cervantes|Anaya|Disponible|
|456|Breve historia del tiempo|Hawking|Crítica|Prestado|
###### Tabla `Usuarios`

|DNI|Nombre|Apellidos|Teléfono|
|---|---|---|---|
|111A|Ana|Pérez|600123456|

4. **Modelo relacional con objetos / orientado a objetos**
	 Este modelo es una extensión que permite usar **objetos complejos** dentro de las tablas, similares a la programación orientada a objetos. 
###### Tabla `Libros`

|ISBN|Título|Autor (objeto)|Portada|
|---|---|---|---|
|789|El nombre de la rosa|{Umberto Eco, italiano, 1932}|imagen.jpg|
El campo **Autor** no es solo texto, sino un **objeto** con varios atributos. Se pueden almacenar **imágenes**, **documentos PDF** o estructuras complejas. Es más complejo y menos usado que el modelo relacional clásico.

#### ***Ventajas de un SGBD.***

Un SGBD ***(Sistema de Gestión de Bases de Datos)*** es el software que permite crear, organizar y gestionar bases de datos de manera eficiente. Aporta varios veneficios a la hora de trabajar con información. 
- Gestión estructurada de datos
- Control de acceso y seguridad
- Manipulación avanzada de datos
- Gestión de transacciones
- Escalabilidad y eficiencia
- Automatización y mantenimiento
- Interfaces graficas y herramientas de gestión

#### ***Modelo entidad relación (MER)***
El **MER** es un modelo conceptual, usado para representar la información de manera **abstracta** antes de implementarla en una base de datos. Se centra en **entidades**, **atributos** y **relaciones**.

1. **Entidades**
Las entidades son los objetos principales sobre los que se deben recoger información. 
![[Pasted image 20260105013059.png]]

2. **Atributos**
Se utilizan para detallar propiedades a las entidades. Una entidad puede tener varios atributos. Si uno o varios atributos identifican a una entidad, este deberá estar subrayado. Ejemplo vamos a registrar en nuestra base de datos nuestros empleados, recopilaremos DNI, nombre, correo y puesto. 

![[Pasted image 20260105013021.png]]

3. **Atributos compuestos**
Son atributos que están fermentados por otros atributos. Se utilizan a nivel organizativo. 
![[Pasted image 20260105013218.png]]

4. **Atributos multivaluados**
Son aquellos atributos que pueden tener más de un valor. Por ejemplo teléfono. 
![[Pasted image 20260105013311.png]]

5. **Atributos calculados o derivados**
Se derivan de otros atributos, no se almacenan físicamente en la entidad. Por ejemplo edad, se calculara automáticamente en base la fecha de nacimiento, con esto evitamos tenerlo desactualizado. 
![[Pasted image 20260105013508.png]]

6. **Relaciones**
Permiten vincular 2 o más entidades indicando como se relacionan entre ellas. Dentro de la relación se usa un verbo que representa la relación entre ambas. Por ejemplo queremos registrar empleados en una base de datos, recopilaremos su **DNI, nombre y puesto**. De los departamentos queremos saber su código y su nombre.  Cada empleado **pertenece** a un departamento.
![[Pasted image 20260105013838.png]]

7. **Cardinalidad**
Representa un numero de instancia que se relaciona con la otra entidad. Debemos representar el mínimo y el máximo de cada una de las entidades. (Los valores que se usan son 0, 1 y N (Varios)) Cuando tengamos ambas, se coge el máximo de cada uno y se obtiene la cardinalidad. 
- Uno a uno (1:1)
- Uno a muchos (1:N)
- Muchos a muchos (N:M)

Con el ejemplo anterior damos el caso que cada empleado pertenece a un departamento
![[Pasted image 20260105014345.png]]

En caso de que cada empleado pertenezca a un departamento y hay varios empleados en un departamento.
![[Pasted image 20260105014506.png]]

En el caso de que cada empleado pertenece a uno o varios departamentos.
![[Pasted image 20260105014840.png]]

8. **Entidades débiles**
Son aquellas que dependen de una entidad fuerte. Existen dos tipos de relaciones: Identificación y existencia. 

- Identificación: 
	 La entidad débil depende de la entidad fuerte para identificarse. La clave de la entidad débil esta formada por la suya y de la entidad fuerte. Siendo ambas claves identificativas. 

Por ejemplo queremos registrar un empleado en la base de datos, su DNI, nombre y puesto. Cada empleado tiene un horario con una hora de entrada y salida. 
![[Pasted image 20260105015915.png]]

- Existencia
	La entidad débil depende de la entidad fuerte para existir, sin ella no tiene sentido su existencia. La clave de de la entidad fuerte a diferencia de la clave entidad débil no la identifica, es decir, la clave de la entidad fuerte únicamente se identifica por la suya. 

Por ejemplo queremos registrar en nuestra base de datos empleados, con su DNI, nombre y puesto. Cada empleado tiene un puesto donde trabaja, queremos saber en que planta y sala se encuentra
![[Pasted image 20260105020419.png]]

9. **Relación reflexiva**
Una entidad puede relacionarse a si misma, siendo el inicio y el fin. Actúa como una relación más. Por ejemplo queremos registrar un empleado en nuestra base de datos, su DNI, nombre y puesto. Un empleado puede tener a su cargo a varios empleados y un empleado solo puede tener un superior.
![[Pasted image 20260105020816.png]]
10. **Generalización / Especialización** 
La generalización y especialización consisten dividir una entidad en diferentes entidades que comparten atributos. En una relación jerárquica, cuanto mas hacia abajo, mas se especializa, y cuanto mas hacia arriba mas se generaliza. Las entidades hijas pueden tener sus propios atributos. 

Se clasifican en dos criterios, exclusividad y cobertura.
1. **Exclusividad**: Determina si una entidad puede pertenecer a mas de una entidad hija o no
	1. **Exclusiva**: Una entidad solo puede pertenecer a una entidad hija especifica.
	2. **Solapada**: Una entidad puede pertenecer a una o mas entidades hijas. 
2. **Cobertura**: Si todas las entidades de la entidad padre están representadas en las entidades hijas o no.
	1. **Total**: Todas las entidades de la entidad padre están cubiertas en las entidades hijas. 
	2. **Parcial**: Todas las entidades de la entidad padre no están cubiertas en las entidades hijas

Combinando ambos criterios podemos tener diferentes tipos de generalización.
- **Solapada y parcial**
	Una entidad puede pertenecer a mas de una entidad hija. Bo todas las entidades padre estan representadas en las entidades hijas. 
		**Ejemplo**: Queremos registrar empleados en nuestra base de datos con su DNI y nombre. Los empleados pueden tener el puesto de administrativos o directivos. Un administrativo puede ser un directivo y viceversa. De los administrativos queremos saber los años de experiencia.
		![[Pasted image 20260105022534.png]]
- **Solapada y total**
	- Una entidad puede pertenecer a mas de una entidad hija. Todas las entidades de la entidad padre están representadas en las entidades hijas. 
		**Ejemplo:** Queremos registrar empleados en nuestra base de datos con su DNI y nombre. Los empleados solo pueden tener el puesto de administrativos o directivos. Un administrativo puede ser un directivo y viceversa. De los administrativos queremos saber los años de experiencia.
		![[Pasted image 20260105023016.png]]
- **Exclusiva y parcial**
	- Una entidad solo puede pertenecer a una entidad hija. No todas las entidades de la entidad padre están representadas en las entidades hijas. 
		**Ejemplo:** Queremos registrar empleados en nuestra base de datos con su DNI y nombre. Los empleados pueden tener el puesto de administrativos o directivos. Un administrativo no puede ser un directivo y viceversa. De los administrativos queremos saber los años de experiencia. 
		![[Pasted image 20260105023315.png]]
- **Exclusiva y total**
	- Una entidad solo puede pertenecer a una entidad hija. Todas las entidades de la entidad padre están representadas en la entidades hija. 
		**Ejemplo:** Queremos registrar empleados en nuestra base de datos con su DNI y nombre. Los empleados solo pueden tener el puesto de administrativos y director. Un administrativo no puede ser directivo y viceversa. De los administrativos queremos saber los años de experiencia. 
		![[Pasted image 20260105023756.png]]


# Modelo Relacional (MR)
Es la **implementación lógica** del MER en tablas de base de datos relacional. Aquí ya hablamos de **tablas**, **columnas**, **llaves primarias** y **foráneas**.

**Transformación MER → MR:**
1. Cada **entidad** se convierte en una **tabla**.
2. Cada **atributo** se convierte en una **columna**.
3. La **clave primaria** del MER se mantiene como **PK** en la tabla.
4. Las **relaciones**:
	- **1:1** → Se puede incorporar la PK de una entidad como FK en la otra
	- **1:N** → La PK de la entidad “1” se convierte en FK en la entidad “N”.
	- **N:M** → Se crea una **tabla intermedia** con las PKs de ambas entidades como FKs y, a menudo, como PK compuesta.

#### **Relaciones 1:1**
En las relaciones 1:1 se pueden presentar 3 casos a la hora de realizar la transformación. 
- Caso 1:
	Si ambas entidades tienen cardinalidad 1:1. Fusionaremos ambas entidades en una única tabla. La clave primaria puede cualquiera de las dos. 
	![[Pasted image 20260105030215.png]]
- Caso 2:
	Una de las entidades tiene cardinalidad 0:1 y otra 1:1. En este caso cada entidad pasara a ser una tabla, la entidad 1:! propagará la clave primaria a la entidad 0:1, de este modo se convertirá en clave foránea (FK) 
	![[Pasted image 20260105030551.png]]
- Caso 3:
	Si ambas entidades obtienen una cardinalidad 0:1 la relación también se transforma en una tabla. Teniendo como clave primaria la concatenación de las claves primarias de las entidades asociadas que ademas tambien seran foraneas (FK)
	![[Pasted image 20260105031126.png]]

#### **Relaciones 1:N**
Cuando la relación es 1:N debemos mirar el mínimo que tiene esa cardinalidad que tiene como máximo el 1. Pueden existir 2 casos. 
- Caso 1:
	Si vemos que hay una cardinalidad 1:1 entonces la relación no se transforma en una tabla. Se propaga la clave primaria de la entidad con cardinalidad máximo 1 a la entidad con cardinalidad máxima N pasando a ser **solo foránea (FK)**. Además los atributos de la relación pasaran a la entidad con cardinalidad máxima N. 
	![[Pasted image 20260105032043.png]]
- Caso 2:
	Si la cardinalidad es 0:1 entonces la relación si se transforma en una tabla. Su clave primaria será la misma que la entidad con cardinalidad máxima N, pasando a ser **también foránea (FK).** Los atributos que tenga la relación también pasan a la tabla. Y la clave primaria de la 
	entidad cuyo cardinalidad máxima es 1 pasa a ser clave foránea en la nueva tabla. 
	![[Pasted image 20260105032536.png]]
#### **Relaciones N:M**
- Cuando la relación entre dos entidades es N:M, tendremos que pasar la relación como una nueva tabla. Esta tabla, obtendrá como clave primaria la concatenación de ambas claves primarias de las entidades asociadas, además la clave primaria también será foránea en la nueva tabla.
  ![[Pasted image 20260105033252.png]]
