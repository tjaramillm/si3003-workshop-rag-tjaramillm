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
**Busqueda**
No sortea
Parametros en capa principal : ef en 0
ef en capas altas = 1
No modifica el inice

**Insercion**
Si sortea por decaimiento exponencial
Parametros en capa prinicipal = ef_construction en l hasta capa 0
ef en capas altas = 1
Modifica el indice


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

¿Cuántos días pueden trabajar remotamente los empleados?
Hasta 3 días por semana, con aprobación del jefe directo.

¿Cuál es el precio del plan Enterprise de CloudSync Pro?
El plan Enterprise de CloudSync Pro cuesta $49/mes por usuario con compromiso anual.

¿Qué pasa con los reembolsos mayores a $100?
Requieren aprobación del supervisor. Una vez aprobados, se procesan en 3 a 5 días hábiles al método de pago original.

¿Qué ocurre durante la primera semana de onboarding?
Durante la primera semana se completan módulos obligatorios de seguridad, cumplimiento y cultura de la empresa.

quien conquisto america?
No tengo esa información en el contexto proporcionado.

## A2 · Tu propio corpus de documentos

_Evidencia:_ …
    {
        "id": "product_001", "title": "CloudSync Pro — Precios",
        "content": "El plan Enterprise cuesta $49/mes por usuario con compromiso anual. El plan mensual sin compromiso cuesta $59/mes por usuario.",
        "metadata": {"department": "sales", "type": "pricing"},
    },
    {
        "id": "hr_001", "title": "Política de trabajo remoto",
        "content": "Los empleados pueden trabajar de forma remota hasta 3 días por semana, con aprobación del jefe directo.",
        "metadata": {"department": "hr", "type": "policy"},
    },
    {
        "id": "finance_001", "title": "Política de reembolsos",
        "content": "Los reembolsos mayores a $100 requieren aprobación del supervisor. Una vez aprobados, se procesan en 3 a 5 días hábiles al método de pago original.",
        "metadata": {"department": "finance", "type": "policy"},
    },
    {
        "id": "hr_002", "title": "Onboarding",
        "content": "Durante la primera semana se completan módulos obligatorios de seguridad, cumplimiento y cultura de la empresa.",
        "metadata": {"department": "hr", "type": "procedure"},
    },
    {
    "id": "ventas_001","title": "Política de descuentos",
    "content": "Los descuentos superiores al 15 % requieren aprobación del gerente comercial",
    "metadata": {"department": "ventas", "type": "policy"}
    },
    {
    "id": "comida_001","title": "Menu del día",
    "content": "El menu del dia es frijoles con chicharron y de bebida hay guandolo",
    "metadata": {"department": "food", "type": "context"}
    }

<img width="1551" height="540" alt="image" src="https://github.com/user-attachments/assets/389771fa-34d4-4eac-a22c-6423c529dac4" />

_Mi respuesta / análisis:_
cual es la bebida del menu?La bebida del menú es guandolo.

cual es el menu del día?El menú del día es frijoles con chicharrón y de bebida hay guandolo.

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

