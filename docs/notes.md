
# Análisis de ventas de productos digitales simuladas

Este proyecto busca analizar patrones de consumo en el mercado de productos digitales (ebooks, cursos online, plantillas, música/licencias) mediante un dataset simulado. 


## Objetivo del proyecto

Identificar:

- Categorías más rentables (ventas vs ingresos).
- Tendencias de compra por mes/temporada.
- Ticket promedio y variación entre categorías.
- Clientes recurrentes vs nuevos.
- Posibles estrategias de retención y crecimiento.

# Dataset 
**Tamaño:** 8,000 registros de órdenes de compra.

**Periodo:** últimos 12 meses (con estacionalidad realista en Ene, Sep, Nov, Dic).

**Unidades de análisis:** cada fila corresponde a una orden (producto comprado por un cliente en una fecha).

**Variables principales:**
- `order_id` → identificador único de la orden.
- `customer_id` → identificador del cliente.
- `product_name` → nombre genérico.
- `category` → tipo de producto digital (Ebook, Curso, Plantilla, Musica).
- `price_usd` → precio unitario en USD.
- `quantity` → cantidad de unidades compradas.
- `discount_rate` → tasa de descuento aplicada (0–15%).
- `gross_amount_usd` → ingreso bruto (precio x cantidad).
- `net_revenue_usd` → ingreso neto tras descuento.
- `purchase_dt` → fecha/hora de la compra.
- `region` → región de compra (NA, EU, LATAM, ASIA, OTHER).
- `channel` → canal de adquisición (Website, Marketplace, Email, SocialAds).
- `payment_method` → método de pago (Card, PayPal, Stripe, Crypto).

**Preguntas guía**
- ¿Qué patrones de consumo caracterizan a los compradores de productos digitales en los últimos 12 meses?

- ¿Qué categorías muestran mayor rentabilidad y estabilidad de ventas?

- ¿Existen diferencias significativas en el comportamiento de compra según el canal?

- ¿Cómo influye la estacionalidad (Ene, Sep, Nov, Dic) en las ventas y en los ingresos netos?

- ¿Qué oportunidades estratégicas podrían derivarse de estos patrones (p. ej. promociones, nuevos lanzamientos, segmentación de clientes)?


## Esquema de trabajo 

```mermaid
graph TD
    FASE1[FASE 1: Preparación de datos]
    
    FASE2[FASE 2: Análisis exploratorio]
    
    FASE3[FASE 3: Insights y segmentación]
    
    FASE4[FASE 4: Comunicación de resultados]
    
    FASE1 --> FASE2
    FASE2 --> FASE3
    FASE3 --> FASE4
    
    style FASE1 fill: #bc942e
    style FASE2 fill: #105e6c
    style FASE3 fill: #939a3f
    style FASE4 fill: #a8522d
```

- **Fase 1. Preparación de datos:** Garantizar la calidad y estructura del dataset para el análisis 
- **Fase 2. Análisis exploratorio** Comprender el comportamiento general del negocio y sus dimensiones clave
- **Fase 3. Insights y segmentación:**  Profundizar en patrones específicos y segmentar para estrategías dirigidas
- **Fase 4. Comunicación de Resultados:** Presentar los resultados de forma clara y accionable

## Fase 1. Preparación de datos
Como ya se mencionó, el objetivo de esta fase es garantizar la calidad y estructura del dataset para poder hacer un buen análisis. Esta fase del proyecto se va a dividir en: 

```mermaid 
    graph LR
    A[1 <br> Cargar datos]
    B[2 <br> Validaciones básicas]
    C[3 <br> Limpieza]
    D[4 <br> Enriquecimiento temporal] 
    
    A-->B
    B-->C
    C-->D

    style A fill: #bc942e
    style B fill: #b59c5c
    style C fill: #ac965c
    style D fill: #aea07f
```

1. **Cargar datos:** Importar el dataset y librerías necesarias
2. **Validaciones básicas:** Verificar estructura, tipos de datos, valores faltantes
3. **Limpieza:** Tratar duplicados, outliers y datos inconsistentes
4. **Enriquesimiento temporal:** Crear variables derivadas (mes, trimestre, día semana, temporada)

## Fase 2. Análisis exploratorio 
El objetivo de esta fase es comprender el comportamiento general del negocio y sus dimensiones clave, esta fase se divide en el siguient esquema:

```mermaid
    graph LR
    A[1 <br> KPIs globales]
    B[2 <br> EDA por dimensiones]
    C[3 <br> Cohorts y recurrencia]
    
    A-->B
    B-->C

    style A fill: #105e6c
    style B fill: #318291
    style C fill: #325b63

```

1. **KPIs globales:**  Calcular métricas principales (ingresos totales, ticket promedio, tasa de descuento promedio)
    
    - **Resultados:**
    
        | KPI | Valor |
        | :--- | :--- |
        | **Ingresos Netos Totales** | $374,647.04 |
        | **Ingresos Brutos Totales** | $379,572.66 |
        | **Total de Unidades Vendidas** | 9,664 |
        | **Valor Promedio de Pedido** | $46.83 |
        | **Valor Máximo de Pedido** | $236.28 |
        | **Valor Mínimo de Pedido** | $2.55 |
        | **Tasa de Descuento Promedio** | 1.29% |

2. **EDA por dimensiones:** Explorar patrones por categoría, región, canal, método de pago y tiempo

    - **Resultados:**
        ![Graficas de barras de las dimensiones](img/plot-eda-dimensions.png)
3. **Cohorts y recurrencia:** Analizar comportamiento de clientes nuevos vs recurrentes
    - **Resultados** 
        - Total de Clientes Únicos: **995**
        - Clientes con más de una compra: **441**
        - Clientes con una sola compra: **554**
        - Cliente que más ha gastado: ID:1 con un total de **$88,350.46**
        - Cliente que menos ha gastado: ID:1962 con un total de **$2.85**
    ![alt text](img/plot-eda-clientes-nuevosvsrecurrentes.png)

## Fase 3. Insight y segmentación 
El objetivo de esta fase es profundizar en patrones específicos y segmentar para estrategias dirigidas, se dividirá en el siguiente esquema:

```mermaid
    graph LR
    A[1 <br> Segmentación simple]
    B[2 <br> Hallazgos y recomendaciones]
    
    A-->B

    style A fill: #939a3f
    style B fill: #818555

```

1. **Segmetación simple:** Agrupar clientes por valor, frecuencia o preferencias
2. **Hallazgos y recomendaciones:** Sintetizar insights clave y proponer acciones estratégicas

## Fase 4. Comunicación de resultados 

Para esta fase se tiene como objetivo principal presentar los resultados obtenidos de manera clara y accionable. Se prentende hacerlo siguiendo este esquema:

```mermaid
    graph LR 
    A[1 <br> Visualizaciones clave]
    B[2 <br> Diseño de Dashboard]
    
    A-->B

    style A fill: #a8522d
    style B fill: #a26449ff
```

1. **Visualizaciones clave:** Crear gráficos que comuniquen los insights principales
2. **Diseño de Dashboard:** Diseñar un tablero interactivo o estático para stakeholders

