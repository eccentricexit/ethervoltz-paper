# Tecnologia EtherVoltz Para Eleições Auditáveis
---
## Resumo 
Este artigo apresenta o desenvolvimento de uma prova de conceito de sistema eleitoral independente de software que remove do administrador a responsabilidade de garantir a disponibilidade, integridade e confiabilidade dos registros digitais dos votos. O código é escrito na linguagem Solidity e posteriormente compilado para byte code que pode ser interpretado pela máquina virtual Ethereum. O resultado é a criação de uma criptomoeda que existe para representar cada voto, onde cada transação fica gravada num blockchain resistente a censura, ataques de negação de serviço e que está sempre disponível para auditorias.

##### Palavras-chave: eleições, auditoria, criptografia, blockchain, criptomoeda
##### Área do Conhecimento: Engenharia da Computação

## Introdução
Em sistemas eleitorais e primeira, segunda e terceira geração, os registros digitais dos votos ficam salvos na memória dos equipamentos que precisam ser levados dos locais de votação de volta para as centrais para que ocorra a apuração dos votos. Além dos custos envolvidos para garantir que estes equipamentos não sejam alterados ou destruídos durante o transporte, o administrador também precisa guardar estes registros após a apuração de votos para posteriores auditorias.

Após o período eleitoral, caso um cidadão queira auditar os resultados das eleições ele precisa interagir com o administrador do processo eleitoral para ter acesso os registros digitais, aos equipamentos e aos registros independentes de software (caso o administrador tenha optado por sistemas que utilizem VICE). Cabe ao administrador decidir se ele tem ou não permissão para realizar a auditoria e quais são condições para a realização da mesma.

Os problemas deste tipo de centralização de poderes ficam evidentes no Brasil. Embora não seja objetivo deste documento discutir os efeitos da centralização de poderes em sistemas eleitorais, alguns casos bem documentados são brevemente listados a seguir: 
  
1. **O Caso Marília, SP - 2004**: Em auditoria, os Arquivos de Espelhos de Boletins de Urna da 400º Zona Eleitoral indicavam que muitas seções eleitorais tiveram seus resultados recebidos para apuração **antes do início da votação**. Dois processos judiciais foram iniciados decorrentes destas constatações, ambos encerraram em 2009 sem julgamento final. [1] 
  
2. **O Caso Itajaí, SC - 2008**: Foi constatada burla intencional na cerimônia de carga e lacração das urnas em que nenhuma urna preparada para a votação passou pelo teste obrigatório prescrito pelo Art. 32 da Res. TSE 22.712/08. Um caso foi o da 97ª Zona Eleitoral onde a urna da seção 236 que foi sorteada para o teste obrigatório **foi substituída por outra** na hora do teste, preparada exclusivamente para este fim. A urna que foi utilizada para o teste foi posteriormente colocada à parte e recarregada, procedimento que destruiu eventuais provas nela gravadas. [2] 
  
3. **O Caso Diadema, SP - 2000**: Foram negados a todos os partidos que solicitaram o acesso aos registros digitais dos votos realizados nas urnas eletrônicas. Somente 9 meses após a eleição os partidos obtiveram acesso, não aos registros dos votos, mas aos Arquivos de LOG das urnas que apontaram que **todas** as urnas haviam sido carregadas **fora** da cerimônia oficial de carga e lacramento das urnas. [3] 
  
4. **O Caso Alagoas - 2006**: Diversas irregularidades nos arquivos gerados pelas urnas foram detectadas por auditores externos [4]. Frente as evidências, o administrador negou acesso aos arquivos solicitados pelos auditores e transferiu ao requerente uma cobrança antecipada no valor de R$ 2 milhões para que fosse desenvolvida uma perícia das urnas. Diante do não pagamento do valor proibitivo, o requerente foi multado e condenado por litigância de má-fé.  
Mesmo tendo apresentado provas de inconsistência no funcionamento das urnas, a perícia das mesmas não foi permitida. [5]

Este projeto faz do _blockchain_, da máquina virtual _Ethereum_ e da infraestrutura já em funcionamento formada pelos milháres de nós ao redor do mundo. 
Ao transformar cada voto em uma criptomoeda, o sistema herda todas as características de segurança que dão robustez a sistemas como o Bitcoin e Litecoin.

## Estratégia

A estratégia utilizada envolve transformar os votos de uma dada eleição em uma criptomoeda que existirá para ser os registros digitais dos votos, de forma que um voto seja a transferência de uma moeda pertencente a uma carteira associada a uma urna para uma carteira associada um candidato. 
`Nota: O candidato não possui nenhum poder administrativo sobre a carteira que receberá os votos.` 
  
A regulamentação da transferência destas criptomoedas e o processo de emissão de novas unidades é definido através do código disponibilizado publicamente no contrato inteligente quando o sistema é criado. 
  
