# Respuestas del workshop RAG
Escribe aquí tus respuestas con tus propias palabras. Pega tablas, resultados y enlaces a las capturas de `evidencias/`.

---

# Bloque 0 · Teoría

## T1 · Cuántos nodos viven en cada capa

_Evidencia:_ …
import numpy as np

M = 16
mL = 1 / np.log(M)
N = 1_000_000
rng = np.random.default_rng(0)
l = np.floor(-np.log(1 - rng.random(N)) * mL).astype(int)

for k in range(1, 4):
    print(f"capa >= {k}: simulado={(l >= k).sum():>7,}  teórico={N / M**k:>9,.0f}")
    
_Mi respuesta / análisis:_
capa >= 1: simulado= 62,675  teórico=   62,500
capa >= 2: simulado=  4,005  teórico=    3,906
capa >= 3: simulado=    270  teórico=      244

Es bueno que hayan pocos Hubs para evitar altos tiempos de computo con el greedy

## T2 · ef, k y el tamaño de la cola

_Evidencia:_ …

_Mi respuesta / análisis:_
Si pongo ef = 5 y k = 10 falla porque no hay suficientes vecinos 5<10
ef = 2·k , Si el recall es insuficiente, súbelo. Para la mayoría de aplicaciones RAG ef = 50–100 con k = 5–10 da >95% recall.
ef y ef construction son el mismo concepto, pero ef construction es para inicializar y tocaria reiniciar el indice, mientras que ef no

## T3 · Inserción frente a búsqueda

_Evidencia:_ …

_Mi respuesta / análisis:_




## T4 · El invariante de FAISSVectorStore

_Evidencia:_ …

_Mi respuesta / análisis:_


## T5 · El costo de la fuerza bruta

_Evidencia:_ …

_Mi respuesta / análisis:_


---

# Bloque A · App RAG empresarial

## A1 · Ejecuta la app RAG de punta a punta

_Evidencia:_ …
<img width="1668" height="630" alt="image" src="https://github.com/user-attachments/assets/8a5513ad-5dac-4feb-ab65-77913e104d4f" />

_Mi respuesta / análisis:_


## A2 · Tu propio corpus de documentos

_Evidencia:_ …

_Mi respuesta / análisis:_


## A3 · Ingeniería del prompt (antes y después)

_Evidencia:_ …

_Mi respuesta / análisis:_


## A4 · Muestra el score de similitud en las fuentes

_Evidencia:_ …

_Mi respuesta / análisis:_


---

# Bloque B · RAG sobre papers

## B1 · Ejecuta el RAG de papers y evalúa con el ground truth

_Evidencia:_ …

_Mi respuesta / análisis:_


## B2 · Experimentos con chunk_size, k y score_threshold

_Evidencia:_ …

_Mi respuesta / análisis:_


## B3 · Preguntas trampa: ¿el RAG admite que no sabe?

_Evidencia:_ …

_Mi respuesta / análisis:_


## B4 · Preguntas en español sobre papers en inglés

_Evidencia:_ …

_Mi respuesta / análisis:_


## B5 · Escribe tu propio quiz con ground truth

_Evidencia:_ …

_Mi respuesta / análisis:_


---

# Reflexión

## R1 · Reflexión final con tus datos

_Evidencia:_ …

_Mi respuesta / análisis:_


---

# Retos

## C1 · HNSW contra fuerza bruta con FAISS

_Evidencia:_ …

_Mi respuesta / análisis:_


## C2 · Un tercer paper: el RAG que explica HNSW

_Evidencia:_ …

_Mi respuesta / análisis:_


## C3 · App Gradio para los papers con filtro por paper

_Evidencia:_ …

_Mi respuesta / análisis:_


## C4 · Evaluación automática de la recuperación

_Evidencia:_ …

_Mi respuesta / análisis:_


## C5 · MMR frente a similitud pura

_Evidencia:_ …

_Mi respuesta / análisis:_


## C6 · Persistencia del índice en disco

_Evidencia:_ …

_Mi respuesta / análisis:_

