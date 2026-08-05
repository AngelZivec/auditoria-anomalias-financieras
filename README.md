# auditoria-anomalias-financieras
Pipeline End-to-End (Python, SQL, Power BI) para la detección de fugas de capital, pagos duplicados y simulación S&amp;OP de recuperación legal.

# 🕵️‍♂️ Auditoría Forense y Detección de Anomalías Financieras
**Pipeline End-to-End para el análisis de riesgo, detección de pagos duplicados y simulación de cobranza S&OP.**

Este proyecto es un caso de estudio corporativo diseñado para resolver un problema crítico en el departamento de Cuentas por Pagar: la fuga de capital por vulnerabilidades en los controles internos (Dirty Data, pagos fraccionados y duplicidad de folios).

## 🛠️ Stack Tecnológico
* **Extracción y Limpieza:** Python (Pandas)
* **Modelado y Almacenamiento:** SQL Server (Transact-SQL)
* **Visualización y Business Intelligence:** Power BI (DAX Avanzado)

## 🏗️ Arquitectura del Proyecto

El flujo de datos se diseñó bajo un enfoque *End-to-End* simulando un entorno empresarial real (tomando como base datos públicos de contrataciones de Compranet):

1. **Fase 01 - Extracción & Transformación (Python):** 
   Lectura de archivos CSV históricos. Estandarización de diccionarios de datos (tipos de contratación), limpieza de espacios invisibles y *casteo* de fechas. Inyección de anomalías sintéticas controladas (duplicados exactos, duplicados parciales y fraccionamiento de pagos) para pruebas de estrés del modelo.
2. **Fase 02 - Almacenamiento & Reglas de Negocio (SQL Server):** 
   Creación de vistas relacionales maestras (`vw_Auditoria_Riesgo_Financiero`). Implementación de funciones de ventana (`COUNT() OVER PARTITION BY`) para auditar la frecuencia de pagos ignorando errores tipográficos intencionales en el ERP.
3. **Fase 03 - Visualización y Toma de Decisiones (Power BI):** 
   Despliegue de un Centro de Mando directivo dividido en tres ejes:
   * **S&OP Financiero:** Simulador *What-If* para calcular la provisión de pérdida vs. meta de capital a recuperar.
   * **Inteligencia Estratégica:** Gráfico de Pareto (Regla 80/20 calculada con DAX) para priorizar el esfuerzo del equipo legal sobre los mayores ofensores.
   * **Ejecución Táctica:** Matriz transaccional dinámica que aísla los folios exactos listos para emitir retenciones de pago.

## 📂 Estructura del Repositorio

- `/scripts_python`: Contiene el script de ETL y generación de anomalías (`data_prep.py`).
- `/scripts_sql`: Contiene las consultas DDL y DML para la generación de vistas de auditoría (`auditoria_views.sql`).
- `/dashboard`: Archivo `.pbix` de Power BI (Versión pública/demo).
- `/docs`: Diagrama de arquitectura del pipeline de datos.

---
*Nota: El manual de usuario detallado para la navegación de la interfaz de Power BI se encuentra actualmente en desarrollo y será añadido en futuras iteraciones.*
