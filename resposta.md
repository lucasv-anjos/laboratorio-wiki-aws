# 📝 Resposta do Laboratório: A Wiki Perdida dos Arquivos Corporativos

> Preencha este arquivo com a sua proposta de solução.
>
> Sua resposta deve explicar como transformar os documentos brutos da pasta `raw/` em uma Wiki Corporativa Inteligente, pesquisável e segura usando apenas serviços da AWS.

---

## 👤 Identificação

**Nome:**  
Lucas anjos

**Data:**  
29/09/2026

**Link do repositório:**  
https://github.com/lucasv-anjos/laboratorio-wiki-aws

---

# ✅ Quest 1: O Mapa dos Arquivos Perdidos

## 1.1 Formatos encontrados na pasta `raw/`

Descreva quais tipos de arquivos existem dentro da pasta `raw/`.

```md
Exemplo de como responder, com o formato e o que ele implica:
- <extensao>: <nasce digital ou precisa de OCR?>, <o que da para extrair>
```

> Abra a pasta e liste o que voce encontrou de fato. Esta quest avalia a sua
> leitura do acervo, entao a resposta certa e a que corresponde aos arquivos.

**Sua resposta:**

```md
dentro da pasta raw existe um arquivo png; um arquivo pdf e um arquivo csv, tratando-se respectivamente de um arquivo salvo como imagem, um salvo como documento e outro como tabela dificultando assim a extração dos dados já que cada um possui caracteristicas diferentes dificultando assim a extração dos dados.
```

---

## 1.2 Principais desafios encontrados

Explique quais dificuldades esses documentos podem apresentar.

```md
Exemplo:
- Arquivos sem padrão de nomenclatura
- Documentos escaneados com baixa qualidade
- Textos manuscritos ou parcialmente ilegíveis
- Atas com estruturas diferentes
- Informações importantes espalhadas em vários formatos
```

**Sua resposta:**

```md
Preencha aqui.
```

---

## 1.3 Informações importantes a serem extraídas

Liste quais informações precisam ser identificadas para transformar os documentos em conhecimento pesquisável.

**Sua resposta:**

```md
Preencha aqui.
```

---

## 1.4 Estratégia de classificação inicial

Como você classificaria os documentos sem depender de subpastas dentro de `raw/`?

**Sua resposta:**

```md
Preencha aqui.
```

---

# ✅ Quest 2: O Portal de Entrada na AWS

## 2.1 Armazenamento dos arquivos brutos

Explique como os arquivos da pasta `raw/` seriam enviados e armazenados na AWS.

Serviços que você pode considerar:

- Amazon S3
- AWS IAM
- AWS KMS
- Amazon S3 Versioning
- Amazon S3 Lifecycle

**Sua resposta:**

```md
utilizando o serviço da amazon S3 é possível armazenar os dados não estruturados e mesmo após a extração e normalização dos dados o S3 ainda sim mantem os arquivos originais fazendo assim com que possa ser possível reprocessa-los novamente caso necessário. efetivamente ele será utilizado como pipeline de dados em que o usuário faz o upload do arquivo e ele é salvo dentro da AWS para que possa ser feito o fluxo de extração e normalização.
```

---

## 2.2 Preservação dos arquivos originais

Explique como garantir que os arquivos originais sejam mantidos intactos e rastreáveis.

**Sua resposta:**

```md
utilizando o serviço da amazon S3 é possível armazenar os dados não estruturados e mesmo após a extração e normalização dos dados o S3 ainda sim mantem os arquivos originais fazendo assim com que possa ser possível reprocessa-los novamente caso necessário
```

---

## 2.3 Extração de texto dos documentos

Explique como cada tipo de arquivo seria processado.

Considere:

- PDFs escaneados;
- Imagens;
- PDFs digitais;
- Arquivos `.txt`;
- Arquivos `.docx`;
- Arquivos `.md`.

Serviços que você pode considerar:

- Amazon Textract
- AWS Lambda
- AWS Step Functions
- Amazon S3
- Amazon CloudWatch

