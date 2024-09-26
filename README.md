# reto8

implementation of generators and decorators in a app that calculate the papa and shows; at least for computing science, if you have free tuiton for the next semester

```
import tkinter as tk
from tkinter import messagebox

def calculo_papa(func):
    def wrapper(*args, **kwargs):
        total_ponderado = 0
        total_creditos = 0
        for nota, creditos in func(*args, **kwargs):
            total_ponderado += nota * creditos
            total_creditos += creditos
        return total_ponderado / total_creditos
    return wrapper

def materias_y_creditos(materias):
    for materia, (nota, creditos) in materias.items():
        yield nota, creditos


@calculo_papa
def calcular_promedio(materias):
    return materias_y_creditos(materias)

# Función para mostrar una ventana de felicitación
def mostrar_felicitaciones():
    ventana = tk.Tk()
    ventana.withdraw() 
    messagebox.showinfo("¡Felicitaciones Has obtenido matrícula gratis!")
    ventana.quit()

# Diccionario con las materias, las notas y los créditos
materias = {
    'Elementos de computadores': (4.9, 3),
    'Integral': (4.5, 4),
    'lineal': (3.9, 4),
    'diferencial': (4.0, 4),
    'vectorial': (3.9, 4),
    'fundamentos de matematicas': (3.3, 4),
    'intro a cc': (4.7, 3),
    'mecanica newtoniana': (4.4, 4),
    'chino I': (4.5, 3),
    'chino II': (4.9, 3),
    'taller de ingenieria': (4.9, 3),
    'POO': (5.0, 3),
}

# Cálculo del promedio ponderado
papa = calcular_promedio(materias)
print(f"Su papa es: {papa}")

# Verificar si el promedio es mayor a 4.4 para mostrar la felicitación
if papa >= 4.35:
    mostrar_felicitaciones()
```
