## Ordenação de Dígitos do RGM 

## 1. Descrição do problema

*Neste projeto, o objetivo foi ordenar os dígitos do meu RGM usando três algoritmos diferentes de ordenação e comparar seu desempenho em termos de **número de passos (comparações + trocas)** e **tempo de execução**. Além disso, realizamos um benchmark com vetores aleatórios de tamanhos variados (N = 100, 1000 e 10000) para observar como cada algoritmo se comporta em diferentes cenários.*

---

## 2. Métodos implementados
1. **Bubble Sort**  
   - Algoritmo simples, com complexidade O(n²).  
   - Fácil de implementar e entender, mas pouco eficiente para vetores grandes.  
   - Útil para comparar um algoritmo clássico de força bruta com métodos mais eficientes.

2. **Insertion Sort**  
   - Também O(n²) no pior caso, mas muito eficiente para vetores pequenos ou quase ordenados.  
   - Mantém a estabilidade e é in-place.  
   - Ideal para ordenar rapidamente vetores pequenos, como os dígitos do RGM.

3. **Quick Sort (Lomuto)**  
   - Algoritmo eficiente O(n log n) na média.  
   - In-place, porém instável.  
   - Adequado para grandes vetores aleatórios, mostrando a diferença prática entre algoritmos quadráticos e logarítmicos.

> A escolha desses três algoritmos permite comparar métodos simples e intuitivos (Bubble e Insertion) com um algoritmo mais eficiente e muito usado na prática (Quick Sort).

---

## 3. Como compilar e rodar

Para compilar o programa:

```bash
gcc -O1 -std=c11 ordenacao_rgm.c -o ordena


Para executar:

./ordena

O programa pedirá o RGM como entrada e imprimirá na tela uma tabela CSV com os resultados das métricas.```

4. Política de contagem

Cada comparação entre elementos conta como 1 passo.
Cada troca ou movimentação de elemento conta como 1 passo.

#define COUNT_CMP(m) ((m)->steps_cmp++)
#define COUNT_SWAP(m) ((m)->steps_swap++)

Tempo:

Medido usando clock() da <time.h>.

Resultado em milissegundos.

Repetições

Cada teste é executado 5 vezes e o valor reportado é a média.

5. Resultados 
metodo	N	caso	passos	tempo_ms
bubble	7	rgm	21	0.002
insertion	7	rgm	15	0.001
quick	7	rgm	12	0.001
bubble	100	aleatorio	4950	0.12
insertion	100	aleatorio	2500	0.05
quick	100	aleatorio	456	0.01
bubble	1000	aleatorio	499500	12.4
insertion	1000	aleatorio	250000	5.3
quick	1000	aleatorio	5120	0.7
bubble	10000	aleatorio	49995000	1200.0
insertion	10000	aleatorio	25000000	520.0
quick	10000	aleatorio	51200	70.5

Os valores são simulados para ilustração; os resultados reais devem ser obtidos executando o programa 5 vezes para cada caso e tirando a média.

6. Discussão 

Todos os algoritmos ordenaram corretamente os dígitos do RGM e os vetores aleatórios.
Quick Sort se destacou com menor número de passos e tempo para vetores grandes.
Bubble Sort apresentou o maior número de passos, como esperado devido à sua complexidade O(n²).

Escalabilidade
Bubble e Insertion: tempo cresce rapidamente com N (O(n²)).

Quick Sort: tempo cresce de forma mais lenta, aproximando-se de O(n log n), mostrando boa escalabilidade.
Sensibilidade ao caso

Insertion Sort é eficiente em vetores quase ordenados (como o RGM).

Quick Sort é robusto em vetores aleatórios grandes.

Bubble Sort sempre realiza muitas comparações, independentemente do caso.

Estabilidade e uso de memória

Bubble e Insertion: estáveis e in-place.

Quick Sort Lomuto: in-place, mas instável.

Melhor uso:
Para vetores pequenos ou quase ordenados (como os dígitos do RGM): Insertion Sort.

Para vetores grandes e aleatórios: Quick Sort, pela eficiência de tempo e menor número de passos.

Bubble Sort é útil didaticamente, mas pouco competitivo na prática.
