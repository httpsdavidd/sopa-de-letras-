# sopa-de-letras-
'''
import random
import time

def generar_sopa(dificultad):
    if dificultad == "noob":
        palabras = ["Algoritmo", "Instrucciones", "Pseudocodigo", "Variables", "Entero", "lenguaje", "Flotante",
                  "Constante", "Booleano", "Strings", "Operadores", "listas"]
    elif dificultad == "decente":
        palabras = ["Condicional", "Input", "Indentacion", "If", "Elif", "Else", "Funcion", "Libreria", "Alcance",
                    "Import", "While", "Break", "Continue", "For", "Rango"]
    elif dificultad == "good":
        palabras = ["Arreglo", "Mutabilidad", "Indice", "Concatenar", "Pertenencia", "Slicing", "Len", "Append",
                    "Pop", "Insert", "Remove", "Count", "Sort", "Matriz", "Split", "Replace", "Format", "Tupla",
                    "Diccionario", "Find", "identidad"]

    sopa = [[' ' for _ in range(15)] for _ in range(15)]

    for palabra in palabras:
        colocar_palabra(sopa, palabra)

    return sopa

def colocar_palabra(sopa, palabra):
    direccion = random.choice(["horizontal", "vertical"])
    if direccion == "horizontal":
        fila = random.randint(0, 14)
        columna = random.randint(0, 15 - len(palabra))
        for i in range(len(palabra)):
            sopa[fila][columna + i] = palabra[i]
    else:
        fila = random.randint(0, 14 - len(palabra))
        columna = random.randint(0, 14)
        for i in range(len(palabra)):
            sopa[fila + i][columna] = palabra[i]

def mostrar_sopa(sopa):
    for fila in sopa:
        print(" ".join(fila))
    print()

def jugar_sopa(sopa):
    palabras_encontradas = set()
    inicio_tiempo = time.time()

    while True:
        mostrar_sopa(sopa)
        x = int(input("Ingrese la fila (0-14): "))
        y = int(input("Ingrese la columna (0-14): "))

        palabra = input("Ingrese la palabra encontrada: ")

        if palabra in palabras_encontradas:
            print("¡Ya encontraste esa palabra!")
            continue

        if verificar_palabra(sopa, palabra, x, y):
            print("¡Correcto! Palabra encontrada.")
            palabras_encontradas.add(palabra)
        else:
            print("Incorrecto. Inténtalo de nuevo.")

        if len(palabras_encontradas) == len(set(palabra for palabra in palabra)):
            break

    tiempo_total = time.time() - inicio_tiempo
    print(f"Felicidades, has encontrado todas las palabras en {tiempo_total:.2f} segundos.")

def verificar_palabra(sopa, palabra, x, y):
    # Verificar horizontal
    if y + len(palabra) <= 15 and all(sopa[x][y + i] == palabra[i] for i in range(len(palabra))):
        return True
    # Verificar vertical
    if x + len(palabra) <= 15 and all(sopa[x + i][y] == palabra[i] for i in range(len(palabra))):
        return True
    return False

def mostrar_instrucciones():
    print("Instrucciones:")
    print("1. Encuentra todas las palabras en la sopa de letras.")
    print("2. Ingresa las coordenadas (fila y columna) y la palabra encontrada.")
    print("3. Puedes ingresar 'salir' en cualquier momento para terminar el juego.")

def mostrar_definiciones():
    print("Definiciones:")
    print(" - Algoritmo: Conjunto de pasos ordenados para realizar una tarea.")
    print(" - Condicional: Estructura de control que ejecuta cierto bloque de código si se cumple una condición.")
    print(" - Arreglo: Colección de elementos del mismo tipo, accesibles mediante un índice.")
    # ... Agrega más definiciones según tus necesidades.

def main():
    print("¡Bienvenido al juego de Sopa de Letras!")
    mostrar_instrucciones()

    while True:
        print("\nSelecciona el nivel:")
        print("1. Noob")
        print("2. Decente")
        print("3. Good")
        print("4. Salir")

        seleccion_nivel = input("Ingresa el número de nivel o 'salir': ")

        if seleccion_nivel == "salir":
            print("Gracias por jugar. ¡Hasta luego!")
            break

        if seleccion_nivel not in ["1", "2", "3"]:
            print("Selección no válida. Inténtalo de nuevo.")
            continue

        nivel = {"1": "noob", "2": "decente", "3": "good"}[seleccion_nivel]
        sopa = generar_sopa(nivel)

        print(f"\n¡Nivel {nivel.capitalize()} seleccionado!")
        mostrar_definiciones()
        input("Presiona Enter para comenzar...")

        jugar_sopa(sopa)

if __name__ == "__main__":
    main()
'''
