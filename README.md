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
    def __init__(self, Marca, Camara, Color): #método especial (constructor), self hace referencia a si mismo.
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
Permite tener a la clase **hija**  acceder a todos los métodos y tener los atributos de la clase **padre**.
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
trabajador1 = Trabajador("José",25,"Peruano")
```

### Herencia Multiple


### MRO
