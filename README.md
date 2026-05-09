# 🛒 Olist — Análisis Financiero con Python

Caso de estudio de análisis financiero que combina **análisis de datos y principios contables** para simular reportes financieros y generar insights de negocio sobre una plataforma de e-commerce brasileña.

> Dataset: [Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) — más de 100.000 órdenes reales (2016–2018).

---

## 📌 Qué hace diferente a este proyecto

La mayoría de los proyectos de análisis de datos se quedan en "ventas totales por mes". Este va más allá aplicando **principios contables reales** a los datos:

- Reconocimiento de ingresos **solo sobre órdenes entregadas** (criterio contable conservador)
- Simulación de **contabilidad por partida doble** por tipo de pago
- Generación de un **balance de comprobación** a partir de datos transaccionales
- **Gráfico waterfall** que muestra la erosión de ingresos por costos logísticos

---

## 🔍 Etapas del análisis

### 1. Auditoría de calidad de datos
Antes de cualquier análisis financiero, se realiza una auditoría estructurada que verifica valores faltantes, duplicados y montos de pago inválidos — simulando la validación de datos requerida en reportes financieros reales.

### 2. Reconocimiento de ingresos
Los ingresos solo se contabilizan cuando `order_status == 'delivered'`, evitando inflar los resultados con órdenes canceladas o pendientes. El análisis temporal se limita a períodos contables completos (hasta agosto 2018) para evitar tendencias engañosas por meses incompletos.

### 3. Simulación de contabilidad por partida doble
Cada venta entregada genera un asiento contable:

| Cuenta | Debe | Haber |
|---|---|---|
| 1.01 Banco – Tarjetas de crédito | monto_pago | — |
| 4.01 Ingresos por ventas | — | monto_pago |

Los tipos de pago se mapean al plan de cuentas: tarjeta de crédito → Banco, boleto → Caja, voucher → Vales.

### 4. Análisis de rentabilidad
Como el costo de mercadería vendida (CMV) no está disponible en el dataset, el análisis se enfoca en el **Margen de Contribución Logístico**:

```
Margen de Contribución Logístico = Ingresos por Productos − Costos de Flete
```

### 5. Erosión de ingresos — Gráfico Waterfall
Desglose visual de cómo los ingresos totales se reducen por los costos logísticos hasta llegar al margen de contribución.

---

## 💡 Insights principales de negocio

- El **pago con tarjeta de crédito** es el canal dominante — principal motor de ingresos
- Los **costos logísticos** representan una porción significativa de los ingresos, destacando la importancia de optimizar el flete en e-commerce
- Los ingresos mostraron **crecimiento sostenido** hasta mediados de 2018, validando la expansión de Olist
- Aplicar un **corte temporal en períodos contables completos** es clave para evitar análisis de tendencias engañosos — un error frecuente en reportes de negocio

---

## 🛠️ Stack tecnológico

![Python](https://img.shields.io/badge/Python-3.12-blue?logo=python)
![Pandas](https://img.shields.io/badge/Pandas-Data-150458?logo=pandas)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)

- **Librerías:** pandas, matplotlib, seaborn, numpy
- **Entorno:** Google Colab
- **Datos:** 5 tablas relacionales (órdenes, pagos, ítems, productos, categorías)
- **Técnicas:** merges, groupby, reconocimiento de ingresos, simulación contable, gráfico waterfall

---

## 📁 Estructura del proyecto

```
olist-financial-analytics/
│
├── olist_financial_analytics.ipynb   # Notebook principal
├── brazilian-ecommerce.zip           # Dataset fuente (Kaggle)
└── README.md
```

---

## 🔗 Contexto

Este proyecto fue desarrollado como caso de estudio personal para explorar la intersección entre **análisis de datos y contabilidad financiera** — un área clave en roles de analytics en empresas de e-commerce, retail y fintech.

---

## 👩‍💻 Autora

**Antonella Ríos**  
Junior Data Analyst | Python · SQL · Power BI · Machine Learning  
[LinkedIn](https://www.linkedin.com/in/antonellarios) · [GitHub](https://github.com/antonellarios)
