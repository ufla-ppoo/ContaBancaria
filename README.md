# Exercício Conta Bancária

Este exercício é dado na parte de revisão de Conceitos Básicos de Orientação a Objetos da disciplina GAC106 - Práticas de Programação Orientada a Objetos.

Basta seguir os passos apresentados a seguir.

## Orientações Gerais

- Você deve fazer um passo de cada vez, testá-lo, fazer o commit e enviar suas alterações.
Somente depois disso é que você deve passar para o próximo passo.

- **ATENÇÃO**: **desligue o GitHub Copilot para fazer o exercício!**

  - Se você utilizá-lo você não estará realmente praticando os conceitos aprendidos.
  - E, com isso, não desenvolverá as habilidades necessárias para se tornar
	um bom programador/desenvolvedor.
  - Sem contar ainda a questão do plágio.
  - Os exercícios trazem exemplos de código em Java, e você também pode (e deve) consultar os
    slides das aulas teóricas de revisão.

- Esse arquivo README pode ser melhor visualizado no VS Code (com formatação adequada) 
  abrindo-o no modo de visualização. Para isso, basta apertar Ctrl+Sfhit+V com ele aberto.

## Passo 1 - Representando uma conta bancária

Esse e os próximos exercícios se referem às operações de uma conta bancária.

Nesse primeiro passo, crie uma classe para representar contas bancárias, que atenda às necessidades abaixo.
Lembre-se de usar adequadamente os modificadores de visibilidade (`public` ou `private`) dos atributos e métodos.

- As contas devem possuir um saldo (`double`) e um limite (`double`).
  - O saldo representa o valor disponível na conta.
  - O limite representa o valor absoluto máximo que a conta pode ficar negativa.
- Devem existir métodos para consultar o saldo e o limite da conta.
- Devem existir métodos para saque e para depósito de valores na conta.
- A conta pode ter saldo negativo no máximo até o limite estabelecido.
  - Exemplo: se o limite da conta for R$ 500, significa que o saldo pode chegar ao valor mínimo de -R$ 500.
- A classe não deve ter nenhuma interação com o usuário (ou seja, dentro dela não deve existir 
  exibição de mensagens, nem obtenção de dados do usuário).

Teste sua implementação usando o `JShell`.

- Você deve testar a criação de objetos da classe, a consulta do saldo e do limite, 
  o depósito e o saque (conferindo se o saldo é atualizado corretamente e se o limite está sendo respeitado).

Ao terminar, faça o commit e sincronize as suas alterações (use `passo1` no comentário do commit).

- Obs.: se precisar fazer novo commit com alguma correção, use o comentário `passo1 - correções`.

## Passo 2 - Representando um caixa eletrônico

Crie agora uma outra classe que represente um Caixa Eletrônico.
Nesta classe, por enquanto, crie um atributo para guardar uma única conta
(**dica**: siga exatamente o que pede o enunciado, portanto, não crie vetor nem ArrayList de contas nesse passo).

Em seguida implemente um menu com as opções abaixo e implemente métodos separados para tratar cada opção.

```
1. Criar Conta
2. Consultar Dados da Conta
3. Depositar
4. Sacar
5. Sair
```

Na opção de criar conta, o programa deve pedir para o usuário informar o valor do limite 
e o saldo inicial da conta e criar o objeto da conta com essas informações.

Na opção de consultar dados da conta, devem ser exibidos o saldo e o limite da conta.

E nas opções de depósito e saque, o programa deve pedir para o usuário informar o valor a ser 
depositado ou sacado e realizar a operação na conta. Além disso, deve ser exibida uma mensagem 
informando se a operação foi realizada com sucesso ou se não pôde ser realizada 
(exemplo: valor de saque além do limite da conta).

Por fim, altere o método `main` da classe `App`, para que nele seja criado um objeto da classe que representa o caixa eletrônico e seja disparada a execução do menu.

- Dica 1: lembre-se de há um exemplo de implementação de menu no Campus Virtual (repositório Carro).
- Dica 2: repare que se o usuário acessar as opções que alteram a conta, antes da conta ser criada, 
  ocorrerá um erro de `NullPointerException`. Podemos facilmente evitar esse problema, 
  verificando primeiro se o atributo que representa a conta é diferente de `null` 
  (e informando apropriadamente ao usuário).

Teste suas alterações!
Depois, faça o commit e sincronize suas alterações (use `passo2` no comentário do commit).

## Passo 3 - Sobrecarga de construtores

Altere a classe que representa as contas bancárias de forma que ela passe a ter dois construtores,
utilizando o conceito de **sobrecarga**.

- Os dois construtores devem receber o valor do limite da conta.
- Mas apenas um deles deve receber o valor do saldo inicial da conta. 
  Portanto, no outro construtor o saldo deve ser inicializado com zero.

Altere então a classe do caixa eletrônico para que existam duas opções diferentes de criação de contas.

- Uma que pede para o usuário o saldo inicial e outra que não pede.
- Cada opção deve chamar o construtor correspondente.

Utiliza o operador `this` para evitar replicação de código na implementação dos construtores.
(Dica: veja os slides de revisão dos conceitos de OO).

