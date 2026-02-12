# 📉💼Medición del Sesgo del Mercado

Análisis de la Posición del Cierre dentro del Rango Diario

## 📌Descripción

Este proyecto mide el sesgo intradía del mercado analizando dónde cierra el precio dentro de su rango diario (High–Low), en lugar de centrarse únicamente en la dirección del precio o en indicadores tradicionales.

La hipótesis es simple pero poderosa:
- si una acción cierra consistentemente cerca del mínimo diario, existe una presión vendedora persistente, incluso aunque la tendencia general no sea claramente bajista.

Este enfoque captura micro-sesgos de distribución que suelen anticipar continuaciones bajistas o fallos de rebote.

## 🧠Insight clave

- ¿Qué acciones han cerrado de forma consistente en el tercio inferior de su rango diario durante la última semana?

Esto revela activos donde:
- Los compradores no logran sostener los precios hacia el cierre
- La oferta domina el final de la sesión
- Existe debilidad estructural intradía

## 📊Valor de negocio

Este análisis es útil para:

- Trading de corto plazo
Identificar activos con presión vendedora persistente.

- Confirmación de señales bajistas
Validar rupturas, pullbacks fallidos o divergencias.

- Gestión de riesgo
Evitar posiciones largas en activos con cierres sistemáticamente débiles.

- Análisis de price action
Detectar distribución silenciosa sin necesidad de volumen.

## 🗂️Estructura de datos requerida

- precios_diarios
- ticker_id
- fecha
- open
- high
- low
- close

## ⚙️Lógica del análisis

*Cálculo del rango diario*

rango_total = high − low


*Normalización del cierre*

ratio_cierre_vs_rango = (close − low) / (high − low)


0 → cierre en el mínimo

1 → cierre en el máximo

*Ventana temporal*

Se analizan los últimos 7 días de mercado.

*Agregación*

Se calcula el promedio del ratio por acción.

*Filtro de sesgo bajista*

Se seleccionan acciones con:

promedio_ratio_cierre < 0.33

## 📈Interpretación de resultados

- Ratio promedio < 0.20
- Fuerte dominancia vendedora
- Alta probabilidad de continuación bajista
- Ratio entre 0.20 y 0.33
- Sesgo bajista moderado
- Riesgo elevado para posiciones largas
- Ratio > 0.50
- Dominancia compradora intradía

Este análisis es independiente de la tendencia y detecta debilidad incluso en mercados laterales o alcistas.

## 🚀Posibles extensiones

- Combinar con volumen (confirmar distribución)
- Separar por sector
- Medir persistencia del sesgo (> n semanas)
- Comparar con retornos futuros
- Construir un Índice de Dominancia Intradía

## 🧪Notas técnicas

- Se filtran días con high = low para evitar errores.

Se recomienda indexar:
- precios_diarios (ticker_id, fecha)
- Funciona especialmente bien en activos líquidos.
- Ideal como filtro previo a estrategias long-only.

##👤Autora
Flavia Hepp Proyecto de SQL aplicó un análisis de riesgo basado en eventos.
