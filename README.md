# Práctica - Progamación Orientada a Objetos
<p align="center">
<img src="https://github.com/jrguignan/Practica_POO/blob/main/images/programador.gif"  height=250>
</p>

## Clase y Objeto 

Clase: la receta que se debe seguir para construir un objeto. Nos perminte definir las caracteristicas del objeto y todo lo referencie a éste.

```python
#ejemlo de clase
class Celular():
    #Atributos estáticos
    marca = "Samsung"
    camara = "48mp"
    color = "Negro"
```

Objeto: Es una instancia de la clase, puedo crear cualquier cantidad. En en el ejemplo sería un celular con las 3 características dadas definidas.

Instanciar: crear una objeto.

```python
#ejemlo de clase
celular1 = Celular() # instamciar o crear una instacion de la clase.
print(celular1.marca) # muestro la propiedad marca del objeto celular1
```

Atributos: Son las propiedades o características de los objetos.

```python
#ejemlo nuevo con atributos instanciables, no estáticos
class Celular():
    def __init__(self, Marca, Camara, Color): #método especial (constructor), self hace referencia a si mismo.
    self.marca = Marca  
    self.camara = Camara 
    self.color = Color

celular1 = Celular("Applet","45mp", "Gris") #Instanciar objeto  

# marca,camara,color son los atributos de la clase   
# Marca,Camara,Color son los valores que se pasan al instanciar el objeto 
```

Métodos: Son acciones de los objetos, es una función dentro de una clase. 

```python
#ejemlo nuevo con atributos instanciables, no estáticos
class Celular():
    def __init__(self, Marca, Camara, Color): #método constructor, self hace referencia a si mismo.
    self.marca = Marca  
    self.camara = Camara 
    self.color = Color
#metodo llamar
def llamar(self):
    print(f"Esta hacieno una llamada desde:{self.modelo}")

celular1 = Celular("Applet","45mp", "Gris") #Instanciar objeto 

#aplicar el metodo al objeto
modelo1.llamar()    
```





## Herencia
### Herencia Multiple
### MRO
