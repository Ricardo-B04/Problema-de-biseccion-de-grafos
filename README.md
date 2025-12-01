# Bisección de Grafos con Algoritmo Genético

Implementación de un Algoritmo Genético para resolver el problema de bisección de grafos, desarrollado como parte del curso de **Algoritmos Matemáticos Bioinspirados** del Tecnológico de Monterrey.

## 📋 Descripción del Problema

El **problema de bisección de grafos** consiste en dividir un grafo no dirigido $G = (V, E)$ en dos subconjuntos de vértices de igual tamaño, minimizando el número de aristas que cruzan entre ambos subconjuntos (aristas de corte).

### Definición Formal
- **Entrada:** Grafo $G = (V, E)$ con $|V| = N$ nodos
- **Objetivo:** Encontrar partición $(S, \bar{S})$ donde $|S| = |\bar{S}| = N/2$
- **Minimizar:** $\text{cut}(S) = |\{(u,v) \in E : u \in S, v \in \bar{S}\}|$

### Complejidad
Este problema es **NP-completo**, lo que justifica el uso de metaheurísticas como los Algoritmos Genéticos.

## 🧬 Algoritmo Genético

### Representación
- **Cromosoma:** Vector binario de tamaño $N$
- `0` = Nodo pertenece al Grupo A
- `1` = Nodo pertenece al Grupo B
- **Restricción:** Exactamente $N/2$ unos (balance cardinal)

### Operadores
| Operador | Descripción |
|----------|-------------|
| **Selección** | Torneo binario |
| **Cruce** | Uniforme con reparación de balance |
| **Mutación** | Swap (intercambio de 0↔1) |
| **Reemplazo** | Generacional con elitismo |

### Parámetros Recomendados
```python
pop_size = 80      # Tamaño de población
max_gen = 400      # Generaciones máximas
pc = 0.85          # Probabilidad de cruce
pm = 0.15          # Probabilidad de mutación
elite = 2          # Individuos élite
```

## 📊 Instancia de Prueba

Grafo de **16 nodos** y **28 aristas**:

```python
edges = [
    (1, 2), (1, 9), (1, 14),
    (2, 3), (2, 5),
    (3, 4), (3, 5), (3, 6), (3, 7),
    (4, 6),
    (5, 7), (5, 9), (5, 10),
    (6, 7), (6, 8),
    (7, 8), (7, 11),
    (8, 11),
    (9, 10), (9, 13), (9, 14),
    (10, 11), (10, 12),
    (12, 16),
    (13, 15), (13, 16),
    (14, 15),
    (15, 16)
]
```

## ✅ Resultados Obtenidos

| Métrica | Valor |
|---------|-------|
| **Mejor costo de corte** | 4 aristas |
| **Generación de convergencia** | ~20 |
| **Tiempo de ejecución** | ~5 segundos |

### Mejor Partición Encontrada
- **Grupo A:** {1, 9, 10, 12, 13, 14, 15, 16}
- **Grupo B:** {2, 3, 4, 5, 6, 7, 8, 11}

### Aristas de Corte
```
(1, 2), (5, 9), (5, 10), (10, 11)
```

## 🛠️ Requisitos

```
numpy
matplotlib
networkx
```

## 🚀 Uso

1. Abrir el notebook `biseccion_grafos_algoritmo_genetico.ipynb`
2. Ejecutar todas las celdas en orden
3. Los resultados incluyen:
   - Convergencia del algoritmo
   - Visualización del grafo particionado
   - Análisis de la solución

## 📁 Estructura del Proyecto

```
Problema de bisección de grafos/
├── README.md
└── biseccion_grafos_algoritmo_genetico.ipynb
```

## 📚 Referencias

- Garey, M. R., & Johnson, D. S. (1979). *Computers and Intractability: A Guide to the Theory of NP-Completeness*
- Kernighan, B. W., & Lin, S. (1970). *An efficient heuristic procedure for partitioning graphs*
- Holland, J. H. (1975). *Adaptation in Natural and Artificial Systems*

## 👤 Autor

**Ricardo B.**  
Tecnológico de Monterrey  
Curso: Algoritmos Matemáticos Bioinspirados

---
*Noviembre 2025*
