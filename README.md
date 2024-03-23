# Practica_POO
Repositorio donde exploro a fondo la progamación orientada a objetos

## Clase y Objeto 

Clase: la receta que se debe seguir para construir un objeto. Nos perminte definir las caracteristicas del objeto y todo lo referencte a éste.

```python
#ejemlo de clase
class Celular():
    #Atributos estáticos
    marca = "Samsung"
    camara = "48mp"
    color = "]Negro"
```

Objeto: Es una instancia de la clase, puedo crear cualquier cantidad. En en el ejemplo sería un celular con las 3 características dadas definidas.

Instanciar: crear una objeto.

```python
#ejemlo de clase
celular1 = Celular() # instamciar o crear una instacion de la clase.
print(celular1.marca) # muestro la propiedad marca del objeto celular1
```

Atributo: Son las propiedades o características de los objetos.

```python
#ejemlo nuevo con atributos instanciables, no estáticos
class Celular():
    def __init__(self, Marca, Camara, Color): #método constructor, self hace referencia a si mismo.
    self.marca = Marca  
    self.camara = ]Camara 
    self.color = Color

celular1 = Celular("Applet","45mp", "Gris") #Instanciar con    

# marca,camara,color son los atributos de la clase   
# Marca,Camara,Color son los valores que se pasan al instanciar el objeto 
```

Método: Es una función que se aplica al objeto a travez de los atributos




## Herencia
### Herencia Multiple
### MRO
