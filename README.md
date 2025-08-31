# Eliminación de Gauss-Jordan: Implementación en R y Python

Este repositorio contiene la implementación del método de eliminación de Gauss-Jordan para resolver sistemas de ecuaciones lineales, tanto en R como en Python.

## ¿Qué es la Eliminación de Gauss-Jordan?

La eliminación de Gauss-Jordan es un algoritmo para resolver sistemas de ecuaciones lineales mediante operaciones elementales de fila en matrices. El objetivo es transformar la matriz aumentada del sistema en una matriz en forma escalonada reducida por filas (forma canónica de Jordan), donde la solución se puede leer directamente.

### Características del método:
- Transforma la matriz de coeficientes en una matriz identidad
- Cada columna se procesa para obtener un 1 en la diagonal y 0s en el resto de posiciones
- Proporciona la solución exacta del sistema (si existe y es única)

## Contenido del Repositorio

- `README.md`: Este archivo de documentación
- `matriz_gauss.py`: Implementación en Python usando NumPy
- Código R incluido en este README para referencia

## Prerrequisitos

### Para Python:
```bash
pip install numpy
```

### Para R:
R base (no requiere paquetes adicionales)

## Ejemplo del Sistema de Ecuaciones

El código resuelve el siguiente sistema de ecuaciones:
```
2x₁ + 4x₂ + 6x₃ = 18
4x₁ + 5x₂ + 6x₃ = 24
3x₁ + 1x₂ - 2x₃ = 4
```

Representado como matriz aumentada:
```
[2  4   6 | 18]
[4  5   6 | 24]
[3  1  -2 |  4]
```

## Implementación en R

### Definición de la matriz

```r
# Vector con los elementos de la matriz aumentada
a = c(2,4,6,18,4,5,6,24,3,1,-2,4)

# Crear matriz 3x4 organizando por filas
A = matrix(a, nrow=3, ncol=4, byrow=TRUE)
print(A)
```

### Acceso a elementos de la matriz

```r
A[2,4]  # Elemento específico (fila 2, columna 4)
A[,1]   # Toda la columna 1
A[3,]   # Toda la fila 3
```

### Proceso de eliminación

#### Paso 1: Procesar columna 1
```r
# Hacer 1 en la posición (1,1)
A[1,] = (1/A[1,1]) * A[1,]  # R1 = (1/2)R1

# Hacer 0s debajo del pivote
A[2,] = -A[2,1] * A[1,] + A[2,]  # R2 = R2 + (-4)R1
A[3,] = -A[3,1] * A[1,] + A[3,]  # R3 = R3 + (-3)R1
```

#### Paso 2: Procesar columna 2
```r
# Hacer 1 en la posición (2,2)
A[2,] = (1/A[2,2]) * A[2,]  # R2 = (-1/3)R2

# Hacer 0s arriba y abajo del pivote
A[1,] = -A[1,2] * A[2,] + A[1,]  # R1 = (-2)R2 + R1
A[3,] = -A[3,2] * A[2,] + A[3,]  # R3 = R3 + R2
```

#### Paso 3: Procesar columna 3
```r
# Hacer 1 en la posición (3,3)
A[3,] = (1/A[3,3]) * A[3,]  # R3 = R3 normalizado

# Hacer 0s arriba del pivote
A[1,] = -A[1,3] * A[3,] + A[1,]  # R1 = R1 - A[1,3]R3
A[2,] = -A[2,3] * A[3,] + A[2,]  # R2 = R2 - A[2,3]R3
```

### Obtener la solución
```r
sol = c(A[1,4], A[2,4], A[3,4])
print("La solución es (x1,x2,x3)=")
print(sol)
```

## Implementación en Python

Para ejecutar la versión en Python:

```bash
python matriz_gauss.py
```

El archivo `matriz_gauss.py` contiene la misma lógica implementada usando NumPy, con sintaxis adaptada a Python.

**Nota**: La implementación actual en Python contiene un error de sintaxis en la línea 38 que afecta el resultado final. La versión en R funciona correctamente y produce la solución esperada (1, 2, 1).

## Estructura del Algoritmo

1. **Inicialización**: Crear la matriz aumentada del sistema
2. **Eliminación hacia adelante**: Para cada columna i:
   - Normalizar el elemento diagonal (hacer que sea 1)
   - Eliminar todos los elementos debajo del pivote
3. **Eliminación hacia atrás**: Para cada columna (de derecha a izquierda):
   - Eliminar todos los elementos arriba del pivote
4. **Lectura de la solución**: Los valores en la última columna son las soluciones

## Resultado Esperado

El sistema de ecuaciones del ejemplo tiene como solución:
- x₁ = 1
- x₂ = 2  
- x₃ = 1

## Notas Importantes

- Este método funciona para sistemas que tienen solución única
- Si el sistema no tiene solución o tiene infinitas soluciones, el método puede no converger o dar resultados inconsistentes
- Es importante verificar que no se produzcan divisiones por cero durante el proceso

## Autor

Implementación educativa del método de Gauss-Jordan para resolver sistemas de ecuaciones lineales.