**Sua resposta:**

```md
para a extração dos dados será utilizado o AWS Lambda como orquestrador, ele identificara o tipo de arquivo e passará para a ferramenta de extração responsável sendo elas:
Amazon Textract - responsável por separar PDF digitalizados, PNG e JPEG com texto e Documentos com tabelas e formulários.
AWS Glue - Serviço de integração e ETL que pode ser utilizado para extrair, transformar e preparar grandes conjuntos de dados como CSV, JSON e Dados tabulares.
```

---

## 2.4 Tratamento de falhas

Explique como sua solução identificaria e registraria erros de processamento.

**Sua resposta:**

```md
seria utilizado o Amazon CloudWatch para Monitorar a execução das funções Lambda e registro de informações sobre o processamento junto com o AWS Step Functions para gerenciamento do fluxo de extração e tratativa de falhas
```

---

# ✅ Quest 3: A Relíquia dos Metadados

## 3.1 Padronização dos textos processados

Explique como os textos extraídos seriam limpos, normalizados e preparados para consulta.

**Sua resposta:**

```md
para a normalização dos dados seria utilizado o AWS glue novamente pois ele é capaz de padronizar dados provenientes das etapas anteriores, limpar; transformar e organizar grandes volumes de dados e converter para JSON caso necessário
```

---

## 3.2 Metadados propostos

Defina quais metadados você extrairia de cada documento.

| Metadado | Por que ele é importante? |
|---|---|
| Nome do documento | Permite identificar o documento de forma rápida e facilita sua localização e organização na Wiki. |
| Tipo do documento |Permite classificar o conteúdo, por exemplo, ata, relatório, manual, contrato, apresentação ou imagem, facilitando filtros e consultas.|
| Data identificada | Permite organizar e consultar os documentos cronologicamente, além de identificar quando determinada informação foi produzida ou registrada. |
| Tema principal | Permite categorizar o documento de acordo com seu assunto principal, facilitando a organização e a pesquisa na Wiki. |
| Participantes | Registra as pessoas, equipes ou organizações mencionadas ou envolvidas no documento, permitindo consultas relacionadas a participantes. |
| Decisões tomadas | Identifica decisões importantes presentes no documento, transformando informações dispersas em conhecimento estruturado e consultável. |
| Responsáveis | Identifica as pessoas ou equipes responsáveis pelas ações, decisões ou atividades mencionadas no documento. |
| Próximos passos | Registra ações futuras identificadas no documento, permitindo acompanhar tarefas e atividades pendentes. |
| Nível de confidencialidade | Permite classificar o grau de acesso ao conteúdo, auxiliando no controle de permissões e na proteção de informações sensíveis. |
| Caminho do arquivo original | Mantém a referência ao arquivo armazenado no Amazon S3, permitindo localizar o documento original e rastrear a origem das informações extraídas. |

Adicione outros metadados, se necessário.

---

## 3.3 Uso de IA para enriquecimento dos documentos

Explique como o Amazon Bedrock poderia ajudar a identificar temas, decisões, responsáveis, pendências e resumos dos documentos.

**Sua resposta:**

```md
O Amazon Bedrock pode ser utilizado após a etapa de extração e antes ou durante a normalização dos dados. Sua função seria analisar o texto extraído dos documentos e gerar informações estruturadas que nem sempre estão explicitamente disponíveis nos metadados originais, o Bedrock disponibiliza acesso a diferentes modelos de IA por meio de uma API, permitindo que o sistema envie o texto extraído para análise sem precisar desenvolver e hospedar um modelo de linguagem próprio
```

---

## 3.4 Armazenamento dos metadados

Explique onde os metadados seriam armazenados e como seriam conectados aos documentos originais.

Serviços que você pode considerar:

- Amazon S3
- Amazon DynamoDB
- AWS Glue Data Catalog
- Amazon Bedrock Knowledge Bases

**Sua resposta:**

