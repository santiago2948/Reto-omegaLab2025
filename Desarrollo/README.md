# 💻 Desarrollo – OmegaLab 2025

## ¡Bienvenidos a la carpeta de Desarrollo!

Aquí se debe subir **todo el material y avances técnicos** que el área de Desarrollo genere durante el reto OmegaLab 2025.

---


# Objetivo:
Desarrollar un sistema predictivo/autocorrectivo capaz de identificar estudiantes universitarios en riesgo de sufrir estrés académico, utilizando datos provenientes de plataformas educativas y variables psicológicas y contextuales. Habiendo identificado la posibilidad de comenzar a padecer estres academico generar estrategias de correccion para impedir el avance del estres academico. Nuesro sistema tiene como factor diferenciador el ayudar a los estudiantes a generarse planes de estudio y hacaer las veces de monitor personal para las asignaturas usando todo el amterial de las clases para generar explicaciones y contenido grafico qeu ayude a la obtencion de los objetivos academicos que se tenga.

# Documentación técnica:

## Modelos predictivos a utilizar:

Se va a realizar uso de una combinacion de modelos con el objetivo de obtener una mayor presision en cuento a las predicciones usando la tecnica de el aprendizaje en conjunto implica la combinación de varios modelos de aprendizaje automático para obtener un rendimiento predictivo superior al de cualquier modelo individual. Al integrar diferentes modelos, se pueden capturar diversas perspectivas y reducir errores individuales, lo que resulta en predicciones más robustas y precisas. Para nuestro caso se espera una precisión superior al 80% en la identificación de estudiantes en riesgo.

### Regresion logistica
**Aplicación:** Identificación de factores asociados al estrés académico.

**Justificación:** Un estudio en la Universidad Politécnica Metropolitana de Hidalgo utilizó regresión logística para determinar que la carga académica y las responsabilidades adicionales son factores significativos en el estrés estudiantil

### Árboles de Decisión

**Aplicación:** Clasificación de estudiantes según niveles de estrés.

**Justificación:** Investigaciones han demostrado que los árboles de decisión pueden predecir eficazmente el nivel de estrés percibido en estudiantes, considerando factores académicos, personales, sociales, institucionales y económicos. ​

### Redes Neuronales Artificiales (Perceptrón Multicapa - MLP)

**Aplicación:** Predicción de efectos fisiológicos causados por el estrés académico.

**Justificación:** Estudios han utilizado modelos MLP para predecir efectos fisiológicos del estrés académico, considerando variables como la procrastinación, el nivel de estrés percibido, la edad y el ingreso económico.

### Variables Académicas
**Fechas de Evaluaciones:** Proximidad y acumulación de exámenes y entregas.

**Cantidad de Trabajo Asignado:** Número de tareas y proyectos en un período determinado.

**Notas:** Descenso en el rendimiento académico.

**Inasistencias:** Aumento en la frecuencia de ausencias a clases.

### Referencias 
- Arrogante, O. (2021). Identificación de Causas del Estrés Académico en Estudiantes de la Universidad Politécnica Metropolitana de Hidalgo. Revista RIDE.

- Lopez Quiroz, L. A., & Soto Salazar, J. G. (2023). Árboles de decisión para la predicción temprana de estrés académico en estudiantes de la Facultad de Ciencias. Universidad Nacional José Faustino Sánchez Carrión.

- Mora Romo, J., & Martell Muñoz, J. (2021). Predicción de efectos fisiológicos causados por el estrés académico mediante redes neuronales artificiales. Revista Iberoamericana de Psicología.

# 📘 Tecnologías Utilizadas

Este proyecto implementa un sistema predictivo de estrés académico utilizando un enfoque de microservicios, event-driven y generación aumentada por recuperación (RAG).

---

## 🖥️ Frontend

| Componente | Tecnología |
|:-----------|:-----------|
| **Single Page Application** | [React.js](https://reactjs.org/) + JavaScript |

- Proporciona la interfaz para estudiantes y administradores.
- Comunicación vía API REST con el backend.

---

## 🛠️ Backend

| Componente | Tecnología | Función |
|:-----------|:------------|:--------|
| **API Gateway** | Python + [FastAPI](https://fastapi.tiangolo.com/) | Autenticación, autorización y enrutamiento de peticiones. |
| **LMS Connector** | Python + FastAPI | Sincroniza datos académicos desde el LMS institucional. |
| **Servicio de Predicción de Estrés** | Python + FastAPI + [scikit-learn](https://scikit-learn.org/) / [TensorFlow](https://www.tensorflow.org/) | Predicción de nivel de estrés basado en métricas académicas. |
| **Servicio de Plan de Estudio & Tutoría AI** | Python + FastAPI + [Pinecone](https://www.pinecone.io/) + [OpenAI API](https://platform.openai.com/) | Generación automática de itinerarios de estudio personalizados (RAG). |
| **Servicio de Notificaciones** | Python + FastAPI + [Celery](https://docs.celeryq.dev/en/stable/) (opcional) | Envío de tests emocionales, recordatorios y alertas por diferentes canales. |

---

## 🛢️ Bases de Datos

| Componente | Tecnología |
|:-----------|:-----------|
| **LMS Data** | PostgreSQL |
| **Métricas Académicas DB** | PostgreSQL |
| **DB de Notificaciones** | Redis |
| **Notificator DB (Embeddings)** | Pinecone o Weaviate |

---

## 🔗 Integraciones Externas

| Servicio | Tecnología |
|:---------|:-----------|
| **API LLM** | OpenAI (GPT-4o) / Anthropic Claude / Google PaLM |

Utilizados para la generación de planes de estudio, ejemplos y explicaciones personalizadas.

---

## 📩 Comunicación Asíncrona

| Componente | Tecnología |
|:-----------|:-----------|
| **Bus de Eventos** | Apache Kafka |

- Publicación y consumo de eventos académicos (e.g., `lms.data`).
- Activación de procesos asincrónicos (cálculo de estrés, generación de test, envío de notificaciones).

---

## ⚙️ Infraestructura

| Componente | Tecnología |
|:-----------|:-----------|
| **Contenerización** | Docker, Docker Compose |
| **Orquestación (Opcional)** | Kubernetes |
| **Monitorización** | Prometheus + Grafana |
| **Gestión de logs** | ELK Stack (Elasticsearch, Logstash, Kibana) |
| **Autenticación** | OAuth2 / JWT |

---

# 📋 Resumen de Stack

- **Frontend**: React.js  
- **Backend**: Python (FastAPI)
- **Machine Learning**: scikit-learn o TensorFlow
- **Bases de Datos**: PostgreSQL + Redis + Pinecone
- **Mensajería**: Apache Kafka
- **Generación de Contenido**: OpenAI API / Claude API
- **Contenedores**: Docker

---

# 📈 Notas Finales

- El sistema está diseñado para ser escalable y resiliente.
- El patrón de eventos desacopla los microservicios y facilita la extensibilidad.
- Se enfoca en intervenciones tempranas para mejorar el bienestar académico de los estudiantes.


### Diagrama de flujo:
![Texto alternativo](./flujo.drawio.png)

### Diagrama de contexto:
![Texto alternativo](./contexto.drawio.png)

### Diagrama de contenedores:
![Texto alternativo](./Diagrama%20sin%20título.drawio.png)


> ℹ️ **Nota:** No es necesario seguir un formato exacto, pero es importante mantener el contenido organizado, claro y actualizado para facilitar su revisión.

---

¡Mucho éxito programando y creando cosas increíbles! 🚀
