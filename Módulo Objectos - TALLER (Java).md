# Módulo Objectos - TALLER (Java)

Created: September 18, 2024 9:08 PM
Clase: TALLER
Tipo: Curso
Reviewed: No

<aside>
📌 **RESUMEN:**

</aside>

## Guía de Estudio:

- Java
    
    Operadores
    
    Libreria (Paquete de Lectura)
    
    Estructuras de control
    
    Arreglos (vectores)
    
    Matrices
    

### **Programación Orientada a Objetos en JAVA**

### **Caracteristicas**

**1)  Java es un lenguaje de propósito general.**

**2) Permite generar aplicaciones multiplataforma.**

**3) Plataforma Java**

- Plataforma de desarollo : ***JDK***
- Plataforma de Ejecucion: ***JRE***

### **Programa principal**

**1) *Main* = "Programa principal". *{ }* delimita el cuerpo**

**2) Sentencias de codigo separado por punto y coma *( ; )***

**3) Se recomienda identar el codigo para facilitar su lectura.**

**4) Comentarios :**

- De lineas múltiples `/* Esto es un comentario */`
- De linea única `//Esto es un comentario`

**5) Case-sensitive(Sensible a las mayúsculas y minúsculas)**

### **Declaracion de variables**

**1) Se declaran en la zona del codigo**

- `Tipo nombre Variable;` (Opcional: dar valor inicial)

**2) Convención de nombres: Comenzar con minúscula, luego cada palabra en mayúscula (CamelCase)**

**3) Asignación: `nombreVariable = valor;`**

**4) Tipos primitivos: La variable almacena un valor**

| Tipo Primitivo | Ejemplo |
| --- | --- |
| Boolean | true false |
| Char | 'a' '0' |
| int | 102 |
| double | 123,4 |

**5) String para manipular cadenas. Ejemplo "esto es un string"**

**Manipulación de variables**

| **Operadores aritmeticos (Tipos de datos numericos)**
`+ Suma`
`- Resta`
`* Multiplicación`
`/ División`
`% Resto` | **Operadores unarios aritmeticos (Tipos de datos numericos)**
`++ (operador de ingremento)`
`-- (operador de decremento)` |
| --- | --- |
| **Operadores Relacionales (Tipos de datos primitivos)**
`== Igual`
`!= Distinto`
`> Mayor`
`>= Mayor Igual`
`< Menor`
`<= Menor Igual` | **Operadores condicionales**
`&& AND`
`|| OR`
`! NOT`
**Operador de concatenación para String**
`+ Operador de concatenación de Strings` |

### **Libreria “Paquete de lectura”**

```java
package practica1;
/* READ */
import PaqueteLectura.Lector; 	

public class Pruebas {
    public static void main(String[] args) {
    String nombre = Lector.leerString();   
    boolean trabaja = Lector.leerBoolean();
    int edad = Lector.leerInt();   
    double sueldo = Lector.leerDouble();   
        
    System.out.println("N:" + nombre + " T:" + trabaja + 
    " E:" + edad + " S:" + sueldo );
    }
}
```

```java
package practica1;
/* GENERAR NÚMEROS ALEATORIOS */
import PaqueteLectura.GeneradorAleatorio;

public class Pruebas 
{
 public static void main(String[] args) {
 GeneradorAleatorio.iniciar();     //inicia el generador aleatorio
 int valor1 = GeneradorAleatorio.generarInt(10);  //genera un int entre 0 y 9
 double valor2 = GeneradorAleatorio.generarDouble(10); //genera un double entre 0 y 9
 boolean valor3 = GeneradorAleatorio.generarBoolean(); //genera un boolean
 String valor4= GeneradorAleatorio.generarString(4); //genera un string de long. 4
  }
}
```

### **Estructuras de Control**

```java
	if (/* CONDICIÓN */) {
	}
	while(/* CONDICIÓN */){
	}
	for (int i = 0; i < 10; i++) { 
        } //for de 1 a 10
	do{
	}while(/* CONDICIÓN */)
```

### **Arreglos**

- Almacenan un número fijo de valores primitivos u Objetos (del mismo tipo)
- Acceso de forma directa a las posiciones
- Dimensión física: Se establece al crearlo  `int df= valorDF;`
- Índice: entero, comenzando en 0.
- Declararcion `int [] contador = new int[10];`
- Carga `for (int i= 0; i < 10; i++) { contador[i]=i // o el dato a almacenar }`

### **Matrices**

- Colección ordenada e indexada de elementos.
- Estructura de datos compuesta que se puede acceder utilizando ***dos índices (filas y columnas)***
- Características
    - Homogénea.
    - Estática.
    - Indexada.
    - Lineal.
- Elementos Primitivos u objetos (del mismo tipo)
- Declaracion `int[][] tabla = new int[10][10];`
- Carga `for (i=0; i< DFi; i++) for(j=0; j< dfJ; j++) tabla[i][j]= GeneradorAleatorio.generarInt(10);`

### **Programación Orientada a Objetos en JAVA (Teoría)**

Paradigmas de la programación: imperativo, objetos, funcional, lógica.

