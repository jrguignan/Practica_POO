# Práctica - Progamación Orientada a Objetos
<p align="center">
<img src="https://github.com/jrguignan/Practica_POO/blob/main/images/programador.gif"  height=250>
</p>

# Índice
* [Clase y Objeto](#Clase-y-Objeto)
* [Herencia](#Herencia)
  * [Herencia Simple](#Herencia-Simple)
  * [Herencia Gerárquica](#Herencia-Gerárquica)
  * [Herencia Multiple](#Herencia-Multiple) 
* [MRO - Método de Resolución de Orden](#MRO---Método-de-Resolución-de-Orden)
* [Polimorfismo](#Polimorfismo)
  * [Paramétrico](#Paramétrico)
  * [De Herencia o Subclases](#De-Herencia-o-Subclases)
* [Encapsulamiento](#Encapsulamiento)



## Clase y Objeto 

Clase: la receta que se debe seguir para construir un objeto. Nos perminte definir las caracteristicas del objeto y todo lo referencie a éste.

```python
#Ejemlo de clase
class Celular():
    #Atributos estáticos
    marca = "Samsung"
    camara = "48mp"
    color = "Negro"
```

Objeto: Es una instancia de la clase, puedo crear cualquier cantidad. En en el ejemplo sería un celular con las 3 características dadas definidas.

Instanciar: crear una objeto.

```python
#Ejemlo de clase
celular1 = Celular() # instamciar o crear una instacion de la clase.
print(celular1.marca) # muestro la propiedad marca del objeto celular1
```

Atributos: Son las propiedades o características de los objetos.

```python
#Ejemlo nuevo con atributos instanciables, no estáticos
class Celular():
    #método especial (constructor), self hace referencia a si mismo.
    def __init__(self, Marca, Camara, Color):  
        self.marca = Marca     
        self.camara = Camara 
        self.color = Color

celular1 = Celular("Applet","45mp", "Gris") #Instanciar objeto  

# Marca,camara,color son los atributos de la clase   
# Marca,Camara,Color son los valores que se pasan al instanciar el objeto 
```

Métodos: Son acciones de los objetos, es una función dentro de una clase. 

```python
#Ejemplo nuevo con atributos instanciables, no estáticos
class Celular():
    def __init__(self, Marca, Camara, Color): #método constructor, self hace referencia a si mismo.
        self.marca = Marca  
        self.camara = Camara 
        self.color = Color
#Método llamar
   def llamar(self):
       print(f"Esta hacieno una llamada desde:{self.modelo}")

celular1 = Celular("Applet","45mp", "Gris") #Instanciar objeto 

#Aplicar el metodo al objeto
modelo1.llamar()    
```
<br>[Volver al Índice](#Índice)

## Herencia
Permite tener a la **clase hija**  acceder a todos los métodos y tener los atributos de la **clase padre**.
La herencia nos permite ahorrar códígo, al utilizar clases padre. Es como usar una receta base a la cual al final de la preparación se le agrega otro ingrediente, cambiando el nombre de la receta original. Ejemplor: galleta - galleta con chispas de chocolate. 

```python
#Ejemplo: Herencia
class Persona:
    def __init__(self, nombre,edad,nacionalidad):
        self.nombre = nombre
        self.edad = edad
        self.nacionalidad = nacionalidad

#La clase trabajador, está heredando todos 
#los atributos de la clase Persona
class Trabajador(Persona):
    pass

#Se puede instanciar la clase Trabajador, 
#con los atributos de la clase Persona
jose = Trabajador("José",25,"Peruano")

#Se pueden llamar los atributos
jose.edad
```
### Herencia Simple
Cuando una **clase hija** hereda de una única **clase padre**

``` python
#Ejemplo: Herencia Simple
class Persona:
    def __init__(self, nombre,edad,nacionalidad):
        self.nombre = nombre
        self.edad = edad
        self.nacionalidad = nacionalidad

    def hablar(self):
          return "La persona habla"    

#La clase trabajador, está heredando el atributo nombre y edad
class Trabajador(Persona):
      def __init__(self,nombre,edad,nacionalidad, puesto,salario):
          #super nos permnite heredar sin nombrar al padre
          super().__init__(nombre,edad,nacionalidad)
          self.puesto=puesto
          self.salario=salario

      #reescribe el metodo habar heredado    
      def hablar(self):
          return "La persona habla cuando quiere"     


trabajador1 = Trabajador("Pedro",25,"chilena","Psicólogo",2500)               
trabajador1.hablar()           
```

Persona es la **clase padre** de Trabajador o es la **superclase** de la clase Trabajador.
Trabajador es la **clase hija** de Persona o es la **subclase** de la clase Persona.

**Nota:** super() nos perminte llamar al método padre, sin nombrarlo y tambien nos permite entrar a métodos de la clase padre, aún si el método está reescrito en la clase hija.
<br>[Volver al Índice](#Índice)

### Herencia Gerárquica
Cuando varias clases tienen una única clase padre. Es como la herencia simple pero agregando más subclases o clases hijas.

### Herencia Multiple
``` python
#Clase padre 1
class Persona:
    def __init__(self, nombre,edad,nacionalidad):
        self.nombre = nombre
        self.edad = edad
        self.nacionalidad = nacionalidad

    def hablar(self):
        return "La persona puede hablar"    
#Clase padre 2   
class Artista():
    def __init__(self, habilidad):
        self.habilidad = habilidad

    def mostrar_habilidad(self):
        return f"Mi habilidad es: {self.habilidad}, clase padre"
    
#Clase hija     
class PersonaArtista(Persona,Artista):
    def __init__(self,nombre,edad,nacionalidad,habilidad,tipoartista):
       #no se puede usar super porque hay 2 clases padre
       Persona.__init__(self,nombre,edad,nacionalidad)    
       Artista.__init__(self,habilidad)
       self.tipoartista=tipoartista

    def hablar(self):
        return "La persona puede hablar, método reescrito"
    
    def mostrar_habilidad(self):
        return f"Mi habilidad es: {self.habilidad}, clase hija"
    
    #super permite ir sobre el metodo mostrar_padre
    def presentarse_padre(self):
        return super().mostrar_habilidad()
    
    #self muestra el metodo modificado de la clase hija
    def presentarse_hija(self):
        return self.mostrar_habilidad()
 
persona = PersonaArtista("Juan",25,"Boliviana","Pintar","Callejero")   

print(persona.presentarse_padre())
#>Mi habilidad es: Pintar, clase padre

print(persona.presentarse_hija())
#>Mi habilidad es: Pintar, clase hija
```
<br>[Volver al Índice](#Índice)

### MRO - Método de Resolución de Orden
Hace referencia a como se buscan los métodos y los atributos en las clases. Da el orden de cuales son los métodos y atributos que heredad las **clases hijas** de las **clases padres**.

*Nota:* print( clase.mro() ) -> muestra los caminos de herencia de clase.

``` python
#Ejemplo MRO 1
# Jugando con este ejemplo se puede ver como python 
#gestiona la herencia entre varios niveles de clses
class A():
    def hablar(self):
        return "Habla desde A"
    
class B():
    def hablar(self):
        return "Habla desde B"   

class C(A):
    pass
    # def hablar(self):
    #     return "Habla desde C"     
    
class D(B):
    def hablar(self):
        return "Habla desde D"

class E(C,D):
    pass
    # def hablar(self):
    #     return "Habla desde E"    

objeto = E()
print(objeto.hablar())  
#>'Habla desde A'

print(E.mro())  
#>[<class '__main__.E'>, <class '__main__.C'>, <class '__main__.A'>, <class '__main__.D'>, <class '__main__.B'>, <class 'object'>]    
```
<p align="center">
<img src="https://github.com/jrguignan/Practica_POO/blob/main/images/ejemploMRO.png"  height=150>
</p>

Primero se busca e método en E, al no encontrarlo pasa a C, porque E hereda primero de C y luego de D, luego sigue buscando la rama de c, hasta encontrarla en A. Si no lo encotrara en A, seguiria a D hasta buscan en B.

<br>[Volver al Índice](#Índice)

``` python
#Ejemplo MRO 2
class A():
    def hablar(self):
        return "Habla desde A"
    
class B():
    def hablar(self):
        return "Habla desde B"   

class C(A,B):
    pass
    # def hablar(self):
    #     return "Habla desde C"     
    
class D(B):
    pass
    # def hablar(self):
    #     return "Habla desde D"

class E(D,C):
    pass
    # def hablar(self):
    #     return "Habla desde E"    

objeto = E()
print(objeto.hablar())  
#>'Habla desde A'

print(E.mro())  
#>[<class '__main__.E'>, <class '__main__.D'>, <class '__main__.C'>, <class '__main__.A'>, <class '__main__.B'>, <class 'object'>]

``` 
<p align="center">
<img src="https://github.com/jrguignan/Practica_POO/blob/main/images/ejemploMRO2.png"  height=150>
</p>

Primero se busca el método en E, Luego debería buscar primero en D y luego en C, pero al tener como herencia comun B, para D y C, primero busca en C y luego en A, si no consigue el método ya busca en B. 
<br>[Volver al Índice](#Índice)

## Polimorfismo

Generar resultados diferentes a partir de un mismo método. Al aplicar un mismo método a diferentes objetos se consigue respuestas distintas. Por ejemplo el metodo hacer_sonido aplicado a un perro sería "guau" y aplicado a una vaca sería "muuu".

### Paramétrico
```python
#Ejemplo polimorfismo paramétrico
class Perro():
    def sonido(self):
        return "Guau"
    
class Gato():
    def sonido(self):
        return "Miau"    
    
gato=Gato()
perro=Perro()

#Usando el mismo metodo obtengo dirente sonido
print(perro.sonido())
#>Guau
print(gato.sonido())
#>Miau

#Usando la misma funcion obtengo dirente sonido
#polimorfismo parametrico
def hacer_sonido(animal):
    print(animal.sonido())

hacer_sonido(gato)
#>Miau

hacer_sonido(perro)
#>Guau

```
Estos ejemplos sirven en python por ser de tipado dinámico, pero en otro lenguajes, se debe utilizar la herencia para llevarlos acabo.

<br>[Volver al Índice](#Índice)

###  Herencia o Subclases
```python
#Ejemplo polimorfismo de herencia
class Animal():
    def sonido(self):
        pass

class Perro(Animal):
    def sonido(self):
        return "Guau"
    
class Gato(Animal):
    def sonido(self):
        return "Miau"    
    
gato=Gato()
perro=Perro()

#Usando el mismo metodo obtengo dirente sonido
print(perro.sonido())
#>Guau
print(gato.sonido())
#>Miau
```
Existen más tipos de polimorfismo baso el mismo principio.

<br>[Volver al Índice](#Índice)

## Encapsulamiento

Se utiliza para hacer inaccesible ciertos métodos y atributos para protegerlos. Sólo se pueden acceder bajo determinadas normas predefinidas dentro de la clase.

```python

class Usuario():
    def __init__(self):
      self.nombre = "Matias"
      #Al colocar __ no me deja acceder al atributo de manera normal.
      #es como si no exitiese.
      self.__contraseña = 1234

usuario=Usuario()     
usuario.nombre
#>'Matias'

usuario.__contraseña
#>AttributeError  

```

Exiten los métodos setter, getter y deleter que permiten agregar, modificar o borrar un atributo privado a traves del uso de los decoradores.

### Getter - Setter - Deleter
```python
class Persona:
    def __init__(self, nombre, edad):
        self.__nombre = nombre
        self.__edad = edad

    # Getter
    @property
    def nombre(self):
        return self.__nombre

    @property
    def edad(self):
        return self.__edad

    # Setter
    @nombre.setter
    def nombre(self, nuevo_nombre):
        self.__nombre = nuevo_nombre

    @edad.setter
    def edad(self, nueva_edad):
        self._edad = nueva_edad

    # Deleter
    @nombre.deleter
    def nombre(self):
        del self.__nombre

    @edad.deleter
    def edad(self):
        del self.__edad

# Crear un objeto de la clase Persona
persona1 = Persona("Juan", 30)

# Obtener valores usando los getters
print("Nombre:", persona1.nombre)
#>Nombre: Juan
print("Edad:", persona1.edad)
#>Edad: 30

# Cambiar valores usando los setters
persona1.nombre = "Pedro"
persona1.edad = 35

print("Nuevo nombre:", persona1.nombre)
#>Nuevo nombre: Pedro

print("Nueva edad:", persona1.edad)
#>Nueva edad: 35

# Eliminar atributos usando los deleter
del persona1.nombre
del persona1.edad

# Esto provocará un error porque hemos eliminado los atributos
print("Nombre:", persona1.nombre)

```

### Métodos Especiales

<p align="center">
<img src="https://github.com/jrguignan/Practica_POO/blob/main/images/metodos especiales.png"  height=300>
</p>




