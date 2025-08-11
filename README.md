# 📊 Análisis de Campaña de Marketing Bancario y Perfilado de Clientes

## 📄 Descripción
Este repositorio contiene un análisis exhaustivo de datos de una campaña de marketing de un banco portugués.  
El objetivo es **identificar los factores clave** que influyen en la suscripción de un cliente a un depósito a plazo fijo, aplicando limpieza de datos, ingeniería de características, análisis exploratorio (EDA) y validación estadística.

---

## 🎯 Objetivos del Proyecto
- Identificar características demográficas y de comportamiento de clientes que aceptan la oferta.
- Analizar resultados de campañas de telemarketing anteriores.
- Validar hallazgos con pruebas estadísticas.
- Proporcionar recomendaciones basadas en datos para mejorar futuras campañas.

---

## 📊 Conjunto de Datos

### **bank-additional.csv**
- `age`: Edad del cliente  
- `job`: Profesión  
- `marital`: Estado civil  
- `education`: Nivel educativo  
- `default`: Historial de incumplimiento (1: Sí, 0: No)  
- `housing`: Préstamo hipotecario (1: Sí, 0: No)  
- `loan`: Otro préstamo (1: Sí, 0: No)  
- `contact`: Método de contacto  
- `duration`: Duración de la última interacción (segundos)  
- `campaign`: Nº de contactos en la campaña  
- `pdays`: Días desde el último contacto  
- `previous`: Nº de contactos previos  
- `poutcome`: Resultado de la campaña anterior  
- `emp.var.rate`, `cons.price.idx`, `cons.conf.idx`, `euribor3m`, `nr.employed`: Indicadores macroeconómicos  
- `y`: Suscripción (Sí/No)  
- `date`, `contact_month`, `contact_year`: Fechas de contacto  
- `id_`: Identificador único  

### **customer-details.xlsx**
Contiene datos demográficos y de comportamiento de compra (3 hojas, años distintos):
- `Income`: Ingreso anual  
- `Kidhome`: Nº de niños en el hogar  
- `Teenhome`: Nº de adolescentes  
- `Dt_Customer`: Fecha de alta como cliente  
- `NumWebVisitsMonth`: Visitas mensuales al sitio web  
- `ID`: Identificador único del cliente  

---

## 📂 Estructura del Proyecto
```bash

├── Gráficos
├── Proyecto_python_data               # proyecto en python completo
├── Pruebas                            # hoja de pruebas 
├── bank_data_EDA_ready                # Datos finales y limpios
├── bank_data_reordenado
├── bank_additional
├── Customer-details                   # Dividido en 2012, 2013 y 2014
└── Readme.md
```


## ✍️ Metodología

1. **Carga de datos**  
   - Subida de archivos CSV y Excel
   - Revisión de datos cargados

2. **Limpieza de datos**  
   - Renombrado de columnas  
   - Manejo de valores nulos  
   - Conversión de formatos (fechas, decimales)  
   - Creación de CSV limpio y unificado

3. **Análisis estadístico y visualización (EDA)**  
   - Estadísticas descriptivas  
   - Análisis de outliers  
   - Análisis bivariado  
   - Mapas de correlación

4. **Análisis estadístico inferencial**  
   - Prueba T para diferencias de ingresos  
   - Chi-Cuadrado para relación profesión–resultado

---

## 📆 Resumen de Sesiones
- **Sesión 1 a 3**: Carga, limpieza, unificación y enriquecimiento de datos  
- **Sesión 4**: Análisis descriptivo y EDA avanzado  
- **Sesión 5 y 6**: Visualizaciones y pruebas estadísticas  
- **Sesión 7**: Creación de la variable `interest_score`, subida a GitHub

---

## 📝 Resultados y Conclusiones

**Hallazgos clave:**
1. **Perfil demográfico**:  
   - Más éxito en jóvenes (estudiantes) y seniors (jubilados)  
   - Ingreso no es el factor más decisivo

2. **Comportamiento en campaña**:  
   - Duración de llamada = mejor predictor  
   - Exceso de contactos reduce conversión

3. **Historial pasado**:  
   - Clientes con `poutcome = success` → >65% conversión

---

## 💡 Recomendaciones
1. Re-segmentar audiencias (Jóvenes/Estudiantes y Seniors/Jubilados)
2. Optimizar estrategia de contacto (máx. 3-4 intentos, priorizar calidad)
3. Priorizar clientes con historial exitoso
4. Simplificar criterios eliminando variables sin valor predictivo

---

## 🔜 Próximos pasos
- **A/B Testing**: Comparar estrategias actual vs. segmentada
- **Dashboard BI**: Tableau o Power BI para monitoreo continuo
- **Machine Learning**: Modelo predictivo de suscripción

---

## 🤝 Contribuciones
Las contribuciones son bienvenidas.  
Abre un *pull request* o *issue* para proponer mejoras.

---

## 👏 Autores y Agradecimientos
Agradecimientos a **The Power** por la oportunidad de desarrollar este proyecto en el marco de Data & Analytics.

