# 📊 Análisis de Campaña de Marketing Bancario y Perfilado de Clientes

## 📄 Descripción
Este repositorio contiene un análisis exhaustivo de datos de una campaña de marketing de un banco portugués.  
El objetivo es **identificar los factores clave** que influyen en la suscripción de un cliente, aplicando limpieza de datos, ingeniería de características, análisis exploratorio (EDA) y validación estadística.

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
   - Manejo de valores nulos y duplicados usando python y las librerías numpy y pandas. 
   - Conversión de formatos (fechas, decimales)  
   - Creación de CSV limpio y unificado

3. **Análisis estadístico y visualización (EDA)**  
   - Estadísticas descriptivas: Se obtuvo una visión general de todas las variables, identificando puntos clave.
   - Análisis de outliers: Mediante boxplots, se identificaron valores atípicos en variables como duration y campaign. Se decidió conservarlos, ya que representaban comportamientos reales y valiosos para el análisis.
   - Análisis bivariado: Se cruzaron todas las variables relevantes contra el resultado (Subscription) mediante gráficos de barras , revelando los primeros perfiles de interés.
   - Mapas de correlación: Un mapa de calor mostró la relación entre las variables numéricas, destacando la fuerte correlación entre los indicadores macroeconómicos.

4. **Análisis estadístico inferencial**  
   - Prueba T para diferencias de ingresos: Confirmó que la diferencia en los ingresos entre los que se suscriben y los que no es estadísticamente significativa.
   - Chi-Cuadrado para relación profesión–resultado: Demostró que existe una asociación estadísticamente significativa entre la profesión del cliente y el resultado de la campaña.

---

## 📆 Resumen de Sesiones
- **Sesión 1**:
  
  • Se realiza la carga de los datos iniciales y el análisis inicial
  
  • Se abre la aplicación de Visual Studio Code, a partir de aquí se carga la carpeta Pandas_python a ttravés de la cual se va a trabajar para el proyecto de python for data.
      
  • Previo paso se hace una apertura del archivo customer_details.xlsx del cuál vamos a extraer las 3 páginas que de información de 2012/2013/2014.
      
  • Una vez hemos subido a jupyter notebook estos archivos y hemos importado pandas, numpy, seaborn y matplotib empezamos a realizar los primeros análisis de los datos.
      
  • Para los análisis empleamos los comandos head, info y hacemos un escrutinio o visualización general de todos los datos que tenemos en los archivos ( bamk-additional, customer_details-2012.csv, customer_details-2013.csv, customer_details-2014.csv).
      
  • Se hace el mismo patrón para todos, empezamos viendo las 5 primeras filas con head(). Posteriormente, buscamos información general con .info() y al final lo que vamos a hacer es ver donde encontramos los valores nulos haciendo un conteo por columnas con .isnull().sum().
      
  • De esta manera, obtenemos toda la información general de los datos y empezamos a aproximarnos en el manejo de los valores nulos y la posterior limpieza y tratamiento de los datos.

   **Sesión 2**
  
    • Se comienza con la limpieza de datos y el tratamiento de los mismos.
  
    • Corregimos los nombres de las columnas, sobre todo la columna ID, la cual se nombrará de esta manera para hacerla coincidir en todos los documentos con formato.CSV.
  
    • Se corrigen algunos tipos de datos ( string a números): columnas como cons.price.idx, cons.config.idx y euribor3m están como texto por usar comas como decimales.
  
    • Manejamos los valores nulos: las columnas age, education, default, housing, loan y euribor3m tienen valores nulos, debemos manejarlos y tratarlos.
  
    • Convertimos fechas.
  
    • Tras observar los datos que tenemos de forma inicial, se ha visto que la columna en común entre ambos datos ha sido la columna ID, esto lo que provoca es que el unico punto de unión de estos datos es ID, por lo que tendremos que renombrar adecuadamente las dos columnas en los dos dataframes que vamos a tener df_bank y df_customers.
      
    • Tras el análisis de nulos se ha visto que hay que corregir datos que están en formato string y hay que pasarlo a formato número, es por ello que tenemos que corregir las comas que convierte los números en texto y sustituirlos por un punto, esto ocurre en columnas como cons.prince.idx, cons.conf.idx y euribor3m.
      
    • Los valores nulos los vamos a manejar en las columnas age, education, default, housing, loan y euribor3m. La decisión que se ha tomado para manejar estos datos ha sido: 
      
    • Los valores de Age y euribor3m usamos la mediana rellenando los nulos con los datos de la mediana que en este caso son más robustos a posibles outliers sobre todo en variables asimétricas como son la edad y euribor3
      
    • Para las variables categóricas como housing, default, loan y education se va a sustituir los valores nulos por el término unknown, permitiéndonos así conocer aquellos casos desconocidos o que no se ha registrado este dato.
      
    • Para las fechas, utilizamos la base locale para permitir que las fechas queden correctamente registradas y que los meses se puedan reconocer en español.
      
    • La variable Age, se modifica a valores enteros ya que no es un número decimal.
      
    • En el caso del data frame de customers, tras unir todos los datos, encontramos que hay que manejar un poco los datos y hacer pequeñas transformaciones.
      
    • cambiamos el valor de la columna ID. hacemos lo de las fechas y en el campo income utilizamos la mediana también para poder tener y rellenar los datos nulos.

  **Sesión 3**
  
    • Se revisa que los datos estén limpios y se hace una fusión de los dataframes , a partir de la columna ID, renombrando el archivo.
  
    •  Para enriquecer el análisis, se crean nuevas columnas más descriptivas:
             - Education: se agruparon los diferentes niveles de educación básica ( basic.4y,basic.6y, basic.9y, illiterate) en una única categoría llamada : “basic”.
  
    • AgeGroup: Se segmentó la edad de los clientes en cuatro grupos categóricos para facilitar el análisis: 'Joven (18-30)', 'Adulto (31-45)', 'Adulto Mayor (46-60)' y 'Senior (60+)'.
  
    • PreviouslyContacted: Se transformó la columna numérica pdays (con el valor especial 999) en una variable binaria (Yes/No) que indica claramente si un cliente había sido contactado previamente.
  
    •  Se realiza un nuevo análisis de valores nulos y se observa un error de 471 valores nulos en la columna cons.price.idx. Dichos nulos fueron imputados usando la media de la columna para no perder información valiosa.
  
    •  Se renombró la variable ‘y’ por ‘ Subscription’.
  
    •  Se eliminaron las columnas originales que ya no eran necesarias (education, pdays, date) y aquellas que no aportaban valor al análisis (ID, latitude, longitude).
  
    • Finalmente, se reorganizaron las columnas del DataFrame para agruparlas de manera lógica: datos demográficos, datos de la campaña e indicadores económicos, dejando la variable ‘Subscription’ al final.
  
    • El proceso completo culmina en la creación de un archivo CSV final: bank_data_EDA_ready.csv. Este archivo contiene el conjunto de datos limpio, procesado y listo para la siguiente fase de análisis visual exhaustivo.
  
