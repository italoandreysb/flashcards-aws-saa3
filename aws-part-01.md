# AWS Solutions Architect Associate (SAA-C03) - Flashcards

**Certificação:** AWS Solutions Architect Associate SAA-C03  
**Professor:** Andre Iacono

---

## Cloud Practitioner - Conceitos Básicos

### Quais são as vantagens da nuvem?

- Pagar conforme o uso.
- Quanto maior o cliente, mais desconto.
- Não precisa pré-dimensionar a capacidade de recursos.
- Tornar-se global em minutos.

### Quais são os modelos de implementação?

- Implantação baseada na nuvem: tudo em nuvem.
- Implantação no local - Nuvem Privada, precisa arcar com energia, resfriamento, mão de obra…
- Implantação híbrida - Utiliza os 2 tipos.

---

## Questões sobre a AWS - Boas Práticas

### O que são Workloads seguras?

Workloads seguras são conjuntos de recursos e códigos (como aplicações, servidores e bancos de dados) que operam sob um modelo de proteção contínua, garantindo a integridade dos dados e a disponibilidade do serviço.

### No processo de migração de uma aplicação para a AWS o que é a abordagem "lift and shift"?

Migrar para a nuvem sem alterações significativas.

---

## Anotações sobre a Prova SAA-C03

> **Dica de Analista para Analista:**
> Como você é da área de Infra, o PDF que mais vai te ajudar a "virar a chave" é o "Architecting for the Cloud: AWS Best Practices". Ele compara diretamente o mundo tradicional com o mundo da nuvem.

> **Aviso direto:** Não tente decorar PDFs. A prova da AWS é 70% sobre "Qual a melhor solução para este problema?" e 30% sobre conhecimento técnico puro. Os PDFs te dão a base teórica, mas o curso do Iacono e os simulados são o que vão te dar a "maldade" para passar.

---

## Sessão 1 - Iniciando na AWS

### Criando Conta

