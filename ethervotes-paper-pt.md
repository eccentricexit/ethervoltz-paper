# EtherVoltz: Blockchain Para Eleições Auditáveis
---




## Resumo		
###### [P1: Introduzir os avanços de segurança e velocidade em processos eleitorais]
Os avanços tecnológicos nos setores de criptografia e segurança da informação permitiram o desenvolvimento de sistemas eleitorais que oferecem celeridade na apuração de registros digitais de votos. 
Já estudos específicos de segurança para sistemas eleitorais, evidenciaram a necessidade de que sejam independentes de software para garantir a auditabilidade das eleições.



###### [P2: Apresentar crescimento da complexidade dos sistemas que controlam os registros digitais e seu custo na dimensão financeira e de transparência devido a centralização do poder.]
 A gerência destes sistemas segue crescendo em complexidade mas principalmente em custos. Custos não só na dimensão de recursos, mas também na dimensão de transparência do processo, visto que requerem progressivamente a centralização de poderes nas mãos do administrador.


###### [P3: Apresentar EtherVoltz como solução para a gerência dos registros digitais e seus beneficios]
Este documento apresenta uma proposta de sistema eleitoral independente de software que remove do administrador a tarefa de garantir a disponibilidade e integridade dos registros digitais dos votos, além de garantir que qualquer pessoa tenha o poder de auditar esses registros, através de uma aplicação distribuida que funciona sobre um blockchain já em funcionamento.





## 1. Introdução	
###### P1: Introduzir os altos custos relacionados ao gerenciamento dos registros digitais e das urnas, após as eleições
Em sistemas eleitorais de primeira, segunda e terceira geração, os registros digitais dos votos ficam salvos na memória dos equipamentos que precisam ser levados dos locais de votação de volta para as centrais onde ocorre a apuração dos votos. Além dos custos envolvidos para garantir que estes equipamentos não sejam alterados ou destruídos durante o transporte, o administrador também precisa guardar estes registros após a apuração de votos para posteriores auditorias.


###### P2: Apresentar solução trivial de cliente-servidor tradicionais e porque não funcionam
Uma solução trivial porém falha que alguém pode pensar, é a utilização de um sistema cliente-servidor para a gerência destes registros. Entretanto, este sistemas apresentam falhas que podem aumentar o custo das eleições significativamente e que introduzem novos pontos de falha ao sistema:
1. **Ataques de negação de serviço**: É imprescindível que eleições não sejam atrasadas devido a um possível ataque de negação distribuído.
2. **Vazamento de chaves**: Se as credenciais utilizadas para a administração do sistema são adquiridas por um atacante, este tem o poder total sobre o resultado das eleições.
3. **Ataques internos**: As vulnerabilidades de um sistema aumentam proporcionalmente ao seu tamanho. Ataques internas crescem como um problema a medida que mais e mais pessoas estão envolvidas no processo de desenvolvimento dos muitos componentes que protegem o sistema.

###### P3: Apresentar problema de auditabilidade das urnas devido a centralização de poderes
Após o período eleitoral, caso um cidadão queira auditar o resultados das eleições ele precisa interagir com o administrador do processo eleitoral para ter acesso os registros digitais, aos equipamentos e aos registros independentes de software (caso o administrador tenha optado por sistemas que utilizem VICE). Cabe ao administrador decidir se ele tem ou não permissão para realizar a auditoria e quais são condições para a realização da mesma.

###### P4: Apresentar casos relevantes
O problema deste tipo de centralização de poderes fica evidente no Brasil, alguns casos bem documentados são brevemente listados a seguir:
1. **O Caso Marília, SP - 2004**: Em auditoria, os Arquivos de Espelhos de Boletins de Urna da 400º Zona Eleitoral indicavam muitas seções eleitorais tiveram seus reultados recebidos para apuração **antes** do início da votação. Dois processos judiciais foram iniciados decorrentes destas contatações, ambos encerraram em 2009 sem julgamento final.[3]

