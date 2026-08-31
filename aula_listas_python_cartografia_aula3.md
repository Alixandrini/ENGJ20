---
categories:
- Python
- Básico
- CEAC
title: Aula 3
---

# 🗺️ Aula: Listas em Python Aplicadas à Engenharia Cartográfica

> **Duração estimada:** 1h40min  
> **Ambiente:** Google Colab / Jupyter Notebook  
> **Pré-requisitos:** Noções básicas de Python (variáveis, tipos de dados, operadores)



## 📋 Plano de Aula

| Etapa | Tópico | Tempo |
|-------|--------|-------|
| 1 | Introdução e Motivação | 10 min |
| 2 | Criando e Acessando Listas | 15 min |
| 3 | Operações Básicas com Listas | 15 min |
| 4 | Métodos de Listas | 20 min |
| 5 | Listas Aninhadas (Matrizes de Coordenadas) | 15 min |
| 6 | List Comprehension | 15 min |
| 7 | Exercícios Práticos Aplicados | 20 min |



## 🎯 1. Introdução e Motivação (10 min)

Em **Engenharia Cartográfica**, trabalhamos constantemente com **conjuntos de dados**:
- Coordenadas geográficas (latitudes e longitudes)
- Altitudes de pontos de uma rede de nivelamento
- Códigos de identificação de marcos geodésicos
- Valores de deslocamento em monitoramento de deformações

Em Python, a estrutura mais versátil para armazenar esses conjuntos é a **`list`** (lista).

### Por que listas?
- Armazenam múltiplos valores em uma única variável
- Permitem acessar, modificar e processar dados de forma eficiente
- São fundamentais para análise espacial e processamento de dados geoespaciais

> 💡 **Pense:** Uma lista é como uma planilha de Excel com uma única coluna — você pode armazenar vários valores ordenados.



## 📦 2. Criando e Acessando Listas (15 min)

### 2.1 Criando listas

Uma lista em Python é criada com colchetes `[]` e os elementos são separados por vírgulas.

```python
# Lista vazia
lista_vazia = []

# Lista de coordenadas geográficas (latitudes de pontos de controle)
latitudes = [-23.5505, -23.5510, -23.5498, -23.5501, -23.5515]

# Lista de longitudes correspondentes
longitudes = [-46.6333, -46.6340, -46.6325, -46.6330, -46.6350]

# Lista de altitudes (em metros)
altitudes = [760.5, 762.1, 759.8, 761.0, 763.5]

# Lista de nomes de marcos geodésicos
marcos = ["MG-001", "MG-002", "MG-003", "MG-004", "MG-005"]

# Lista mista (Python permite!)
ponto_controle = ["MG-001", -23.5505, -46.6333, 760.5]
```

### 2.2 Acessando elementos pelo índice

Cada elemento tem uma **posição** (índice), começando em **0**.

```python
latitudes = [-23.5505, -23.5510, -23.5498, -23.5501, -23.5515]

# Primeiro elemento
print(latitudes[0])   # -23.5505

# Terceiro elemento
print(latitudes[2])   # -23.5498

# Último elemento
print(latitudes[-1])  # -23.5515

# Penúltimo elemento
print(latitudes[-2])  # -23.5501
```

### 📝 Exercício Rápido 1
Execute o código abaixo e complete as lacunas:

```python
longitudes = [-46.6333, -46.6340, -46.6325, -46.6330, -46.6350]

# Acesse a longitude do terceiro ponto de controle
print("Longitude do 3º ponto:", longitudes[___])

# Acesse a longitude do último ponto
print("Longitude do último ponto:", longitudes[___])
```



## 🔧 3. Operações Básicas com Listas (15 min)

### 3.1 Slicing (fatiamento)

Permite extrair subconjuntos de uma lista.

