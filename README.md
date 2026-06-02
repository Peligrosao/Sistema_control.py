# Sistema_control.py
Sistema de control de alumnos (Basico)


alumnos = []

while True:
    
    nombre = input("Ingresa el nombre del alumno: ")
  
    try:
        edad = int(input("Ingresa la edad del alumno: "))
        calificacion = float(input("Ingresa la calificación del alumno: "))
    except ValueError:
        print("Error: Debes ingresar valores numéricos para edad y calificación.")
        continue

    # Evaluar estado
    estado = "Aprobado" if calificacion >= 70 else "Reprobado"

    # Crear ficha del alumno
    ficha = {
        "nombre": nombre,
        "edad": edad,
        "calificacion": calificacion,
        "estado": estado
    }

    # Guardar en lista
    alumnos.append(ficha)

    # Continuar o salir
    continuar = input("¿Deseas agregar otro alumno? (S/N): ")
    if continuar.upper() != "S":
        break


# Guardar en archivo
with open("alumnos.txt", "w") as archivo:
    for alumno in alumnos:
        archivo.write(
            f"Nombre: {alumno['nombre']}, "
            f"Edad: {alumno['edad']}, "
            f"Calificación: {alumno['calificacion']}, "
            f"Estado: {alumno['estado']}\n"
        )


# Leer archivo
with open("alumnos.txt", "r") as archivo:
    contenido = archivo.read()

print("\n--- LISTA DE ALUMNOS ---")
print(contenido)