2. **O Caso Itajaí, SC - 2008**: Foi constatada burla intencional na cerimônia de carga e lacração das urnas em que nenhuma urna preparada para a votação passou pelo teste obrigatório prescrito pelo Art. 32 da Res. TSE 22.712/08. Um caso foi o da 97ª Zona Eleitoral onde a urna da seção 236 que foi sorteada para o teste obrigatório **foi substituída por outra** na hora do teste, preparada exclusivamente para este fim. A utilizada para o teste foi posteriormente colocada à parte e recarregada, procedimento que destruiu eventuais provas nela gravadas.

3. **O Caso Diadema, SP - 2000**: Foram negados a todos os partidos que solicitaram o acesso aos registros digitais dos votos realizados nas urnas eletrôncias. Somente 9 meses após a eleição os partidos obtiveram acesso, não ao registros dos votos, mas aos Arquivos de LOG das urnas que apontaram que **todas** as urnas haviam sido carregadas **fora** da cerimônia oficial de carga e lacramento das urnas.[1]

4. **O Caso Alagoas - 2006**: Diversas irregularidades nos arquivos gerados pelas urnas foram detectadas por auditores externos [4]. Frente as evidências, o administrador negou acesso aos arquivos solicitados pelos auditores e transferiu ao requerente uma cobrança antecipada no valor de R$ 2 milhões para que fosse desenvolvida uma perícia das urnas. Diante do não pagamento proibitivo, o requerente foi multado e condenado por litigância de má-fe. Mesmo tendo apresentado provas de inconsistência no funcionamento das urnas, a perícia das mesmas não foi permitida.[5]


5. **Assinaturas Divergentes - 2002 e 2008**: Nas eleições de 2º Turno de 2002 e 2008, foram detectadas durante verificação dos arquivos carregados nas urnas eletrônicas, a presença de um conjunto de arquivos com resumos digitais diferentes das publicadas nas respectivas cerimônias oficiais de lacramento dos sistemas. A providência tomada pelo administrador frente a estas descobertas, foi a de publicar novas Tabelas de Hash, calculadas **a portas fechadas e fora de uma cerimônia oficial**. A perícia das urnas foi indeferida e as Tabelas de Hash originais que demonstravam a impropriedade, foram removidas do local.[2]



###### P5: Apresentar EtherVoltz como uma solução para estes problemas
O núcleo do projeto EtherVotlz propoem a utilização do _blockchain_ _Ethereum_ como o _backend_ dos registros digitais dos votos. Embora algumas vantagens da estratégia estejam listadas abaixo, mais detalhes serão apresentados na Seção 3 deste documento.
1. Distribuição: Diferente de sistemas que utilizam servidores comuns, aplicações que executam na máquina virtual _Ethereum_ são resistentes a ataques de negação de serviço distribuidos.
2. Decentralização: Como a máquina virtual não possui um dono ou entidade responsável por sua administração, nenhuma instituição ou pessoa possui poder de censurar ou de alguma forma impedir que aplicações construídas na plataforma se mantenham em execução.
3. Todas atualizações na base de dados são registradas permanentemente no blockchain  estão disponíveis para auditoria por qualquer pessoa, a qualquer momento em qualquer lugar.

## 2. Conceitos e Definições

###### P1: Explicar o motivo desta seção
Para facilidar a explicação altamente abstrata do funcionamento da solução proposta, são definidas nesta seção, diversos termos utilizados ao longo do documento. Embora definidos brevemente aqui, o leitor se beneficiará se possuir conhecimento sobre os mecanismos envolvidas tanto em sistemas eleitorais quanto aspectos técnicos específicos do desenvolvimento de software e segurança da informação mas principalmente de tecnologias _blockchain_ como o Bitcoin e Ethereum.
### 2.1 Princípio da Independência de Software em Sistemas Eleitorais
Do mesmo autor da chave de assinatura digital RSA [6]: 
```
Um sistema eleitoral é independente do software se uma modificação ou erro não-detectado no seu software não pode causar uma modificação ou erro indetectável no resultado da apuração.
```
### 2.2 VICE 
Voto Impresso Conferível Pelo Eleitor: É um documento em papel que é apresentado ao eleitor no momento da votação. O VICE é apresentado para que ele possa confirmar visualmente o voto mas ao qual ele não tem contato físico (e nem leva para casa). Os termos VICE e Registro de Voto Físico são utilizados de forma intercambeável e significam a mesma coisa.