```python
latitudes = [-23.5505, -23.5510, -23.5498, -23.5501, -23.5515]

# Do 2º ao 4º elemento (índice 1 até 3)
print(latitudes[1:4])   # [-23.5510, -23.5498, -23.5501]

# Do início até o 3º elemento
print(latitudes[:3])    # [-23.5505, -23.5510, -23.5498]

# Do 3º elemento até o final
print(latitudes[2:])    # [-23.5498, -23.5501, -23.5515]

# Toda a lista, saltando de 2 em 2
print(latitudes[::2])   # [-23.5505, -23.5498, -23.5515]
```

### 3.2 Concatenação e Repetição

```python
latitudes_norte = [-23.5505, -23.5510]
latitudes_sul = [-23.5498, -23.5501]

# Concatenar listas
todas_latitudes = latitudes_norte + latitudes_sul
print(todas_latitudes)  # [-23.5505, -23.5510, -23.5498, -23.5501]

# Repetir lista
repetida = [0.0] * 5
print(repetida)  # [0.0, 0.0, 0.0, 0.0, 0.0]
```

### 3.3 Verificando elementos

```python
marcos = ["MG-001", "MG-002", "MG-003", "MG-004", "MG-005"]

# Verificar se um elemento existe
print("MG-003" in marcos)   # True
print("MG-010" in marcos)   # False

# Contar elementos
print(len(marcos))  # 5
```

### 📝 Exercício Rápido 2

```python
altitudes = [760.5, 762.1, 759.8, 761.0, 763.5, 758.2, 764.0]

# Crie uma sublista com as 3 primeiras altitudes
sublista = altitudes[___]
print(sublista)

# Verifique se a altitude 761.0 está na lista
print(___ in altitudes)
```



## 🛠️ 4. Métodos de Listas (20 min)

Listas possuem métodos embutidos muito úteis para processamento de dados cartográficos.

### 4.1 Adicionar e remover elementos

```python
altitudes = [760.5, 762.1, 759.8, 761.0]

# Adicionar ao final
altitudes.append(763.5)
print(altitudes)  # [760.5, 762.1, 759.8, 761.0, 763.5]

# Inserir em posição específica
altitudes.insert(2, 760.0)
print(altitudes)  # [760.5, 762.1, 760.0, 759.8, 761.0, 763.5]

# Remover último elemento
removido = altitudes.pop()
print(removido)     # 763.5
print(altitudes)    # [760.5, 762.1, 760.0, 759.8, 761.0]

# Remover elemento específico
altitudes.remove(760.0)
print(altitudes)    # [760.5, 762.1, 759.8, 761.0]
```

### 4.2 Ordenação e estatísticas básicas

```python
altitudes = [760.5, 762.1, 759.8, 761.0, 763.5, 758.2, 764.0]

# Ordenar (modifica a lista original)
altitudes.sort()
print(altitudes)  # [758.2, 759.8, 760.5, 761.0, 762.1, 763.5, 764.0]

# Ordenar em ordem decrescente
altitudes.sort(reverse=True)
print(altitudes)  # [764.0, 763.5, 762.1, 761.0, 760.5, 759.8, 758.2]

# Valor máximo e mínimo
print(max(altitudes))  # 764.0
print(min(altitudes))  # 758.2

# Soma dos valores
print(sum(altitudes))  # 5349.1

# Média
media = sum(altitudes) / len(altitudes)
print(f"Altitude média: {media:.2f} m")
```

### 4.3 Encontrar índice e contar ocorrências

```python
codigos = ["A1", "B2", "A1", "C3", "A1", "D4"]

# Encontrar índice de um elemento
print(codigos.index("C3"))  # 3

# Contar ocorrências
print(codigos.count("A1"))  # 3
```

### 📝 Exercício Rápido 3

