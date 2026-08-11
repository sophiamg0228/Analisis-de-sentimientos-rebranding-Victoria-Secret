# 💗 Análisis de Sentimientos — Rebranding de Victoria's Secret

## 📋 Descripción del Proyecto

Análisis de la percepción del público frente al rebranding de Victoria's Secret (2019–2023), en el que la marca eliminó a sus icónicos "Ángeles", lanzó el VS Collective y amplió su oferta a tallas inclusivas, cerrando el proceso con el documental "The Tour" (2023). El proyecto busca entender la crisis de relevancia que llevó a la marca a perder participación de mercado, y traducir esa comprensión en insights y estrategias de negocio.

## 👥 Integrantes

| Nombre | Rol |
|---|---|
| Manuela Giraldo | Análisis y desarrollo conjunto |
| Sophia Mateus | Análisis y desarrollo conjunto |

## 🎯 Objetivo

Comprender la respuesta del público al nuevo formato de Victoria's Secret y extraer insights accionables que le permitan a la marca equilibrar su apuesta por la inclusión con la esencia y el glamour que históricamente la caracterizaron.

## 🗂️ Fuente de Datos

Se seleccionaron 3 videos de YouTube con formatos distintos, para capturar la opinión desde ángulos complementarios:

- **Trailer oficial** de "The Tour '23" — la voz de la marca y la reacción inmediata del público.
- **Video de análisis** sobre el ascenso y caída de Victoria's Secret — enfocado en la crisis de identidad de marca.
- **Reseña de una influencer de moda** — una mirada externa y crítica al nuevo show.

Los comentarios se descargaron con `youtube-comment-downloader`, priorizados por popularidad (hasta 5,000 por video), capturando autor, texto, likes, respuestas, fecha y video de origen.

## 🛠️ Metodología

1. **Limpieza de texto**: conversión de emojis a texto, eliminación de URLs y caracteres especiales, filtrado a comentarios en inglés y español, y lematización para reducir las palabras a su raíz.
2. **Análisis exploratorio**: distribución de idiomas, densidad de contenido por video, nube de palabras y engagement por fuente.
3. **Análisis de sentimientos con RoBERTa** (`cardiffnlp/twitter-roberta-base-sentiment`), elegido por su buen desempeño interpretando contexto, sarcasmo y lenguaje coloquial de redes sociales.
4. **Contraste con VADER**: se descartó por su baja sensibilidad al lenguaje complejo (tendía a clasificar como positivos comentarios sarcásticos o nostálgicos).
5. **Validación manual**: muestra aleatoria de 150 comentarios (50 por sentimiento) clasificados manualmente y comparados contra RoBERTa, obteniendo una **precisión (accuracy) de 0.81**.
6. **Análisis temático**: embeddings semánticos (`sentence-transformers`) + clustering (K-Means) para identificar temáticas dentro de cada sentimiento (nostalgia, admiración, críticas a la representación, entre otras).

## 📊 Hallazgos Principales

- **41.9%** de los comentarios se clasificaron como negativos, frente a **21.8%** positivos.
- Los comentarios negativos promediaron **44.86 likes**, frente a **25.44** de los positivos — el descontento generó más engagement que la aprobación.
- El comentario con más likes de todo el dataset señala que el rechazo del público no es hacia la inclusión en sí, sino hacia la pérdida del glamour y la "fantasía" que caracterizaba al show original.
- Más de 170 comentarios se asociaron con nostalgia por el Fashion Show clásico, y tendían a ser negativos o neutrales.
- Los comentarios más extensos y con mayor engagement se concentraron en canales externos (no en el video oficial de la marca), lo que sugiere que Victoria's Secret perdió el control de la narrativa de su propio rebranding.

## 💡 Estrategias de Negocio Propuestas

1. **Regreso aspiracional**: reintroducir elementos icónicos del show (alas, brillo, glamour) modelados por el nuevo elenco diverso, en lugar de tratar inclusión y lujo como conceptos opuestos.
2. **Gestión de la nostalgia**: campaña de "Legado y futuro" que conecte a modelos históricas con las nuevas embajadoras, transformando la nostalgia negativa en orgullo por la evolución de la marca.
3. **Plan de contingencia y respuesta ante crisis**: estrategia de PR digital dirigida a analistas y líderes de opinión de moda, para recuperar el control de la narrativa pública.

## 🧰 Tecnologías Utilizadas

- **Python**: `pandas`, `re`, `emoji`, `langdetect`, `nltk`
- **NLP / Sentimiento**: `transformers` (RoBERTa), `vaderSentiment`
- **Embeddings y clustering**: `sentence-transformers`, `scikit-learn` (K-Means, Silhouette Score)
- **Visualización**: `matplotlib`, `seaborn`, `wordcloud`
- **Recolección de datos**: `youtube-comment-downloader`

## 📎 Notas

Este proyecto usa datos públicos de comentarios de YouTube (no incluye información personal identificable más allá de nombres de usuario públicos de la plataforma).
