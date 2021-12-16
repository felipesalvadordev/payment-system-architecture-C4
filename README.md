# Desenho da arquitetura do enunciado abaixo:

Sistema de gestão de riscos que será utilizado para avaliar todas as transações realizadas (pagamentos por cartão, Pix, pagamentos via sistemas de parceiros etc.) e, de acordo 
com vários critérios para cada tipo de transação, o sistema deverá definir um score de risco para a transação.  

A empresa utiliza um ambiente de computação em nuvem híbrido, formado por um data 
center onpremise, em São Paulo, onde rodam os principais sistemas da empresa e um data 
center em nuvem, contrato de um cloud provider de mercado. Os dois data centers são 
interligados por links redundantes de baixa latência, além de largura de banda suficiente 
para os próximos 5 anos de crescimento da empresa. O data center em nuvem é utilizado 
como redundância para o data center onpremise. Entretanto, as funcionalidades de BI e Big 
Data rodam exclusivamente na nuvem. Além disso, as redes da nuvem e onpremise 
funcionam como uma única rede de todos os serviços.  

1. ESB1 disponível no data center onpremise.
2. ESB2 disponível no data center da nuvem com as configurações replicadas do 
ESB1.
3. Serviços de monitoramento do ambiente com controle de downtimes e SLA.
4. Serviços de gerenciamento de capacity planning.
5. Gateway de pagamentos (centralizador de todas as demandas de pagamento 
solicitadas pelos clientes).
6. Serviços de negócio para atender às diferentes demandas de clientes.
7. Serviços para rotinas de administração do ambiente, como execução de backup e 
expurgo de dados.
Sabe que o sistema será composto pelos seguintes componentes:
1. Módulo web, de uso interno, com as funcionalidades de administração do sistema. 
Ele permitirá gerenciar o cadastro dos operadores (funcionários da empresa), 
configurar clientes, definir políticas de riscos para cada meio de pagamento e 
emissão de relatórios e consultas.
2. Serviço central de avaliação do score de riscos das transações (será consumido pelo 
gateway de pagamentos).
3. Rotinas de integração com as plataformas de BI e Big Data.
4. Conjunto de serviços que outros times da empresa poderão consumir para consultar 
score de transações, abrir reclamações etc.
Por ser um sistema crítico (após a implantação, nenhuma transação poderá ser aprovada 
sem o score computado), o sistema deverá ser executado no data center primário e, em 
caso de falhas, sua réplica precisará ser acionada com o menor downtime possível.
Espera-se, para os primeiros meses, um volume de transações de 15K requests/sec. 
As informações poderão ser armazenadas em SQL Server ou MongoDB (NoSQL), ambos 
estão disponíveis nos dois data centers, porém, sem replicação automática de dados  

A aplicação web e todos os serviços devem ter backend stateless, e o frontend deve seguir 
o modelo de arquitetura SPA.