- **Sesión 4**: Análisis descriptivo y EDA avanzado
- 
    • Se realiza la primera parte del análisis descriptivo y vemos los primeros datos de la media, mediana, cuartiles, desviaciones estándar de las diferentes columnas tanto para las variables numéricas como las variables categóricas.
  
    • El objetivo de la sesión de hoy fue profundizar en el análisis exploratorio de datos (EDA), moviéndonos más allá de las métricas básicas para realizar un análisis exhaustivo. Se buscaba descubrir relaciones más complejas entre las variables, validar los hallazgos con rigor estadístico y preparar el terreno para la creación de un informe final completo.
  
    • Análisis de Interacción de Variables:
        ◦ Técnica: Se utilizó un gráfico de facetas (catplot) para analizar si el efecto de los ingresos (Income) sobre la suscripción (Subscription) era consistente a través de los diferentes grupos de edad (AgeGroup).
  
    • Análisis de Antigüedad del Cliente:
        ◦ Técnica: Se calculó la antigüedad de cada cliente en años a partir de su fecha de alta en el banco (Dt_Customer) y se comparó la distribución de esta variable entre los que aceptaron la oferta y los que no.
  
    • Análisis de Efectividad de Campañas Anteriores:
        ◦ Técnica: Se analizó la variable poutcome (resultado de la campaña anterior) y se visualizó la tasa de éxito actual para cada categoría mediante un gráfico de barras 100% apilado.
  
- **Sesión 5 y 6**: Visualizaciones y pruebas estadísticas

    • Se realizan más gráficos y pruebas de estadística inferencial ( Prueba de T y valor de Chi-Cuadrado
    • Se realiza un gráfica de correlación de datos
  
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