Teste suas alterações!
Depois, faça o commit e sincronize suas alterações.

## Passo 4 - Numeração automática de contas

Neste passo, a ideia é que as contas bancárias tenham um novo atributo para guardar 
o número da conta e um método que retorne essa informação.

Nós poderíamos receber o número de cada conta no construtor e deixar a classe do caixa 
eletrônico definir a numeração.
Mas é mais interessante que a própria classe que representa as contas trate automaticamente 
a numeração, utilizando o conceito de **atributos estáticos**.

A ideia é ter dois atributos novos na classe que representa as contas:

- Um atributo comum para guardar o número da conta (que é diferente para cada conta).
- E um atributo estático para guardar o número da última conta criada (que tem o mesmo valor para todas as contas).

No construtor da classe que representa as contas:

- o atributo estático deve ser incrementado, 
- e o seu valor deve ser usado como número da conta que está sendo criada.

Dica: utilize o `JShell` para testar a criação de contas e verificar se a numeração automática 
está funcionando corretamente.

Teste suas alterações!
Depois, faça o commit e sincronize suas alterações.

## Passo 5 - Tratando várias contas

Na classe que trata o caixa eletrônico, crie um atributo para guardar um vetor de contas 
(atenção: você **deve** usar um vetor e **não um ArrayList**).

- O vetor deve substituir o atributo criado no passo 2 para guardar uma única conta.
- Na opção de menu de criar contas, uma nova conta deve ser criada e acrescentada no vetor
  (se ainda existir espaço disponível).
- Após a criação de uma conta, o programa deve exibir o número gerado para a conta.
- Nas operações de consulta, saque e depósito, o programa deve pedir para o usuário informar o 
  número da conta sobre a qual deseja operar e, então, deve procurar a conta correspondente no 
  vetor para realizar a operação.
- Deve ser acrescentada uma opção de menu chamada `Exibir contas` que exibe o número de todas as contas.
- E, claro, lembre-se também de alterar as demais opções de menu (consultar dados, saque e depósito), 
  pois o usuário terá agora que informar o número da conta sobre a qual deseja operar.

Teste suas alterações!
Depois, faça o commit e sincronize suas alterações.

## Passo 6 - Fazendo PIX - Parte 1

Agora que conseguimos criar contas diferentes, poderemos fazer pagamentos via PIX entre elas.

Para isso, primeiramente, altere a classe que representa as contas para que ela tenha um novo atributo 
para guardar a chave PIX da conta (uma `String`), e um método para consultar essa informação.

- Você deve também alterar os construtores da classe para receber a chave PIX como parâmetro 
  e inicializar o atributo correspondente.

Em seguida, altere a classe do Caixa Eletrônico para que:

- na opção de criação de conta, o programa também peça para o usuário informar a chave PIX da conta 
- e na opção de exibir contas, o programa mostre também a chave PIX de cada conta (além do número da conta).

## Passo 7 - Fazendo PIX - Parte 2

Crie agora um método na classe que representa as contas para tratar os pagamentos via PIX.

- O método deve receber por parâmetro o valor a ser pago via PIX e o objeto da conta que receberá o pagamento.
- O valor deve ser sacado da conta que está realizando o pagamento e depositado na conta que está 
  recebendo o pagamento.
- O método não deve alterar diretamente os saldos das contas, mas sim chamar os métodos de 
  saque e depósito apropriadamente.
- Lembre-se que o pagamento não deve ser realizado se o valor solicitado estiver além do limite da conta de origem.

Na classe que representa o caixa eletrônico, crie uma opção de menu para pagamentos via PIX.

- O usuário deverá informar o número da conta de origem, a chave PIX da conta de destino e o valor do pagamento.
- A classe deverá então encontrar as contas de origem e de destino e chamar o método de pagamento via PIX 
  da conta de origem, passando o valor e a conta de destino como parâmetros.

Teste suas alterações!
Depois, faça o commit e sincronize suas alterações.

## Passo 8 - Rendimento na conta

Suponha que nossa conta é especial e possui um rendimento periódico.
Para tratá-lo faça o seguinte:

- Na classe que representa as contas, crie um atributo **estático** para guardar o valor da taxa de rendimento (percentual).
- Crie um método `render` que aplica a taxa de rendimento ao saldo da conta. Avalie se tal método deve ser **estático** ou não.
- Por fim, crie uma opção de menu na classe que representa o caixa eletrônico para que o usuário possa fazer a conta render.
  - Obs.: claro que em uma situação real, o rendimento não seria algo que o usuário poderia escolher quando quisesse, 
  mas para fins de prática de POO, vamos imaginar que seja possível fazer isso.

Teste suas alterações!
Depois, faça o commit e sincronize suas alterações.

## Passo 9 - Alterando rendimento

Crie um método na classe que representa as contas para alterar a taxa de rendimento da conta 
(e crie uma opção de menu para o usuário informar a nova taxa).

Avalie se o método deve ser **estático** ou não.

Teste suas alterações!
Depois, faça o commit e sincronize suas alterações.