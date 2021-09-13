**Introducción**

El objetivo del presente trabajo es entender y familiarizarse con la estructura del lenguaje SQL tanto como sus sentencias, para así aplicarlo a la
creación de esquemas entidad relación. Además, se espera crear un pequeño documento donde se establece un estándar para el nombre de entidades, atributos, 
tipos de datos, llaves primarias y llaves secundarias. Por ende, se realizó una lectura previa al manual de MySQL 8.0 y se extrajo la información pertinente, 
también se tomó como inspiración parcial distintos estándares ubicados en la web, estos se encuentran referenciados en la bibliografía.


**Justificación**

Entre las ventajas de mi esquema podemos enumerar:
	->_Facilidad y simplicidad:_ En el presente esquema se encuentra redactado de forma simple y concisa, pues la idea es que el lector pueda memorizar o hacer uso del esquema 
fácilmente. Pues, se hace énfasis en los objetos, keywords, restricciones y palabras reservadas que más son utilizadas.
	->_Claridad y reducción de errores:_ En el presente estándar se hace un énfasis en el uso de mayúsculas, minúsculas, sangría y snake_case. Por un lado,
el que se escriba en mayúsculas nos permite dar importancia a las palabras claves, palabras reservadas y restricciones que se están usando en las sentencias SQL. 
Esto debería de reducir el margen de cometer un error al redactar dichas sentencias.
	->_Versatilidad:_ De la forma que se ha redactado el siguiente esquema se toma en cuenta que se pueden añadir modificaciones futuras. A su vez, este esquema para nombres
puede ser utilizado en ingles tanto como en español, pues se ha limitado el uso de tildes y de la letra ñ.

Y, sin embargo, la mayor limitación de mi esquema es su simplicidad. Mi esquema no aborda aún todas las posibles palabras claves, palabras reservadas y restricciones con su 
respectivas sintaxis. Lo que podría contradicciones o incertidumbre de crear esquemas de bases de datos con sentencias SQL que no se ejemplifiquen en este documento. Esto ultimo
es debido a mi limitación de tiempo, así como mi falta de experiencia con SQL. Por ende, a futuro se espera agregar aún más contenido de relevancia a este esquema tanto como a mi
conocimiento de SQL y bases de datos.

	

**Table_of_Contents**

