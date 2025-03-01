# Proyecto de Conversión de Parquet a JSON
Este proyecto demuestra cómo leer un archivo Parquet, convertir su contenido a un diccionario de Python y luego guardar ese diccionario como un archivo JSON. Utiliza las bibliotecas `pandas` y `json` para realizar estas tareas.

## Estructura del Proyecto
El proyecto debe tener la siguiente estructura de archivos:

project
│   README.md
│   archivo4.json
│   script.py
│
└───data
    │   business.parquet


    

README.md: Este archivo.
archivo4.json: El archivo JSON generado.
script.py: El script de Python con el código proporcionado.
data/business.parquet: El archivo Parquet que se va a convertir.

## Contribución 

Si deseas contribuir a este proyecto, por favor sigue estos pasos:

Haz un fork del repositorio.
Crea una nueva rama (git checkout -b feature/nueva-funcionalidad).
Haz tus cambios y commitea (git commit -am 'Añade nueva funcionalidad').
Haz push a la rama (git push origin feature/nueva-funcionalidad).
Abre un Pull Request.
Licencia
Este proyecto está licenciado bajo la Licencia MIT. Consulta el archivo LICENSE para más detalles.


Este README proporciona una descripción completa de cómo usar tu código, instalar las dependencias necesarias, y detalla la estructura del proyecto y los pasos para contribuir.

## Requisitos

Antes de ejecutar el código, asegúrate de tener instaladas las siguientes bibliotecas de Python:

- `pandas`
- `pyarrow`
- `json` (esta biblioteca está incluida en la instalación estándar de Python)

Puedes instalar las bibliotecas necesarias usando `pip`:


pip install pandas pyarrow

Uso
A continuación se muestra un ejemplo de cómo utilizar el código.

Código

```sh
import pandas as pd
import pyarrow as pyw
import json 

# Lee el archivo Parquet
df = pd.read_parquet(r'ruta')
df


# convierte el dataframe en una lista de diccionarios usando como clave el registro de la columna id y el valor el resto de los registros de las demas columnas.
result = df.set_index('ID_CLIENTE').apply(lambda row: row.to_dict(), axis=1).to_dict()
result

# Utiliza la función json.dumps() para convertir la lista de diccionarios a una cadena JSON. Esta linea de codigo es útil solo para ver como quedara el JSON en formato de cadena antes de escribirlo en un archivo.
cadena_json = json.dumps(result, indent=4)
print(cadena_json)

# Escribir la lista de diccionarios en un archivo JSON
with open('archivo4.json', 'w') as archivo:
    json.dump(result, archivo, indent=4)