### 2.3 Livro razão Público
Livro razão é o nome dado a um documento que agrupa dados que registram o estado atual de alguma razão. _Blockchains_ são comumente comparados a livros razão públicos, pois são uma sequência de alterações de estado ordenadas uma após a outra e cujas alterações dependem necessariamente do estado anterior:

Remetente | Operação | Parâmetros | Destinatário
--- | --- | --- | ---
João | enviou | 3  reais | para  Alice
Alice | enviou | 2  reais | para Carlos
Carlos | enviou | 1 real | para João
João | enviou | 1 real | para Alice

No exemplo acima, Carlos só poderá enviar 1 real para João se tiver recebido 1 real ou mais anteriormente.

### 2.4 Estado 
O estado da aplicação é o conjunto de todas as informações e variáveis da aplicação em um determinado instante.

### 2.5 Transação 
Uma transação é uma mensagem enviada à aplicação que possui dados sobre uma determinada operação que o remetente deseja realizar.Transações discutidas netes documento possuem, além de outras informações:
- O endereço do destinatário que também é sua chave pública. 
- Uma assinatura criptográfica que comprova o remetente da transação.
- Informações sobre a operação a ser realizada, como o nome da operação e parâmetros.

Sempre que uma transação é confirmada, um _hash_  que identifica esta transação individualmente é gerado a partir do conjunto de informações contidas nela e na história do blockchain até o momento. Com este _hash_ é possível solicitar à máquina virtual informações sobre a transação. Este recurso é explorado no EtherVoltz para garantir a rastreabilidade das operações realizadas na aplicação durante uma auditoria.
### 2.6 P1: Conceito de bloco
Um bloco "b" é uma pacote contendo uma referência à um bloco anterior "d" e uma lista de transações T. A inclusão de um bloco no blockchain implica na atualização do estado, mas o bloco só é incluído se for considerado válido. Um bloco b é considerado válido se: 
1. Todas as transações t pertencentes a T listadas nele são válidas.
2. As condições impostas pelo protocolo de consenso são atingidas.

### 2.8 Blockchain
Um blockchain é uma sequência de blocos "b" B=[b0,b1,b2,b3...] em que cada bloco referencia o bloco precedente e até o _bloco gênesis_ "b0". Um _blockchain_ é dito válido se cada bloco b pertencente a B for válido.
Em discussões sobre desenvolvimento de aplicações distribuídas empoderadas por tecnologia blockchain - e em alguns trechos neste documento-, é comum se referir ao mesmo como um banco de dados distribuído, visto que existem copias dela armazenadas nos computadores dos milhares de nós e minaradores espalhados pelo mundo.

### 2.9 Algorítmo ou Protocolo de Consenso
Um algorítmo ou protocolo de consenso, no âmbito de sistemas distribuidos é um processo pelo qual uma rede de computadores entra em acordo de qual é o estado atual do sistema. 
No Bitcoin, o protocolo de consenso utilizado é chamado de "Prova de Trabalho" ou "_Proof of Work_" e é o que dá segurança ao sistema contra transações inválidas ao sistema. Na máquina virtual Ethereum, o protocolo de consenso dá garantia de que nenhum programa como o EtherVoltz terá seu estado atual modificado por um atacante.

### 2.7 Nó Completo
Neste documento, "Nós" são computadores conectados à rede ethereum através de algum cliente como _geth_ ou _pyeth_ e que possui uma cópia completa ou parcial do blockchain. O termo "nó completo" é utilizado para explicitar que o nó em questão possui uma copia do blockchain completa e válida, já que nós "leves" existem e estão em desenvolvimento para garantir o acesso de dispositivos sem recursos ao blockchain.


### 2.9 P1: EVM / Maquina virtual Ethereum como um computador global de natureza distribuida, decentralizada e imutável.

### 2.9 P1: Smart Contract - Apresentar o conceito de smart contracts e a linguagem de programação solidity	

### 2.10 P1: Criptomoeda/token - Apresentar o conceito de criptomoeda


