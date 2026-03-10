# 🧠 15 Conceitos de Arquitetura que Mais Caem nas Provas AWS

Nas provas da **Amazon Web Services**, principalmente nas certificações

* AWS Certified Cloud Practitioner
* AWS Certified Solutions Architect – Associate
* AWS Certified Developer – Associate

as questões são baseadas em **arquitetura de sistemas**. Ou seja, você recebe um cenário e precisa escolher **a melhor solução técnica**.

Abaixo estão os **15 conceitos de arquitetura que mais aparecem nas provas AWS**.

---

# 1️⃣ Alta Disponibilidade (High Availability)

Capacidade do sistema continuar funcionando mesmo quando **uma parte falha**.

Na AWS isso normalmente significa:

* múltiplas **Availability Zones**
* balanceamento de carga
* redundância de serviços

Serviços comuns:

* Elastic Load Balancing
* Amazon EC2
* Amazon RDS

Exemplo de prova:

> Uma aplicação precisa continuar funcionando se um datacenter falhar.

Resposta esperada: **deploy em múltiplas AZs**.

---

# 2️⃣ Escalabilidade (Scalability)

Capacidade de aumentar recursos conforme a demanda.

Existem dois tipos:

### Vertical

Aumentar poder da máquina.

### Horizontal

Adicionar mais máquinas.

Na AWS é muito comum usar **escala horizontal**.

Serviços envolvidos:

* Amazon EC2
* Elastic Load Balancing

---

# 3️⃣ Elasticidade (Elasticity)

Capacidade de **aumentar e diminuir recursos automaticamente**.

Exemplo:

* tráfego aumenta → mais servidores
* tráfego diminui → menos servidores

Serviço muito cobrado:

* Amazon EC2 Auto Scaling

---

# 4️⃣ Fault Tolerance (Tolerância a falhas)

Sistema continua funcionando mesmo quando um componente falha.

Estratégias:

* múltiplos servidores
* replicação de banco
* balanceamento de carga

Serviços comuns:

* Elastic Load Balancing
* Amazon RDS

---

# 5️⃣ Arquitetura Desacoplada

Componentes do sistema **não dependem diretamente uns dos outros**.

Isso evita que uma falha derrube todo o sistema.

Exemplo clássico:

App → fila → worker

Serviço muito cobrado:

* Amazon SQS

---

# 6️⃣ Arquitetura Event-Driven

Sistema baseado em **eventos**.

Exemplo:

* upload no S3
* dispara Lambda
* processa arquivo

Serviços:

* AWS Lambda
* Amazon EventBridge
* Amazon S3

---

# 7️⃣ Arquitetura Serverless

Aplicações sem gerenciamento de servidores.

Benefícios:

* escala automática
* paga apenas pelo uso
* menos manutenção

Serviços principais:

* AWS Lambda
* Amazon API Gateway
* Amazon DynamoDB

---

# 8️⃣ Microservices

Sistema dividido em pequenos serviços independentes.

Benefícios:

* deploy independente
* escalabilidade isolada
* maior resiliência

Serviços usados:

* Amazon ECS
* Amazon EKS
* AWS Lambda

---

# 9️⃣ CDN e Edge Computing

Distribuir conteúdo globalmente para reduzir latência.

Serviço:

* Amazon CloudFront

Exemplo de prova:

> Usuários em vários países precisam acessar conteúdo rapidamente.

Resposta: **CDN**.

---

# 🔟 Caching

Armazenar dados em memória para acesso rápido.

Reduz carga do banco de dados.

Serviço:

* Amazon ElastiCache

---

# 1️⃣1️⃣ Segurança por Camadas (Defense in Depth)

Segurança aplicada em **várias camadas**.

Exemplos:

* autenticação
* rede privada
* criptografia
* firewall

Serviços comuns:

* AWS IAM
* AWS WAF
* Amazon VPC

---

# 1️⃣2️⃣ Least Privilege

Dar **apenas as permissões necessárias**.

Muito cobrado nas provas.

Serviço principal:

* AWS IAM

---

# 1️⃣3️⃣ Backup e Disaster Recovery

Estratégias para recuperação após falhas graves.

Exemplos:

* snapshots
* replicação
* backup automático

Serviços comuns:

* Amazon S3
* Amazon RDS

---

# 1️⃣4️⃣ Multi-Region Architecture

Aplicações distribuídas em **várias regiões da AWS**.

Objetivos:

* menor latência
* recuperação de desastre

Serviços usados:

* Amazon Route 53
* Amazon S3

---

# 1️⃣5️⃣ Otimização de Custos

Escolher arquitetura com **melhor custo-benefício**.

Na prova AWS geralmente a resposta correta envolve:

* serverless
* auto scaling
* storage adequado

Serviços comuns:

* Amazon S3
* AWS Lambda
* Amazon EC2

---

# 🎯 Dica muito importante para provas AWS

Sempre observe palavras-chave na pergunta:

| Palavra                  | Conceito     |
| ------------------------ | ------------ |
| Alta disponibilidade     | Multi-AZ     |
| Escalar automaticamente  | Auto Scaling |
| Baixa latência global    | CloudFront   |
| Desacoplamento           | SQS          |
| Processamento de eventos | Lambda       |
| Arquitetura sem servidor | Serverless   |