```python
# Dados de uma nivelada: altitudes de 10 pontos
nivelada = [100.50, 101.20, 100.80, 99.50, 101.50, 
            100.00, 102.30, 101.00, 100.20, 99.80]

# 1. Encontre a altitude máxima e mínima
alt_max = ___
alt_min = ___
print(f"Máx: {alt_max} m, Mín: {alt_min} m")

# 2. Calcule a altitude média
media = ___
print(f"Média: {media:.2f} m")

# 3. Adicione um novo ponto com altitude 100.90
___
print(nivelada)

# 4. Ordene a lista em ordem crescente
___
print(nivelada)
```



## 🗂️ 5. Listas Aninhadas — Matrizes de Coordenadas (15 min)

Em cartografia, frequentemente trabalhamos com **coordenadas 2D ou 3D**. Listas aninhadas são perfeitas para isso!

### 5.1 Representando pontos como listas aninhadas

```python
# Cada ponto: [latitude, longitude, altitude]
pontos = [
    [-23.5505, -46.6333, 760.5],   # Ponto 1
    [-23.5510, -46.6340, 762.1],   # Ponto 2
    [-23.5498, -46.6325, 759.8],   # Ponto 3
    [-23.5501, -46.6330, 761.0],   # Ponto 4
]

# Acessar coordenadas do 2º ponto
print(pontos[1])           # [-23.5510, -46.6340, 762.1]

# Latitude do 2º ponto
print(pontos[1][0])        # -23.5510

# Longitude do 3º ponto
print(pontos[2][1])        # -46.6325

# Altitude do 1º ponto
print(pontos[0][2])        # 760.5
```

### 5.2 Percorrendo listas aninhadas

```python
# Imprimir todas as coordenadas formatadas
for i, ponto in enumerate(pontos):
    lat, lon, alt = ponto
    print(f"Ponto {i+1}: Lat={lat}, Lon={lon}, Alt={alt}m")
```

### 5.3 Representando uma grade regular (raster simplificado)

```python
# Matriz 3x3 de altitudes (modelo digital de terreno simplificado)
mdt = [
    [100.0, 101.5, 102.0],
    [100.5, 101.0, 102.5],
    [101.0, 102.0, 103.0]
]

# Acessar altitude da célula da 2ª linha, 3ª coluna
print(mdt[1][2])  # 102.5
```

### 📝 Exercício Rápido 4

```python
# Coordenadas de vértices de um polígono (lat, lon)
poligono = [
    [-23.5500, -46.6300],
    [-23.5500, -46.6400],
    [-23.5600, -46.6400],
    [-23.5600, -46.6300],
    [-23.5500, -46.6300]  # Fechando o polígono
]

# 1. Quantos vértices tem o polígono? (desconsidere o último se for repetição)
num_vertices = ___
print(f"Número de vértices: {num_vertices}")

# 2. Imprima a latitude do 3º vértice
print(___)

# 3. Calcule a latitude média dos vértices
soma_lat = 0
for vertice in poligono[:-1]:  # Exclui o último (repetido)
    soma_lat += vertice[0]
media_lat = soma_lat / num_vertices
print(f"Latitude média: {media_lat}")
```



## ⚡ 6. List Comprehension (15 min)

**List comprehension** é uma forma concisa e elegante de criar listas a partir de outras listas. Muito usada em processamento de dados geoespaciais!

### 6.1 Conceito básico

```python
altitudes = [760.5, 762.1, 759.8, 761.0, 763.5]

# Criar nova lista com altitudes em centímetros
altitudes_cm = [alt * 100 for alt in altitudes]
print(altitudes_cm)  # [76050.0, 76210.0, 75980.0, 76100.0, 76350.0]

# Criar lista com altitudes acima de 761m
altitudes_altas = [alt for alt in altitudes if alt > 761]
print(altitudes_altas)  # [762.1, 763.5]
```

### 6.2 Aplicação cartográfica: converter coordenadas