- Criar conta em: [aws.amazon.com](https://aws.amazon.com)

### Vai cobrar? O que devo considerar ao criar uma conta?

Depende. Toda vez que iniciar a conta precisa ser visto se é gratuito ou pago. Se esquecer de deletar o serviço, vem uma conta grande. Utilizar em inglês, facilita o entendimento.

> **Nota:** Antigamente a Amazon tinha 2 sistemas de login (free tier e pay-as-you-go). Atualmente ela tem um novo "Free Tier Novo", que te dá 6 meses de acesso (US$ 100,00) e se fizer algumas tarefas pode ganhar mais US$ 100.

### Tipos de Suporte

É interessante verificar com calma em caso de empresa.

- Básico: pouca atenção
- Developer
- Business
- Enterprise on ramp
- Enterprise

---

## Infraestrutura Global da AWS

- **AZ (Availability Zone):** Um ou mais datacenters fisicamente separados dentro de uma Região AWS, com energia, rede e conectividade independentes. Utilizadas para alta disponibilidade e tolerância a falhas.
- **PoP (Point of Presence):** Pontos de presença da rede global da AWS usados para cache, aceleração de tráfego, CDN e serviços de borda (edge), aproximando o conteúdo dos usuários.
- **Edge Location:** Tipo de PoP usado principalmente pelos serviços de edge da AWS, como Amazon CloudFront e Route 53, para reduzir latência e acelerar acesso ao conteúdo.
- **Outposts:** Infraestrutura gerenciada pela AWS instalada no datacenter ou ambiente do cliente, permitindo executar serviços AWS on-premises de forma integrada à nuvem.
- **Wavelength:** Infraestrutura AWS integrada às redes 5G de operadoras para aplicações que exigem latência ultrabaixa, como IoT, streaming em tempo real e jogos online.

> **Nota:** Às vezes um Edge location e um POP location estão fisicamente em outra empresa. Cada região cobra um preço diferente.

---

## Sessão 2 - S3 (Simple Storage Service)

### O que é o S3?

- S3 = Simple Storage Service;
- É possível hospedar um site no S3;
- Possui escalabilidade Automática;
- Forma de pagamento Pay-as-you-go (conforme utilização);
- Acessível por 99.99999999999% (11 noves após a vírgula);
- Extremamente confiável;
- Não tem um limite máximo de armazenamento.

## Estrutura de Buckets

### Como são divididos os tipos de bucket?

- **General Purpose Bucket** → Bucket padrão do S3 para armazenamento geral de arquivos, aplicações, backups e conteúdo web.
- **Directory Bucket** → Bucket otimizado para altíssima performance e baixa latência, ideal para workloads intensivos como IA e HPC.
- **Table Bucket** → Bucket voltado para dados tabulares e analytics, integrado a formatos como Apache Iceberg.
- **Vector Bucket** → Bucket especializado em armazenar embeddings vetoriais para IA generativa e busca semântica.

### Quais regras se aplicam ao nome do bucket?

- Precisa ser único no mundo.
- Geralmente utiliza-se o nome da empresa.

### Quais são as configurações padrão de um bucket?

- **Versionamento:** desabilitado
- **Tags:** Forma de organizar no modelo "key/value" (chave/valor)
- **Encryption:** Server-side encryption with Amazon S3 managed keys (SSE-S3)
- **Bucket Key:** Enable

## Classes de Armazenamento (Storage Classes)

### O que são as classes de armazenamento?

A escolha de uma classe de armazenamento desenvolvida para seu caso de uso permite otimizar os custos de armazenamento, o desempenho e a disponibilidade dos objetos. Todas essas classes de armazenamento oferecem alta durabilidade. Ao trocar de classes de armazenamento, também é cobrado.

### Quais as classes de armazenamento existentes?

- **Acessados com frequência:** Standard, S3 Express One Zone e Reduced Redundancy Storage.
- **Otimização automática com padrões de acesso alterados ou desconhecidos:** S3 Intelligent Tiering (5 modelos internos).
- **Acessados com pouca frequência (IA - Infrequent Access):** S3 Standard-IA, S3 One Zone-IA.
- **Acessados raramente (Rarely Access):** S3 Glacier Instant Retrieval, S3 Glacier Flexible Retrieval, S3 Glacier Deep Archive.

### Quais são as classes de armazenamento para objetos acessados com frequência?

**S3 Standard:** A classe de armazenamento padrão. Se você não especificar a classe de armazenamento ao fazer upload de um objeto, o Amazon S3 atribuirá a classe S3 Standard.

**S3 Express One Zone:** É uma classe de armazenamento de zona única e alta performance do Amazon S3 desenvolvida com o propósito específico de fornecer acesso consistente aos dados e com latência inferior a dez milissegundos para as aplicações mais sensíveis à latência. A classe S3 Express One Zone é a classe de armazenamento de objetos em nuvem de menor latência disponível atualmente, com velocidades de acesso aos dados até dez vezes mais rápidas e custos de solicitação 50% mais baixos do que a classe S3 Standard. Com a classe S3 Express One Zone, os dados são armazenados de forma redundante em vários dispositivos dentro de uma única zona de disponibilidade.

**Reduced Redundancy Storage (RRS):** A classe Reduced Redundancy Storage (RRS) foi criada para dados reproduzíveis não críticos que podem ser armazenados em níveis de redundância menores do que a classe de armazenamento S3 Standard. Atualmente a classe S3 Standard apresenta melhor custo benefício.

### Qual a classe de armazenamento para otimizar automaticamente dados com padrões de acesso alterados ou desconhecidos?

**S3 Intelligent-Tiering:** É a classe de armazenamento ideal quando você quer otimizar os custos de armazenamento dos dados com padrões de acesso desconhecidos ou variáveis. Não há taxas de recuperação para o S3 Intelligent-Tiering. Por uma pequena taxa mensal de automação e monitoramento de objetos, o S3 Intelligent-Tiering monitora os padrões de acesso e move automaticamente os objetos que não foram acessados para níveis de acesso de custo mais baixo. Projetado para oferecer 99,9% de disponibilidade e 99,999999999% de durabilidade.

- **Acesso frequente:** Objetos recém-enviados ficam inicialmente nesta camada.
- **Acesso infrequente:** Objetos sem acesso por 30 dias são movidos automaticamente para esta camada de menor custo.
- **Acesso instantâneo ao arquivamento:** Objetos sem acesso por 90 dias são movidos automaticamente para uma camada ainda mais barata, mantendo recuperação imediata.

Além destes 3, o S3 Intelligent-Tiering permite habilitar 2 níveis de acesso opcionais:

- **Archive Access:** Camada opcional para dados acessados raramente; objetos sem acesso por 90 dias podem ser arquivados com recuperação assíncrona.
- **Deep Archive Access:** Camada opcional de menor custo para retenção longa; objetos sem acesso por 180 dias podem ser movidos para arquivamento profundo com recuperação assíncrona.

### Quais são as classes de armazenamento para objetos acessados com pouca frequência (IA - Infrequent Access)?

Acesso infrequente, porém disponível em milissegundos. Seguem as diferenças entre eles:

**S3 Standard-IA:** O Amazon S3 armazena dados de objetos de maneira redundante em várias zonas de disponibilidade separadas geograficamente (de maneira semelhante à classe de armazenamento S3 Standard). Os objetos S3 Standard – IA são resistentes à perda de uma zona de disponibilidade. Essa classe de armazenamento oferece maior disponibilidade e resiliência que a classe S3 One Zone – IA.

**S3 One Zone-IA:** O Amazon S3 armazena dados de objetos em apenas uma zona de disponibilidade, e isso a torna menos cara que a classe S3 Standard-IA. No entanto, os dados não são resilientes à perda física da zona de disponibilidade resultante de desastres, como terremotos e inundações. Use se você puder recriar os dados em caso de falha da zona de disponibilidade, e para réplicas de objetos ao configurar a Replicação do S3 Entre Regiões Diferentes (CRR).

### Quais são as classes de armazenamento para objetos acessados raramente (Rarely Accessed)?

Glacier = Geleira

- **Glacier Instant Retrieval:** Arquivamento com acesso raro, mas recuperação imediata em milissegundos.
- **Glacier Flexible Retrieval:** Arquivamento de baixo custo com recuperação em minutos ou horas.
- **Glacier Deep Archive:** Arquivamento de custo mínimo para retenção longa e acesso extremamente raro.

### Server Access Logging

### O que é o AWS S3 Server Access Logging?

No Amazon Web Services, o Server Access Logging do Amazon S3 é um recurso que registra detalhes das requisições feitas a um bucket S3.

Ele gera logs contendo informações como:

- Quem acessou o bucket
- Hora da requisição
- Tipo da operação (GET, PUT, DELETE)
- Status HTTP
- IP de origem
- Latência
- Objeto acessado

Os logs são gravados em outro bucket S3 escolhido pelo administrador.

---

## Seção 8 - Permissões e Website Estático no S3

### O que é um S3 URI?

Uri: endereço específico daquele objeto, é um S3 URI. Ex: `s3://italobezerra-bucket1/file.png`

### Como liberar acesso público aos arquivos dentro de uma bucket do S3?

Para liberar o acesso público aos arquivos dentro da bucket do S3, além de desabilitar a opção padrão "Block all public access" nas propriedades da bucket, é necessário criar uma Bucket Policy (`.json`).

### É possível hospedar um site estático em uma bucket do S3?

Apesar de não muito usual, é possível hospedar um site estático em uma bucket do S3, criando um arquivo `.html`, e definindo a policy do bucket e em propriedades, habilitar e configurar a função "static website hosting".

> **Nota:** O serviço Amplify faz isso de forma melhor.

### Qual ferramenta pode ser usada para estimar custos de serviços AWS?

Calculator.aws

---

## Seção 9 - Versionamento e Replicação

### Podemos apagar uma bucket com arquivos?

Não, é uma trava de segurança da AWS. Geralmente quando se remove uma bucket, não tem como recuperar.

### No AWS S3, como funcionam os versionamentos no bucket, com markers e lifecycle?

Quando o versionamento está habilitado, cada alteração de um objeto gera uma nova versão em vez de sobrescrever a anterior. Ao deletar um arquivo sem informar o version-id, o S3 não remove os dados imediatamente; ele cria um delete marker, fazendo o objeto "sumir" da visualização normal, mas mantendo as versões antigas armazenadas. Para apagar definitivamente uma versão, é necessário deletá-la usando seu version-id. As regras de Lifecycle automatizam limpeza e retenção: Expiration cria delete markers para objetos atuais, enquanto NoncurrentVersionExpiration remove versões antigas (noncurrent) após um período definido.

### Replication Types

- **CRR - Cross-Region Replication:** Replica os dados de um bucket em uma região, para outra região, melhorando a latência no acesso.
- **SRR - Same-Region Replication:** Replica os dados de um bucket para um outro bucket na mesma região, usado para redundância.

### Como configurar a replicação?

- **bucket1:** Management/replication rules e crie a regra.
- **bucket2:** bucket/properties/bucket versioning.

> **Importante:** Para a replicação funcionar, o versionamento precisa estar habilitado nas 2 buckets, pagamento dobrado! Pode-se fazer filtro, ex: não replicar determinada extensão de arquivo. Se possível crie uma regra de IAM automática e ajuste as permissões. Os arquivos replicados serão os criados após a regra, para replicar arquivos existentes anteriores à regra, estude o Batch Replication ou reupload.

---

## Seção 10 - Encriptação e Storage Gateway

### Todos os objetos são encriptados?

Sim.

### Encryption

### Em repouso (quando o objeto está na bucket):

- **SSE-S3 (Server-side encryption with S3):** A AWS gerencia a chave.
- **SSE-KMS:** A chave é gerenciada pelo serviço da AWS (KMS), feito pelo administrador.
- **DSSE-KMS (Dual-layer Server Side Encryption)**
- **SSE-C (Cliente):** O cliente é responsável pela chave, nem a AWS tem a chave, se perder a chave já era.

> **Dica:** É sempre bom criptografar o bucket.

### Em trânsito (quando o objeto está em processo de upload ou download/read/write):

- HTTPS

### Storage Gateway

### O que é o Storage Gateway?

O Storage Gateway da Amazon Web Services é uma ponte entre seu ambiente local (on-premises) e a nuvem. Ele faz sua infraestrutura local "conversar" com serviços como o Amazon S3.

Você instala um appliance virtual (ou físico, antigamente) dentro da empresa, e ele:

- Envia dados automaticamente para a nuvem.
- Pode manter um cache local (dados mais acessados ficam rápidos).
- Pode funcionar como backup, armazenamento ou arquivamento.

**Resultado:** Acesso rápido local + escalabilidade da nuvem.

### Quais são os tipos de Storage Gateway?

- **File Gateway:** Interface de arquivos (NFS/SMB), parece um servidor de arquivos comum.
- **Volume Gateway:** Interface de disco (iSCSI), como um HD virtual.
- **Tape Backup:** Simula uma biblioteca de fitas, integra-se aos softwares antigos de backup.

### Snow Family

### Situação: Ter 15TB de dados na empresa e precisar levar para a nuvem, como proceder?

Storage GW não é o ideal, levaria muito tempo pela internet, custo e latência altos. Snow Family é ideal para o cenário.

- **Snow Cone:** Dispositivo portátil.
- **Snowball Edge:** A Amazon envia um dispositivo físico para a empresa. Cópiamos via LAN, criptografa automaticamente, despachamos o equipamento de volta e a AWS transfere para o serviço S3. Até 80TB/dispositivo.
- **Snowmobile:** (Possivelmente encerrado) Um caminhão blindado estaciona perto do seu DC. Copiam os dados via links de alta velocidade (fibra), caminhão volta pra AWS e dados são carregados na nuvem. Até 100PB/carreta física (um caminhão da AWS).

---

## Seção 11 - Lifecycle com Event Notification

### O que são Lifecycle Rules e por que são importantes?

Sem isso, a conta do S3 fica gigante, ele gerencia os arquivos mais antigos. Podemos, por exemplo, manter sempre a versão atual, e remover os versionamentos não utilizados há 90 dias. Aplica-se ao bucket, com o versionamento já habilitado anteriormente, em "Lifecycle Rules".

### Event Notification

### O que é Event Notification no S3?

Serve para recebermos algum e-mail a partir de algum gatilho, ex: alterar um arquivo `.png`, copiar um documento, deletar um documento. Podemos definir um destino para uma Lambda function script, SNS topic ou SQS queue.

### S3 Requester Pays

### O que é o S3 Requester Pays?

Função nova na AWS, pode ser aplicada na seguinte situação: Supondo que uma outra empresa queira acessar os dados da sua bucket via API, conectando-se e coletando os dados, porém são muitos dados. Em situações comuns, o dono do bucket paga pelo acesso, porém com esta função nova habilitada, quem paga é quem está requerendo os dados. Porém a bucket deixa de ser acessível anonimamente, o cliente precisará ter uma conta na AWS e receberá um aviso de que estará pagando pelo acesso.

**Local:** bucket/properties/request pays

---

## Seção 3 - EC2 (Elastic Compute Cloud)

### O que é o Amazon EC2?

O Amazon EC2 é basicamente infraestrutura como serviço (IaaS): você provisiona máquinas virtuais sob demanda.

### Conceitos Fundamentais

1. **Elasticidade:** Ajusta o recurso conforme a demanda.
2. **Escalabilidade:** Capacidade de crescer verticalmente/horizontalmente.

> **Nota:** Na plataforma da AWS, em EC2/Summary, verifique o campo "instances" e confirme que está "0 in 0 regions" se não quiser ser cobrado.

### O Amazon EC2 é compatível com quais hipervisores?

- **Xen:** Mais antigos.
- **Nitro:** Mais novos, mais rápidos.

### Tipos de Instâncias e Preços

> Sempre verificar a documentação da AWS.

### Quais são os tipos de instância EC2?

| Tipo | Descrição |
|------|-----------|
| t | Barato (burst) |
| m | Padrão (General Purpose) |
| c | CPU |
| r | Memória |
| i/d | Disco |
| g/p | GPU |
| hpc | Extremo |

> **Dica:** Sem letra → Intel/AMD (x86). Com `g` → ARM (Graviton da AWS, via AWS Nitro System).

### O que é uma AMI?

AMI (Amazon Machine Images) são como templates.

### O que é o Amazon EBS?

Amazon EBS (Elastic Block Store): Disco persistente da VM, diferente do S3, ele fica anexado à VM.

### Modelos de Preço

### Quais são os modelos de preço da AWS para instâncias?

1. **On demand/sob demanda:** Mais caras, sem contrato, sem desconto.
2. **Reserved:** Contratual, pode economizar em até 75% em reais comparado ao on demand.
3. **Saving Plan:** Economiza em até 72% em comparação ao on demand em troca de compromisso de uso. (EC2, Fargate & Lambda)
4. **Spot instance:** Tipo um leilão, é feito uma oferta e a Amazon aceita se quiser, porém a máquina pode ser terminada a qualquer momento.
5. **Dedicated Instance/instância dedicada:** Um hardware dedicado para você, muito utilizado pelas empresas de finanças, mas mais cara que a on demand.
6. **Dedicated hosts:** Servidor exclusivo, mais caro de todos.

### O que são as instâncias On Demand?

As instâncias sob demanda/on demand permitem que você pague pela capacidade de computação ou banco de dados por hora ou segundo (mínimo de 60 segundos), dependendo de quais instâncias são executadas, sem compromissos de longo prazo nem pagamentos adiantados.

### O que são Savings Plans?

Os Savings Plans são um modelo de precificação flexível que oferece preços baixos no uso do Amazon EC2, do AWS Lambda e do AWS Fargate, em troca de um compromisso com uma quantidade consistente de uso (medido em USD/hora) por um período de um ou três anos.

### O que são Instâncias Spot?

Instâncias spot são um mecanismo de definição de preço do Amazon EC2 que permite solicitar capacidade de computação sobressalente sem compromisso inicial e com desconto por hora (até 90% de desconto no preço sob demanda).

### O que são Reserved Instances?

As reservas/reserved oferecem um desconto maior, de até 75%, no pagamento pela capacidade antecipadamente.

### Criação de Instância EC2

### Security Group: como funciona?

Security group permite acessos por IP.

Se o status está como terminated, não será cobrado pela VM, nem disco, nem recursos.

---

## Security Groups

### O que são Security Groups?

Security Groups são firewalls para instância, trabalham somente com o tipo statefull.

**ENI:** Ethernet Network Interface

### Qual a diferença entre firewall stateless e stateful?

- **Firewall Stateless:** Analisa cada pacote de forma isolada, sem considerar conexões anteriores. Mais rápido e leve, consome menos memória e processamento.
- **Firewall Stateful (com estado):** Mantém uma tabela de estados de conexão, rastreando o que está acontecendo na comunicação, mais seguro e inteligente, detecta tráfego malicioso com mais precisão, reduz a necessidade de regras detalhadas, porém é mais pesado (memória e CPU).

### Posso associar um security group a várias VMs?

Sim. É possível ter um security group e associar a várias VMs.

### Posso associar mais de um security group a uma instância?

Sim. São executados de cima para baixo.

> **Exercício:** Criar 2 instâncias EC2, fazer uma pingar na outra impedindo tráfegos ICMPs de outras origens nos security groups.

---

## Serviços de Infraestrutura

### Quais as diferenças da CLI para o CloudShell?

- **AWS CLI:** Ferramenta de linha de comando que você instala e executa localmente.
- **AWS CloudShell:** Terminal já pronto dentro do console AWS, executado na nuvem.

### O que é uma AZ?

Availability Zone, ou zona de disponibilidade.

### O que é uma Local Zone?

Zonas Locais, indicadas para latência de um dígito.

### O que é a AWS Wavelength?

Permite que desenvolvedores criem aplicativos que exigem infraestrutura de computação de borda para fornecer baixa latência a dispositivos móveis e usuários finais ou aumentar a resiliência de seus aplicativos de borda existentes. O Wavelength implanta serviços padrão de computação e armazenamento da AWS na borda das redes de provedores de serviços de comunicação (CSPs).

### O que é um AWS Outposts?

Com o Outposts, a Amazon instala racks de servidores físicos no seu escritório, fábrica ou datacenter, mas eles continuam funcionando integrados com a nuvem AWS. Ideal para baixa latência, precisa manter dados localmente por regras legais, não pode depender totalmente da internet.

---

## IAM - Identity and Access Management

### O que é o AWS IAM?

Identity Access Management, é um serviço de gerenciamento de usuários, grupos e permissões. Pode ser acessível via CLI, API ou AWS CloudShell. Permite ajustes granulares de permissão.

### Quais os tipos de políticas do AWS IAM?

- **IBP (Identity Based Policy):** Gerencia acesso a identidade (Pode ser Inline policy 1 para 1, ou gerenciada pela AWS).
- **RBP (Resource Based Policy):** Aplicada ao usuário/grupo para gerenciar recursos (EC2…).

### Sobre o AWS IAM, as roles e policies são direcionadas a quem?

- **Roles:** Direcionada a serviços, ex: EC2 pode escrever no S3.
- **Policies:** Direcionadas aos usuários e grupos.

### Ao criarmos a primeira conta da AWS recebemos permissões de root. É recomendado utilizá-la no dia a dia?

Não, deve-se utilizar do AWS IAM para criar novas contas para seu próprio ambiente, mesmo que estas tenham acesso root.

### Ao criar o usuário, o que significam "Access Key" e "Password" no IAM?

- **Access Key - Programmatic Access:** Gera uma chave/key para liberar acesso via CLI, API, SDK, automação.
- **Password - AWS Management Console:** Cria usuário que possibilita acesso web via AWS Console.

### Qual a importância de habilitar o MFA no IAM?

Função opcional, mas relevante, impede que outra pessoa acesse a console da AWS mesmo tendo as credenciais de acesso do colaborador autorizado. Ao inserir as credenciais a AWS enviará um código solicitando a "senha adicional".

### O que é o AWS STS (Security Token Service)?

Permite que um recurso da AWS (ex: EC2) acesse um outro recurso (Ex: Bucket em um S3) via Access key e Security key temporárias, sem que estes dados de acesso estejam gravados nos serviços. Em outras palavras, faz o meio campo entre os serviços que se comunicam.

### Qual a vantagem de se alterar o password policy padrão no IAM?

Impedir que as pessoas criem senhas fáceis.

### Quais são as boas práticas do AWS IAM?

- Não utilizar a conta root inicial.
- Crie contas individuais, não compartilhadas, do contrário, não dará para interpretar os logs.
- Crie grupos, evite utilizar policies individuais, do contrário pode se perder nas permissões.
- Utilize o mínimo de permissão para cada usuário/recurso.
- Habilite o MFA.
- Revise as policies password (políticas de senhas).

---

## Seção 9 - Architect - Armazenamento AWS

### Posso criar 2 buckets com o mesmo nome?

Não, as buckets necessitam ter nome único, mas podemos definir flags.

---

## Seção 10 - Architect - Servidores EC2

### Qual a diferença entre acessar um S3 via EC2 com IAM User e com IAM Roles?

**1. Usando IAM User na EC2 (Não recomendado)**

Você cria um usuário no AWS IAM com Access Key ID e Secret Access Key, e coloca essas credenciais dentro da instância EC2 (arquivo `~/.aws/credentials`, variáveis de ambiente, etc.).

**Fluxo:** EC2 → usa access key fixa → acessa S3

**Problemas:**
- Credenciais ficam armazenadas na máquina.
- Pode vazar em: Git, logs, AMI, backup.
- Rotação manual.
- Expira só se você trocar.
- Mais difícil de auditar.
- Anti-pattern em ambientes modernos AWS.

```bash
# aws configure
# aws s3 ls
```

**2. Usando IAM Role na EC2 (Recomendado)**

Você cria uma IAM Role com permissões para S3 e anexa à instância EC2 via Instance Profile. A AWS entrega credenciais temporárias automaticamente para a instância através do metadata service.

**Fluxo:** EC2 → assume IAM Role → recebe credenciais temporárias → acessa S3

**Vantagens:**
- Não existe access key fixa salva.
- Rotação automática.
- Credenciais temporárias.
- Mais seguro.
- Melhor prática AWS.
- Integra nativamente com SDK/CLI.
- Fácil revogar permissões.
- Melhor auditoria no AWS CloudTrail.

```bash
# aws s3 ls
```

### Na AWS, como funciona a cobrança mínima para instâncias virtuais (VMs) Windows e Linux?

Instâncias Windows e versões Enterprise possuem cobrança mínima de 1 hora de uso, enquanto instâncias Linux são cobradas por segundo, com mínimo de 1 minuto.

### Qual a diferença entre o modelo de cobrança de VMs Linux e Windows na AWS?

VMs Linux têm cobrança granular por segundo após o primeiro minuto, tornando-se mais econômicas para usos rápidos. Já VMs Windows e Enterprise são cobradas com período mínimo de 1 hora, independentemente do tempo efetivamente utilizado.

### Quais são as diferenças entre Reserved Instances Standard e Convertible?

As Instâncias Reservadas Standard oferecem maior desconto em comparação ao modelo Convertible, sendo ideais para workloads previsíveis e estáveis, onde não há expectativa de mudança significativa no tipo de instância, sistema operacional ou região ao longo do contrato. Já as Instâncias Reservadas Convertible oferecem mais flexibilidade, permitindo trocar atributos da reserva durante sua vigência, como família da instância, sistema operacional ou tenancy. Em contrapartida, o desconto é menor quando comparado ao modelo Standard.

- **Standard RI:** Maior economia, menor flexibilidade.
- **Convertible RI:** Menor economia, maior flexibilidade para mudanças futuras.

---

## Savings Plans

### O que são AWS Savings Plans?

São modelos de desconto da AWS onde o cliente se compromete com um valor de uso por hora (USD/hora) durante 1 ou 3 anos em troca de descontos nos serviços de computação.

### Qual a diferença entre Savings Plans e Reserved Instances?

Reserved Instances reservam capacidade específica de instância. Savings Plans oferecem maior flexibilidade, permitindo trocar tipos de instâncias, regiões ou sistemas operacionais dependendo do plano contratado.

### Quais tipos de Savings Plans existem?

Existem dois principais:

- **Compute Savings Plans**
- **EC2 Instance Savings Plans**

### O que é Compute Savings Plans?

É o modelo mais flexível. Aplica desconto para EC2, Lambda e Fargate independentemente da família, região ou tipo de instância.

### O que é EC2 Instance Savings Plans?

Oferece descontos maiores, mas exige compromisso com uma família específica de instâncias em uma região determinada.

### Como podemos estimar os gastos de um EC2?

Com a calculadora da AWS.

### Quais os estados das VMs em EC2?

### Pagamos o mesmo valor para uma instância nos estados stopped e hibernated? Por quê?

Não. No estado hibernated, além do armazenamento do disco (EBS), também há custo relacionado à memória RAM, porque o conteúdo da memória é salvo no volume EBS para que a instância possa ser retomada exatamente do ponto em que parou. Já no estado stopped, a memória RAM é descartada, então não existe essa cobrança adicional; permanecem apenas os custos de armazenamento e recursos associados, como volumes EBS e IP elástico (se aplicável).

### O que é um Placement Group no Amazon EC2 e quais tipos existem?

Um Placement Group no Amazon EC2 é um recurso que define como as instâncias EC2 serão distribuídas fisicamente dentro da infraestrutura da AWS.

- **Cluster:** Instâncias próximas para baixa latência e alto desempenho. Indicado para HPC, big data, machine learning. Porém se houver falha no rack/datacenter, várias instâncias podem ser afetadas.
- **Spread:** Instâncias separadas em hardware físico para alta disponibilidade. Indicado para aplicações críticas, sistemas que exigem HA. Quantidade limitada de instâncias por AZ.
- **Partition:** Instâncias divididas em grupos isolados para tolerância a falhas. Cada instância recebe Rack, rede e energia separadamente. Evita que falhas afetem todo o cluster. Boa combinação. Indicado para Hadoop, Kassandra, Kafka e sistemas distribuídos grandes.

### Qual a diferença entre ENI, ENA e EFA na AWS?

- **ENI (Elastic Network Interface):** É uma interface de rede virtual que pode ser anexada a uma instância EC2. Ela possui endereço IP privado, IP elástico, MAC Address e grupos de segurança próprios.
- **ENA (Elastic Network Adapter):** É um adaptador de rede de alta performance que oferece maior throughput e menor latência para instâncias EC2, suportando até 100 Gbps em alguns tipos de instância.
- **EFA (Elastic Fabric Adapter):** É uma interface de rede especializada para aplicações HPC (High Performance Computing) e Machine Learning, permitindo comunicação de baixa latência entre instâncias usando MPI (Message Passing Interface).

### Em quais cenários você utilizaria ENI, ENA e EFA?

**ENI:**
- Separação de tráfego de rede.
- Failover entre instâncias.
- Uso de múltiplas interfaces de rede.

**ENA:**
- Aplicações com alto tráfego de rede.
- Workloads de baixa latência.
- Servidores que precisam de maior desempenho de rede.

**EFA:**
- Clusters HPC.
- Simulações científicas.
- Treinamento distribuído de IA/ML.
- Aplicações que usam MPI e exigem comunicação extremamente rápida entre nós.

### Como podemos adicionar uma ENI extra ao EC2?

A instância EC2 deve estar no estado running ou stopped. A ENI precisa estar na mesma AZ (Availability Zone) da instância. O tipo da instância deve suportar múltiplas ENIs. Verifique o limite de ENIs por tipo de instância.

1. Crie a interface de rede.
2. Selecione a subrede.
3. Escolha se é DHCP ou estático.
4. Escolha o security group (da própria VM).
5. Anexe a VM à interface criada.

### Como funciona o NAT com EC2?

Permite que instâncias em sub-redes privadas acessem a internet para saída (updates, downloads etc.), sem permitir acesso direto da internet às instâncias.

### Como funciona o Elastic IP (IP Elástico)?

Um Endereço IP elástico é um endereço IPv4 estático projetado para computação em nuvem dinâmica. Um endereço IP elástico é alocado para a conta da AWS e será seu até que você o libere. Com um endereço IP elástico, é possível mascarar a falha de uma instância ou software remapeando rapidamente o endereço para outra instância na conta.

> **Na prática:** Se não for utilizar o IP elástico, é necessário desassociar da VM e depois liberá-lo (release) da conta AWS.

### Qual a diferença entre VPC com subnet privada e VPC com subnet pública?

A subnet pública tem rota para internet (passando pelo Internet GW), a privada não.

### O que é e como funcionam os Bastion Hosts (Jump Hosts/Jump Box)?

São computadores EC2 que estão com VPC públicas, logo acessam a internet, que servem de acesso inicial para se tornar possível acessar outras máquinas, evitando necessidade de configurar firewalls em VMs com IPs públicos.

### Qual a diferença entre NAT GW e Internet GW?

- **Internet Gateway:** Conecta a VPC diretamente à internet. Requisitos: Estar em uma sub-rede pública, ter rota para o IGW e ter um IP público ou Elastic IP.
- **NAT Gateway:** Permite apenas conexões de saída para a internet. Permite instalar pacotes, baixar atualizações.

---

## Sessão 11 - VPC (Virtual Private Cloud)

### É verdade que VPC é similar às VLANs convencionais?

Sim.

### Qual a diferença entre criar um VPC com assistente e manualmente?

O assistente pode criar mais coisas automaticamente, inclusive o que não queremos.

### No momento da criação de um VPC, o que significam alocação padrão e dedicada?

A opção Padrão é recomendada na maioria das situações. Na opção Dedicada, as instâncias da VPC são executadas em hardware físico dedicado à sua conta.

### Tendo criado um VPC com subnets, como podemos torná-las públicas ou privadas?

Elas já se iniciam privadas. É necessário acessar as configurações da sub-rede e habilitar a opção "Habilitar endereço IPv4 público de atribuição automática".

**Caminho:** VPC/Subnets/\<seleciona\_subrede\>/Ações/Editar config sub-rede


### Como adicioanr uma instância à uma rede privada (se comunicando com outras máquinas da rede)? Como provar que a rede é privada?


### Quais os principais componentes de uma VPC e suas definições?
**Sub-redes e Endereçamento**

- CIDR Block: Define a faixa de endereços IP privados da VPC (ex: 10.0.0.0/16).

- Subnet Pública: Sub-rede com rota para a internet, usada para recursos expostos ao público (ex: Web Servers, Load Balancers).

- Subnet Privada: Sub-rede isolada da internet direta, usada para dados e aplicações internas (ex: Bancos de Dados, APIs).

**Conectividade e Roteamento**

- Route Table (Tabela de Roteamento): Regras de rede que direcionam para onde o tráfego de cada sub-rede deve ir.

- Internet Gateway (IGW): Porta de entrada e saída para conexões bidirecionais entre a VPC e a internet.

- NAT Gateway: Permite que recursos da sub-rede privada acessem a internet sem ficarem visíveis a conexões externas.

- VPC Endpoints: Conexões privadas para acessar serviços da AWS fora da VPC sem passar pela internet pública.

**Segurança e Controle de Acesso**

- Security Group: Firewall virtual associado ao recurso (nível de ENI/instância). Controla portas e é stateful (respostas ao tráfego liberado retornam automaticamente).

- Network ACL (NACL): Firewall associado à sub-rede. Funciona como uma camada extra de proteção e é stateless (exige regras explícitas de entrada e saída).