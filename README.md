# Indice de estudos para Aws Cloud Practitioner 
1. [Introduction](#introduction)
2. [Conceitos Iniciais](#conceitosIniciais)
    1. [Aws Global Infrastructure](#GlobalInfra)
	2. [Cloud Economics](#CloudEconomics)
	3. [Supporting Aws Infrastrtucture](#SupAwsInfra)
	4. [Cenários](#cenarios01)
3. [Aws Core Services](#CoreServices)
	1. [Compute Services on Aws](#CompServices)
	2. [IAM](#IAM)
	3. [Content and Network Delivery Services](#ContentNetworkDeliveryServices)
	4. [File Storage Service](#FileStorageServ)
	5. [Databases & Analytics](#databases)
	6. [Cenários](#cenarios02)
4. [Other Compute Services](#OtherCompServ)
	1. [ECS](#ECS)
	2. [Fargate](#Fargate)
	3. [ECR](#ECR)
	4. [Serverless](#Serverless)

## Introduction <a name="introduction"></a>
Habilidades validadas pela certificação

```
Conhecimento da infra AWS
Conhecimento da arquitetura AWS
Proposta de valor
Principais serviços
Casos de uso
Segurança
Definição de preço
Onde encontrar documentação e suporte
Como implementar isso na prática
Aws consegue reduzir seus valores por conta do Economies of scale.
```

Domínios
```
Cloud Concepts = Proposta de valor, casos de uso e etc
Security = Segurança e conformidade 
Technology = Os serviços da AWS em sí 
Billing and Pricing = Precificação
```

Tempo de prova: 90 min.
Valor: $100
Validade: 3 anos
Qtd questões: 50
Pontos mínimos para aprovação: 700pts === 35 qts
Não existe limitação de quais certificações primeiro entregar, pode ser feito em qualquer ordem.

## Principais Conceitos <a name="conceitosIniciais"></a>
Principais conceitos de Cloud Computing e principais conceitos da nuvem da AWS como infra e acesso a nuvem da AWS

Conceito cloud:
```
	•	On demand delivery
	•	entregue através de uma plataforma via internet
	•	Precificação baseada em consumo (pay-as-you-go)
```

Vantagens:
```
	•	Mudança na modalidade de gastos (CAPEx x OPEx) - Pague pelo que consumir
	•	Economia de escala - AWS compra em grande escala, acarretando um preço menor ao usuário final
	•	Capacidade - Crescer ou diminuir pagando apenas consumo
	•	Agilidade e velocidade - Recursos disponíveis imediatamente
	•	Economia - Foco no negócio
	•	Global em minutos
```

Tipo de Cloud:
```
	•	IaaS - Infrastructure as a Service, Físico/Virtuais (Hospedagem), Maximo controle sobre o funcionamento dos serviço(manutenção e etc).
	•	Paas - DC responsável por tudo até a camada de software, Ex.: Wordpress. Gerencia apenas dos dados. 
	•	SaaS - Software as a Service, Utilização do serviço apenas (Office 365), mínimo controle.
```

Tips de instalação:
```
	•	Public Cloud - AWS, Azure (Pagamento On Demand)
	•	Hybrid Cloud - Misto de Publica e privada (DC conectando na AWS)
	•	Private Cloud - DC interno
```

Elasticity:
	- Possibilildade de adquirir/utilizar recursos de acordo com a demanda e liberálos quando não precisar mais.

Reliability - Confiança:
	- Sempre disponível com recursos para seus clientes.

Agility:
	- Reduzir o tempo para manter a infraestrutura
	- Diminuir o custo 
	- Reduzir os riscos de segurança e compliance, através do modelo de responsabilidade compartilhada.
	- Acesso a tecnologias emergentes


### Aws Global Infrastructure <a name="GlobalInfra"></a>
Funcionamento da infraestrutrura de Cloud Computing

Regions and Availability:
```
	Regions - Onde a AWS esta fisicamente. Os DCs propriamente ditos
	- Atualmente em +- 22 regiões
	- Availabilitys zones: 1+ DC por regiões da Aws, +60 zones, entregando disponibilidade com menos propensão a falhas. Uso para deployar infra.
	- Region Identifier: us-east-2a(area-subarea-NumeroAvailabilityZone)
	4 Pontos a serem considerados ao escolher:
		1 - Compliance with data governance
		2 - Proximity to customers
		3 - availableservices
		4 - features within a Region
```

Edge Locations - CDN:
```
	- CloudFront, modulos de entrega global de conteúdos
	- Route53, DNS da Aws
	- Presente em +200 locais, possibilitando que a Aws entregue o conteúdo de acordo com a localização do serviço, mesmo que este esteja configurado em uma região diferente. 

```

AWS NUNCA move/copia dados ou recursos entre regiões sem que o dono solicite isso explícitamente
	•	AZ - Os DCs em cada região  (Em SP, 3 DCs)
Alta disponibilidade, desempenho, tolerância a falhas, disaster recovery

### Understanding Cloud Economics <a name="CloudEconomics"></a>
A melhor opção para quem não possui capital inicial e quer colocar sua aplicação no ar é o Pay-as-you-Go.

Aws Cost Explorer:
```bash
- Previsão de gastos
- organizado por serviços e por tag
- pode ser acessado via interface e por API
- AWS Budgets - oferece a capacidade de definir orçamentos personalizados que alertam você quando seus custos ou uso excedem (ou estão previstos para exceder) o valor orçado. Além de ver os custos atuais de utilização.
- TCO - Total Cost of Ownership, Custo de migração para a nuvem com report para executivos. http://awstcocalculator.com
- Simple Monthly Calculator - Calculadora mensal da AWS,possibilidade de calculos mais específicos
```

Aws Resource Tags:
```
 - Detalhamento de custo por tag, name/optionalvalue
```

AWS Organizations:
```
- Gerencia de multiplas contas através de uma conta master
- Gestão de custos por conta
```

Preços na AWS: 
```
https://aws.amazon.com/pt/pricing/

Preços são cobrados por computação, armazenamento e rede

	•	Pay-as-you-go
	•	Economize ao reservar (reserved)
	•	Descontos na utilização continua - Quanto mais usa menos paga
	•	Serviços com cobranças diferentes
	•	Regiões podem ter preços diferenciados
	•	Muitos serviços free tier

Informações importantes a considerar
	•	Dados de entrada não são cobrados
	•	Dados de saída sempre são cobrados

Transfer Acceleration - Cobrado a parte

Free Tier

	•	Sempre gratuito (Lambda, DynamoDB)
	•	12 meses gratuitos (EC2, S3, RDS)
	•	testes (SageMaker)
	•	Não se aplica por serviço, mas sim, por conta
```

AWS Cost and Usage Reports
Quanto tempo o recurso ficou no ar e a quantia cobrada ao longo do tempo

Who has control of the data security in an AWS account?
AWS Account Owner (Segurança dos dados é ligada ao customer)

Decoupling
Desacoplar, melhor prática

Consolidating billing
Faz agrupamento do faturamento das contas

### Supporting Aws Infrastructure <a name="SupAwsInfra"></a>
Ferramentas de suporte da Aws:
```
	•	AWS Trusted Advisor - acesse as 7 principais verificações(Cost Optimization, Performance, Security, Fault Tolerance,Service Limits) e orientações do Trusted Advisor para provisionar seus recursos seguindo as práticas recomendadas para aumentar o desempenho e melhorar a segurança.

	•	AWS Personal Health Dashboard - Uma visão personalizada da saúde dos serviços da AWS e alertas quando seus recursos são afetados. Este plano não oferece suporte a nenhuma orientação arquitetônica.

	- Assistentes para migrações vindo da Aws: Aws Quick Starts, Aws Partner Network Consulting Partness..
```

Planos de suporte AWS
```
	•	Basic - O plano básico fornece acesso apenas ao seguinte: Atendimento ao cliente e comunidades - acesso 24 horas por dia, 7 dias por semana ao atendimento ao cliente, documentação, white papers, fóruns de suporte e Trusted Advisor. Sem custo mensal.

	•	Developer - a AWS recomenda o suporte ao desenvolvedor se você estiver testando ou desenvolvendo antecipadamente na AWS e quiser obter suporte técnico por e-mail durante o horário comercial, bem como orientação geral de arquitetura durante a construção e o teste. Você não obtém acesso ao Gerenciamento de eventos de infraestrutura com este plano. Este plano oferece suporte apenas para orientações gerais de arquitetura. Começa com $29.

	•	Business - a AWS recomenda o suporte de negócios se você tiver cargas de trabalho de produção na AWS e quiser acesso 24x7 por telefone, e-mail e chat para suporte técnico e orientação arquitetônica no contexto de seus casos de uso específicos. Você obtém acesso total às Verificações de práticas recomendadas do AWS Trusted Advisor. Você também obtém acesso ao Gerenciamento de eventos de infraestrutura por uma taxa adicional. Começa com $100.
	Em caso de falha == Open a production system down support case

	•	Enterprise - O AWS Enterprise Support oferece aos clientes serviços semelhantes aos de concierge, em que o foco principal é ajudar o cliente a alcançar seus resultados e ter sucesso na nuvem. Com o Enterprise Support, você obtém suporte técnico 24 horas por dia, 7 dias por semana, de engenheiros de alta qualidade, ferramentas e tecnologia para gerenciar automaticamente a integridade do seu ambiente, revisão consultiva e orientação com base em seus aplicativos e um Gerente Técnico de Conta (TAM) designado para coordenar o acesso ao proativo / programas preventivos e especialistas no assunto da AWS. Este plano oferece suporte à orientação arquitetônica contextual à sua aplicação.

```

### Cenários <a name="cenarios01"></a>
1 - DC interno com VMWare para administração da infra, querem utilizar Aws + sua infra?
==> Modelo de implementação Hybrid Cloud

2 - Monetizar uma nova tecnologia emergente, nova infra. Qual o benefício de usar cloud?
==> Pay as you Go.

3 - Cia de seguros, considerando mover sua infra para cloud, com maximo controle. Qual o modelo de infra mais adequado?
==> IaaS

4 - Empresa em transição para Aws, armazenamento de dados em diversas áreas. Qual o benefício da Aws cobre as necessidades?
===> Aws Regions

5 - Site com alcance global,  procurão por performance de qualidade. Qual  elemento da Aws será usado?
===>Aws Edge Location

6 - Transição de Aplicação legada que precisa de 99% de disponibilidade. Qual elemento da Aws suporta essa necessidade?
==> Aws Availability Zones, trás a segurança de possuir várias zonas por regiao.

7 - Empresa quer separar os custos de cada conta de  acordo com o departamento. Qual abordagem atenderia a essa necessidade?
==> Tag para o Depto.

8 - X quer fazer a transição de um DC físico para a Cloud e quer saber quanto irá custar/economizar. Qual a melhor ferramenta?
==>Aws TCO Calculator

8 - X quer mover seu site para a Cloud e quer saber quanto sairá a infraestrutura para isso na Aws. Onde é possível ter esse levantamento?
==> Aws Pricing Calculator

9 - X quer migrar sua aplicação para Aws, precisa de 100% de disponibilidade e de 24h/7 de suporte por ligação. Qual o plano mais economico indicado?
==> Business Support

10 - Empresa X possui diversos polos pelo Mundo, precisa de disponibilidade para ligações/texto/email se algum problema ocorrer e com limite de tempo de resposta de até 15 min. Qual o plano de suporte adequado?
==> Enterprise Support

11 - x possui uma conta pessoal, nao precisa de suporte, mas quer acessar o Trusted Advisor. Qual o plano adequado?
==> Basic Support

12 - O que não deve ser considerado quando se escolhe uma região na Aws?
==> Capacity, pois é ilimitada.

## Aws Core Services <a name="CoreServices"></a>
Modos de interação com a Aws:
```
Console: Dashboard que interage com +150 serviços da Aws
CLI - Command line para administrar via API, ótimo para tarefas automatizadas.
SDK - Java, .NET, Python, Go, C++
CloudShell - CommandLine acessível via Console
```
### IAM -  Identity and Access Management <a name=IAM></a>
Serviço Global que controla acesso a recursos na AWS

Permite criar e controlar usuários, autenticação ou limitar acesso de usuários a recursos
IAM CONTROLA QUEM PODE FAZER O QUE NA SUA CONTA AWS

4 Grandes elementos:
	•	Users - pessoa ou serviço
	•	Groups - grupo de usuários
	•	Roles (Funções) - Recursos acessando recursos. Usam policies.
	•	Policies - Managed que são criadas pela AWS e Inline que são criadas pelo cliente (quem tem acesso ao que e o que podem fazer) em JSON

Princípio do privilégio mínimo(least privilege principle): não se dá mais permissões do que o usuário precisa.

Iam Policies:
```
Estrutura JSON que define permissões de Usuario/grupo/role:
 "Version": "2012-10-17",  --> Versão da linguagem, req
 "Id": "s3-teste" --> identificador da política, opcional 
 "Statement": [-->regras da política, pode ser +1
        {
			"Sid": "1"--> organizador da politica, opcional 
            "Effect": "Allow", --> Obrigatorio, Allow / Deny
            "Principal": {
				"AWS": ["arn:aws:iam::12345678:root"] --> Conta/user/role que a política será APLICADA
			},
            "Action": [ --> Lista das aços que está sendo permitido/bloqueado
                "s3:List*",
                "s3:Get*"
            ],
            "Resource": [
                "arn:aws:s3:::testett", --> Recurso onde a policie terá EFEITO
            ],
            "Condition": { --> Condicional para quando essa policie estivar ativa, OPCIONAL
                "StringEquals": {
                    "aws:sourceVpc": []
                }
            }
        } 
``` 

Iam Roles:
```
Feito para serviços da Aws que precisam de específicas permissões
Casos comuns: EC2 Intances, Lambdas, CloudFormation
```

Iam Security Tools:
```
Credentials Report: Todos os dados IAM da conta
Access Advisor: Mostra quando os recursos disponíveis daquele user foram acessados por ele.
```

Melhores Práticas:
```
Não usar a conta root para serviços diarios
Um usuário  físico = 1 aws user
Criar um política de senhas fortes
Reforçar o uso de MFA
Crie Roles para permissões de serviços que rodam na Aws
AccessKey para accessos programados (CLI/SDK)
Faça audiorias de segurança com Credentials Report
Nunca compartilhar accesskeys
```

Modelo de Responsabilidade Compartilhada:
```
Security and Compliance são responsabilidades compartilhadas entre a AWS e o cliente.
aws: compliance validation, infraestrutura global..
User: Rotação de keys, aplicação da arquitetura recomendada..
```

### Computer Services on Aws <a name="CompServices"></a>
Compute services -> 4 principais serviços

EC2 (Máquina virtual):
```
Casos de uso: Web application hosting, batch processing(processamento de dados), servidor API, Desktop in the cloud;
Para rodar comandos: Campo User Data
Reduced operational overhead
Conceitos:
	- Intance Types não podem ser alteradas em um downtime, algumas possuem capacidades únicas.

	- Instance Store: Efemera
	Um armazenamento de instância fornece armazenamento temporário em nível de bloco para sua instância. Esse armazenamento está localizado em discos fisicamente conectados ao computador host. Essa é uma boa opção quando você precisa de armazenamento com latência muito baixa, mas não precisa que os dados persistam quando a instância é encerrada ou pode aproveitar as arquiteturas tolerantes a falhas.

	- EBS (Block Storage) - Disco de instâncias. Permite snapshots, é persistente.

	- AMI - Amazon Machine Image: Templates para EC2 com configurações e S.O. prontos para utilização, podendo ser personalizados.

	- Modalidades de precificação:
	    On demand - Pay-as-you-go, preços por hora, bom para ad-hoc
	    Reservada - 1 ou 3 anos, desconto de até 75%, pagamento à vista, ou parte à vista parte mensal, somente mensal. Podem ser 	  Standart(maior desconto), Convertible ou Schedule.
	    Spot - Leilão, cliente define um preço a pagar pela capacidade ociosa da AWS, se preço é aceito instância é provisionada, tempo de utilização limitada
	    Dedicado (Servidor fisico e dedicado)- Preço por hora, descontos chegam a 70%, mas é a opção mais cara. Softwares com licença.

	* Se quiser que a instancia esteja sempre disponível: Stardart ou Convertible Reserved;
	* Se possui serviços que não são afetados por uma possível interrupção da EC2 ==> Spot Instances
	* Se possuir serviços com compliances específicas => Dedicated Host
	* Cargas previsíveis e agendadas => Schedule Reserved Instance

Criação de instancias EC2:
	•	Qtde e tipo de CPU
	•	Qtde de memória RAM
	•	Tam e tipo de disco EBS (Encryption on Rest e Snapshots )
	- Security Group para garantir o tráfegoin/out na instancia

Modelo de Segurança Compartilhada:
	Aws: Compliance, isolação de hosts, infraestrutura
	User: Configuração de SG,aplicação de patches, Softwares que estao na instancia
```

Elastic Beanstalk (Deploy de aplicações na web - PaaS):
```
Plataforma como Serviço, processo de provisionamento, gerenciamento, deploy é automatizado.
Casos de uso: deploy de aplicações com pouco conhecimento de como fazer e com poucas personalizações necessárias.
```
Lambda (Serverless - F(function)aaS):
``` 
execução de códigos sem provisionamento de infra,
pay-as-you-go,
Programação orientada a eventos (Trigger)
```

Elasticity:
```
Refere-se à capacidade de adquirir recursos conforme você precisa e liberar quando eles não são mais necessários é denominada como elasticidade da nuvem.
```

Scalability:
```
Habiilidade de acomodar mais recursos de hardware(scale up) à uma instancia ou de adicionar nodes(scale out)
```

Agility:
```
Não está relaciolada a escalabilidade,trata-se da agilidade de possuir novos recursos e disponibilizalos 
```

Elastic Load Balancing:
```
ELB: É o serviço de balanceamento de carga, gereciado pela AWS, com multiplos Ec2 como backend.
	3 Tipos:
		•	Classic Load Balancing - Camada 4 e 7, ELB mais antigo, esta sendo desativado aos poucos. Pouco indicado.
		•	Network Load Balancing - Grandes cargas podendo atuar na camada 4 (TCP/UDP)
		•	Application Load Balancing - Funciona na camada 7 (HTTP/S) podendo distribuir baseado no conteúdo (URL por exemplo)
	
	Aws garante HA, atualizações e manutenções, entre +1 Availability zones
	Integrado com IP, Ec2 e Lambda
	faz cehck regulares das instancias
	custa menos que criar um Load Balancer próprio
	pode prover SSL terminations(HTTPS) para websites
	Backend nao escalável

Auto Scaling Groups(ASG): Capacidade de crescer o ambiente
	•	Critérios: Grupos EC2 (configs) e Critério para escalar (CPU e Tráfego In/Out)
	Vertical Scaling ==> Scale In: alocar mais recursos as instancias. limite de hardware.
	Horizontal Scaling == Scale out: adição de instancias para lidar com o tráfego da app
	Estratégias dinamicas:		
		Substitui Ec2 instáveis SEM MUDAR SEUS TIPOS
		Definição de recursos mínimos e maximos para escalação de novos recursos. 

High Availalibity:
	- Geralmente utilizado com Horizontal Scaling
	- Rodar a aplicação em +1 AZ, para caso um deste sofrer um desastre, o outro assuma a carga.
```

Application Load Balancer (ALB)

### Serviços de distribuição de conteúdos - CDN <a name="ContentNetworkDeliveryServices"></a>

AWS Route53:
```
Serviço de DNS.
Registro de domíniio, roteamento de DNS e verificação de integridade (verifica periodicamente se um recurso esta acessível, disponível e funcional)
Global service Altamente disponível
Possibilidade de configuração de failover, onde caso uma região de deploy caia, ele direciona para outra em correto funcionamento
```

VPC:
```
É a sua rede particular, isolada e privada dentro da AWS.
Suporta IPv4 e IPv6, podendo ser pública ou privada, ou somente privada para quem tiver acesso a VPC
É possível configurar: Range de IP, Subnets, Route tables, network gateways
Suporta multiplos AZ
A VPC spans all the Availability Zones in the region
Tipos:
	•	Padrão - Para cada conta AWS é criada uma rede padrão (VPC) com configs básicas pela própria AWS onde novas funcionalidades podem ser adicionadas
	•	Não Padrão - O cliente cria de acordo com a sua necessidade para cada region

Subredes (subnets):
	A VPC cobre toda uma região e a subnet é uma ou mais subredes criadas em cada AZ
		•	Route Tables - Controla o tráfego que sai das subnets
		•	Internet Gateway - Permite que a VPC tenha acesso a internet
		•	NAT Gateway - Permite que subnets tenham acesso a internet
		•	Network Acess Control List (NACL) - Controla acesso a subnets, allow/ deny ryle, atinge todos os recursos
		•	Security Groups - O firewall, allow rules, somente alguns recursos
```

AWS Transit Gateway
```
 is a service that enables customers to connect their Amazon Virtual Private Clouds (VPCs) and their on-premises networks to a single gateway.
```
Aws Direct Connect:
```
	Facilita a conexão entre um DC local diretamente para a Aws, sem exposição do tráfico.
	Mesma região
```

CloudFront:
```
É o CDN e trabalha com Edge Locations (parceiros onde não existirem Regions). 
Acelera a entrega de conteúdo
Inclui camadas de segurança(WAF, Shield for DDoS)
```

API Gateway:
```
É um serviço gerenciado que permite que desenvolvedores criem, publiquem, mantenham, monitorem e protejam APIs(Rest, WebSocket) em qualquer escala com facilidade.
Integrado com diversos serviços, provendo monitoramento e metricas
Serverless and scalable
arquitetura:
Client <-- Rest API --> API GATEWAY <--Proxy Requests--> Lambda <--CRUD--> DynamoDB
```

AWS Global Accelerator:
```
O AWS Global Accelerator é um serviço de rede que envia o tráfego do seu usuário por meio da infraestrutura de rede global do Amazon Web Service(Edge), melhorando o desempenho do usuário da Internet em até 60%.
Não confia em resolução de DNS, pois é bseado em IP para acesso.
Casos de Uso: Serviços que não usam HTTP = UDP, Voip. IP Estático. Melhores táticas de failover.
```

### File Storage Services <a name="FileStorageServ"></a>
Serviços gerais de armazenamento na Aws

Elastic Block Storage (EBS):
```
Operações podem ser feitas em apenas alguns blocos do objeto (partes)
É um drive na cloud, pode ser retirado de uma EC2 e alocado em outra. ==> Como se fosse um HD externo
Utiliza a internet para o seu tráfego, podendo ter latencia
Redundancias dentro de uma zona de disponibilidade
Possibilidade de snapshots e provisionamento
Multipos tipos  de volumes:
	SSD - Uso geral (Gp2)
	SSD Prov IOPS - Permite definir IOPS DB (io1)
	Throughput Optimized HDD - Disco magnetico alta taxa de transferência BigData (st1)
	Cold HDD - Arquivo (sc1)
snapshot in s3
```

EFS (Armazenamento de arquivos):
```
Sistema NFS de arquivos
pay-per-use
Pode ser compartilhado entre ate 100 instâncias e pode ser conectado ao DC local via direct connect
Suporta pentabytes entre multimas AZ
2 tipos de volume:
	Stardart
	Infrequent Access
Possibilidade de conf de lyfecycle
Compartilhamento de arquivos entre várias EC2 LINUX ao mesmo tempo, em várias AZ
Possui a opção para Windows Systems ==> FSx
```

Hospedando um site estático em um S3 Bucket Websites:
```
 Acesso imediato. Nome único. Ideal para conteúdo estático
	•	Acesso via Console, CLI e SDK
	•	Cada objeto até 5TB de tamanho
	•	Objetos no S3 são armazenados em Buckets. Nomes dos objetos são Object Key, versões são Version ID e endereço são Link Address
	•	Definições para objetos e buckets	
		Politica de acesso (policy)
		Versionamento - habilitada via propriedades do bucket, protege de remoção de arquivos inesperada/erronea via restore version. Possibilidade de rollback. 
		Criptografia
	•	Cross-Region Replication - Objetos de um bucket de uma região para outra. 
```

Durability == em quanto tempo voce pode perder o arquivo, +-10 mil anos em média
Availability == o quão está disponível, varia dependendo da classe e pode ficar até 53min indisponivel ao ano.

Amazon S3:
Classes de armazenamento (6 storage class):
```
1 - Standard - General Purpose: 
		classe padrão, para objetos acessados frequentemente
		pouca lentencia. 
		Ex.: Big Data

2 - Intelligent-Tiering:
		automaticamente mover dados entre classes de armazenamento de  acordo com o acesso,
		mesma performance que a Standart, mas podendo ser mais economica.

3 - Standart-Infrequent Access: 
		dados que não são acessados com frequencia
		pode requerer recuperação rápida quando necessário.
		melhor custo benefício em comparação ao Standart General
		Aguenta a integridade dos objetos por até 2 falhas
		Caso de uso: Disaster recovery, backup.

4 - One Zone IA: 
		dados não acessados frequentemente
		mas hospedado em apenas uma zona de disponibilidade.
		menor disponibilidade
		20% mais barato que S3-IA
		Caso de uso: backup secundário de BD on-premise, armazenamento de arquivos que podem ser recriados.
```

Storages para Backup:
5 - Glacier (Object Storage):
```
 Archiving. Acesso não imediato. 
 Ideal para objetos que você não usa mais, objetos arquivados, backups e arquivos retidos por quetões legais.
 Possibilidade de configuração de quando esses dados podem ser acessados, 90 dias  mínimo.
 Pode ser recuperado em horas. Valor mais acessível.
 Opções de recuperação:
	Expedited - 1/5 min
	Standard - 3/5h
	Bulk - 5/12h
```

6 - S3 Glacier Deep Archive:
```
é a classe de armazenamento de menor custo do Amazon S3
Opção para recuperação sem pressa.
oferece suporte para retenção de longo prazo e preservação digital para dados que podem ser acessados uma ou duas vezes por ano.
Opções de recuperação:
	Standard - 12h 
	Bulk - 48h
```

S3 Object Lock & Glacier Vault Lock:
```
Object Lock:
	Modelo WORM(Write Once Read Many)
	Bloqueia em uma versão do objeto por um tempo especifico, sem modificações posterioes

Glacier Vault Lock:
	Força que a policy seja mantida.
	Possibilidade de controles
	Uma vez trancada, não é possível abrir novamente a policy.
```

Ciclo de vida (Lifecycle Policie):
```
Mover/Deletar entre diferentes classes de acordo com o tempo e frequencia de acesso
```

S3 Transfer Acceleration:
```
Transf. de grandes quantidades de dados em uma distância (region) muito longa (Alocado em Edge Location (Cloudfront)) de forma mais ágil.
```

Storage Gateway (Armazenamento híbrido)
```
 Permite conectar arquivos, volumes e backups entre AWS e storage local
 Hybrid cloud strategy, onde a Cloud aumenta os recursos locais da empresa
 Tipos:
	Amazon S3 File Gateway,
	Amazon FSx File Gateway,
	Tape Gateway e Volume Gateway
The Gateway Virtual Tape Library can be used with popular backup software such as NetBackup, Backup Exec and Veeam.
```

Cross-Account Access via Bucket Policy:
```
Definifir Allow/Autorização no bucket via bucket policy, citando qual conta pode ter acesso e com quais ações
Aws disponibiliza policiy generator para guia de policies seguras
```

Settings for Block Public Access:
```
Feito para evitar Data leaks(quando um dado sensível é exposto)
Pode ser uma configuração a nivel de conta
```

S3 Access Logs:
```
Modo para efetuar analises de quem está tendo contato com aquele bucket, habilitado na propriedade do bucket.
Os logs são direcionados para outro bucket
```

S3 Replication:
```
Necessário habilitar Versionamento nos buckets de origem e destino.
Regras definidas em Gerenciamento/Management
Podem estar em contas diferentes
Cópia Assincrona
IAM necessita ter a permissão nas contas.
Tipos:
	CRR - Cross Region Replication:
		Compliance
		Pouca latencia
		Replicação entre contas
	SRR - Same Region Replication:
		Agregação de logs
		Replicação em tempo real entre contas de produção/teste
```

Modelo de Responsabilidade compartilhada:
```
Aws:
	Infraestrutura
	Configuração e análise de vulnerabilidade
	Compliance
User: 
	S3 Versioning
	S3 Bucket Policies
	S3 Replication Setup
	S3 Storage
	Logs e monitoria
	Data encryption
```

Ferramentas para coleta/migração de dados para/fora a Aws:
	Desafios que supera:
		Conexão limitada/instável
		Alto custo de transferencia caso não tenha link de internet
		Consumo de toda a banda da empresa para fazer a transferencia
	Aws Snow Family:
		equipamentos offline para migração de dados
		se leva +1 semana para transferir pela internet, use um dispositivo Snow da Aws!

Snowball
```
(Transf. de dados para a AWS)
Dispositivo físico. Suporta Petabytes.
Amazon enviam dispositivo, coleta e envia para a cloud
```

Ferramenta para migração de dados de Edge Computing
	EdgeComputing = locais como estrada, navios, minas
	Não necessariamente possui acesso a internet
	Conexões/Energia Limitadas
	Rodam em Ec2 eLambdas
	Necessitam de Aws CLI, podendo usar o software OpsHub para gerenciar o processo de migração.

Snowball Edge (Dispositivo para processamento de serviços como EC2 e Lambda):
```
 Suporta 100 TB até 10PB
 Oferece recursos de computação - EC2
 Permite utilização em locais sem acesso a cloud e posterior sincronização (Navios, fábricas, desertos)
 Tipos:
	Storage Optimized: 80 TB de HDD, compatível com S3 object, ideal para transferencias regulares
	Compute Optimized: 42 TB dde HDD, ideal para servicoes como stream
Casos de uso: Grande transferencia de dados para a nuvem, DC decomposição, disaster recovery 
```

AWS Snowcone:
```
is a small, portable, rugged, and secure edge computing and data transfer device.
It provides up to 8 TB of usable storage.
Em casos onde a empresa quer transferir até 8 TB para a Aws mas não possui os melhores recursos
Pode ser enviado para a Aws o dispositivo ou conectalo e enviar via internet usando Aws Datasync
```

Snowmobile
```
(Transf. de dados para dentro ou para fora da Aws)
Suporta 1000 PB //1 EB
Literalmente um Caminhão Container entregue pela Aws.
	Cada caminhão suporta 100PB
Aws configura, recolhe e envia para a cloud.  Altamente seguro
Casos extremos onde a tranferencia é de mais 80 PB
```

Macie
```
Amazon Macie is a fully managed data security and data privacy service that uses machine learning and pattern matching to discover and protect your sensitive data in Amazon S3.

Macie applies machine learning and pattern matching techniques to the Amazon S3 buckets you select to identify and alert you to sensitive data, such as personally identifiable information (PII).
```

Amazon Elasticsearch Service
```
is involved with operational analytics such as application monitoring, log analytics and clickstream analytics. Amazon Elasticsearch Service allows you to search, explore, filter, aggregate, and visualize your data in near real-time.
```
### Databases & Analytics <a name="databases"></a>
Estruturação dos dados que forem alocados, com maior eficiencia nas consultas.
Possui:
	BD Relacional ==> quando uma tabela é pensada para ser referenciada em outra.
					  utilização de linguagem SQL para efetuar consultas
	BD NoSQL ==> é um BD Key-value, suporta arrays e mudanças via Json
				 Com maior Flexibilidade, Escabilidade, High-Performance
				 Ex.: JSON	
	Opção Gerenciada pela Aws, onde cuidam de toda a infra.

Serviços de banco de dados
RDS - Relational Database Service:
```
PasS
100% gerenciado. Escolha de tipo de instância. Escalável vertical e horizontalmente. 
Simplifica as tarefas de administracao.
Benefícios:
	Continuos Backups Aplicação patches (PostgreSQL, Amazon Aurora, Oracle, MySQL, MariaDB, SQL Server)
	•	Alta Escalabilidade - Computação, storage e #Read Replicas (Performance - É um snapshot (cópia de leitura) que pode ser disponibilizado em outras AZs ou Regions)
	•	Alta disponibilidade - Backups Automáticos, snapshots e #Mult-AZ deployments (Disaster Recovery - Master em uma AZ e uma replica em outra AZ. Chaveamento para apontar para outra instancia de 60 a 120 segundos)
Não é possível acesso via  SSH
Aws faz o software patching
Online Transaction Processing - OLTP
Arquitetura behind:
	ELB + Ec2 Instances == RDS
	
Modos de deploy:
	Read Replicas:
		Criação de até 5 replicas que podem ficar LENDO*READ* a aplicação
		Para WRITE somente o RDS Main pode fazer
	Multi-AZ:
		Possibilita HA em caso de alguma AZ falhar
		Pilar de reability da Aws Well-Archtecture
	Multi-Region(Read Replicas):
		Possbilidade de aplicar a técnica de ReadReplicas CrossTregion
		Melhor performance de acordo com a regiao que o cliente esta
		Possibilidade de recovery em caso de desastre em uma regiao
```	
Amazon Aurora
```
OLTP -  Online Transaction Processing 
 - Compatível com MySQL e Postgre (mais rápido que os dois) e funciona com instância ou servless
						custa 20%menos
						cresce de forma automática
						não disponível em free tier, não opensource
						feito para ser a opção mais ágil em Cloud
						backup automatico
Relacional
cloud-optimized
```
DynamoDB:
```
Milhoes de requisicoes por seg, pouca latencia
replicacao em ate 3 AZ
Tipo de dado: key/value
Serverless. NoSQL. 100% gerenciado. Escalavel. (Aplicações web, mobile, IoT e Jogos)
	•	Métricas de utilização e operacionais no CloudWatch
	•	Capacidade adaptável
	•	Backup e recuperação sob demanda point-in-time
	•	TTL - Time to Live, fermite definir a vida útil do dado
	•	DAX (DynamoDB Accelerator) - Uso de cache de memória gerenciado e altamente disponível
	•	DEV - Uso local, streams (criar sequencias quando alterações acontecerem nas tabelas do Dynamo DB) e Trigger, executar código Lambda baseado em uma condição
``` 

RedShift (Colunar)
```
Baseado em PostgreSql, pay-as-you-go
100% gerenciado.Escalável. Envio de dados de 1h em 1h
OLAP - Online Analytical Processing
Data warehouse, Big data e data lake (volume alto de dados)
SQL interface para consultas
Caso de uso: used for analytics applications using SQL
```

ElastiCache
```
In-memory databases com alta permofomance e baixa latencia
Ajuda a reduzir o trafego no RDS, pois aproveita resultados ja obtidos anteriormente.
Arquitetura == EC2 Instances + Read/Write RDS + Read/write ElastiCache In-memory
```

EMR
```
Elastic MapReduce
Hadoop clusters(BigData) para analisar e processar grande quantidade de dados
Feito de varias EC2 
```

Athena
```
Serverless DB com funcoes SQL
usado para salvar consultas em S3
pay per query
Casos de uso: one-time queries, logs analytics
```

Amazon QuickSight:
```
dashboard que possibilita administracao visual dos BD
Escalavel automaticamente, integrado com todos os BD disponiveis na Aws
casos de uso = Business Analytics, Ad-hoc analysis
```

DocumentDB
```
NoSQL
Aws implementando o mesmo que o MongoDB
MongoDB: armazenar, consultar e criar data em JSON
Banco de dados de documentos com compatibilidade com o MongoDB
100% gerenciado, possibilidade de alta disponibilidade com replicacao entre 3 AZ
Até 64TB
Escala automaticamente com workloads de milhoes de requests por seg
```

Neptune
```
Graph Database
Altamente disponivel com 3 AZ, com possibilidade de ate 15 replicas
Casos de uso: biblioteca de conteudos, fraud detection, redes sociais
```

QLDB - Quantum Ledger Database
```
Ledger - Livro registro de transacoes financeiras
100% gerenciado, Serverless, replicacao entre 3 AZ
Usado para revisar todo o historico de aplicacoes no BD
Imutável: sem possibilidade de remocao e com assinatura de criptografia disponivel
Possibilidade de manipulacao com linguagem SQL
2x melhor performance que Blockchain
```

Managed Blockchain
```
Faz com que seja possível publicar aplicacoes com transicoes sem a necessidade de uma CA autenticadora
Caso de uso: se uniar a publick boclchain networds
compativel com Hyperledger e ethereum
```

AWS Glue
``` 
O AWS Glue é um serviço de extração, transformação e carregamento (ETL) totalmente gerenciado que torna mais fácil para os clientes preparar e carregar seus dados para análise.
prepare/transform data for analytics
Serveless

Glue data catalog == central repository to store stuctural and operational metadata for all data assets.
```

Amazon Simple Workflow Service (SWF) is a web service that makes it easy to coordinate work across distributed application components. SWF enables applications for a range of use cases, including media processing, web application back-ends, business process workflows, and analytics pipelines, to be designed as a coordination of tasks.

DMS
```
Database Migration Service viabiliza migrações homogêneas, como de Oracle para Oracle,
além de migrações heterogêneas entre plataformas de banco de dados diferentes, como de Oracle ou de Microsoft SQL Server para Amazon Aurora.
BD permanece disponivel durante a migração

Glue Data Catalog: catálogo dos seus BD, pode ver a estruturade cada
```
### Cenários <a name="cenarios02"></a>
1 - Roger possui uma aplicação em React que precisa que ada usuário cadastrado  seja salvo n Aws Cognito de modo personalizado. Qual o melhor método de utilização?
==> Aws SDK

2 - Elisa esta considerando a migração para a Aws, mas querem testar um BD Relacional antes de começar. Qual o melhor modo de interação?
==> Aws Console

3 - Jenn possui um startup, onde precisa automatizar alguns processos para gerar reports. Qual o método de utilização?
==>Aws CLI

4 - Syl esta em processo de mover suas aplicações para Aws, com previsão de 5 anos. Qual a melhor opção de EC2?
==> Todas do tipo Reservado

5 - Ed não possui muita experiencia com Aws, mas quer publicar sua app em PHP. Qual a melhor opção para  ele?
==> Elastic Beanstalk

6 - Cindy esta migrando para a Cloud com seus processos de ingestão de dados, onde nao há problemas caso ocorra interrompimento da instancia. qual o melhor tipo de instancia?
==> Spot instances, por conta do processo de poder parar sem causar problemas .

7 - Jane possui 2 DC locais e quer fazer a migração para a Aws,mas quer que o tráfego seja de forma privada e segura. Qual o melhor serviço para utilizar?
==> Aws Direct Connect.

8 - Tim possui um site global e quer otimizar a performance para seus usuários com um CDN(ContentDeliveryNetwork). Qual serviço o ajudará?
==> Aws Cloudfront

9 -  Ell possui uma app rodando em EC2, mas está passando problemas de downtime com demandas inesperadas. Qual a melhor forma de escalar sua EC2 e combater esse problema?
==>Horizontal Scaling usando ELB

10 - Ely tem um site estático utilizando um S3,mas possui dados de ativos que são raramente acessados. Como ela pode reduzir os custos?
==> S3 lifecycles rules, onde podem ser criadas regras para mudar o tipo de classe armanezamento de acordo com o tempo publicado, com S3 Standart IA storage class.

11- Est esta migrando para a Cloud e possui 2PB de arquivos para migrar e está procurando um modo mais ágil para isto. Qual a melhor tática?
==> Aws Snowball

12 - Emi procura um sistema de compartilhamento de arquivos entre 8 diferentes instanes Ec2 Linux, beirando 1PB. Qual a melhor ferramenta?
==> EFS

Resumo de Opções de Armazenamento:
	Block - EBS + Ec2 Instance Store
	FILE - EFS
	Object - S3 // Glacier
	Buckets e Objetos precisam de nome único e direcionamento para uma região
	S3 security: IAM policy, s3bucket policy, s3 encryption
	S3 lifecycle Rules: transição de objetos entre diferentes classes

## Other Compute Services<a name="OtherCompServ"></a>
ECs, Fargate, ECR

### ECS - Elastic Container Service <a name="ECS"></a>
Elastic Container Service
Cria containers Docker na Aws com o usuário criando EC2 instances
Integração com Application Load Balancer
Aws cuida do start/stop do container

### Fargate <a name="Fargate"></a>
Cria container Docker 100% gerenciados
Usuário não cria EC2, mais fácil
Serverless
Aws roda o container de acordo com CPU/RAM necessário

### ECR - Elastic Container Registry <a name="ECR"></a>
Registro/Arquivo privado de imagens Docker

### Serverless <a name="Serverless"></a>
É um modelo de desenvolvimento nativo em nuvem para criação e execução de aplicações sem o gerenciamento de servidores.
Apenas deploy do codigo/função
Não significa que não possui servidor, apenas não é gerenciado por nós
ex.: Lambda(pioneira), S3, DynamoD, Fargate

Lambda
```
Virtual functions
sem servidores para gerenciar == Serverless
limitados por tempo, com  curtas execuções
roda on-demand
Pricing is based on calls and durations:
	Per Calls: 1M are free, after $0.20 
	Per Duration: 400KGB-seg ofcomputetime per month is FREE
				  After that $1.00 for 600K GB-seg
	usualmente mais barata e popular	
Integrado com todos os serviços Aws
Invocado somente com evento ou quando neccessário
fácil monitoramento via CloudWatch
roda várias linguagens(Python, c#,Java, Ruby..)
Limites: 15 min de job, runtimes, temporary disk space
CRON Job: Configurando um trigger no CloudWatch  Events,a lambda irá ser acionada no período configurado
event-driven = invocada  quando necessario
```

Aws Batch
```
Lote de processamento dinamico em qualquer escala, de acordo com a demanda
sem necessidade de gerenciamento de infra
é um job que tem início e fim, oposto de contínuo
automaticamente cria Ec2 instances // Spot Instances através de um ECS
Ajuda em otimização de custos e foca menos em infraestrutura
sem tempo limte
```

Amazon Lightsail
```
Aws faz o deploy total da aplicação para um usuário iniciante com conhecimento limitado
Preço baixo e previsível
ótimo para pessoas com pouco conhecimento
Notificações e monitoramento de recursos deployados
Casos de uso: Web Applications(LAMP, Nginx..), Websites(Wordpress, Joomla..), Dev/Test environment
Hight availability but no auto-scaling, limited Aws integrations
```
AWS Well-Architected Framework
https://wa.aws.amazon.com/index.pt_BR.html

Documenta as melhores práticas para a utilização em cloud mais específicamente para os serviços da AWS. Depois de desenhar e revisar milhares de arquiteturas de clientes, a AWS identificou melhores práticas e principais estratégias para arquitetar sistemas para Cloud e criou um White Paper

5 pilares

Operacional Excellence - Executar e monitorar sistemas para entregar valor empresarial e melhorar continuamente processos e procedimentos.
	•	Principais tópicos: Gerenciamento e automação de alterações, reação a eventos e definição de padrões para gerenciar com êxito as operações diárias
	•	Principais serviços: AWS Config, Amazon CloudWatch, AWS CloudFormation

Security - Proteção de sistemas
	•	Principais tópicos: Confidencialidade e integridade de dados, identificação e gerenciamento de quem pode fazer o quê com o gerenciamento de privilégios, proteção de sistemas e estabelecimento de controles para detectar eventos de segurança
	•	Principais serviços: IAM, Cloudtrail, WAF, KMS

Reliability - Capacidade de evitar e se recuperar rapidamente das falhas para atender a demanda comercial e de clientes
	•	Principais tópicos: Elementos básicos sobre configuração, requisitos entre projetos, planejamento de recuperação e como lidamos com as mudanças
	•	Principais serviços: AWS CloudFormation, Amazon CloudWatch, S3, Glacier
	Casos de uso: Testing recovery procedures
				  Automatically recoring from failure
				  Use AWS Conﬁg to generate an inventory of AWS resources
				  Use AWS CloudTrail to record AWS API calls into an auditable log ﬁle

Perfomance Efficiency - Uso eficiente de recursos de TI e computação
	•	Principais tópicos: Seleção dos tipos e todos tamanhos certos dos recursos tomando como base os requisitos de carga de trabalho, a performance do monitoramento e a tomada de decisões funcdamentadas para manter a eficiência à medida que as necessidades comerciais evoluem
	•	Principais serviços: Autoscaling, Elasticcache, CloudWatch, CloudFront

Cost Optimization - Evitar gastos desnecessários
	•	Principais tópicos: Compreensão e controle de onde o dinheiro está sendo gasto, seleção do número certo e mais adequado dos tipos de recursos, análise dos gastos ao longo do tempo e escalabilidade para atender às necessidades de negócios sem gastar excessivamente
	•	Principais serviços: Tag Resources, AWS Cost Explorer, Autoscaling


AWS_Well-Architected_Framewor...746.1 KB

AWS Trusted Advisor
Avaliacao de Performance, custo e segurança dos recursos AWS
faz avaliacao do que esta sendo inutilizado para reducao de custos
trusted x cost explorer

Tópicos:
Cost Optimization
Performance
Security
Fault Tolerance
Service Limits

# 4. O que cai na prova
Qual é a ferramenta que pode ser utilizada para obter recomendações de performance, segurança e otimização de custos
Suporte AWS x Trusted Advisor = Analise é limitada 

Security Group
Firewall propriamente dito


AWS Integrated Services

AWS Step Functions
```
 lets you coordinate multiple AWS services into serverless workflows so you can build and update apps quickly.
  AWS Step Functions lets you build visual workflows that enable fast translation of business requirements into technical requirements.
  assincrono
```
AWS CloudTrail
Registra QUEM fez O QUE em QUAL RECURSO e QUANDO
	•	Trilhas para eventos específicos (serviço, ação, usuário e etc)
	•	Pode ser armazenado no S3 para analises futuras, auditoria e Insights com AWS Athena
	•	Pode ser integrado com Lambda, CloudWatch logs e events (se algum recurso na AWS sofre uma alteração, eu disparo um evento e a partir desse evento uma ação)

CloudWatch
Serviço de monitoração que monitora meus recursos na AWS
	•	Collect, Monitor, act and Analyse
	•	Ações - CloudWatch Events para responder a eventos como a partir de um problema de performance eu executar o Auto Scaling e adicionar mais máquinas
	Basic monitoring collects metrics every 5 minutes 
	detailed monitoring collects metrics every 1 minute
	Amazon CloudWatch is a monitoring service for AWS cloud resources and the applications you run on AWS. 
	CloudWatch performs performance monitoring and can monitor custom metrics generated by applications and the operational health of your AWS resources

CloudTrail x CloudWatch = Acesso a recursos x Monitoração dos recursos



AWS DevTools
Ferramentas de desenvolvimento

	•	Cloud9 - IDE colaborativa
	•	Code Pega o código no CodeCommit, faz o build no CodeBuild e usa o CodeDeploy para deployar a aplicação (fluxo exemplo)
	•	CodeStar - Desenvolvimento, compilação, implantação utilizando as outras ferramentas unificadas

AWS Elastic Beanstalk
PaaS. Pós fornecimento do código, o mesmo se encarrega de provisionar a infra

AWS X-Ray
Analise de comportamento e rastreamento completo de aplicações distribuídas (diversos serviços/microserviços)
	•	Traces - A coleta de cada chamada realizada pela aplicação
	•	Instrumentação - Aplicativos usados no EC2, ECS, Lambda e Beanstalk
	•	Suporte node.js, Java e .NET
	•	Detecção de latência do lado servidor e cliente

AWS Rekognition
Analise de imagens e videos utilizando Machine Learning retornando informações categorizadas e classificadas

AWS Config
```
Serviço que fornece uma visão detalhada da configuração dos recursos da AWS em sua conta da AWS. Qualquer recurso que esteja habilitado na AWS, essa configuração é registrada e pode ser gerênciada via AWS Config.
	•	Configurações presentes e passadas
	•	Avaliação de recursos com regras - Avalia se um recurso esta em conformidade com uma regra de configuração. Regras Gerenciadas são criadas e mantidas pela AWS. Regras Personalizadas são regras criadas pelo cliente.
```

# 5. O que cai na prova
Principais casos de uso do AWS Config: Administração de recursos, auditoria e compatibilidade, Gerenciar e solucionar problemas e análise e segurança

AWS SNS
Serviço de notificação da AWS. Divide-se em Publicador, tópico e assinantes (Lambda, email, SQS, SMS, HTTP/s)

AWS SQS
Serviço de filas de mensagens (mensageria). Divide-se em Produtor e consumidor
Assincrono

AWS SES
Envio e recebimento de emails em alta escala (email MKT, email transacional, notificações e recebimento) e custo efetivo


AWS CloudFormation
Descreve e modela toda a sua infraestrutura na AWS utilizando um arquivo de texto ou linguagem de programação
	•	CloudFormation design


Security

Segurança na AWS

	•	AWS IAM - Gestão de usuários e acessos - Serviço Global
	•	AWS KMS - Gestão de certificados
	•	AWS Shield - Proteção de DDoS contra exploits comuns
	•	AWS WAF - Firewall para aplicações web
	•	AWS Inspector - Analise de vulnerabilidades
	•	AWS GuardDuty - Monitoração de ameaças baseado em machine Leaning
	•	AWS Cognito - Gestão de acesso para aplicativos móveis integrado com Facebook, Google, AWS Active Directory, outros.

Produtos que estão dentro de outros produtos

	•	Security Groups - Firewall
	•	Network ACL - Controle de acesso a redes baseado em regras
	•	Route53 - Proteção a nível de DNS

Produtos que não são SEC mas que trabalham integrados

	•	CloudTrail - Coleta de logs de acesso a recursos e APIs
	•	CloudWatch - Monitora e gera alarmes de regras pré-definidas

Modelo de segurança compartilhada


Amazon Inspector
Analise automática de segurança em aplicações em instâncias EC2

AWS Shield
Serviço gerenciado de proteção de DDoS
	•	Standard - Sem custos adicionais
	•	Advanced - Adiciona proteção a outros elementos (CloudFront, route53, EC2, ELB e Elastic IP). Configura o NACL durante o ataque para evitar a parada do serviço e utilização em excesso de recursos como capacidade da rede. Protege contra custos de DDoS e neste caso a AWS devolve como créditos. Contato com o DRT (DDoS Response Team). Protege contra diversos tipos de ataques como SYN Flood, UDP Reflection atacks e etc.

AWS WAF
Firewall para aplicações web

	•	Atua junto ao CloudFront
	•	Usado para identificar como o Application Load Balance responde a requisições web
	•	Filtra requisições HTTP e HTTPs distinguindo requisições legítimas e prejudiciais
	•	Componentes do WAF - Conditions que define quais elementos (HTTP e HTTPs) o WAF deve monitorar, Rules que são um conjunto de conditions que devem ser satisfeitas e Web ACL que são ações aplicadas a uma lista de rules podendo ser allow, block ou count.

AWS Organizations
Serviço que gerencia contas da AWS

MFA
Camada a mais de autenticação

DR
Maior tempo = Backup restore. Menor tempo = Warm standby

Uma estratégia de recuperação de falhas faz sentido quando o recurso esta em uma região da AWS diferente da qual você está
https://imasters.com.br/aws/arquiteturas-de-dr-disaster-recovery-conheca-casos-praticos

Penetration testing
Nas suas instâncias com autorização da AWS

Trusted Advisor
Performance, cost optimization, security, fault tolerance and service limits

Golden image
Imagem padrão. AMIs

PCI AWS
Escolha (choose) serviços da AWS que você sabe que são compliance PCI
Garanta (ensure) que os passos necessários durante o desenvolvimento da aplicação sejam PCI Compliance

Support Concierge (balcão)
Somente Enterprise

Response critical (CRITICA) and need to have response times less than 15 minutes
Enterprise

REQUIREMENT (DEVE SER ATENDIDO) host a database server for a minimum period of one year
Partial upfront costs Reserved (instancia)

Data redundancy across regions
Read replica

Geographical location
Region

Aurora
Cresce o armazenamento de forma automática



EBS (Modelo de segurança compartilhada)
Cliente cria snapshot

Erros, dúvidas e anotações

Which of the following disaster recovery deployment mechanisms that has the highest downtime ?
https://aws.amazon.com/blogs/aws/new-whitepaper-use-aws-for-disaster-recovery/

Which of the following are services where you don’t need to manage the underlying Infrastructure? Choose 2 answers from the options given below:
https://aws.amazon.com/s3/ || https://aws.amazon.com/dynamodb/

Your company is planning to offload some of the batch processing workloads on to AWS. These jobs can be interrupted and resumed at any time. Which of the following instance types would be the most cost effective to use for this purpose ?
http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-spot-instances.html
Instâncias Spot são uma escolha econômica se você puder ser flexível sobre quando seus aplicativos são executados e se eles podem ser interrompidos

Ver mais IAM (Conceito de users, roles, groups e policies)
http://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html

Ver um pouco de shared responsibility model
https://aws.amazon.com/compliance/shared-responsibility-model/

Ver um pouco de billing and pricing

Your company is planning to host resources in the AWS Cloud. They want to use services which can be used to decouple resources hosted on the cloud. Which of the following services can help fulfil this requirement ?
https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/Welcome.html
SQS permite integrar e desacoplar sistemas e componentes de software distribuídos



Which of the following does AWS perform on its behalf for EBS volumes to make it less prone to failure?
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSVolumes.html
O volume é replicado na mesma AZ

Ver mais sobre autoscaling
https://aws.amazon.com/autoscaling/

When giving permission to users via the AWS Identity and Access Management tool which of the following principles should be applied when granting permissions ?
https://en.wikipedia.org/wiki/Principle_of_least_privilege
Deve ser capaz de acessar apenas as informações e recursos necessários para sua finalidade legítima

Which of the following terms refers to another geographic location in AWS?
https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Concepts.RegionsAndAvailabilityZones.html

Which of the following statements are FALSE when it comes to elasticity ? Choose 2 answers from the options given below:
https://aws.amazon.com/autoscaling/

When working with the AWS Cloud which of the following are headaches you don’t need to worry about ? Choose 2 answers from the options given below:
https://aws.amazon.com/application-hosting/benefits/

Your design team is planning to design an application that will be hosted on the AWS Cloud. One of their main non-functional requirements is given below: * Reduce inter-dependencies so failures do not impact other components Which of the following concepts does this requirement relate to?
http://whatis.techtarget.com/definition/decoupled-architecture
Uma arquitetura desacoplada permite que cada componente execute suas tarefas independentemente dos outros, ao mesmo tempo em que permite variações estruturais entre a origem e o destino.

Ver mais Aurora
https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Aurora.Overview.html

Ver mais CloudFront
https://aws.amazon.com/cloudfront/details/

Which of the following services helps provide a dedicate connection from on-premise infrastructure to resources hosted in the AWS Cloud without using public internet?
https://aws.amazon.com/directconnect/?p=tile
O AWS Direct Connect é um serviço de nuvem que facilita estabelecer uma conexão de rede dedicada do seu local de hospedagem para a AWS

Which of the below cannot be used to get data onto Amazon Glacier ?
https://docs.aws.amazon.com/amazonglacier/latest/dev/uploading-an-archive.html
No entanto, você não pode carregar arquivos no S3 Glacier usando o console de gerenciamento.

What is the key difference between an availability zone and an edge location?
AZ is an isolated location within an AWS region. Edge location will deliver cached  content

When working on the costing for on-demand EC2 instances. Which are the following are attributes which determine the costing of the EC2 Instance ? Choose 3 answers from the options given below:
Instance type, AMI type, Region

A company is deploying a new two-tier web application in AWS. The company wants to store their most frequently used data so that the response time for the application is improved. Which AWS service provides the solution for the company’s requirements?
Crie aplicativos com uso intenso de dados ou aumente a performance de aplicativos existentes recuperando dados de armazenamentos de dados na memória de alto throughput e baixa latência.


A company wants to utilize AWS storage. For them low storage cost is paramount and the data is rarely retrieved and data retrieval times of several hours are acceptable for them. What is the best storage option to use?
AWS Glacier


You are exploring what services AWS has off-hand. You have a large number of data sets that need to be processed. Which of the following services can help fulfil this requirement?
O Amazon EMR ajuda você a analisar e processar grandes quantidades de dados, distribuindo o trabalho computacional em um cluster de servidores virtuais em execução na nuvem AWS.

What service from AWS can help manage the costs for all resources in AWS?
Cost Explorer é uma ferramenta que permite visualizar e analisar seus custos e uso.


Which of the following is the MOST cost-effective option to purchase an EC2 Reserved Instance?
Qualquer pagamento de 3 anos é mais compensatório em instancias reserved

A big data analytics company is moving its IT infrastructure from an on-premises data center to AWS Cloud. The company has some server-bound software licenses that it wants to use on AWS. As a Cloud Practitioner, which of the following EC2 instance types would you recommend to the company?
Dedicated host e dedicated instance são diferentes

Compared to the On-demand prices, what is the highest possible discount offered for spot instances?
90% (Dedicado é 70% e reserved 75%)

Which AWS Support plan provides architectural guidance contextual to your specific use-cases?
Business

A silicon valley based healthcare startup stores anonymized patient health data on Amazon S3. The CTO further wants to ensure that any sensitive data on S3 is discovered and identified. As a Cloud Practitioner, which AWS service would you recommend addressing this use-case?
O Amazon Macie é um serviço de segurança e privacidade de dados totalmente gerenciado que usa machine learning e correspondência de padrões para descobrir e proteger seus dados confidenciais na AWS. O Amazon Macie automatiza a descoberta de dados confidenciais em escala e reduz o custo da proteção de seus dados.

Amazon Transcribe
Converte automaticamente fala em texto

Amazon Polly 
Amazon Polly é um serviço que transforma texto em fala real, permitindo que você crie aplicativos que falam e construa categorias inteiramente novas de produtos habilitados para fala.



Which of the following AWS services support reservations to optimize costs? (Select three)
Serviços com possibilidade reserved

AWS Shield Advanced provides expanded DDoS attack protection for web applications running on which of the following resources?
Route53, AWS Global Accelerator


A cyber forensics team has detected that AWS owned IP-addresses are being used to carry out malicious attacks. As this constitutes prohibited use of AWS services, which of the following is the correct solution to address this issue?
AWS Abuse Team

Which of the following AWS services support VPC Endpoint Gateway for a private connection from a VPC? (Select two)
VPC Endpoint permite que você conecte de forma privada seu VPC a serviços AWS suportados e serviços de ponto de extremidade VPC fornecidos por AWS PrivateLink. Apenas S3 e DynamoDB são compatíveis com VPC Endpoint Gateway.

A startup wants to migrate its data and applications from the on-premises data center to AWS Cloud. Which of the following options can be used by the startup to help with this migration? (Select two)
Utilize AWS Partner Network (APN) to build a custom solution for this infrastructure migration
A AWS Partner Network (APN) é o programa de parceria global para empresas de tecnologia e consultoria que utilizam Amazon Web Services para criar soluções e serviços para clientes. A startup pode trabalhar com especialistas da APN para construir uma solução personalizada para essa migração de infraestrutura.
Leverage AWS Professional Services and set up AWS Landing Zone to accelerate the
O AWS Landing Zone é uma solução que ajuda os clientes a configurar mais rapidamente um ambiente AWS seguro e com várias contas com base nas práticas recomendadas da AWS.

AWS Professional Services
A AWS Professional Services disponibiliza ofertas que ajudam você a alcançar resultados específicos na adoção da nuvem empresarial. Cada oferta proporciona um conjunto de atividades, melhores práticas e documentação que refletem a nossa experiência no suporte a centenas de clientes em sua jornada para a Nuvem AWS.

The DevOps team at an IT company is moving 500 GB of data from an EC2 instance to an S3 bucket in the same region. Which of the following scenario captures the correct charges for this data transfer?
The company would not be charged for this data transfer
De acordo com os preços da AWS, a transferência de dados entre os serviços da AWS na mesma região não é cobrada, portanto, não haveria cobrança de transferência de dados para mover 500 GB de dados de uma instância EC2 para um bucket S3 na mesma região.

Which of the following S3 storage classes takes the most time to retrieve data (also known as first byte latency)?
S3 Glacier Deep Archive é a classe de armazenamento de menor custo do Amazon S3 e oferece suporte para retenção de longo prazo e preservação digital para dados que podem ser acessados uma ou duas vezes por ano

Customer Managed CMK
Uma chave mestra do cliente (CMK) é uma representação lógica de uma chave mestra.

EBS Única instancia, mesma AZ
EFS Múltiplas instancias, múltiplas AZs
AWS Config mesma region

Agility
No mundo da computação em nuvem, "Agilidade" se refere à capacidade de desenvolver, testar e lançar aplicativos de software que impulsionam o crescimento dos negócios. Outra maneira de explicar "Agilidade" - a AWS fornece uma enorme infraestrutura em nuvem global que permite inovar rapidamente, experimentar e iterar. Em vez de esperar semanas ou meses pelo hardware, você pode implantar novos aplicativos instantaneamente. Essa habilidade é chamada de Agilidade.

Reliability
Refere-se à capacidade de um sistema de se recuperar de interrupções de infraestrutura ou serviço, adquirindo dinamicamente recursos de computação para atender à demanda e mitigar interrupções.
Scalability
A escalabilidade é a medida da capacidade de um sistema de crescer para acomodar um aumento na demanda ou diminuir para uma demanda decrescente.

AWS Artifact
O AWS Artifact é sua primeira opção de recurso para informações relacionadas à conformidade que importam para você. Ele oferece acesso sob demanda aos relatórios de segurança e conformidade da AWS e a acordos online específicos.

Quick Starts = faz o deploy para o usuario
Aws Outposts = ver o que é, conecta no onpremise e tem conexao na Aws com baixa latencia.
Puppet e Chef = AwsOpsWork
SCP = policy a nivel de conta

loose coupling = microservicos independentes
TCO == you need to document all of the costs you’re incurring today to run your IT operations. That includes facilities equipment installation and data center security costs. That way you get to compare the full cost of running your IT on-premises today, to running it in the cloud.

CloudHSM
```
Hardware Secrets Manager - Serve para o CLIENTE gerenciar suas próprias chaves KMS. Quando ele não quer que esse controle fique na mão da AWS. A AWS manda um aparelho FÍSICO pro cliente, o cliente conecta isso com a nuvem e esse aparelho gera as chaves.
```