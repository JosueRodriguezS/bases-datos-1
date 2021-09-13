**Introducción**

En el siguiente trabajo se pretende crear un pequeño documento que establesca un estandar a utilizar en SQL 

**Justificación**

**Table_of_Contents**

[Entidades](#entidades)

**Entidades** <a name="entidades"></a>

Para la definición de tablas y demás Schema Objects es preferible escribir sus identificadores en mayúscula.
	En vez de escribir **table** se escribe **TABLE**.
	
A su vez, para dar nombre a una tabla es recomendable evitar nombres confusos, para ello debemos omitir el uso de abreviaturas 
y caracteres especiales (como ?/!%$&) e inclusive tildes. En nuestro caso vamos a empezar siempre con **UNA** mayúscula al inicio del
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

**Atributos**

Para la definicion de atributos es escensial evitar que su nombre sea igual o muy similar al de la tabla.
	Si la tabla se llama Modelos, en vez de escribir **Modelo** es preferible escribir **modelo_id**.
	
El nombre del atributo se va a escribir siempre en minúsculas, en singular y si hay espacios se usa **Snake Case**.
	En vez de escribir **LibrosID** se escribe **libro_id**.
	
En el caso de añadir una nueva o borrar una columna las keywords **siempre** se escriben en mayúscula.
	En vez de escribir **add** se escribe **ADD** y en vez de **drop column** se escribe **DROP COLUMN**.
	
_Ejemplo completo:_

	CREATE TABLE Carrocerias(
		modelo_id PRIMARY KEY NOT NULL,
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
	 
**Tipos de datos**

Al definir un atributo, el tipo de dato siempre se va escribir en mayúscula.
	En vez de escribir **int** se va a escribir **INT**.
	
Para trabajar con numeros enteros se va hacer uso de **INT** siempre y cuando no se trabaje con numeros muy grandes.
	En caso de que el numero con el que vamos a trabajar fuese mayor a _2147483647_ podemos utilizar un **BIGINT**.
	
Para trabajar con cadenas de caracteres se hace uso de **VARCHAR(30)**, excepto cuando el string ocupe mas de 30 bytes.
	Si la cadena de caracteres ocupase mas de 30 bytes podriamos ir incrementando hasta que tengamos una cantidad adecuada, ejemplo **VARCHAR(50)**.
	
A la hora de usar constraints (restricciones en español), como _not null_, se va a escribir siempre en mayúscula.


**Llaves Primarias**

**Llaves Foraneas**

**Bibliografía**