```python
# Converter latitudes de graus decimais para graus, minutos, segundos (formato simplificado)
latitudes = [-23.5505, -23.5510, -23.5498]

latitudes_gms = []
for lat in latitudes:
    graus = int(lat)
    minutos_decimais = (lat - graus) * 60
    minutos = int(minutos_decimais)
    segundos = (minutos_decimais - minutos) * 60
    latitudes_gms.append([graus, minutos, segundos])

print(latitudes_gms)
# [[-23, 33, 1.8], [-23, 33, 3.6], [-23, 32, 59.28]]
```

### 6.3 Filtrando dados de qualidade

```python
# Dados de GPS com precisão (em metros)
leituras_gps = [
    {"lat": -23.5505, "lon": -46.6333, "precisao": 2.5},
    {"lat": -23.5510, "lon": -46.6340, "precisao": 8.2},
    {"lat": -23.5498, "lon": -46.6325, "precisao": 1.8},
    {"lat": -23.5501, "lon": -46.6330, "precisao": 15.5},
]

# Filtrar apenas leituras com precisão < 5m
leituras_boas = [p for p in leituras_gps if p["precisao"] < 5]
print(leituras_boas)
```

### 📝 Exercício Rápido 5

```python
altitudes = [760.5, 762.1, 759.8, 761.0, 763.5, 758.2, 764.0]

# 1. Crie uma lista com as diferenças de cada altitude em relação à média
media = sum(altitudes) / len(altitudes)
diferencas = [___ for ___ in ___]
print(diferencas)

# 2. Crie uma lista apenas com altitudes entre 760 e 763
filtradas = [___ for ___ in ___ if ___]
print(filtradas)
```



## 🏋️ 7. Exercícios Práticos Aplicados (20 min)

### 📝 Exercício 1: Perfil Topográfico

Dado um perfil topográfico com altitudes a cada 20m:

```python
# Perfil: distância (m) e altitude (m)
perfil = [
    [0, 100.0],
    [20, 102.5],
    [40, 105.0],
    [60, 104.0],
    [80, 108.5],
    [100, 110.0],
    [120, 109.5],
    [140, 112.0],
    [160, 115.5],
    [180, 114.0],
    [200, 118.0]
]

# a) Extraia apenas as altitudes em uma lista
altitudes = [p[1] for p in perfil]
print("Altitudes:", altitudes)

# b) Encontre a altitude máxima e mínima
print(f"Alt máx: {max(altitudes)} m")
print(f"Alt mín: {min(altitudes)} m")

# c) Calcule a declividade média do perfil (Δalt / Δdist)
delta_alt = altitudes[-1] - altitudes[0]
delta_dist = perfil[-1][0] - perfil[0][0]
declividade = (delta_alt / delta_dist) * 100
print(f"Declividade média: {declividade:.2f}%")

# d) Encontre os trechos com declividade acima de 15%
declividades = []
for i in range(1, len(perfil)):
    d_alt = perfil[i][1] - perfil[i-1][1]
    d_dist = perfil[i][0] - perfil[i-1][0]
    decl = (d_alt / d_dist) * 100
    declividades.append([perfil[i-1][0], perfil[i][0], decl])

trechos_acentuados = [t for t in declividades if abs(t[2]) > 15]
print("Trechos com declividade > 15%:")
for t in trechos_acentuados:
    print(f"  De {t[0]}m a {t[1]}m: {t[2]:.2f}%")
```

### 📝 Exercício 2: Análise de Poligonal

```python
# Estação, ângulo horizontal (graus), distância (m)
poligonal = [
    ["E1", 0.0, 50.0],
    ["E2", 120.5, 45.0],
    ["E3", 95.0, 60.0],
    ["E4", 110.2, 55.0],
    ["E5", 85.5, 48.0]
]

# a) Calcule o comprimento total da poligonal
distancias = [est[2] for est in poligonal]
comprimento_total = sum(distancias)
print(f"Comprimento total: {comprimento_total:.2f} m")

# b) Encontre a estação com a maior distância
max_dist = max(distancias)
for est in poligonal:
    if est[2] == max_dist:
        print(f"Maior trecho: {est[0]} com {max_dist} m")

# c) Calcule a média dos ângulos horizontais
angulos = [est[1] for est in poligonal]
media_angulos = sum(angulos) / len(angulos)
print(f"Ângulo horizontal médio: {media_angulos:.2f}°")

# d) Crie uma lista apenas com os nomes das estações
nomes = [est[0] for est in poligonal]
print("Estações:", nomes)
```

