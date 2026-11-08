# Conversor de conciliaciones a Akountik — v1.1

## Uso
1. Descomprime el ZIP.
2. Abre `index.html` en Edge o Chrome.
3. Selecciona el Excel de conciliación y pulsa **Analizar conciliación**.
4. Descarga únicamente el archivo o archivos que correspondan: IMPO, EXPO o ambos.

La herramienta lee las hojas `Importaciones` y `Exportaciones` cuando existen. Los datos se procesan en el navegador. Se requiere conexión a internet para cargar SheetJS desde jsDelivr.

## Reglas configuradas
- IMPO: DOCUMENTO = declaración de importación; REFERENCIA = factura; VALOR USD = FOB de la declaración.
- EXPO: Documento = declaración de exportación; Fecha = fecha de declaración; Referencia = factura; FOB = FOB de la declaración; Gastos = fletes + seguros + otros gastos.
- Genera solo los formatos con registros. No consolida declaraciones diferentes.
- Cuando la factura está vacía en una fila de declaración, conserva la última referencia de factura encontrada dentro del bloque.
- Los archivos de salida se generan en formato `.xlsx`, conservando los nombres y el orden de columnas de las plantillas.

## Importante
Esta es una primera versión funcional para validar con conciliaciones reales. Revisa las alertas y los resultados antes de cargarlos en Akountik.


### Validación de declaraciones EXPO (v1.1)

En la hoja Exportaciones, solo se exportan filas cuyo identificador de declaración DEX sea numérico. Los conceptos no numéricos (por ejemplo, notas crédito y comisiones) se excluyen de la plantilla y se muestran en un apartado informativo con su fila de origen. Los registros que sí tienen número DEX pero carecen de fecha o FOB permanecen en el resultado y generan alertas.
