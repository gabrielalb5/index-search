# 📋 Busca Sequencial Indexada com dois índices<br>- Indexed Sequential Search with two indexes (C)

O vídeo apresentação do código e da execução do programa está disponível no [YouTube](https://youtu.be/4nHoYfQRUYM?si=Io27demb5mjNZned).

## Definição de busca
Algoritmos de busca são métodos utilizados para **localizar registros dentro de uma coleção de dados**, sejam eles estruturados em tabelas, vetores, listas, intervalos numéricos, strings, entre outros. Eles desempenham um papel fundamental em diversas áreas da computação, garantindo que as informações sejam localizadas de forma eficiente. Cada algoritmo possui sua vantagem e melhor aplicação de acordo com o contexto. A busca sequencial, por exemplo, é a mais básica e mais didática para a introdução à programação, enquanto a busca binária se mostra mais eficiente, quando sabe-se ordenar o conjunto de elementos. Nessa atividade, implementei uma busca sequencial indexada.

## Busca sequencial indexada
A busca indexada assemelha-se à dicionários. O conceito é simples: as tabelas possuem uma **tabela auxiliar** chamada de "tabela de índices", além do próprio arquivo ordenado, onde **cada índice corresponde a um intervalo dentro da do arquivo original**. A ABNT define índice como "*Lista de entradas ordenadas segundo determinado critério, que localiza e remete para as informações contidas num texto*", e é exatamente dessa forma que este algoritmo trabalha. A maior vantagem é que essa busca é feita a partir do ponto indicado na tabela, **não precisando percorrer toda a coleção de registros**. Abaixo, uma imagem de um índice de um livro de receitas e um rascunho de como funciona o algoritmo.

<img src="https://github.com/user-attachments/assets/d665a92b-7b13-4f8d-8d61-13bf7a3540f1" alt="índice de um livro de receitas" width=39%>
<img src="https://github.com/user-attachments/assets/737535d9-0265-403b-a3c7-bd16dc5d083c" alt="rascunho do algoritmo de busca indexada" width=60%>

## Desenvolvimento 
A tarefa principal desta atividade era implementar pelo menos uma tabela de índices para um arquivo ordenado com um milhão de registros. Para isso, optei por utilizar duas tabelas auxiliares: uma atuando como índice da tabela original e outra como subíndice do índice. Na primeira etapa, gerei um arquivo ordenado utilizando uma seed fixa e o dividi em **mil índices**, de forma que cada índice representa um **intervalo de mil registros**. Em seguida, subdividi esse índice em **10 partes**, criando um **subíndice** em que cada entrada corresponde a um **intervalo de 100 números**. É importante ressaltar que a minha **tabela de registros** e os **índices** foram **implementados com matrizes**.
<br><br>Após a separação e a leitura do número procurado, é iniciado o processo de busca. O algoritmo **começa pela menor tabela**, de 10 índices, procurando o intervalo que representa o espaço de 100 números que engloba o número buscado. O intervalo e os valores são armazenados em uma matriz chamada de ```inicioFim```. O processo se repete, dessa vez procurando o valor apenas no trecho indicado pela matriz ```inicioFim``` dentro do arquivo de mil índices. Ou seja, após refinar o intervalo pelo menor índice, **a busca será feita apenas em um intervalo de 100 índices dentro do outro índice de mil**, o que faz com que esse algoritmo seja muito eficiente.
<br><br>A busca afunila ainda mais o trecho que contém o número procurado, retornando um outro intervalo, representado por dois índices, que aponta para um espaço de mil registros no arquivo original. No último passo, uma busca sequencial é aplicada e retorna o número encontrado e sua posição caso ele exista no registro. Para demonstrar a eficiência, também adicionei contadores de tempo de execução e comparei com um algoritmo de busca sequencial simples, procurando valores que estão ou não presentes na tabela.

### Comparativo - tempo de execução busca sequencial indexada x simples
| **Presente** | **Tempo Indexada (s)** | **Tempo Simples (s)** | **Não Presente** | **Tempo Indexada (s)** | **Tempo Simples (s)** |
|--------------|------------------------|-----------------------|------------------|------------------------|-----------------------|
| 1            | 0,000003               | 0,002444              | 2                | 0,000005               | 0,002445              |
| 21805        | 0,000005               | 0,001213              | 30000            | 0,000005               | 0,002445              |
| 448702       | 0,000006               | 0,001005              | 251000           | 0,000006               | 0,002478              |
| 344550       | 0,000005               | 0,002471              | 559851           | 0,000005               | 0,001111              |
| 1111111      | 0,000006               | 0,002476              | 1000000          | 0,000005               | 0,002458              |
| 4502731      | 0,000008               | 0,002699              | 5000000          | 0,000002               | 0,002459              |

## Conclusão
A busca sequencial indexada se destaca como uma opção eficiente, especialmente por utilizar um recurso interessante: a divisão dos dados em tabelas auxiliares para facilitar a busca. Ela pode ser uma ótima escolha para quem já domina algoritmos de ordenação e trabalha com grandes volumes de dados ordenados. Entretanto, quando o conjunto de dados é constantemente alterado, seja em tamanho geral ou na redefinição dos índices, seu uso não é recomendado. Isso ocorre porque o código exige uma manutenção cuidadosa, sendo mais adequado para casos específicos e com menor frequência de alterações.
<br><br>Durante os testes, também contabilizei o tempo de execução incluindo a divisão das tabelas auxiliares e observei um desempenho muito semelhante ao da busca sequencial simples. Porém, considerando que essa divisão é feita apenas uma vez e que o algoritmo será utilizado posteriormente para várias consultas, ele se torna, de fato, uma ótima opção para cenários de busca frequente.
