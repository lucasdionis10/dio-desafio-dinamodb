# **Desafio de Projeto DynamoDB**

### Repositório para Desafio da DIO
Aluno: Lucas Dionísio

*****

## **Tipos de bancos de dados**

- **SQL** - Banco de dados relacional, usa apenas SQL para fazer as queries. Usa índices, chaves primárias, colunas e diversos outros recursos relacionais para organizar as informações.

- **NOSQL** - Banco de dados não relacional, não se limita ao SQL para realizar as queries. Trabalha com chave-valor, atributos, sort key, partition key e atributos para organizar e realizar a localização das informações.

****

## **DynamoDB**
Banco de dados não relacional, gerenciado e fornecido pela AWS (recursos são automaticamente providos pelo sistema da Amazon, garantindo escalabilidade)

Aplicação espcializada em atender grande volume de dados com baixa latência, podendo processar até 10 trilhões de solicitações por dia, suportando picos de até 20 milhões de solicitações por segundo, garantindo disponibilidade de 99,9%. 

### **Componentes do DynamoDB**
  -**Tabelas -** organização semelhante à organização relacional, podendo conter coleções de dados em atributos ou itens.

- **Item-** é uma entidade no armazenamento, semelhante a um objeto, contendo atributos(pelo menos 1 para ser identificado).
  
- **Atributo-** menor divisão da organização, sendo fundamental para a organização dos itens nas tabelas.
  
- **Chave primária (primary key)-** elemento capaz de identificar o item na tabela, sendo uma identificação exclusiva para cada elemento. Pode ser partition key, sort key ou combinação destas.
  
- **Partition key-** chave primária simples, normalmente resulta em um hash para identificação, que costuma oferecer informação do armazenamento físico.

- **Partition key + sort key-** Combinação que permite a repetição de uma ou outra, porém o conjunto deve resultar em uma chave primária única capaz de tornar o elemento exclusivo.

## Componentes 
- **índices secundários-** permite a consulta em relação à chave primária e permite consulta por chave alternativa. O DynamoDB é compativel com índice secundário local e índice secundário global. Pode usar atributos para organização, não apenas chaves. 
  
- **índice secundário global-** Contém chave de partição e de classificação que podem divergir das da tabela.

- **índice secundário local-** Apresenta a mesma chave de partição da tabela, porém a de classificação é diferente.

## Tipos de dados
- **Escalares-** representa o valor exato (número, booleano, string, nulo);
- **Documentos-** representa uma estrutura complexa com atributos aninhados (JSON);
- **Conjunto-** conjunto de valores escalares.
  
## Modos de leitura e gravação
*Define a forma de cobrança e gerenciamento de capacidade*

- **Sob demanda-** opção flexível, variando o limite de solicitações conforme a necessidade, sem a necessidade de planejar dimensionar a capacidade.
  
- **Provisionado-** opção com especificação de leitura e gravação conforme a necessidade da aplicação. Permite manter um limite solicitações e estabilizar abaixo deste para ter previsibilidade de custos. 

## Fora da caixa
*Pensamento do DynamoDB é fora da caixa*
- Não normalizado
- Não existe uma entidade por tabela
- Sem joins para pesquisa de dados
- Tabelas podem receber atributos de forma dinâmica

## Boas práticas
- **Access patterns:** padrões de acesso definem como os elementos serão buscados na tabela, sendo responsáveis pela modelagem do BD;
  
- **Regras de negócio bem definidas:** o Dynamo não é flexível a mudanças na modelagem após implementado, logo as regras têm que ser bem definidas e claras; 
  
- **Dimensionamento:** saber as dimensões e antecipar qual o pico de carga de consulta facilita a determinação de particionamento de dados para melhor uso de E/S (otimizar a capacidade de leitura e escrita).
  
- **Manter o mínimo de índices possível:** criar pensando nos atributos mais consultados, e não criar para os pouco consultados e pequenos.

- **Design eficiente:** 3 propriedades do padrão de acesso: tamanho dos dados, forma dos dados e velocidade dos dados. 