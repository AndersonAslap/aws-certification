# 📚 Criando e Testando uma Função com AWS Lambda

---

## 🧠 Introdução

O **AWS Lambda** é um serviço de computação **serverless** da Amazon Web Services que permite executar código **sem precisar gerenciar servidores**.

Em vez de configurar máquinas, instalar sistemas operacionais ou gerenciar escalabilidade, o desenvolvedor simplesmente:

1. Escreve o código
2. Define **quando a função deve executar**
3. Deixa a AWS cuidar da infraestrutura

Isso torna o desenvolvimento **mais rápido, escalável e econômico**, pois você paga apenas pelo tempo em que o código realmente executa.

Neste material você aprenderá:

* O que é o **AWS Lambda**
* Como criar uma função diretamente no **console da AWS**
* Como **testar uma função**
* Como **monitorar sua execução**
* Como enviar **parâmetros para uma função**
* Como interpretar o **resultado da execução**

---

## 📖 Conceitos Fundamentais

Antes de criar uma função Lambda, é importante entender alguns conceitos essenciais.

### 🔹 AWS Lambda

O **AWS Lambda** é um serviço de execução de código orientado a eventos que permite rodar funções sob demanda.

Características principais:

* **Serverless**: não há servidores para gerenciar
* **Escalabilidade automática**
* **Cobrança baseada em uso**
* **Execução baseada em eventos**

---

### 🔹 Função (Lambda Function)

Uma **função Lambda** é um pequeno bloco de código que executa uma tarefa específica.

Exemplos:

* Processar uma requisição HTTP
* Processar arquivos enviados para um bucket
* Executar tarefas assíncronas
* Integrar serviços AWS

---

### 🔹 Evento (Event)

Um **evento** é o dado que dispara a execução da função.

Exemplo de evento em JSON:

```json
{
  "name": "Anderson"
}
```

A função recebe esse evento e executa sua lógica com base nesses dados.

---

### 🔹 Execution Role (IAM Role)

Uma função Lambda precisa de permissões para acessar outros serviços AWS.

Essas permissões são controladas por uma **Role do IAM**.

Exemplo:

* Escrever logs no **CloudWatch**
* Ler dados do **S3**
* Escrever em **DynamoDB**

---

### 🔹 CloudWatch

O **Amazon CloudWatch** é o serviço de monitoramento da AWS.

Ele registra:

* Logs
* Erros
* Tempo de execução
* Uso de memória
* Métricas de desempenho

---

## 🔎 Explicação Detalhada

### 1️⃣ Acessando o AWS Lambda

No **console da AWS**, procure por:

```
Lambda
```

Isso abrirá o **Dashboard do AWS Lambda**, onde você pode visualizar:

* Funções existentes
* Aplicações
* Recursos adicionais

---

### 2️⃣ Criando uma nova função

Clique em:

```
Create Function
```

Você verá três opções:

| Opção               | Descrição                    |
| ------------------- | ---------------------------- |
| Author from scratch | Criar função do zero         |
| Use a blueprint     | Usar modelo pré-configurado  |
| Container image     | Executar função em container |

Neste exemplo utilizamos:

```
Author from scratch
```

---

### 3️⃣ Configurações da função

Durante a criação da função você define:

#### Nome da função

Exemplo:

```
my_Name_Function
```

---

#### Runtime (Linguagem)

Exemplo utilizado na aula:

```
Python 3.13
```

O Lambda também suporta:

* Node.js
* Java
* Go
* .NET
* Ruby

---

#### Arquitetura

Opções disponíveis:

* **x86_64**
* **ARM64**

Na aula foi utilizado:

```
x86_64
```

---

### 4️⃣ Permissões

Por padrão, o Lambda cria automaticamente uma **execution role** com permissões básicas.

Essa role permite:

* Enviar logs para o **CloudWatch**

Também é possível:

* Criar uma nova role
* Usar uma role existente

---

### 5️⃣ Configurações adicionais

O Lambda permite várias configurações extras.

Algumas importantes:

| Configuração | Função                              |
| ------------ | ----------------------------------- |
| Code Signing | Verificação de assinatura do código |
| Encryption   | Criptografia                        |
| Function URL | Criar endpoint HTTP                 |
| Tags         | Organização de recursos             |
| VPC          | Acesso a recursos privados          |

---

### 6️⃣ Estrutura da tela da função

Depois de criada, a função possui várias abas:

| Aba           | Função                   |
| ------------- | ------------------------ |
| Code          | Código da função         |
| Test          | Criar eventos de teste   |
| Monitor       | Métricas do CloudWatch   |
| Configuration | Configurações gerais     |
| Aliases       | Apontadores para versões |
| Versions      | Versionamento da função  |

