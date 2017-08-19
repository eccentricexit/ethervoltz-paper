# EtherVoltz: Blockchain Para Eleições Auditáveis
---
## Resumo		
P1: Introduzir os avanços de segurança e velocidade em processos eleitorais não dependentes de software.
P2: Apresentar crescimento da complexidade dos sistemas que controlam os registros digitais e seu custo na dimensão financeira e de transparência devido a centralização do poder.
P3: Apresentar EtherVoltz como solução para a gerência dos registros digitais e seus beneficios
## 1. Introdução	
P1: Introduzir os altos custos relacionados ao gerenciamento dos registros digitais e das urnas, após as eleições
P2: Apresentar solução trivial de cliente-servidor tradicionais e porque não funcionam
P3: Apresentar problema de auditabilidade das urnas devido ao monopólio do TRT
P4: Apresentar casos relevantes
P5: Apresentar EtherVoltz como uma solução para estes problemas
P6: Detalhar a natureza de resistencia a ataques DDoS do projeto
P7: Detalhar as vantagens de transparência devido a natureza imutável do blockchain e resistência a ataques internos
P8: Detalhar as vantagens de remover do trt a necessidade gerenciar a base de dados
## 2. Conceitos e Definições
P1: Explicar o motivo desta seção
### 2.0 P1: Princípio da independência de software
### 2.0 P1: VICE/Boleta de urna
### 2.1 P1: Conceito de estado
### 2.2 P1: Criptografia assimétrica, chave pública, privada e o termo "carteira" utilizado neste documento
### 2.3 P1: Conceito de transação
### 2.4 P1: Conceito de bloco
### 2.5 P1: Conceito de blockchain
### 2.6 P1: EVM / Maquina virtual Ethereum como um computador global de natureza distribuida, decentralizada e imutável.
### 2.7 P1: Smart Contract - Apresentar o conceito de smart contracts e a linguagem de programação solidity	
### 2.8 P1: Criptomoeda/token - Apresentar o conceito de criptomoeda
### 2.8 P1: Conceituar VoteToken
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
## 7. Conclusão		
P1: Descrever que o uso de um livro razao público e imutável decentraliza o processo de auditorias
P2: Descrever que o uso de um blockchain atualmente em funcionamento tira do governo o trabalho de administrar e proteger registros digitais e acelera o processo de apuração
## 8. Referências	


-------------
Definição de transação
Segurança
