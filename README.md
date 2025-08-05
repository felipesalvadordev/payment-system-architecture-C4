# Payment System Design using the C4 model

XP education architecture bootcamp challenge: https://www.xpeducacao.com.br/bootcamp-pass/arquitetura

Risk management system that will be used to evaluate all transactions carried out (payments by card, Pix, payments via partner systems, etc.) and, according to various criteria for each type of transaction, the system must define a risk score for the transaction.

The company uses a hybrid cloud computing environment, formed by an on-premise data center, in São Paulo, where the company's main systems run, and a cloud data center, contracted with a market cloud provider. The two data centers are interconnected by redundant low-latency links, as well as sufficient bandwidth for the company's next 5 years of growth. The cloud data center is used as redundancy for the on-premise data center. However, BI and Big Data functionalities run exclusively in the cloud. Furthermore, cloud and on-premise networks work as a single network for all services.

ESB1 available in the onpremise data center.
ESB2 available in the cloud data center with configurations replicated from ESB1.
Environment monitoring services with downtime control and SLA.
Capacity planning management services.
Payment gateway (centralizing all payment demands requested by customers).
Business services to meet different customer demands.
Services for environment administration routines, such as performing backups and data purging.
You know that the system will consist of the following components:

Web module, for internal use, with system administration functionalities. It will allow you to manage the registration of operators (company employees), configure clients, define risk policies for each payment method and issue reports and queries.
Central transaction risk score assessment service (will be consumed by the payment gateway).
Integration routines with BI and Big Data platforms.
Set of services that other teams in the company can consume to consult transaction scores, open complaints, etc. As it is a critical system (after implementation, no transaction can be approved without the computed score), the system must be run in the primary data center and, in the event of failures, its replica will need to be activated with the least possible downtime. For the first few months, a transaction volume of 15K requests/sec is expected. Information can be stored in SQL Server or MongoDB (NoSQL), both are available in both data centers, however, without automatic data replication
The web application and all services must have a stateless backend, and the frontend must follow the SPA architecture model.

# Payment Context
![alt text](https://github.com/Fsalvador91/arquitetura-pagamentos-C4/blob/main/Contexto%20Pagamentos.drawio.png?raw=true)  
# Payment Container
![alt text](https://github.com/Fsalvador91/arquitetura-pagamentos-C4/blob/main/Container%20Pagamentos.drawio.png?raw=true)  
# Gateway Component
![alt text](https://github.com/Fsalvador91/arquitetura-pagamentos-C4/blob/main/Container%20Gateway%20Pagamentos.drawio.png?raw=true)
# Admin Container
![alt text](https://github.com/Fsalvador91/arquitetura-pagamentos-C4/blob/main/Container_Administrador.drawio.png?raw=true)  

Referências:  
https://dev.to/simonbrown/diagramming-distributed-architectures-with-the-c4-model-51cm?signin=true  
https://www.youtube.com/watch?v=tx1O55Aq1CA  
https://mariocarrion.com/2020/12/30/documenting-software-architecture-c4-model.html  
https://www.eximia.co/insights/quanto-de-esforco-se-deve-dedicar-a-arquitetura-de-software-apenas-o-suficiente/