---

### 7️⃣ Entendendo Versionamento e Aliases

O Lambda permite criar **versões da função**.

Exemplo:

```
v1
v2
v3
```

Um **Alias** funciona como um **apelido que aponta para uma versão específica**.

Exemplo:

```
prod → versão 3
dev → versão 2
```

Isso facilita **deploys controlados**.

---

### 8️⃣ Criando um evento de teste

Na aba **Test**, podemos criar um evento JSON.

Exemplo:

```json
{
  "name": "Broadus"
}
```

Esse objeto será enviado como **input da função**.

---

### 9️⃣ Executando o teste

Clique em:

```
Test
```

A função será executada imediatamente.

Exemplo de resposta:

```json
{
  "statusCode": 200,
  "body": "Hello, Broadus"
}
```

---

### 🔟 Métricas de execução

Após executar a função, o Lambda mostra informações importantes:

| Métrica         | Descrição              |
| --------------- | ---------------------- |
| Init Duration   | Tempo de inicialização |
| Execution Time  | Tempo de execução      |
| Billed Duration | Tempo cobrado          |
| Max Memory Used | Memória utilizada      |

---

### 💰 Modelo de cobrança

No **AWS Lambda** você paga apenas pelo tempo de execução.

Exemplo:

```
Billed Duration: 3 ms
```

Isso significa que você pagou apenas por **3 milissegundos de execução**.

---

## 💡 Exemplos práticos

### Exemplo de função Lambda em TypeScript (Node.js)

```ts
interface LambdaEvent {
  name?: string;
}

interface LambdaResponse {
  statusCode: number;
  body: string;
}

export const handler = async (event: LambdaEvent): Promise<LambdaResponse> => {

  const name = event.name ?? "World";

  return {
    statusCode: 200,
    body: `Hello, ${name}`
  };
};
```

---

### Exemplo de evento de entrada

```json
{
  "name": "Anderson"
}
```

---

### Resultado esperado

```json
{
  "statusCode": 200,
  "body": "Hello, Anderson"
}
```

---

### Exemplo sem nome informado

Entrada:

```json
{}
```

Saída:

```
Hello, World
```

---

## ⚠️ Pontos importantes

Alguns pontos importantes ao trabalhar com Lambda:

**1️⃣ Funções devem ser pequenas**

Lambda funciona melhor com **funções pequenas e específicas**.

---

**2️⃣ Execução stateless**

Cada execução da função é **independente**.

Não confie em variáveis em memória entre execuções.

---

**3️⃣ Logs são essenciais**

Sempre use logs para debug.

Exemplo:

```ts
console.log("Evento recebido:", event);
```

Os logs podem ser visualizados no **CloudWatch**.

---

**4️⃣ Timeout**

Funções Lambda possuem limite de tempo de execução.

Valor padrão:

```
3 segundos
```

Pode ser configurado até:

```
15 minutos
```

---

**5️⃣ Limite de memória**

Você pode configurar entre:

```
128 MB até 10 GB
```

---

## 📝 Resumo do conteúdo

Neste material aprendemos:

* O que é **AWS Lambda**
* Como criar uma função pelo **console da AWS**
* Como definir runtime e permissões
* Como enviar eventos para uma função
* Como testar uma função
* Como analisar métricas de execução
* Como funciona o **modelo de cobrança serverless**

O Lambda permite **executar código sob demanda**, sem gerenciar servidores.

---

## 🎯 Perguntas para revisão

1️⃣ O que significa **serverless** no contexto do AWS Lambda?

2️⃣ Qual é a função do **CloudWatch** no Lambda?

3️⃣ O que é um **evento** em uma função Lambda?

4️⃣ Para que servem **Aliases** em funções Lambda?

5️⃣ Como funciona o modelo de cobrança do AWS Lambda?

---

## 📌 Conclusão

O **AWS Lambda** é uma das tecnologias mais importantes da arquitetura **serverless** na AWS.

Com ele, desenvolvedores podem:

* Criar aplicações altamente escaláveis
* Reduzir custos operacionais
* Focar apenas na lógica de negócio

Ao aprender a criar, testar e monitorar funções Lambda, você dá um passo importante para construir **arquiteturas modernas baseadas em eventos na AWS**.

Esse conhecimento é essencial para quem deseja trabalhar com:

* **Microservices**
* **Arquiteturas serverless**
* **Integrações entre serviços AWS**
* **Automação em nuvem**.

---