### 📝 Exercício 3: Processamento de Coordenadas UTM

```python
# Coordenadas UTM (Easting, Northing) em metros
coordenadas_utm = [
    [333500.00, 7394500.00],
    [333520.50, 7394480.25],
    [333480.75, 7394510.80],
    [333510.20, 7394495.50],
    [333495.00, 7394520.00]
]

# a) Calcule o centroide (média de Easting e Northing)
eastings = [c[0] for c in coordenadas_utm]
northings = [c[1] for c in coordenadas_utm]

centroide_e = sum(eastings) / len(eastings)
centroide_n = sum(northings) / len(northings)
print(f"Centroide: E={centroide_e:.2f}, N={centroide_n:.2f}")

# b) Encontre a coordenada mais ao norte (maior Northing)
max_northing = max(northings)
idx = northings.index(max_northing)
print(f"Ponto mais ao norte: E={eastings[idx]:.2f}, N={max_northing:.2f}")

# c) Calcule a variação (amplitude) em Easting e Northing
amp_e = max(eastings) - min(eastings)
amp_n = max(northings) - min(northings)
print(f"Amplitude E: {amp_e:.2f} m")
print(f"Amplitude N: {amp_n:.2f} m")
```


## 🎓 Desafio Extra (para casa)

### Desafio: Cálculo de Área do Polígono (Fórmula do Shoelace)

Implemente o cálculo da área de um polígono a partir de suas coordenadas UTM.

```python
# Coordenadas UTM de um polígono (Easting, Northing)
vertices = [
    [333500.00, 7394500.00],
    [333550.00, 7394500.00],
    [333550.00, 7394550.00],
    [333500.00, 7394550.00]
]

# Fórmula do Shoelace
# A = 0.5 * |Σ(xi * yi+1 - xi+1 * yi)|

n = len(vertices)
area = 0
for i in range(n):
    x_i, y_i = vertices[i]
    x_next, y_next = vertices[(i + 1) % n]
    area += x_i * y_next - x_next * y_i

area = abs(area) / 2
print(f"Área do polígono: {area:.2f} m² = {area/10000:.4f} ha")
```


## 📚 Resumo dos Conceitos

| Conceito | Sintaxe | Exemplo |
|----------|---------|---------|
| Criar lista | `[]` | `coords = [1, 2, 3]` |
| Acessar elemento | `lista[i]` | `coords[0]` |
| Último elemento | `lista[-1]` | `coords[-1]` |
| Slicing | `lista[inicio:fim]` | `coords[1:3]` |
| Adicionar | `.append(x)` | `coords.append(4)` |
| Inserir | `.insert(i, x)` | `coords.insert(0, 0)` |
| Remover | `.remove(x)` | `coords.remove(2)` |
| Ordenar | `.sort()` | `coords.sort()` |
| Tamanho | `len(lista)` | `len(coords)` |
| Soma | `sum(lista)` | `sum(coords)` |
| Máximo/Mínimo | `max()/min()` | `max(coords)` |
| List comprehension | `[x for x in lista]` | `[x*2 for x in coords]` |



> ✨ **Dica para o Colab:** Use `Ctrl + Enter` para executar uma célula e `Shift + Enter` para executar e ir para a próxima. Adicione células de texto (Markdown) para documentar seu código!

> 🗺️ **Lembrete:** Em cartografia, listas são a base para trabalhar com coordenadas, altitudes, atributos e geometrias. Dominar listas é essencial antes de avançar para bibliotecas como **GeoPandas**, **Shapely** e **NumPy**!