```md
para armazenamento dos meta dados será utilizado o amazon DynamoDB; enquanto o amazon S3 ficará responsável pelo armazenamento dos dados normalizados o DynamoDB será utilizado para armazenamento de meta dados ja que esses não possuem uma estrutura de atributos definida e podem variar de acordo com cada documento fazendo com que um banco noSQL seja uma opção melhor
```

---

# ✅ Quest 4: O Oráculo da Wiki Inteligente

## 4.1 Estratégia de indexação

Explique como os documentos seriam divididos em trechos menores e preparados para busca semântica.

**Sua resposta:**

```md
Preencha aqui.após os dados serem normalizados eles serão encaminhados até o amazon Bedrock que fará o embedding dos dados para possa ser utilizado o Amazon OpenSearch Service para consultar os embeddings gerados pelo bedrock
```

---

## 4.2 Busca semântica e base vetorial

Explique como embeddings seriam gerados e onde seriam armazenados.

Serviços que você pode considerar:

- Amazon Bedrock Knowledge Bases
- Amazon OpenSearch Serverless
- Amazon Aurora PostgreSQL com pgvector
- Amazon S3 Vectors
- Modelos de embeddings no Amazon Bedrock

**Sua resposta:**

```md
os embeddings seriam gerados pelo amazon bedrock e ficariam salvos no amazon openSearch
```

---

## 4.3 Geração de respostas com IA

Explique como a Wiki responderia perguntas em linguagem natural com base nos documentos originais.

Considere explicar:

- Como a pergunta do usuário seria recebida;
- Como os trechos relevantes seriam recuperados;
- Como o Amazon Bedrock geraria a resposta;
- Como a resposta indicaria as fontes utilizadas.

**Sua resposta:**

```md
com a utilização do embedding gerado pelo amazon bedrock o amazon openSearch consegue tanto realizar uma busca textual procurando por palavras especificas nos documentos quanto uma busca semântica utilizando de linguagem natural  
```

---

## 4.4 Interface de consulta

Proponha como os usuários acessariam essa Wiki Inteligente.

Serviços que você pode considerar:

- Amazon Q Business
- AWS Amplify
- Amazon API Gateway
- AWS Lambda
- Amazon Cognito

**Sua resposta:**

```md
pode se utilizar do Amazon CloudFront para criação de uma interface juntamente com o Amazon API gateway para criar uma API para processar a consulta e chamar os serviços necessários, 
```

---

## 4.5 Segurança, auditoria e monitoramento

Explique como controlar acesso, proteger dados, auditar consultas e monitorar custos, erros e qualidade das respostas.

Serviços que você pode considerar:

- AWS IAM
- AWS KMS
- Amazon Cognito
- AWS CloudTrail
- Amazon CloudWatch
- Amazon Macie
- AWS Cost Explorer

**Sua resposta:**

```md
os dados ficaram salvos no amazon S3, será utilizado o Amazon CloudWatch para controle de falhas e monitoramento da qualidade, ja a parte de controle de acessos seria configurada diretamente utilizando o Amazon API Gateway
```

---

# 🧩 Arquitetura Final da Solução

Agora reúna tudo em uma visão única.

## 1. Visão geral

Explique em poucas linhas a ideia central da sua arquitetura.

**Sua resposta:**

```md
┌──────────────┐
│   Upload     │
│ dos arquivos │
└──────┬───────┘
       ▼
┌──────────────┐
│  Amazon S3   │
│ Dados brutos │
└──────┬───────┘
       ▼
┌──────────────────────┐
│      Extração        │
│ Lambda / Textract /  │
│      AWS Glue        │
└──────┬───────────────┘
       ▼
┌──────────────────────┐
│      Amazon S3       │
│   Dados extraídos    │
└──────┬───────────────┘
       ▼
┌──────────────────────┐
│    Amazon Bedrock    │
│ Enriquecimento com IA│
└──────┬───────────────┘
       ▼
┌──────────────────────┐
│      AWS Glue        │
│    Normalização      │
└──────┬───────────────┘
       ▼
┌──────────────────────┐
│      Amazon S3       │
│  Dados processados   │
└──────┬───────────────┘
       ▼
┌──────────────────────┐
│     AWS Lambda       │
│       Chunking       │
└──────┬───────────────┘
       ▼
┌──────────────────────┐
│    Amazon Bedrock    │
│     Embeddings       │
└──────┬───────────────┘
       ▼
┌──────────────────────┐
│ Amazon OpenSearch    │
│ Indexação + Busca    │
└──────┬───────────────┘
       ▲
       │
┌──────┴───────────────┐
│    Interface Wiki    │
│  + API / Backend     │
└──────────────────────┘

        ┌─────────────────┐
        │ Amazon DynamoDB │
        │    Metadados    │
        └─────────────────┘
```

