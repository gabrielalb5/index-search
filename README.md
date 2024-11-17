# 📋 Busca Indexada com dois índices - Indexed Search with two indexes (C)

## Definição de busca
Algoritmos de busca são métodos utilizados para **localizar registros dentro de uma coleção de dados**, sejam eles estruturados em tabelas, vetores, listas, intervalos numéricos, strings, entre outros. Eles desempenham um papel fundamental em diversas áreas da computação, garantindo que as informações sejam localizadas de forma eficiente. Cada algoritmo possui sua vantagem e melhor aplicação de acordo com o contexto. A busca sequencial, por exemplo, é a mais básica e mais didática para a introdução à programação, enquanto a busca binária se mostra mais eficiente, quando sabe-se ordenar o conjunto de elementos. Nessa atividade, implementei uma busca sequencial indexada.

## Busca sequencial indexada
A busca indexada assemelha-se à dicionários. O conceito é simples: as tabelas possuem uma **tabela auxiliar** chamada de "tabela de índices", além do próprio arquivo ordenado, onde **cada índice corresponde a um intervalo dentro da do arquivo original**. A ABNT define índice como "*Lista de entradas ordenadas segundo determinado critério, que localiza e remete para as informações contidas num texto*", e é exatamente essa a forma que este algoritmo trabalha. A maior vantagem é que essa busca é feita a partir do ponto indicado na tabela, **não precisando percorrer toda a coleção de registros**. Abaixo, uma imagem de um índice de um livro de receitas e um rascunho de como funciona o algoritmo.

<img src="https://github.com/user-attachments/assets/d665a92b-7b13-4f8d-8d61-13bf7a3540f1" alt="índice de um livro de receitas" width=400>
<img src="https://github.com/user-attachments/assets/737535d9-0265-403b-a3c7-bd16dc5d083c" alt="rascunho do algoritmo de busca indexada" width=600>








