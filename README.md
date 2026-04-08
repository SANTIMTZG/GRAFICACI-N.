Unidad 2: Graficación 2D**

## **2.1 Transformación bidimensional**

Las transformaciones bidimensionales son operaciones matemáticas que permiten modificar la posición, tamaño, orientación o forma de un objeto en un plano 2D. Estas transformaciones son fundamentales en gráficos por computadora, animación y modelado en herramientas como Blender.

Se aplican sobre puntos representados como coordenadas (x, y), modificando sus valores mediante operaciones matemáticas.

---

## **2.1.1 Traslación**

La traslación consiste en mover un objeto de una posición a otra sin alterar su forma, tamaño ni orientación.

Se define mediante un desplazamiento en los ejes X y Y:

* Fórmula:

  * x' = x + tx
  * y' = y + ty

Donde:

* (x, y) = coordenadas originales
* (tx, ty) = desplazamiento
* (x', y') = nuevas coordenadas

**En Blender:**
Se realiza moviendo el objeto con la tecla **G** (Grab), restringiendo con **X** o **Y**.

---

## **2.1.2 Escalamiento**

El escalamiento cambia el tamaño de un objeto. Puede ser:

* Uniforme (misma escala en X y Y)

* No uniforme (escala diferente en cada eje)

* Fórmula:

  * x' = x * sx
  * y' = y * sy

Donde:

* sx, sy = factores de escala

**En Blender:**
Se usa la tecla **S** para escalar, y **X** o **Y** para restringir.

---

## **2.1.3 Rotación**

La rotación gira un objeto alrededor de un punto (generalmente el origen).

* Fórmulas:

  * x' = x cosθ - y sinθ
  * y' = x sinθ + y cosθ

Donde θ es el ángulo de rotación.

**En Blender:**
Se usa la tecla **R** para rotar.

---

## **2.1.4 Sesgado (Shear)**

El sesgado inclina un objeto en una dirección, deformándolo sin cambiar su área.

* Fórmulas:

  * x' = x + shx * y
  * y' = y + shy * x

Donde:

* shx, shy = factores de sesgado

**Aplicación:**
Se usa en animación y efectos visuales.

---

## **2.2 Representación matricial de las transformaciones bidimensionales**

Las transformaciones se representan mediante matrices, lo que permite combinar múltiples transformaciones en una sola operación.

Se utilizan coordenadas homogéneas:

(x, y, 1)

### Matrices básicas:

**Traslación:**

```
| 1  0  tx |
| 0  1  ty |
| 0  0  1  |
```

**Escalamiento:**

```
| sx  0   0 |
| 0   sy  0 |
| 0   0   1 |
```

**Rotación:**

```
| cosθ  -sinθ  0 |
| sinθ   cosθ  0 |
| 0      0     1 |
```

**Ventaja:**
Permiten combinar transformaciones mediante multiplicación de matrices.

---

### **Ejercicio: Control con teclas de dirección (Blender Python)**

Este ejemplo permite mover un objeto en 2D usando teclas:

```python
import bpy

obj = bpy.context.object

def mover(dx, dy):
    obj.location.x += dx
    obj.location.y += dy

# Simulación de control
mover(1, 0)   # Derecha
mover(-1, 0)  # Izquierda
mover(0, 1)   # Arriba
mover(0, -1)  # Abajo
```

---

## **2.3 Trazo de líneas curvas**

Las curvas permiten representar formas suaves y complejas, fundamentales en diseño gráfico y animación.

---

## **2.3.1 Curvas Bézier**

Son curvas definidas por puntos de control.

Características:

* No necesariamente pasan por todos los puntos
* Son suaves y fáciles de controlar

Fórmula general (grado n):

```
B(t) = Σ (Pi * Bi,n(t))
```

**En Blender:**

* Se crean con curvas tipo Bézier
* Se manipulan mediante handles (manijas)

---

## **2.3.2 B-Spline**

Son curvas más complejas que las Bézier:

Características:

* Mayor suavidad
* Control local (afecta solo una parte de la curva)

Diferencia clave:

* Bézier: control global
* B-Spline: control local

---

### **Ejercicio: Dibujo y animación en Blender**

Ejemplo básico:

```python
import bpy

# Crear curva
curve_data = bpy.data.curves.new(name='Curva', type='CURVE')
curve_data.dimensions = '2D'

polyline = curve_data.splines.new('BEZIER')
polyline.bezier_points.add(2)

polyline.bezier_points[0].co = (0, 0, 0)
polyline.bezier_points[1].co = (2, 2, 0)
polyline.bezier_points[2].co = (4, 0, 0)

curve_obj = bpy.data.objects.new('CurvaObj', curve_data)
bpy.context.collection.objects.link(curve_obj)
```

---

## **2.4 Fractales**

Los fractales son estructuras geométricas que se repiten a diferentes escalas.

Características:

* Autosimilitud
* Complejidad infinita
* Generados mediante algoritmos

Ejemplos:

* Conjunto de Mandelbrot
* Copo de nieve de Koch

**Aplicación en Blender:**

* Generación procedural
* Modelado complejo

---

## **2.5 Uso y creación de fuentes de texto**

En gráficos 2D, las fuentes son esenciales para interfaces, animaciones y diseño.

### Uso:

* Texto como objeto
* Aplicación de materiales y animación

### En Blender:

* Se usa el objeto tipo **Text**
* Se puede convertir a malla (Mesh)

### Creación:

* Uso de tipografías externas (.ttf)
* Diseño vectorial

---

# **Conclusión**

La graficación 2D es la base de la animación y los gráficos por computadora. Las transformaciones permiten manipular objetos, mientras que las curvas y fractales ayudan a crear formas complejas. Blender integra todas estas herramientas para facilitar el diseño y la animación.

---

# **Referencias bibliográficas (Formato APA)**

* Foley, J. D., van Dam, A., Feiner, S. K., & Hughes, J. F. (1996). *Computer Graphics: Principles and Practice*. Addison-Wesley.
* Hearn, D., & Baker, M. P. (2011). *Computer Graphics with OpenGL*. Pearson.
* Rogers, D. F. (2001). *An Introduction to NURBS: With Historical Perspective*. Morgan Kaufmann.
* Blender Foundation. (2024). *Blender Manual*. [https://docs.blender.org](https://docs.blender.org)
* Angel, E., & Shreiner, D. (2015). *Interactive Computer Graphics*. Addison-Wesley.


