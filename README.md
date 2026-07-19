SQL SELECT

consultas_basicas.sql — Las tres consultas del ejercicio:

Exploración general de la tabla (SELECT *).
Selección de columnas específicas para el equipo de finanzas.
Selección con alias en español para stakeholders no técnicos.

1. ¿Por qué es mala práctica usar SELECT * en producción?

 Rendimiento. SELECT * trae todas las columnas de la tabla, aunque no las
necesites. Sobre tablas con millones de filas, esto genera consultas más lentas y
tiempos de carga más largos, además de consumir más memoria y recursos del servidor.
Traer solo las columnas necesarias hace la consulta más rápida y eficiente.

 Mantenibilidad. Si una consulta usa SELECT * y alguien agrega, elimina o
reordena columnas en la tabla, la consulta empieza a devolver un resultado distinto
sin avisar. Esto puede romper los reportes de Power BI o los procesos que dependen de
un conjunto de columnas específico. Al listar las columnas de forma explícita
(SELECT columna1, columna2), la consulta pide exactamente lo que necesita y no se ve
afectada por cambios en el resto de la tabla.

2. ¿Por qué son importantes los alias para un stakeholder no técnico?

Los nombres de columnas en una base de datos suelen ser técnicos o estar en inglés, y
una persona del área de finanzas o negocio no tiene por qué entenderlos. Los alias
(AS) renombran las columnas en el resultado para que sean legibles sin conocer la
base de datos.

Ejemplo concreto: la columna total_amount no le dice mucho a un contador —tiene
que interpretar qué significa, y encima está en inglés. Al renombrarla:

SELECT total_amount AS monto_total FROM sales;

el encabezado del resultado pasa a ser monto_total, que cualquier persona del área
de finanzas entiende directamente como el importe de la venta, sin preguntarle nada al
equipo técnico. Además, si esos datos se llevan a Power BI o Excel, los alias ya dejan
los encabezados listos y presentables para el reporte final.
