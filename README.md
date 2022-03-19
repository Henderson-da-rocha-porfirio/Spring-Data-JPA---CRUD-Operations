# Paging and Sorting
## Eles não fazem parte do JPA. Eles fazem parte do Spring Data que torna nossa vida um pouco mais fácil ao implementar paging e sorting.

## Exemplo: Uma página de produtos ou lista do que quer que seja:

### A. Pagination:

#### 1. A aplicação não precisa ler todos os dados de uma só vez, mas ler umas poucas gravaçoes do database.
#### 2. Para isso ela permite que haja uma paginação para busca no final da página para checar os próximos resultados sem precisar exibir, por exemplo, os milhares de produtos que se encontram no database.
#### 3. As Interfaces-chaves quando se está usando o Paging:
##### a. Pageable
##### b. PageRequest
#### 4. Depois de habilitado o Paging na camada de serviços (services) ou em alguma outra camada da aplicação onde está se recuperando as gravações do database usando métodos que usam a Interface Pageable e PageRequest.

### B. Sorting:

#### 1. Significa "sortear"( escolher ) os produtos numa listagem, os produtos baseados na filtragem. Por exemplo, por preço e etc.
#### 2. As Classes-chaves quando se está usando o Sorting:
##### a. Sort
##### b. Direction
##### c. Order

### C. Herança:

#### 1. ProdutoRepository herda de PagingAndSortingRepository que é uma sub-classe de CRUDRepository: uma vez que isso é feito, é feito um tipo de getPaging e getSorting no método findAll dentro do ProdutoRepository. ( usando JPQL )


### D. Criando a paginação e o sort:

#### * Em versões antigas do Spring Boot, para criar uma página de Request(solicitação):

#### 1. Era utilizado um Construtor:

##### a. new PageRequest(page, size, new Sort(...)):
##### b. passado dentro do parâmetro o que você quer acesar:
##### c. page: a página que queremos acessar.
##### d. size: o tamanho da página em cada página(o número de gravações no database em cada página.
##### e. new Sort(...): É opcional passar no parâmetro as opções sorting que quiser.


#### * Em versões mais atuais faremos uso do método of em vez de usar o new Sort:

#### 2. Método of:

#### 1. PageRequest.of(page, size, Sort.by(...))
