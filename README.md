# Cafetería Central | Ventas y metas

Caso práctico de inteligencia de negocios que analiza **760 ventas de cuatro sucursales**, registradas de enero a junio de 2026. El tablero de Power BI permite explorar los ingresos por mes, producto, sucursal, canal y país de destino.

[Abrir el archivo de Power BI](powerbi/dashboard_coffee_sales_bi.pbix) · [Ver el tablero en PDF](docs/dashboard_coffee_sales_bi.pdf)

## Datos del proyecto

| Hoja de Excel | Contenido |
| --- | --- |
| `Ventas` | 760 transacciones con precios, costos, moneda y tipo de cambio. Incluye 713 ventas nacionales en CRC y 47 de exportación en USD. |
| `Metas_Mensuales` | 30 metas de ingresos por mes, sucursal, canal y moneda. |
| `Datos_Crudos_ETL` | Muestra independiente de 62 filas para practicar limpieza de fechas, nombres, duplicados, faltantes y cantidades. |
| `Diccionario_Datos` | Definiciones, tipos y unidades de las columnas. |

El CSV contiene las transacciones de la hoja `Ventas`. El documento de correcciones describe el tratamiento de nombres, valores faltantes y cantidades negativas en la muestra ETL.

## Indicadores conciliados

Los ingresos y costos en USD se convierten a colones con el tipo de cambio de cada transacción. Los importes en CRC conservan su valor. La utilidad bruta se calcula restando los costos convertidos de los ingresos convertidos.

| Indicador | Cuatro sucursales | Sucursal Centro |
| --- | ---: | ---: |
| Transacciones | 760 | 239 |
| Ingresos | ₡19.985.995,60 | ₡18.265.295,60 |
| Costos de venta | ₡12.645.035,30 | ₡12.060.745,30 |
| Utilidad bruta | ₡7.340.960,30 | ₡6.204.550,30 |

La Sucursal Centro registra toda la exportación del caso. Este canal aporta el **96,92 % de sus ingresos**.

### Cumplimiento de metas de Sucursal Centro

La comparación del semestre mantiene la misma sucursal, canal y moneda en los ingresos y la meta.

| Canal | Ingresos | Meta | Cumplimiento |
| --- | ---: | ---: | ---: |
| Nacional | ₡562.500,00 | ₡598.500,00 | 93,98 % |
| Exportación | USD 33.635,00 | USD 30.960,00 | 108,64 % |

Un indicador conjunto de cumplimiento en CRC requiere una tasa presupuestaria para convertir las metas en USD. El PDF conserva la vista original filtrada a **Sucursal Centro**. Sus tarjetas de utilidad y cumplimiento requieren ajustar la conversión de costos y la comparación de metas. Las cifras anteriores se recalcularon a partir del Excel.

## Abrir el proyecto

### Power BI Desktop

1. Abre `dashboard_coffee_sales_bi.pbix` en Power BI Desktop.
2. Cambia el filtro de sucursal para explorar la evolución mensual y la composición de las ventas.
3. Si la actualización solicita la ruta del origen, ajusta la conexión en Power Query a la ubicación local de los datos.

### SQL Server

1. Abre `db_coffee_sales_bi.sql` en SQL Server Management Studio. En una instancia de pruebas, ejecuta los dos primeros lotes para crear y seleccionar `CafeteriaCentral_BD_Integral_BI`.
2. Importa la hoja `Ventas` o su CSV a una tabla llamada `dbo.CafeteriaCentral_BD_Integral_BI` en esa base. El CSV usa UTF-8, separador de punto y coma, fechas día/mes/año y coma decimal en los importes.
3. Ejecuta el `SELECT` final después de la importación para revisar las ventas cargadas.

## Archivos del repositorio

| Archivo | Uso |
| --- | --- |
| [dashboard_coffee_sales_bi.pbix](powerbi/dashboard_coffee_sales_bi.pbix) | Reporte editable con filtros y visualizaciones. |
| [dashboard_coffee_sales_bi.pdf](docs/dashboard_coffee_sales_bi.pdf) | Vista estática del reporte para Sucursal Centro. |
| [db_coffee_sales_bi.xlsx](data/db_coffee_sales_bi.xlsx) | Ventas, metas, práctica de limpieza y diccionario. |
| [db_coffee_sales_bi.csv](data/db_coffee_sales_bi.csv) | Exportación de las 760 transacciones de venta. |
| [db_coffee_sales_bi.sql](sql/db_coffee_sales_bi.sql) | Creación de la base y consulta de la tabla importada. |
| [doc_correcciones_db.docx](docs/doc_correcciones_db.docx) | Registro de correcciones descritas en la práctica ETL. |

## Autor

**Donald Aguilar Fonseca** · Caso práctico de Business Intelligence, grupo 5.
