# EtherVoltz: Blockchain Para Eleições Auditáveis
---
## Resumo		
P1: Introduzir os avanços de segurança e velocidade em processos eleitorais não dependentes de software.
P2: Apresentar crescimento da complexidade dos sistemas que controlam os registros digitais e seu custo na dimensão financeira e de transparência devido a centralização do poder.
P3: Apresentar EtherVoltz como solução para a gerência dos registros digitais e seus beneficios
---
## Abstract		
---
## 1. Introdução	
P1: Apresentar os dois principais problemas que este artigo pretende resolver, quanto aos registros digitais de votos
P2: Definir que este artigo não pretende discutir a necessidade da independência de software
P3: Apresentar a organização deste documento
## 2. Eleições Opacas (Motivação/Problema)	
P1: Descrever função desta seção
### 2.1 Custos		
P1: Apresentar quantos países utilizam a urna DRE sem vice e a opinião internacional sobre ela.		
P2: Apresentar o caso Marília, o caso Itajaí, o caso Diadema e o caso Alagoas		
P3: Apresentar custo de urnas DRE sem e com VICE		
P4: Concluir introduzindo a necessidade de VICE e conceito de independência de software, e proposta do trabalho para baratear e aumentar a segurança de sistemas  eleitorais com VICE ao mover a urna à máquina virtual ethereum.		
## 3. Informações contextuais		
P1: Apresentar a maquina virtual ethereum como um computador global e a linguagem de programação solidity		
P2: Apresentar desafios de escalabilidade atuais e o conceito de canais de estado		
## 4. Revisão do estado da arte		
P1: Apresentar desafios de escalabilidade do blockchain citando e-vox e followmyvote		
P2: Apresentar problemas de auditabilidade de soluções dependentes de software		
## 5. EtherVoltz (Solução)		
P1: Descrever que os objetivos da proposta são delegar a responsabilidade da integridade e disponibilidade dos votos à EVM
### 5.1 Arquitetura e Metodologia		
P1: Apresentar problemas de soluções baseadas apenas em blockchain (tempo de transação, limitações da evm)		
P2: Apresentar canais de estado (Rede raiden) como solução		
P3: Concluir com a criação de VoteToken.sol e o procedimento de transferência de tokens para carteiras de candidatos.		
P4: Notar que estes contratos são simples, ficam disponíveis no enderenço na EVM após deployment e seus códigosfonte podem e devem ser publicados para inspeção independente.		
###  5.2 VoteToken		
P1: Descrever o procedimento da emissão de moedas fazendo um paralelo ao bitcoin.		
P2: Notar sobre a vantagem de segurança contra ataques internos, já que só possuem poder de voto carteiras que receberam votetokens que o STE emitiu. 		
###  5.3 Controle de carteiras		
P1: Descrever o contrato MachineRegistry.sol como solução para exposição e controle de carteiras (chaves públicas)		
P2: Descrever efeito da impressão da carteira da urna nas boletas contra fraudes		
###  5.4 Após a eleição		
P1: Descrever o que ocorre após as eleições no modelo antigo. Forças armadas, logística e transporte das urnas e boletas para apuração dos votos, perigo de fraude através da destruição de evidências (destruir urnas e boletas não favoráveis).	
P2: Descrever que no ethervotes os votos estão registrados no blockchain, por isso não há necessidade de segurança no transporte do equipamento eletrônico. Na verdade, o mesmo poderiam ou deveriam ser destruídas para evitar o vazamento de chaves privadas.		
P3: Descrever o processo de apuração atual e autoridade responsável.		
P4: Descrever o processo de apuração no ethervotes (getBalance)		
###  5.5 Auditorias		
P1: Descrever processo de auditoria de uma única urna no ethervotes. 	
````
1. Analisar o código fonte dos dois contratos utilizados 
2. Analisar o histórico de todas as transações realizadas 
3. Solicitação de todas as boletas com a chave pública utilizada na urna a ser auditada (Envolve o TRE)
4. Comparar boletas entregues pelo TRE com as transações registradas no blockchain.		
````
## 6. Conclusão		
P1: Celeridade e Transparência nas auditorias		
P2: Decentralização do poder		
P3: Barateamento das eleições		
 		
## 7. Experimentos		
P1: Apresentar prova de conceito construida e resultados
## 8. Referências		
[1] Relatório sobre o Sistema Brasileiro de Votação Eletrônica do Comitê Multidisciplinar Independente  CMind  pg. 10		
[2] Justica Eleitoral Trabalha Para Desenvolver Nova Urna Eletronica Que Terá o Voto Impresso  Acessoria de Comunicação do TSE  Disponível em http://www.tse.jus.br/imprensa/noticiastse/2017/Junho/justicaeleitoraltrabalhaparadesenvolvernovaurnaeletronicaqueteraovotoimpresso, acesso em 13/08/2017		
[3] Globo  Disponível em http://g1.globo.com/politica/noticia/2015/11/tseapontadificuldadesparaimplementarvotoimpresso.html , acesso em 13/08/2017
