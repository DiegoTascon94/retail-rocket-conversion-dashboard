# 🛒 E-commerce Funnel & Conversion Intelligence — Retail Rocket

## 🎯 Contexto del Negocio
En el e-commerce, la mayoría de los visitantes nunca completan una compra. Entender dónde se rompe el funnel, qué segmentos de usuarios tienen mayor potencial de conversión y qué variables del comportamiento predicen una transacción son preguntas críticas para cualquier equipo comercial o de marketing digital. Este proyecto desarrolla un análisis end-to-end sobre el dataset público de Retail Rocket, cubriendo desde el funnel de conversión hasta un modelo predictivo de Random Forest, con resultados comunicados en un dashboard ejecutivo de 5 vistas en Power BI.

---

## 🚀 Objetivo del Proyecto
Desarrollar un análisis end-to-end sobre el comportamiento de usuarios en una plataforma de e-commerce que permita:

- Medir y visualizar el funnel de conversión global y por categoría de producto.
- Identificar patrones temporales de actividad y conversión por hora y día de la semana.
- Cuantificar el abandono de carrito y el revenue recuperable asociado.
- Segmentar la base de usuarios mediante K-Means (k=4) para estrategias diferenciadas.
- Predecir la probabilidad de conversión de un visitante con un modelo Random Forest.

---

## 📊 Alcance del Proyecto
- **Fuente de datos:** Retail Rocket Recommender System Dataset (Kaggle) — 2.7M+ eventos de comportamiento.
- **Período:** Mayo — Septiembre 2015.
- **Eventos analizados:** `view`, `addtocart`, `transaction`.
- **Módulos:** 8 módulos analíticos estructurados en un único notebook documentado.
- **Stack completo:** Python → SQLite → Power BI.

---

## 💡 Principales Insights

- **Funnel con caída crítica en AddToCart:** Solo el 2.69% de visitantes agrega al carrito y el 0.84% completa una transacción, evidenciando una oportunidad de optimización significativa en la etapa de consideración.
- **Miércoles como día pico de conversión:** La tasa de conversión alcanza su máximo los miércoles, mientras que fines de semana registran caídas del 35% respecto al promedio semanal.
- **71.96% de tasa de abandono:** Más de 27,000 carritos son abandonados, con el 73% del abandono ocurriendo en los primeros 30 minutos — ventana crítica para campañas de retargeting.
- **Revenue recuperable cuantificado:** Calculado sobre el precio mediano real de los ítems (extraído de `item_properties`, propiedad 790), representando una oportunidad concreta de recuperación con estrategias de remarketing.
- **Compradores con Intención como segmento prioritario:** Con una tasa de conversión del 28% y un promedio de 1.56 AddToCart, este segmento representa el mayor retorno por esfuerzo de retención.
- **Random Forest con diseño temporal anti-leakage:** El modelo se entrena sobre el 70% inicial del período (features) y predice conversiones en el 30% posterior (target), simulando condiciones reales de producción. Las variables de mayor importancia predictiva son `total_atc` y `atc_rate`.

---

## 🛠️ Enfoque Técnico
El proyecto sigue un flujo analítico estructurado en 8 módulos que simula un entorno profesional real:

- **Python:** Limpieza, exploración, análisis de funnel, segmentación K-Means y modelado predictivo con Scikit-learn.
- **SQLite:** Almacenamiento intermedio del dataset procesado para consultas eficientes.
- **Power BI:** Dashboard ejecutivo de 5 vistas conectado a los CSVs exportados desde Python.

---

## 🧠 Impacto en Decisiones de Negocio

- **Optimización del funnel:** Las categorías con mayor tasa de conversión permiten focalizar inversión publicitaria donde el retorno es más predecible.
- **Recuperación de carritos:** El 73% de abandono en los primeros 30 minutos define una ventana de acción concreta para campañas de email o notificaciones push inmediatas.
- **Personalización por segmento:** Los 4 clusters habilitan estrategias diferenciadas — reactivación para Visitantes Fantasma, incentivos para Exploradores Pasivos y programas de fidelización para Usuarios Fieles y Compradores con Intención.
- **Modelo predictivo en producción:** El RF Optimizado usa separación temporal (feature window / target window) para evitar data leakage y puede integrarse en un sistema de scoring en tiempo real para priorizar visitantes con alta probabilidad de conversión.

---

## 💻 Tecnologías y Herramientas

- **Lenguaje:** Python
- **Librerías:** Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn
- **Base de datos:** SQLite
- **Visualización:** Power BI
- **Control de versiones:** Git & GitHub

---

## 📂 Estructura del Repositorio
```
├── notebook/                  # Análisis end-to-end documentado (8 módulos)
├── data/
│   ├── category_tree.csv      # Árbol de categorías del dataset
│   └── powerbi/               # CSVs exportados para Power BI (13 archivos)
├── dashboard/                 # Capturas del dashboard Power BI
├── README.md                  # Documentación del proyecto
└── requirements.txt           # Dependencias del entorno
```

---

## ▶️ Cómo Ejecutar el Proyecto

1. **Clonar el repositorio:**
```bash
git clone https://github.com/DiegoTascon94/retail-rocket-conversion-dashboard.git
```

2. **Descargar el dataset original:**
   - El dataset no está incluido en el repositorio por su tamaño (~1GB).
   - Descargarlo desde [Kaggle — Retail Rocket Recommender System Dataset](https://www.kaggle.com/datasets/retailrocket/ecommerce-dataset)
   - Colocar los archivos en `data/`:
     - `events.csv`
     - `item_properties_part1.csv`
     - `item_properties_part2.csv`

3. **Instalar dependencias:**
```bash
pip install -r requirements.txt
```

4. **Ejecutar el notebook:**
   - Abrir `notebook/retail_rocket.ipynb` en Jupyter
   - Ejecutar las celdas en orden — el notebook genera automáticamente todos los CSVs en `data/powerbi/`

5. **Explorar el dashboard:**
   - Las capturas del dashboard están disponibles en `dashboard/`
   - Para abrir el archivo `.pbix` contactar al autor — el archivo no está incluido en el repositorio por su tamaño.

---

## 📝 Conclusiones
Este proyecto demuestra cómo un análisis end-to-end de comportamiento de usuarios puede transformar eventos crudos de e-commerce en inteligencia comercial accionable. La combinación de Python, SQLite y Power BI refleja un flujo de trabajo profesional donde cada herramienta cumple un rol específico: análisis y modelado, almacenamiento eficiente, y comunicación ejecutiva de resultados.

---

## 🔮 Próximos Pasos / Mejoras Futuras

- **Scoring en tiempo real:** Integrar el modelo RF Optimizado en un pipeline de scoring que evalúe visitantes activos y active ofertas personalizadas en función de su probabilidad de conversión.
- **Análisis de cohortes:** Incorporar análisis de retención por cohorte para identificar qué períodos de adquisición generan usuarios de mayor valor a largo plazo.
- **Recomendador de productos:** Explotar la estructura del dataset para construir un sistema de recomendación basado en comportamiento colaborativo, aprovechando las relaciones entre visitantes e ítems.
- **Migración a nube:** Migrar el pipeline a un entorno cloud (AWS S3 + Redshift o GCP BigQuery) para escalar el análisis a volúmenes de datos en tiempo real.