---

## 2. Serviços AWS utilizados

| Serviço AWS | Papel na solução |
|---|---|
| Amazon S3 | Preencha aqui |
| Amazon Textract | Preencha aqui |
| Amazon Bedrock | Preencha aqui |
| Amazon Bedrock Knowledge Bases | Preencha aqui |
| AWS Lambda | Preencha aqui |
| AWS Step Functions | Preencha aqui |
| Amazon CloudWatch | Preencha aqui |
| AWS IAM | Preencha aqui |
| AWS KMS | Preencha aqui |

Adicione, remova ou ajuste os serviços conforme sua proposta.

---

## 3. Fluxo de dados de ponta a ponta

Descreva o caminho dos dados desde a pasta `raw/` até a Wiki Inteligente.

```md
Exemplo de estrutura:

1. Arquivos estão inicialmente na pasta raw/
2. Arquivos são enviados para o Amazon S3
3. Documentos escaneados passam pelo Amazon Textract
4. Arquivos digitais têm seus textos extraídos
5. Textos são limpos e padronizados
6. Metadados são extraídos
7. Conteúdos são indexados em uma base pesquisável
8. Usuário pesquisa na Wiki
9. IA responde com base nos documentos originais
```

**Sua resposta:**

```md
Preencha aqui.
```

---

## 4. Diagrama textual da arquitetura

Crie um diagrama simples usando texto.

```md
Exemplo:

raw/ → Amazon S3 → Lambda/Step Functions → Textract → S3 Processado → Bedrock Knowledge Bases → Interface de Consulta → Usuário Final
```

**Sua resposta:**

```md
Preencha aqui.
```

---

## 5. Riscos e limitações

Liste possíveis desafios da sua solução.

```md
Exemplo:
- Documentos ilegíveis podem prejudicar a extração de texto.
- OCR pode gerar erros em documentos com baixa qualidade.
- Custos podem aumentar conforme o volume de documentos.
- Metadados inferidos por IA podem precisar de validação humana.
- Respostas geradas por IA devem sempre referenciar documentos de origem.
```

**Sua resposta:**

```md
Preencha aqui.
```

---

## 6. Melhorias futuras

Descreva como a solução poderia evoluir.

```md
Exemplo:
- Criar uma interface web para consulta.
- Criar um chat interno para perguntas sobre atas.
- Adicionar controle de acesso por departamento.
- Criar dashboard de decisões e pendências.
- Gerar alertas automáticos sobre ações em aberto.
- Integrar com ferramentas corporativas.
```

**Sua resposta:**

```md
Preencha aqui.
```

---

# 🧠 Checklist Final

Antes de entregar, confirme se sua solução responde:

- [x] Como transformar documentos escaneados em texto?
- [x] Como lidar com diferentes formatos dentro da mesma pasta `raw/`?
- [x] Como armazenar os documentos originais?
- [x] Como preservar a rastreabilidade entre resposta e documento fonte?
- [x] Como organizar metadados?
- [x] Como criar busca semântica?
- [x] Como usar Amazon Bedrock na solução?
- [x] Como proteger documentos sensíveis?
- [x] Como monitorar falhas?
- [x] Como a empresa usaria essa Wiki no dia a dia?

---

# 🏁 Conclusão

Escreva uma breve conclusão defendendo sua solução como se estivesse apresentando para uma liderança técnica ou de negócio.

**Sua resposta:**

```md
Preencha aqui.
```
