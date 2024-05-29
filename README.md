# Implementación de Criptografía de Curvas Elípticas

Este proyecto implementa operaciones básicas de criptografía de curvas elípticas (ECC). Incluye la definición de curvas elípticas, puntos sobre la curva, y entidades que pueden cifrar y descifrar mensajes utilizando dichas curvas.

## Autores
- Arroyo Erick
- David Silva

## Clases Principales

### Clase `Punto`
La clase `Punto` representa un punto en la curva elíptica definido por sus coordenadas `(x, y)`.

### Clase `CurvaEliptica`
Esta clase representa una curva elíptica de la forma \( y^2 = x^3 + ax + b \mod p \). Proporciona métodos para verificar si un punto está en la curva, sumar y restar puntos, multiplicar puntos por un escalar, y otras operaciones relacionadas.

#### Métodos Principales
- `__init__(a, b, p)`: Constructor que define los coeficientes `a`, `b` y `p` de la curva.
- `tiene(punto)`: Verifica si un punto dado está en la curva.
- `puntos()`: Devuelve una lista de todos los puntos en la curva.
- `orden(punto)`: Calcula el orden de un punto en la curva.
- `cofactor(punto)`: Calcula el cofactor de un punto en la curva.
- `suma(p, q)`: Suma dos puntos en la curva.
- `resta(p, q)`: Resta dos puntos en la curva.
- `mult(k, punto)`: Multiplica un punto por un escalar.
- `inv(punto)`: Calcula el inverso aditivo de un punto.

### Clase `Entidad`
Esta clase representa una entidad que puede cifrar y descifrar mensajes utilizando curvas elípticas. Cada entidad tiene un nombre, un mensaje, una curva elíptica, un punto generador, una llave privada, y un punto privado. Además, puede generar y recibir llaves públicas.

#### Métodos Principales
- `__init__(nombre, mensaje, curva, G, orden_G, llave_privada=None, punto_privado=None)`: Constructor de la clase.
- `cifrar(mensaje, tabla)`: Cifra un mensaje utilizando la curva elíptica y una tabla de caracteres.
- `descifrar(mensaje_cifrado, tabla)`: Descifra un mensaje cifrado utilizando la curva elíptica y una tabla de caracteres.
- `generaLlavesPublicas()`: Genera las llaves públicas de la entidad.
- `recibeLlavesPublicas(pks)`: Recibe las llaves públicas de otra entidad.
- `llavesFinales()`: Genera la llave final de la entidad.
- `obtener_caracter(diccionario, punto)`: Obtiene el caracter que corresponde a un punto en la curva a partir de un diccionario.

## Ejemplo de Uso

### Definición de una Curva Elíptica
```python
from Punto import Punto
from CurvaEliptica import CurvaEliptica

# Definir los coeficientes a, b y p
a = 2
b = 3
p = 97

# Crear una instancia de la curva elíptica
curva = CurvaEliptica(a, b, p)
print(curva)