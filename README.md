# Prueba Técnica - Procesamiento de Datos

## Descripción
Este repositorio contiene la solución a la prueba técnica, donde se procesaron diversas listas utilizando **Google Sheets**. A continuación, se describen los pasos realizados para cumplir con las consignas especificadas en cada archivo.

---

## Detalles de la Solución


### ANAERÓBICOS

1. Configuré la región en **Argentina**.
2. Eliminé filas vacías para evitar problemas durante el procesamiento.
3. Aplicación de fórmulas:
   - **Código:**
     ```
     =IF(B5<>"", LEFT(B5, FIND(" ", B5)-1), "")
     ```
   - **Descripción:**
     ```
     =IF(B5<>"", MID(B5, FIND(" ", B5)+1, LEN(B5)), "")
     ```
4. Eliminación de fórmulas:
   - Duplicando las columnas generadas, copiando sus valores y utilizando **Pegado especial > Pegar solo valores**.
5. Ordenamiento de precios de mayor a menor:
   - **Datos > Ordenar rango**, seleccionando "Los datos tienen fila de encabezado" y ordenando por la columna de precios de **mayor a menor**.

---

### HARD

1. Configuré la región en **Argentina**.
2. Conversión de CSV a XLSX:
   - Descargué el archivo en formato CSV, abrí una nueva hoja de cálculo y desde **Archivo > Importar**, cargué el archivo.
3. Agregué columnas para **Código**, **Descripción** y **Precio**, eliminando las demás.
4. Ajustes en precios:
   - Utilicé la fórmula:
     ```
     =ENTERO(D1) + 0,00
     ```
     para obtener solo la parte entera y los decimales como ceros.
   - Eliminé las fórmulas y pegué solo los valores.
   - Reapliqué formato desde **Formato > Número > Número**.
5. Ordenamiento:
   - Ordené los precios de mayor a menor desde **Datos > Ordenar rango**.

---

### FORD

1. Configuré la región en **Argentina**.
2. Limpieza de códigos:
   - Eliminé espacios utilizando **Editar > Buscar y Reemplazar**, dejando el campo de reemplazo vacío.
3. Ajustes en precios:
   - Utilicé formato numérico para añadir automáticamente la coma decimal.
   - Eliminé ceros finales donde fuera necesario.
4. Limpieza de símbolos:
   - Aunque no encontré los símbolos especificados (`╝`, `┤`, entre otros), investigando llegué a la conclusión que se eliminaron automáticamente al copiar los datos.
5. Ordenamiento:
   - Ordené las columnas por precio de mayor a menor.

---

### RASA

1. Configuré la región en **Argentina**.
2. Descargar archivo TXT y convertir a formato XLS:
   - Abrí una nueva hoja de cálculo y desde **Archivo > Importar**, cargué el archivo.

3. Limpieza de códigos:
   - Utilicé la función **Buscar y Reemplazar** de Google Sheets con la expresión regular `[^0-9]` para eliminar todo lo que no fueran dígitos, dejando solo números enteros.

4. Eliminación de caracteres:
   - Los caracteres codificados (`\xe2\x86\x92`, `伃`, `厲`) no fueron encontrados. Investigando llegué a la conclusión de que se eliminaron automáticamente al hacer una copia del archivo.

5. Ajustes en precios:
   - Identifiqué que los precios estaban unidos a otros 14 números. Para separarlos, utilicé la fórmula:
     ```
     =SI(LARGO(C2)>14, DERECHA(C2, LARGO(C2) - 14), C2)
     ```
     - **LARGO(C2):** Calcula el número de caracteres en la celda C2.
     - **DERECHA(C2, LARGO(C2) - 14):** Extrae todos los caracteres a la derecha después de eliminar los primeros 14.
     - **SI:** Verifica si el largo del texto es mayor a 14. Si no lo es, devuelve el contenido original.
   - Luego, utilicé la fórmula:
     ```
     =VALOR(C2)
     ```
     para convertir el contenido en un número y eliminar automáticamente los ceros iniciales.
   - Para filas con datos incorrectos (del 2 al 1583), usé **Buscar y Reemplazar** con la expresión regular `^[0-9]0*` para eliminar el primer dígito y ceros consecutivos.

6. Unión de columnas:
   - Creé una nueva columna combinando las columnas A y B con:
     ```
     =A1 & " " & B1
     ```

7. Ordenamiento:
   - Ordené las columnas por precio de mayor a menor.

---

## Resultados

Los archivos procesados y formateados están disponibles en una carpeta de Google Drive compartida con acceso público. 

[Enlace a la carpeta de resultados](https://drive.google.com/drive/u/0/folders/11Wjv5CwkpsKqRYgK69rVbpyX4K-r-6e7).

---

## Herramientas Utilizadas
- **Google Sheets**: Para el procesamiento de datos.
- **ChatGPT**: Consultas de fórmulas y optimización del proceso.
- **YouTube**: Referencias y tutoriales para operaciones específicas.

