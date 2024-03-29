# Modelo de Classes

Em posse da visão de caso de uso do sistema, os desenvolvedores devem prosseguir no desenvolvimento

Atores:

Externamente ao sistema, os atores visualizam resultados. Cálculos, gráficos, relatórios, etc.

Objetos: 

Internamente, objetos colaboram entre si para produzir os resultados visíveis de fora.
Colaboração pode ser vista sob aspecto dinâmico ou sob aspecto estrutural estático.

## Objetivos

- Descrever método para identificação das classes de objetos de um sistema a partir dos casos de uso;

- Apresentar alguns dos elementos do diagrama de classes;

- Descrever a construção do modelo de domínio;

- Descrever a inserção do modelo de classes no desenvolvimento.

É importante notar que a modelagem de classes é um processo evolutivo.
Existem três níveis:
- Modelo de classes de domínio
- Modelo de classes de especificação
- Modelo de classes de implementação.

## Padrão de Nomeclatura:

- Espaço e preposições são removidos

- Nomes de classes e relacionamentos são escritos com iniciais maiúsculas

ex: Cliente, ItemPedido, OrdemServiço.

- Atributos e operações possuem primeira letra minúscula e junções iniciadas por letra maíuscula, ex: idade, numeroPedidos, obterTotal.

- OU junções substituídas por '_' Ex: numero_pedidos, obter_total.

Boas práticas: O nome usado no diagrama de classe é o nome que vai ser usado em código

## Diagrama de Classes

### Classes

Classes são uma representação abstrata de um conjunto de objetos que compartilham atributos e operações. No Diagrama de Classes, uma classe é representada como uma caixa que possui no máximo 3 compartimentos:

- Um compartimento com o nome da classe;
- Um compartimento com os atributos da classe;
- Um compartimento com as operações da classe.

<img src="../.assets/classes.jpg">

Atributos: representam a descrição dos dados armazenados pelos objetos de uma classe. Podem incluir possíveis valores (tipagem).

- idade: Integer

Operações: correspondem às ações que os objetos de uma classe sabem realizar. Operações são as mesmas para todos os objetos de uma classe. Podem incluir possíveis valores de retorno (tipagem).

- somar (valor1, valor2): Float

OBS: MUITO IMPORTANTE

```
sublinhados - Quer dizer que o atributo ou o método é estático

itálicos - Quer dizer que o atributo ou o método é abstrato
```


### Relacionamentos

Para representar que objetos/instâncias podem se relacionar durante a execução do sistema, utilizamos a associação.

- No diagrama, utilizamos uma linha reta entre classes para mostrar associações.

Exemplos:

Vendas: um cliente compra produtos

<img src="../.assets/clienteproduto.jpg">

Bancário: uma conta-corrente possui um histórico de transações.

<img src="../.assets/contahist.jpg">

Associações são entre classes, mas representam ligações possíveis entre objetos.

Associações podem também informar os limites inferiores e superiores de quantidade de objetos. Em UML, chamamos de Multiplicidade. Os valores são mostrados em cada extremo da linha de associação.

<img src="../.assets/tabmult.jpg">

Exemplos de Multiplicidade:

<img src="../.assets/exmulti.jpg">

Associações podem ser separadas em três grandes grupo: “um para um”, “um para muitos”, e “muitos para muitos”. Esses grupos refletem a Conectividade das classes.

<img src="../.assets/conectividade.jpg">

Exemplos:


<img src="../.assets/ex1.jpg">

Um empregado pode gerenciar 0 ou 1 departamento, um departamento pode ser gerenciado por 1 empregado.


<img src="../.assets/ex2.jpg">

Um empregado pode atua em 1 departamento, um departamento possui 0 ou mais empregados.


<img src="../.assets/ex3.jpg">

Um empregado está associado a 1 ou mais projetos, Um projeto possui 0 ou mais empregados.

**Participação**:

**Obrigatória**, caso multiplicidade mínima seja 1.

**Opcional**, caso multiplicidade mínima seja 0.

### Recurso da Associação

**Recurso da Associação:** características do diagrama para facilitar entendimento da relação.

Nome da Associação é escrita na linha, ao meio do caminho entre as duas classes.

Direção de Leitura, representada por um pequeno triângulo em um dos lados do nome de associação.

Papéis são posicionados em cada extremo da linha de associação, indicando o papel de cada classe nesta.

<img src="../.assets/n_associacao.JPG">

<img src="../.assets/n_associacao2.JPG">

### Relacionamentos - Agregação

**Agregação** é um tipo especial de associação, representa relação todo-parte.

**Diferença é semântica**! Na agregação um objeto está contido dentro do outro.

- Assimétrico. Se um objeto A é parte do objeto B, B não pode ser parte de A.

- Agregações propagam comportamento.

