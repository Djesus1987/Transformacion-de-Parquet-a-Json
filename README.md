# Proyecto de Conversión de Parquet a JSON

Este proyecto demuestra cómo leer un archivo Parquet, convertir su contenido a un diccionario de Python y luego guardar ese diccionario como un archivo JSON. Utiliza las bibliotecas `pandas` y `json` para realizar estas tareas.

## Requisitos

Antes de ejecutar el código, asegúrate de tener instaladas las siguientes bibliotecas de Python:

- `pandas`
- `pyarrow`
- `json` (esta biblioteca está incluida en la instalación estándar de Python)

Puedes instalar las bibliotecas necesarias usando `pip`:

```sh
pip install pandas pyarrow

Uso
A continuación se muestra un ejemplo de cómo utilizar el código.

Código


import pandas as pd
import pyarrow as pyw
import json 

# Lee el archivo Parquet
df = pd.read_parquet(r'ruta')

df

result = df.set_index('ID_CLIENTE').apply(lambda row: row.to_dict(), axis=1).to_dict()
result

# Convertir la lista de diccionarios a una cadena JSON (opcional, para ver el resultado)
cadena_json = json.dumps(result, indent=4)
print(cadena_json)

# Escribir la lista de diccionarios en un archivo JSON
with open('archivo4.json', 'w') as archivo:
    json.dump(result, archivo, indent=4)