1.[Entidades](#entidades)

2.[Atributos](#atributos)

3.[Tipos de Datos](#data_type)

4.[Llaves Primarias y Llaves Foraneas](#keys)

5.[Bibliografía](#bibliografia)


**Entidades** <a name="entidades"></a>

Para la definición de tablas y demás Schema Objects es preferible escribir sus identificadores en mayúscula.
	En vez de escribir **table** se escribe **TABLE**.
	
A su vez, para dar nombre a una tabla es recomendable evitar nombres confusos, para ello debemos omitir el uso de abreviaturas, 
caracteres especiales (como ?/!%$&), inclusive tildes y la letra ¨Ñ¨. En nuestro caso vamos a empezar siempre con **UNA** mayúscula al inicio del
nombre, vamos a hacer uso de **Snake Case** (utilizar _ en vez de espacios ¨ ¨) y además hacer uso de plurales (siempre que sea lógico con el 
objetivo de tener nombres únicos e identificables fácilmente.
	En vez de escribir **tarjetaCredito** se escribe **Tarjetas_Credito**.

Durante la creación de una entidad o tabla la keyword _create_ se va a escribir siempre en mayúscula.
	En vez de escribir **create** se escribe **CREATE**.
	
Y por último, para alterar una tabla la keyword _alter_ se va a escribir siempre en mayúscula y antes de las siguientes sentencias SQL que 
modifiquen la tabla se va a usar sangria.
	En vez de escribir **alter** se escribe **ALTER**.

_NOTA:_El resto de keywords y palabras reservadas tambien se van a escribir siempre en mayúscula.

_Ejemplo completo:_

	CREATE TABLE Deluxe_Rooms(
		room_id INT PRIMARY KEY NOT NULL,
		price INT NOT NULL,
		floor INT NOT NULL,
		bed_num INT NOT NULL,
		location VARCHAR(30)
		);
		
	ALTER TABLE Deluxe_Rooms
		ADD tv_num INT NOT NULL;


**Atributos** <a name="atributos"></a>

Para la definicion de atributos es escensial evitar que su nombre sea igual o muy similar al de la tabla.
	Si la tabla se llama Modelos, en vez de escribir **Modelo** es preferible escribir **modelo_id**.
	
El nombre del atributo se va a escribir siempre en minúsculas, en singular y si hay espacios se usa **Snake Case**.
	En vez de escribir **LibrosID** se escribe **libro_id**.
	
En el caso de añadir una nueva o borrar una columna las keywords **siempre** se escriben en mayúscula.
	En vez de escribir **add** se escribe **ADD** y en vez de **drop column** se escribe **DROP COLUMN**.
	
_Ejemplo completo:_

	CREATE TABLE Carrocerias(
		modelo_id INT PRIMARY KEY NOT NULL,
		modelo_name VARCHAR(30) NOT NULL,
		precio INT NOT NULL,
		color VARCHAR(30) NOT NULL
		);
	
	ALTER TABLE Carrocerias(
		ADD unidades INT,
		DROP COLUMN color;

_NOTA:_Para los atributos existen una serie de sufijos facilmente reconosibles, si bien su uso no es recomendado pueden llegar
a ser utiles en casos extremos.
	Algunos ejemplos son:
	 -> **_id** se utiliza para indicar que es un identificador unico o una llave primaria.
	 -> **_name** se utiliza para indicar que es un nombre de algun tipo.
	 -> **_total** se utiliza para indicar que el valor corresponde al total o la suma de un numero de valores.
	 -> **_status** se utiliza para indicar que el atributo representa un estado booleano de la identidad.
	
	
**Tipos de datos** <a name="data_type"></a>

Al definir un atributo, el tipo de dato siempre se va escribir en mayúscula.
	En vez de escribir **int** se va a escribir **INT**.
	
Para trabajar con numeros enteros se va hacer uso de **INT** siempre, cuando se trabaje con numeros muy grandes podemos varia el tipo.
	En caso de que el numero con el que vamos a trabajar fuese mayor a _2147483647_ podemos utilizar un **BIGINT**.
	
Para trabajar con cadenas de caracteres se hace uso de **VARCHAR(30)**, excepto cuando el string ocupe mas de 30 bytes.
	Si la cadena de caracteres ocupase mas de 30 bytes podriamos ir incrementando hasta que tengamos una cantidad adecuada, ejemplo **VARCHAR(50)**.
	
A la hora de usar constraints (restricciones en español), como _not null_, se va a escribir siempre en mayúscula.
	En vez de escribir **not null** se escribe **NOT NULL**.
	
_Ejemplo Completo:_

	CREATE TABLE Bodegas(
		bodega_id INT PRIMARY KEY NOT NULL
		address VARCHAR(250) NOT NULL,
		nombre VARCHAR(30) NOT NULL,
		productos_total BIGINT NOT NULL
	);
	
		

**Llaves Primarias y Llaves Foraneas** <a name="keys"></a>

Se espera que el nombre de una llave primaria sea único y distinguible. Este debe ser todo en minúscula y de ser necesario en formato **snake_case**.
	En vez de escribir **EmpleadoID** se escribe **empleado_id**.

A la hora de identificar un atributo como llave primaria la restriccion _primary key_ debe ir siempre en mayúscula e ir después del tipo de atributo.
	En vez de escribir **int primary key** se escribe **INT PRIMARY KEY**.
	
Se espera que la definición de la llave primaria de la tabla se encuentre justo después de la sentencia _CREATE TABLE_.
	Ejemplo:
	
		CREATE TABLE Telas(
			tela_id INT PRIMARY KEY NOT NULL,
			unidades INT NOT NULL
		);
		
Por su parte, a la hora de especificar una o más llaves foraneas su nombre debe ser escrito en minúscula y usar formato **snake_case**.
	En vez de escribir **codigoLibro** se escribe **codigo_libro**.
	
Al especificar una o más llaves primaria la restricción _foreing key ( ) references tables_name( )_ debe ir todo en mayúscula y en formato **snake_case** en los nombres
de los atributos.
	En vez de escribir **foreing key (seguroID) references SeguroCaja(seguroID)** vamos a escribir **FOREING KEY (seguro_id) REFERENCES Seguros_caja(seguro_id)**.
	
_Ejemplo Completo:_

	CREATE TABLE Muebles(
		mueble_id VARCHAR(30) PRIMARY KEY NOT NULL,
		asientos_num INT NOT NULL,
		largo INT NOT NULL,
		ancho INT NOT NULL
		);
		
	)
	CREATE TABLE Combos(
		juego_name VARCHAR(30) PRIMARY KEY NOT NULL,
		FOREING KEY (mueble_id) REFERENCES Seguros_caja(mueble_id)
		precio INT NOT NULL
	);


**Bibliografía** <a name="bibliografia"></a>

Oracle. (2021, 10 de septiembre). _MySQL 8.0 Reference Manual_. Consultado el 11 de septiembre del 2021. https://dev.mysql.com/doc/refman/8.0/en/

Calbimonte, D. (2015, 19 de junio). _Estándares de formato SQL – Mayúsculas y minúsculas, Sangría, Comentarios, Paréntesis_. Consultado el 11 de septiembre del 2021. https://solutioncenter.apexsql.com/es/estandares-de-formato-sql-mayusculas-y-minusculas-sangria-comentarios-parentesis/

Holywell, S.(s. f.). _SQL Style Guide_. Consultado el 11 de septiembre del 2021. https://www.sqlstyle.guide/#column-data-types
