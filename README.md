# Análisis de ventas y rentabilidad de Superstore

## Objetivo y datos

Analizar qué categorías, regiones y tipos de cliente aportan más ventas y beneficio, y comprobar cómo cambia la rentabilidad según los descuentos.

Fuente: [superstore.csv, publicado en el repositorio de ANAPBORGES en GitHub](https://github.com/ANAPBORGES/tableau-sales-profitability-dashboard/blob/main/data/superstore.csv).

Se utiliza el conjunto completo de una tienda ficticia de Estados Unidos: **9.994 líneas de venta, correspondientes a 5.009 pedidos distintos**, entre 2015 y 2018. Cada fila representa una línea de un pedido, no un pedido completo. Los importes están en dólares estadounidenses (USD). No se ha aplicado muestreo.

## Preparación y comprobación de los datos

1. Se conservaron las 21 columnas originales en la hoja **Datos originales**.
2. Se conservaron 11 columnas y se añadió el año del pedido, dando 12 columnas para el análisis. Se tradujeron las categorías, subcategorías, regiones y tipos de cliente al español.
3. Se comprobaron identificadores, valores vacíos, fechas y tipos numéricos. Las fechas y los importes se guardaron con los tipos y formatos adecuados en Excel.
4. Se convirtió **Datos limpios** en una tabla de Excel, utilizada como origen común de las tablas dinámicas.
5. Se resumieron ventas, beneficio y número de líneas por categoría, región, año, subcategoría, descuento y tipo de cliente. El margen se calcula como **beneficio total / ventas totales**, no como el promedio de los márgenes de cada línea.

Las comprobaciones y las decisiones están recogidas en **Limpieza**:

| Comprobación | Resultado y decisión |
|---|---|
| Valores vacíos | Hay 11 códigos postales vacíos. No hay nulos en las columnas utilizadas en el análisis. El código postal no se utiliza y no se inventan valores. |
| Códigos postales | Hay 438 códigos de cuatro caracteres. Se conserva exactamente el texto del archivo original, incluidos los vacíos. |
| Duplicados | No hay filas completamente duplicadas ni identificadores de línea repetidos. Hay dos líneas iguales si se excluye su identificador; se conservan porque tienen identificadores distintos y no se puede confirmar que sean un error. |
| Fechas | No hay fechas inválidas ni envíos anteriores al pedido. Los últimos pedidos de 2018 incluyen envíos de enero de 2019. |
| Rangos numéricos | Las ventas y las cantidades son positivas; las cantidades son enteras y los descuentos están entre el 0 % y el 80 %. |
| Pérdidas | Se conservan las 1.871 líneas con beneficio negativo: son necesarias para estudiar la rentabilidad. |

## Informe del análisis

Los siguientes resultados corresponden a todos los datos, sin filtros.

| Indicador | Resultado |
|---|---:|
| Ventas | 2.297.200,86 USD |
| Beneficio | 286.397,02 USD |
| Margen | 12,47 % |
| Líneas de venta | 9.994 |

### Categorías y subcategorías

**Tecnología** obtiene las mayores ventas (836.154,03 USD) y el mayor beneficio (145.454,95 USD), con un margen del 17,40 %. **Material de oficina** alcanza un margen del 17,04 %.

**Muebles** vende 741.999,80 USD, pero su beneficio es de 18.451,27 USD y su margen del 2,49 %. Dentro de esta categoría, **Mesas pierde 17.725,48 USD** y **Librerías pierde 3.472,56 USD**. Sus márgenes son del −8,56 % y del −3,02 %, respectivamente. El buen resultado de otras subcategorías compensa estas pérdidas.

### Descuentos

Las 4.798 líneas sin descuento generan 320.987,60 USD de beneficio y un margen del 29,51 %. Las 3.803 líneas con descuentos superiores al 0 % y hasta el 20 % mantienen un margen positivo del 11,91 %.

En cambio, el grupo de descuentos superiores al 20 % y hasta el 40 % pierde 35.817,47 USD. Las **66 líneas con un 50 % de descuento presentan pérdidas**, que suman 20.506,43 USD. Los descuentos más elevados se asocian con menor rentabilidad, aunque esta comparación no demuestra que sean la única causa: también cambia la combinación de productos vendidos.

### Clientes, regiones y años

**Particular** aporta más ventas: 1.161.401 USD. Su margen del 11,55 % es inferior al de **Empresa** (13,03 %) y **Oficina en casa** (14,03 %).

**Oeste** lidera las ventas (725.457,82 USD) y el beneficio (108.418,45 USD). **Centro** obtiene el margen más bajo, un 7,92 %, frente al 14,94 % de Oeste.

**2018** es el año con mayores ventas (733.215,26 USD) y beneficio (93.439,27 USD). Las ventas no crecieron todos los años: bajaron de 484.247,50 USD en 2015 a 470.532,51 USD en 2016, antes de aumentar en 2017 y 2018.

### Conclusiones

- Revisar precios, costes y descuentos de Mesas y Librerías, donde se concentran las pérdidas de Muebles.
- Comprobar el margen esperado antes de aplicar descuentos elevados; no decidir solo por el volumen de ventas.
- Analizar las diferencias de productos y descuentos de Centro y del cliente Particular antes de atribuir sus menores márgenes a la región o al tipo de cliente.

## Libro y dashboard

El archivo **ventas_superstore.xlsx** contiene cinco hojas:

- **Dashboard:** cuatro indicadores, seis gráficos y cuatro segmentadores.
- **Tablas dinámicas:** siete tablas con el mismo origen de datos.
- **Limpieza:** comprobaciones, resultados y decisiones.
- **Datos limpios:** las 9.994 líneas preparadas para el análisis.
- **Datos originales:** los datos completos de la fuente.

Los segmentadores de **Año, Región, Categoría y Tipo de cliente** filtran conjuntamente las tablas dinámicas, los indicadores y los gráficos. El icono de borrar filtro de cada segmentador permite recuperar la vista completa.

![Dashboard de ventas sin filtros](imagenes/dashboard.png)