## 3. Confiabilidade e Transparência Através de um Livro-Razão Público
P1: Descrever a estratégia do projeto mover os registros digitais para uma base de dados distribuída e decentralizada e seus efeitos

P2: Descrever a estratégia da utilização de uma criptomoeda como voto

P4: Descrever a estratégia de as chaves públicas das urnas em um contrato para rastreabilidade e auditoria das urnas

P3: Descrever a consequência decentralizadora do uso do blockchain

### 3.1 A Urna

P1: Descrever a urna como qualquer interface que comunique com um cliente ethereum (e.g. Metamask, Infura, Geth, Pyeth). Uma carteira e sua chave privada associada também deve ser fornecida, esta chave é sucetível a vazamento como em qualquer sistema de voto que envolve registros digitais criptografados, mas no ethervotes, diferente da urna de primeira geração brasileira, a detectabilidade de fraudes se torna possível porque elas produzem provas na forma de incoerências entre as evidências digitais salvas no blockchain e nos registros físicos.

P2: Descrever que as urnas possuem  como identificador, a chave pública que ela utiliza para transferir os votetokens. Assim, as urnas e todos os votos emitidos por elas são rastreáveis no blockchain.

P2: Descrever que a eleição possui uma janela de tempo para ocorrer, definido no blockchain. Nenhum voto acontece antes ou depois deste período.
### 3.2 O Procedimento do Voto

P1: Descrever o procedimento de voto aos olhos do eleitor

### 3.3 Após a Votação

P1: Descrever que após cada voto, a urna eletrônica pode ser destruída e os registros digitais estão seguros no blockchain.

P2: Descrever que após o tempo estipulado no contrato, nenhum novo voto pode ser efetuado

### 3.4 Auditoria
P1: Descrever os que no sistema ethervotes, os registros de votos estão em dois lugares, nos registro físicos que são as boletas, e nos registros digitais, localizados no blockchain em milhares de computadores ao redor do mundo.

#### 3.4.1 VoteTokens
P0: Descrever que auditoria consiste em solicitar ao administrador das eleições, as boletas referentes a =determinada urna a ser auditada e solicitar à máquina virtual ethereum através de qualquer navegador de blocos, as transações realizadas pela identifica

P1: Descrever que qualquer pessoa no planeta pode analizar o código utilizado para a emissão e gestão dos votetokens no blockcahin sem precisar pedir permissão do administrador. 

P2: Descrever que, na verdade, o código do contrato deve ser público para que qualquer pessoa possa propor melhorias ANTES das eleições, mas que também ficará enquanto o blockchain existir.

P3: Descrever que todas os votos realizados com votetokens estão registrados no contrato do votetoken, disponíveis para qualquer cidadão auditar. Os votos registrados apontam também, qual é a origem do voto. Isto é, de qual urna ele saiu. 

P4: A registro do voto contém também o códígo hash da transação o mesmo código presente na boleta

#### 3.4.2 VICE
P1: Descrever a utilidade da boleta e sua necessidade

P2: Descrever que a boleta deve necessáriamente possuir duas informações impressas. Um comprovante visual para o eleitor validar no momento da votação que pode ser uma foto ou número do candidato e o hash da transação executada no blockchain.

## 4. Conclusão		
P1: Descrever que o uso de um livro razao público e imutável decentraliza o processo de auditorias

P2: Descrever que o uso de um blockchain atualmente em funcionamento tira do governo o trabalho de administrar e proteger registros digitais e acelera o processo de apuração

## 5. Referências	
[1] 1º Relatório do Comitê Multidisciplinar Independente - pg 24.
[2] 1º Relatório do Comitê Multidisciplinar Independente - pg 25.
[3] 1º Relatório do Comitê Multidisciplinar Independente - pg 27.
[4] Fernandes, C.T. - Radiografia das Urnas Eleitorais. S. J. dos Campos: ITA, dezembro de 2006 - http://www.votoseguro.org/arquivos/AL06-laudoFerITA.zip
[5] 1º Relatório do Comitê Multidisciplinar Independente - 
[6] RIVEST, Ronald L. - On the notion of 'software independence' in voting systems
