# Extracción de víctimas y victimarios de extorsión con LLM local

Prototipo que convierte noticias policiales sobre extorsión en una base de datos estructurada,
usando un modelo de lenguaje que corre localmente (Ollama + `qwen2.5:7b`), sin costo de API.

Basado en la metodología de Ortiz y Freitas (2025), *Automated News Scraping and AI-Powered
Analysis for Municipal Crime Mapping* (ICAART 2025).

## Estructura de datos

noticias (1) ──► eventos (1) ──► actores (N)

- **eventos:** un caso de extorsión (distrito, modalidad, organización, resumen).
- **actores:** una fila por cada víctima o victimario (rol, tipo, rubro, sexo, edad, cantidad, detenido).

## Archivos

| Archivo | Descripción |
|---|---|
| `paso1_extraccion_llm.ipynb` | Primer prototipo: esquema, extracción y validación con noticias ficticias |
| `reporte_avance_actores_extorsion.ipynb` | Reporte de avance: esquema de actores, prompt y resultados |
| `eventos.csv` | Eventos extraídos |
| `actores.csv` | Actores extraídos |
| `eventos_piloto.csv` | Eventos extraídos ejemplo|


## Resultados preliminares

Con una noticia de prueba, el modelo generó 1 evento y 7 actores (3 victimarios y 4 víctimas),
sin nombres propios, y registró a los 12 detenidos. Pendiente: mejorar la clasificación y medir la precisión con 10 noticias.

## Requisitos

pip install ollama pydantic pandas notebook
ollama pull qwen2.5:7b

## Datos y privacidad

- No se incluyen textos originales de noticias (derechos de autor); se indica la URL de la fuente.
- No se almacenan nombres de personas; los alias publicados por la prensa se omiten.

Autora: Paola Prado — Universidad Nacional de Ingeniería
