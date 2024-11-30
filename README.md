# Algoritmo de Colônia de Formigas (ACO) - Otimização de Caminho

## Descrição

Este projeto implementa o algoritmo de **Colônia de Formigas (ACO)**, um algoritmo inspirado no comportamento de formigas para resolver problemas de otimização, como o problema do Caixeiro Viajante (TSP). O algoritmo simula formigas se movendo entre locais e deixando feromônio, o qual é usado para guiar outras formigas em iterações subsequentes, até que o caminho ótimo seja encontrado.

No código, o problema é modelado como uma matriz de distâncias entre `n_locais`, e a tarefa é encontrar o melhor caminho que percorre todos os locais com a menor distância total.

## Objetivo

O objetivo deste projeto é implementar e testar o **Algoritmo de Colônia de Formigas (ACO)** para otimizar o caminho entre locais, levando em consideração parâmetros como:
- Número de formigas (`n_ants`),
- Número de melhores caminhos (`n_best`),
- Número de iterações (`n_iterations`),
- Taxa de decaimento do feromônio (`decay`),
- Parâmetros de controle de feromônio e visibilidade (`alpha` e `beta`).

## Como Funciona

### Passos do Algoritmo

1. **Inicialização**: As formigas são posicionadas em locais aleatórios e começam a explorar os caminhos disponíveis. O feromônio é inicializado de maneira uniforme em todas as distâncias.
2. **Construção de Caminhos**: As formigas constroem caminhos com base em dois fatores:
   - **Feromônio**: A quantidade de feromônio presente no caminho, controlada pela fórmula `(pheromone ** alpha) * (1 / distance) ** beta`.
   - **Distância**: A distância entre os locais, que é inversamente proporcional à probabilidade de escolha de um caminho.
3. **Atualização de Feromônio**: Após todas as formigas percorrerem seus caminhos, o feromônio é atualizado. Formigas que percorreram os melhores caminhos deixam mais feromônio.
4. **Decaimento de Feromônio**: O feromônio decai após cada iteração, simulando a evaporação natural do feromônio.

### Parâmetros

- `n_ants`: Número de formigas no processo.
- `n_best`: Número de melhores caminhos que serão usados para atualizar o feromônio.
- `n_iterations`: Número de iterações do algoritmo.
- `decay`: Taxa de decaimento do feromônio após cada iteração.
- `alpha`: Peso do feromônio na escolha dos caminhos.
- `beta`: Peso da distância na escolha dos caminhos.

## Instalação

Este código requer a biblioteca **NumPy** para o cálculo das distâncias e atualização do feromônio. Para instalar as dependências, basta rodar:

```bash
pip install numpy
Como Usar
Definir o número de locais: O número de locais (ou cidades) a serem visitados é definido pela variável n_locais.
Gerar a matriz de distâncias: A matriz de distâncias entre os locais é gerada aleatoriamente.
Configurar os parâmetros do algoritmo: Ajuste os parâmetros como n_ants, n_best, n_iterations, decay, alpha, e beta.
Executar o algoritmo: O algoritmo é executado para diferentes quantidades de formigas, e o melhor caminho e a distância total percorrida são exibidos.
Exemplo de Execução
python
Copiar código
n_locais = 35  # Número de locais
distances = np.random.randint(1, 101, size=(n_locais, n_locais)).astype(float)  # Gerando distâncias aleatórias
np.fill_diagonal(distances, 1000)  # Impedindo auto-loops

# Tornando a matriz simétrica
distances = np.minimum(distances, distances.T)

# Parâmetros do algoritmo
n_best = 3
n_iterations = 1000
decay = 0.5
alpha = 1
beta = 5

# Testando diferentes quantidades de formigas
for n_ants in [100, 200, 300, 500]:
    print(f"\nExecutando o ACO com {n_ants} formigas:\n")
    ant_colony = AntColony(distances, n_ants, n_best, n_iterations, decay, alpha, beta)
    best_path, best_distance = ant_colony.run()
    print(f"Melhor caminho com {n_ants} formigas: {best_path}")
    print(f"Melhor distância com {n_ants} formigas: {best_distance}")
Como o Código Funciona
Classe AntColony: A classe principal implementa os métodos necessários para o funcionamento do algoritmo, incluindo a geração de caminhos, cálculo de distâncias, atualização de feromônio, e escolha do próximo movimento com base na probabilidade.

Funções Importantes:

gen_all_paths(): Gera todos os caminhos possíveis para as formigas.
spread_pheromone(): Atualiza o feromônio nos caminhos percorridos pelas formigas.
pick_move(): Decide o próximo movimento de uma formiga com base no feromônio e na distância.
Resultados: Para cada número de formigas (n_ants), o algoritmo imprime o melhor caminho encontrado e a distância total percorrida.

Exemplos de Resultados
Ao executar o código com diferentes números de formigas, o melhor caminho e a distância correspondente são exibidos, permitindo observar como o número de formigas afeta o desempenho do algoritmo.

Conclusão
Este código implementa com sucesso o algoritmo de colônia de formigas para o problema do Caixeiro Viajante, demonstrando como simular o comportamento de formigas e utilizar feromônio para encontrar caminhos ótimos em problemas de otimização. A eficiência do algoritmo pode ser ajustada variando os parâmetros e o número de formigas.

Licença
Este projeto está licenciado sob a MIT License.

lua
Copiar código

Esse README explica de forma clara como o algoritmo de Colônia de Formigas funciona, como usar o código e os parâmetros ajustáveis. Você pode copiar e colar este conteúdo em seu repositório.





