# Tecnologia EtherVoltz Para Eleições Auditáveis
---
## Resumo 
Este artigo apresenta o desenvolvimento de uma prova de conceito de sistema eleitoral independente de software que remove do administrador a responsabilidade de garantir a disponibilidade, integridade e confiabilidade dos registros digitais dos votos. O código é escrito na linguagem Solidity e posteriormente compilado para byte code que pode ser interpretado pela máquina virtual Ethereum. O resultado é a criação de uma criptomoeda que existe para representar cada voto, onde cada transação fica gravada num blockchain resistente a censura, ataques de negação de serviço e que está sempre disponível para auditorias.

##### Palavras-chave: eleições, auditoria, criptografia, blockchain, criptomoeda
##### Área do Conhecimento: Engenharia da Computação

## Introdução
Em sistemas eleitorais e primeira, segunda e terceira geração, os registros digitais dos votos ficam salvos na memória dos equipamentos que precisam ser levados dos locais de votação de volta para as centrais para que ocorra a apuração dos votos. Além dos custos envolvidos para garantir que estes equipamentos não sejam alterados ou destruídos durante o transporte, o administrador também precisa guardar estes registros após a apuração de votos para posteriores auditorias.

Após o período eleitoral, caso um cidadão queira auditar os resultados das eleições ele precisa interagir com o administrador do processo eleitoral para ter acesso os registros digitais, aos equipamentos e aos registros independentes de software (caso o administrador tenha optado por sistemas que utilizem VICE). Cabe ao administrador decidir se ele tem ou não permissão para realizar a auditoria e quais são condições para a realização da mesma.

Os problemas deste tipo de centralização de poderes ficam evidentes no Brasil. Embora não seja objetivo deste documento discutir os efeitos da centralização de poderes em sistemas eleitorais, quatro casos bem documentados são brevemente listados a seguir: 
  
1. **O Caso Marília, SP - 2004**: Em auditoria, os Arquivos de Espelhos de Boletins de Urna da 400º Zona Eleitoral indicavam que muitas seções eleitorais tiveram seus resultados recebidos para apuração **antes do início da votação**. Dois processos judiciais foram iniciados decorrentes destas constatações, ambos encerraram em 2009 sem julgamento final. [1] 
  
2. **O Caso Itajaí, SC - 2008**: Foi constatada burla intencional na cerimônia de carga e lacração das urnas em que nenhuma urna preparada para a votação passou pelo teste obrigatório prescrito pelo Art. 32 da Res. TSE 22.712/08. Um caso foi o da 97ª Zona Eleitoral onde a urna da seção 236 que foi sorteada para o teste obrigatório **foi substituída por outra** na hora do teste, preparada exclusivamente para este fim. A urna que foi utilizada para o teste foi posteriormente colocada à parte e recarregada, procedimento que destruiu eventuais provas nela gravadas. [2] 
  
3. **O Caso Diadema, SP - 2000**: Foram negados a todos os partidos que solicitaram o acesso aos registros digitais dos votos realizados nas urnas eletrônicas. Somente 9 meses após a eleição os partidos obtiveram acesso, não aos registros dos votos, mas aos Arquivos de LOG das urnas que apontaram que **todas** as urnas haviam sido carregadas **fora** da cerimônia oficial de carga e lacramento das urnas. [3] 
  
4. **O Caso Alagoas - 2006**: Diversas irregularidades nos arquivos gerados pelas urnas foram detectadas por auditores externos [4]. Frente as evidências, o administrador negou acesso aos arquivos solicitados pelos auditores e transferiu ao requerente uma cobrança antecipada no valor de R$ 2 milhões para que fosse desenvolvida uma perícia das urnas. Diante do não pagamento do valor proibitivo, o requerente foi multado e condenado por litigância de má-fé.  
Mesmo tendo apresentado provas de inconsistência no funcionamento das urnas, a perícia das mesmas não foi permitida. [5]

Este projeto faz do _blockchain_, da máquina virtual _Ethereum_ e da infraestrutura já em funcionamento formada pelos milháres de nós ao redor do mundo para transformar cada voto em uma criptomoeda que existe somente para este fim. Assim o sistema herda todas as características de segurança da plataforma como redundância, resistência contra ataques de negação de serviço, transparência e autenticação com criptografia por chaves assimétricas.

## Fundamentação Teórica

## Metodologia

## Discussão

## Resultados

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

