# Práctica - Progamación Orientada a Objetos
<p align="center">
<img src="https://github.com/jrguignan/Practica_POO/blob/main/images/programador.gif"  height=250>
</p>

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

### MRO
``` python

```