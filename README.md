# Formulario-nutri
Necesito que el codigo en python que suba sea capaz de ponerlo en un formulario en linea que puedan completar los pacientes


    def calcular_metabolismo_basal(sexo, edad, peso, altura):
    if sexo.lower() == 'hombre':
        BMR = 88.362 + (13.397 * peso) + (4.799 * altura) - (5.677 * edad)
    elif sexo.lower() == 'mujer':
        BMR = 447.593 + (9.247 * peso) + (3.098 * altura) - (4.330 * edad)
    else:
        BMR = None
        print("Por favor, introduce 'hombre' o 'mujer' para el sexo.")
    return BMR

    def clasificar_segun_tablas_metropolitan(sexo, peso, altura, estructura):
    
    rangos_peso_hombre = {
        150: {'mediana': (52, 58), 'grande': (56, 62)},
        155: {'mediana': (55, 61), 'grande': (59, 65)},
        160: {'mediana': (58, 65), 'grande': (62, 69)},
        165: {'mediana': (61, 69), 'grande': (66, 74)},
        170: {'mediana': (65, 73), 'grande': (69, 77)},
        175: {'mediana': (68, 77), 'grande': (73, 82)},
        180: {'mediana': (72, 81), 'grande': (77, 86)},
        185: {'mediana': (76, 85), 'grande': (81, 90)},
        190: {'mediana': (80, 89), 'grande': (86, 96)}
    }
    rangos_peso_mujer = {
        150: {'mediana': (46, 51), 'grande': (49, 54)},
        155: {'mediana': (49, 54), 'grande': (52, 57)},
        160: {'mediana': (52, 58), 'grande': (56, 62)},
        165: {'mediana': (55, 61), 'grande': (59, 65)},
        170: {'mediana': (58, 65), 'grande': (62, 69)},
        175: {'mediana': (61, 69), 'grande': (66, 74)},
        180: {'mediana': (65, 73), 'grande': (69, 77)},
        185: {'mediana': (68, 77), 'grande': (73,82)}
    }


    if sexo.lower() == 'hombre':
        for altura_rango, rangos_peso in rangos_peso_hombre.items():
            if altura == altura_rango:
                for clasificacion, rango in rangos_peso.items():
                    if rango[0] <= peso < rango[1]:
                        return clasificacion + " (dentro de los parámetros)"
                return "Fuera de los parámetros"
    elif sexo.lower() == 'mujer':
        for altura_rango, rangos_peso in rangos_peso_mujer.items():
            if altura == altura_rango:
                for clasificacion, rango in rangos_peso.items():
                    if rango[0] <= peso < rango[1]:
                        return clasificacion + " (dentro de los parámetros)"
                return "Fuera de los parámetros"
            
    def calcular_imc(peso, altura):
    altura_m = altura / 100  
    imc = peso / (altura_m ** 2)
    return imc

    peso = float(input("Ingresa tu peso en kg: "))
    altura = float(input("Ingresa tu altura en cm: "))
    sexo = input("Introduce tu sexo (hombre/mujer): ")
    edad = int(input("Introduce tu edad en años: "))
    estructura = input("Introduce tu estructura corporal (mediana/grande): ")

    imc = calcular_imc(peso, altura)
    BMR = calcular_metabolismo_basal(sexo, edad, peso, altura)
    clasificacion = clasificar_segun_tablas_metropolitan(sexo, peso, altura, estructura)

    if BMR:
    print(f"Tu metabolismo basal es {BMR} calorías por día.")
    iclasificacion = clasificar_segun_tablas_metropolitan(sexo, peso, altura, estructura)

    if clasificacion:
    print(f"Tu clasificación según las tablas de Metropolitan es: {clasificacion}.")
    
    if imc:
    print(f"Tu IMC es: {imc}.")