Após _deployment_ na máquina virtual, a regras não podem ser alteradas por ninguém, mas todas as alterações de estado e o código fonte do programa podem ser auditados por qualquer um a qualquer instante. 
  
Na prova de conceito do projeto EtherVoltz, a criptomoeda foi batizada de VoltToken e será discutida em mais detalhes na seção 4.1. 

Para garantir o principío de independência ao sistema, o projeto propõe o uso de um registro físico do voto ou VICE que fica sobre posse do administrador do processo eleitoral. A diferença deste modelo de VICE aos modelos propostos nas urnas de segunda e terceira geração, é que esta inclui o hash resultante da transferência do VoltToken. Detalhes sobre este modelo de VICE são discutidos na Seção 4.2. 
  
Portanto, em cada voto são produzidas duas provas que se referenciam: Uma é o VICE que fica sobre controle do administrador do processo. A outra é o registro digital e que fica salvo no blockchain e sobre qual o administrador não possui controle. 
  
![](https://raw.githubusercontent.com/mtsalenc/ethervoltz-paper/master/images/architecture.png) 

Na figura, as imagens rotuladas pelas letras A, B, C, D, E e F representam respectivamente: 
- Um computador conectado à rede Ethereum. 
- A rede Ethereum composta por milhares de nós ao redor do mundo. 
- Uma cópia do blockchain em nó na rede. 
- Uma impressora para imprimir o registro de voto físico. 
- Caixa lacrada para coleta dos VICE 
- Cofre para armazenamento dos VICE sob controle do administrador 
  
Note que de "A" saem duas setas, elas representam os destinos dos registros digitais e físicos respectivamente. A área demarcada por linha tracejada representa a base de dados decentralizada, isto é, a região do sistema sobre a qual nenhuma entidade central possui controle. Dados e programas que executam nesta região, são resistentes a censura e operam exatamente como definidos nos contratos. 

## Produção e Auditoria do Código Fonte 
Os requisitos que o contrato inteligente utilizado da prova de conceito pretende atender estão listados a seguir: 
- A transferência de VoltTokens só pode ocorrer durante o período eleitoral. Portanto, votos só podem ser emitidos nesta janela de tempo. 
- Apenas endereços de carteiras registradas no contrato podem transferir VoltTokens. 
- Apenas endereços de carteiras que representam candidatos podem receber VoltTokens. 
- Todas as urnas e suas respectivas carteiras são identificadas através de suas chaves públicas e estão definidas no contrato inteligente. 
- O número total de moedas em circulação é definido no momento da criação do sistema. 
- Nenhuma nova unidade da moeda pode ser emitida após a criação do sistema. 
- Cada urna recebe precisamente o número de VoltTokens correspondente ao número de eleitores que devem votar naquela urna. 
- As regras anteriores são auditáveis por qualquer um através do código fonte do contrato disponibilizado pelo administrador. 
  
Muito antes do período eleitoral, o administrador publica uma proposta do código fonte do contrato inteligente que será utilizado para regulamentar a emissão e controle de transferência das criptomoedas, para que o grande público possa propor melhorias e descobrir falhas. 
  
Após as melhorias serem implementadas, em cerimônia oficial, o administrador compila o código, envia o contrato à EVM e publica o endereço do mesmo para que o público possa acompanhar auditar todas as mudanças de estado que ocorrerem no programa. 
  
O administrador publica o código fonte do contrato inteligente para que qualquer auditor possa comparar o _byte code_ resultante da compilação, com o _byte code_ do contrato no endereço disponibilizado na cerimônia oficial. 
  
### O Procedimento do Voto 
Do ponto de vista do eleitor, o voto ocorre da mesma forma que em uma urna de segunda geração comum, exceto que a impressão do VICE ocorre em duas etapas.
  
A seguir são detalhados eventos relevantes que ocorrem durante a emissão de um voto. 
1. O eleitor, após ser autorizado pelo mesário, digita o código do candidato. 
2. A impressora imprime o VICE que fica visível para que o eleitor possa conferir. 
3. Se os dados estão corretos o eleitor pressiona "confirma". 
4. A urna envia uma transação à aplicação que está no endereço publicado na cerimônia oficial para transferir 1 VotltToken da carteira da urna para a carteira que representa o candidato. 
5. Após a confirmação da transação, a urna recebe um _hash_ que identifica unicamente este voto no blockchain. 
6. A impressora imprime este hash no VICE. 
7. O VICE é cortado e cai em uma caixa lacrada. 
  
![](https://raw.githubusercontent.com/mtsalenc/ethervoltz-paper/master/images/VICE.png)
  
### Pós-Voto 
Após o período eleitoral existem dois registros de cada voto contado. Um deles é o registro digital do voto que está gravado no blockchain da máquina virtual Ethereum. O outro é o voto impresso conferível pelo eleitor. 
  
Os registros digitais dos votos podem ser solicitados por qualquer pessoa a qualquer momento para auditoria e possuem as seguintes informações: 
- De qual urna o voto foi emitido. 
- Qual candidato recebeu o voto. 
- O hash que identifica unicamente esta transação no blockchain 
  
Já os registros físicos do voto, ficam sob controle do administrador da eleição e possuem as seguintes informações: 
- De qual urna o voto foi emitido. 
- Qual candidato recebeu o voto. 
- O hash que identifica unicamente esta transação no blockchain 
  
A apuração dos votos é instantânea e consiste em apenas solicitar ao computador mundial, o balanço das carteiras criadas para receberem os votos dos candidatos. 
  
### Auditorias 
Os passos para uma auditoria simples de uma urna estão listados a seguir. 
1. O auditor solicita à maquina virtual uma lista com todas as transações realizadas pela urna em questão, passando a chave pública da urna. 
2. O auditor solicita ao administrador da eleição, a caixa contendo os votos impressos conferíveis pelo eleitor, da mesma urna. 
3. O auditor compara as duas provas, atento as regras listadas abaixo. 
- O número de VICE's na caixa deve ser exatamente igual ao número de registros de voto digital retornados pela máquina virtual Ethereum 
- Cada registro digital de voto retornado pela máquina virtual Ethereum precisa ter um VICE associado na caixa que o administrador entregou ao auditor. 
- Cada VICE precisa ter um _hash_ válido. 
  
Um _hash_ impresso no VICE é considerado válido se: 
- Ele existir no blockchain Ethereum 
- O endereço do remetente for igual ao da urna que está sendo auditada 
- O endereço da carteira do candidato que recebeu o voto for o mesmo que o impresso no VICE 
- O endereço do contrato da criptomoeda for o mesmo publicado na cerimônia oficial. 

## Discussão


## Resultados
Ao transformar o voto do eleitor em uma criptomoeda, o sistema imediatamente ganha todas as propriedades de segurança do protocolo de consenso e de disponibilidade da rede _peer-to-peer_ utilizado na plataforma.

## Conclusão
EtherVoltz é uma proposta que visa decentralizar o processo eleitoral e de auditorias ao transferir a responsabilidade de gerenciar dos registros digitais de votos a um programa que executa em uma máquina virtual que não possui autoridade central, é imutável e resistente a censura.  Ao transformar o voto do eleitor em uma criptomoeda, o sistema imediatamente ganha todas as propriedades de segurança do protocolo de consenso e de disponibilidade da rede _peer-to-peer_ utilizado na plataforma.
  
Embora ainda exista a necessidade da emissão e controle dos VICE para garantir o Princípio da Independência de Software ao sistema, a separação do destino das duas provas produzidas no momento do voto dá aos eleitores poder de auditoria com limitada necessidade do envolvimento de intermediários. 

## Referências

[11] YUAN, B.; LIN, W.; MCDONNELL, C. Blockchains and electronic health records - p. 3

[12] Bitcoin Vocabulary - Disponível em: https://bitcoin.org/en/vocabulary. Acesso em: 27 ago. 2017.

[8] BRUNAZO, Amilcar  - Modelos e Gerações dos Equipamentos de Votação Eletrônica - Disponível em: http://www.brunazo.eng.br/voto-e/textos/modelosUE.htm#3o. Acesso em: 27  ago. 2017.

[1] Comitê Multidisciplinar Independente, 1º Relatório do Comitê Multidisciplinar Independente - p. 27. 

[2] Comitê Multidisciplinar Independente -  1º Relatório do Comitê Multidisciplinar Independente - p. 34. 

[3] Comitê Multidisciplinar Independente -  1º Relatório do Comitê Multidisciplinar Independente - p. 24. 

[5] Comitê Multidisciplinar Independente - 1º Relatório do Comitê Multidisciplinar Independente - p. 27. 

[6] Comitê Multidisciplinar Independente - 1º Relatório do Comitê Multidisciplinar Independente - p. 25. 

[10] ETHEREUM F. Ethereum Wiki Glossary - acesso em https://github.com/ethereum/wiki/wiki/Glossary, 27/08/2017

[14] ETHEREUM F. What is Ethereum - Disponível em: https://github.com/ethereum/wiki/wiki/What-is-Ethereum - Acesso em 
27 ago. 2017.

[4] FERNANDES, C.T. - Radiografia das Urnas Eleitorais. S. J. dos Campos: ITA, dezembro de 2006.

[9] WOOD, G. ETHEREUM:  A  SECURE  DECENTRALISED  GENERALISED  TRANSACTION  LEDGER - p. 2-6

[13] WOOD, G. ETHEREUM:  A  SECURE  DECENTRALISED  GENERALISED  TRANSACTION  LEDGER - p. 15-16

[7] RIVEST, Ronald L. On the notion of 'software independence' in voting systems. 

[15] CHOHAN, Usman W. Cryptocurrencies: A Brief Thematic Review