Sejam duas classes X e Y. Podemos verificar se X agrega Y respondendo as seguintes perguntas:

- X tem um ou mais Y?

- Y é parte de X?

No diagrama de classes, representamos agregações como uma linha com um diamante (losango) branco perto da classe do todo.

<img src="../.assets/exagregacao.JPG">

###  Relacionamentos - Classes associativas 

**Classes associativas** são classes relacionados com associações, ao invés de outras classes.

São utilizadas quando precisamos manter informações que são da associação e não das classes associadas.

Na UML, classes associativas são representadas da mesma forma que classes normais. 

No entanto, a classe associativa estará ligada por uma **linha tracejada** à uma associação. Neste caso, o nome da classe substitui o nome da associação na linha.

<img src="../.assets/esclasasso1.jpg">

<img src="../.assets/esclasasso2.jpg">

###  Relacionamentos - Associações Ternárias 

**Associações Ternárias** são usadas quando precisamos associar objetos de três classes diferentes.

É possível ter associações ternárias e classes associativas em conjunto.

<img src="../.assets/assoter.JPG">

<img src="../.assets/assoter2.JPG">

### Relacionamentos - Associações Reflexivas

**Associações Reflexivas** ou auto-associações relaciona objetos de uma mesma classe. Onde objetos de uma classe possuem papéis distintos.
Uso de papéis é importante para evitar ambiguidade.

<img src="../.assets/associrefl.JPG">

## Interpretadas

### Identificando Classes Iniciais

Identificar classes candidatas e remover classes desnecessárias. Processo **não** sequencial.

Identificar classes a partir de seus comportamentos relevantes para o sistema. De forma a cumprir suas **responsabilidades**.

Responsabilidades são tudo que um objeto conhece ou faz (só ou com ajuda).

- Objeto Cliente conhece seu nome, endereço e telefone.

- Objeto Pedido conhece sua data de realização e deve ser capaz de calcular seu valor total.

Existem casos onde a responsabilidade não pode ser cumprida pelo objeto sozinho. Nesses casos, o objeto requisita **colaborações**.

- Fatura de um pedido é solicitada.

- Objeto Pedido tem responsabilidade de fornecer seu valor total.

- Objeto Cliente tem responsabilidade de fornecer seu nome.

- Objeto ItemPedido fornece quantidade do produto e subtotal.

- Objetos Produto fornecem nome e valor unitário.

Colaborações são nossos **Relacionamentos**.

<img src="../.assets/indenticlassini.JPG">

**Objetos de Entidade:**

- Representam conceitos do negócio;

- Costumam armazenar informações persistentes do sistema;

- Atores do sistema não possuem acesso direto a objetos de entidade, apenas por meio de comunicação com outros objetos;

- Participam de muitos casos de uso e possuem ciclo de vida longo;

- Conhecer fácil de identificar, normalmente fornecido por atores;

- Fazer: fornecer valores de atributos, realizar cálculos simples, criar/destruir objetos partes.


**Objetos de Fronteira:**

- Utilizados para comunicação do sistema com os atores;

- Traduzem eventos gerados por um ator em relevantes ao sistema;

- E apresentam resultados internos do sistema para atores;

- Pode se comunicar com humanos, outros sistemas ou dispositivos atrelados ao sistema;

- Conhecer informações manipulados por meio de interface;

- Fazer notificações à objetos de controle sobre eventos gerados externamente e notificações aos atores sobre interações internas.

- Identificação inicial ignora comportamentos, considera apenas informações.



**Objetos de Controle:**

- Ponte de comunicação entre objetos de fronteira e objetos de entidade;

- Controlam lógica de execução de um caso de uso;

- Decidem curso de ação após evento externo;

- Propagam requisições de operações para objetos relacionados;

- Conhecer: valores acumulados ou derivados durante a realização do caso de uso;

- Fazer: realizar monitorações, coordenar realização de caso de uso, assegurar regras do negócio, coordenação criação de associações entre objetos de entidade.


**Divisão de Responsabilidades** facilita as eventuais modificações no sistema, tornando-as mais localizadas.

<img src="../.assets/indeclassinit2.JPG">

### Identificando Classes

É realizada a análise dos casos de uso e todos os seus fluxos.

- Na descrição textual, são destacados os **substantivos** e **locuções equivalentes** a substantivos;

- Sinónimos são removidos;

- Os nomes permanecentes correspondem às classes.

- Substantivos relacionados a atores aos quais o sistema **não** precise armazenar informações devem ser removidos;

- Responsabilidade de fazer são os verbos, a classe responsável costuma ser o sujeito ao qual o verbo está ligado;

- Responsabilidade de conhecer e colaborações são as informações adicionais do caso de uso.


**Propriedades:**

- atributos guardam valores atômicos;

- não possuem estrutura interna (modelar como classe);

- aplica-se a **todos** os objetos de uma classe.