Imperativo: modelo top-down. 

*Objetos: un objeto es una abstracción de un objeto del mundo real, definiendo lo que lo caracteriza (**Estado interno** - los valores de estas características) y las acciones que realiza (**Comportamiento**- las cosas que sabe hacer).*

Encapsulamiento de Información: Se oculta la implementación del objeto hacia el exterior. Desde el exterior sólo se conoce la interfaz del objeto. **Facilita el mantenimiento y evolución del sistema** ya que no hay
dependencias entre las partes del mismo.

<aside>
⚙ Son los objetos los que realizan las operaciones (cómputos)

</aside>

Una clase es por así decir, el molde por donde construimos objetos: conjunto de objetos comunes. El objeto es una instancia de una clase.

![Representación UML de una clase.](image.png)

Representación UML de una clase.

La instanciación se realiza enviando un mensaje de creación a la clase `new NombreObjeto` el cual funciona igual que el new de pascal en pocas palabras. Reserva espacio de memoria para el objeto y la dirección de memoria. 

El constructor del objeto es una instancia especial donde puedo definir y asignarle valores a todas las variables de instancia del objeto.

Cuando un objeto no es referenciado, se libera de memoria (la programación orientada a objetos es eficiente con el uso de memoria).

Envío de mensaje al objeto: si tenemos dos objetos y los queremos comparar o hacer alguna operación entre esos objetos `objeto.nombreMétodo(..);`  

Ejemplo: 

`String test1 = new String ("Hola");` 

`String test2 = new String ("Hola");`

`System.out.print(test2.equals(test1));`

`OUTPUT: true`

Métodos:

`System.out.print(test1.length());` // out 4.

`System.out.print(test1.charAt(0));` // out H.

`System.out.print(test1.toUpperCase());` // out HOLA.

### **¿Cómo crear una clase?**

Tenemos que pensar que es un molde para hacer algo.
public class NombreDeClase {
`/*Declaración del estado*/
/*Declaración del comportamiento*/
/*Declaración de constructores*/`
}

```java
Ejemplo:
public class Producto {
	private double precio = 100;
	private String nombre;
	private String descripción = "Sin descripción";
	}
```

// CONSTRUCTOR

/* Cada vez que creo un producto necesito un objeto los creo con el constructor como referencias. Lo definíamos como Producto p= new Producto ("Pepe",,3) */

```java
public Producto (String unNombre, String unaDescripcion, double unPrecio){
	nombre = unNombre;
	precio = unPrecio;
	descripción = unaDescripcion;
}
```

// FIN CONSTRUCTOR

/*Comienzo de declaración de comportamientos*/

```java
public boolean esCaro(double valor) { return (precio > valor);
}

public double getPrecio(){
return precio
} //para poder leerlo en el programa

public double setPrecio(){
return precio
} //para poder setearlo en el programa

// si apretamos insertar en los botones de arriba tambien podemos hacerlo más facil
public String toString() {
return "Producto: " + nombre + " vale " + precio;
}
```

/*Fin de declaración de comportamientos*/

*En resumen, trabajamos con la creación de clases y a partir de estas creamos objetos. En las clases definimos un conjunto de características (atributos), y comportamientos que poseen (métodos).*

*También trabajamos con la interacción entre objetos a través del envio de mensajes y delegación de y trabajos en otro objeto que puede ser parte de él mismo o no.* 

![Ejemplo de delegación de tareas. ](image%201.png)

Ejemplo de delegación de tareas. 

### **Jerarquía y Herencia**

**Herencia**

Solución a muchos elementos repitiendose entre clases. Este mecanismo permite que una clase herede características y comportamiento (atributos y métodos) de otra clase.

## Ventaja: reutilización de código.

![Definimos una SUPERCLASE figura y definimos clases con esa superclase (madre). Decimos que por ejemplo un triangulo es un triangulo y a su vez es una figura.](image%202.png)

Definimos una SUPERCLASE figura y definimos clases con esa superclase (madre). Decimos que por ejemplo un triangulo es un triangulo y a su vez es una figura.

Superclase: *define* atributos y comportamiento COMÚN. 

Subclases de Superclase: *heredan* atributos y metodos de la superclase, *definen* atributos y metodos propios y *definen* constructores. 

![Como se define una superclase. ](image%203.png)

Como se define una superclase. 

Clases Abstractas

Una clase abstracta es una clase que no puede ser instanciada (no se pueden crear objetos de esta clase). Define características y comportamiento común para un conjunto de clases (subclases). Puede definir métodos abstractos (sin implementación) que deben ser implementados por las subclases.

![Ejemplo en clase figura, en este caso, tendremos que definir dentro de cada figura, por ejemplo circulo, la “función” de calcular área ya que esta es distinta para cada figura. El resto es compartido. ](image%204.png)

Ejemplo en clase figura, en este caso, tendremos que definir dentro de cada figura, por ejemplo circulo, la “función” de calcular área ya que esta es distinta para cada figura. El resto es compartido. 

![image.png](image%205.png)

Con la palabra clave super(..) instancio a la superclase.