[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/vT72CUxW)
[![Open in Codespaces](https://classroom.github.com/assets/launch-codespace-2972f46106e565e64193e422d61a12cf1da4916b45550586e14ef0a7c637dd04.svg)](https://classroom.github.com/open-in-codespaces?assignment_repo_id=23225912)
# Práctica 6

`data/distances.csv` contiene la lista de adyacencias de la gráfica dirigida del ejercicio 4.

## Integrantes

- (Si no modificas esta línea lloro) Babilonia, Aureliano
- Infante Flores Leonardo
- Marban Ayala Catalina

## Uso e instalación

para ejecutar el código, instalar:

- `matplotlib`
- from numpy import zeros

(Si no eliminas esta línea lloro) Y dime cómo debería ejecutar tu código y en qué orden. 
Recuerda que antes de ejecutar tu código leeré tu `README.md`. Por ejemplo la manera en la que propongo que organizes tu código es

- `main.py`: Contiene el código para graficar cada uno de los tres ejercicios
- `data.py`: Tal vez aquí puedes leer el csv para a partir crear una matriz de adyacencia


# Ejercicio 1:


```python
def dijkstra(M, origin):
    n = len(matriz_pesos)
```
Define la función pidiendo la matriz de costos y el nodo de origen. 
Calculamos n que es el número total de vértices en la gráfica midiendo el tamaño de la matriz 
```
D = [float('inf')] * n
D[origin] = 0
```
Crea el arreglo unidimensional D que guardará el costo del camino mínimo desde el origen hasta cada vértice
```
P = [None] * n
ED = [False] * n
```
Crea el arreglo P para guardar el vértice predecesor de cada nodo en el camino mínimo, y el conjunto ED (como un arreglo de booleanos) para marcar los vértices cuyo camino mínimo ya se determino
```
for _ in range(n):
    distancia_minima = float('inf')
    u = -1
```
Iniciamos un ciclo que se repetira n veces (una por cada vértice) y declaramos variables temporales para buscar el nodo no visitado más cercano.
```
for i in range(n):
    if not ED[i] and D[i] < distancia_minima:
        distancia_minima = D[i]
        u = i
```
Recorre todos los nodos buscando cuál de los que no están en ED tiene la menor distancia acumulada en D
```
if u == -1:
    break
    ED[u] = True
```
Si u sigue siendo -1, significa que los nodos que faltan son inalcanzables y la gráfica esta desconectada así que rompe el ciclo. Si encontramos un nodo válido u, lo marcamos como True en el arreglo ED.
```
for v in range(n):
    peso_arista = M[u][v]
```
Iteramos sobre todos los posibles nodos v de la gráfica para encontrar los vecinos de nuestro nodo permanente u y consultamos el costo de la arista en la matriz MD
```
if peso_arista > 0 and not ED[v]:
```
Un valor mayor a 0 en la matriz de adyacencia significa que existe una arista conectando u y v, tmb verificamos que v no sea ya un nodo marcado como permanente
```
distancia_temporal = D[u] + peso_arista
```
La distancia temporal hacia el vecino $v_i$ es la distancia que ya tiene el nodo permanente en D más la distancia de la arista que los conecta
```
if distancia_temporal < D[v]:
    D[v] = distancia_temporal
    P[v] = u
```
Si la nueva ruta calculada (distancia_temporal) es más corta que la que el nodo v tenía guardada en D, la sobrescribimos y registramos en P que para llegar a v mas rapido, el paso nodo de origen es u

```
return D, P
```
la función devuelve las dos listas finales

## Conclusión

¿Te gustó la programación dinámica? ¿Sientes que te será útil? ¿Se te hace una buena estrategia para la resolución de problemas?
