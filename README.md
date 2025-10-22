# gerenciamento-de-instancias-EC2-na-AWS

Este projeto foi desenvolvido como parte do desafio proposto pela DIO, cujo foco está no gerenciamento de instâncias EC2 dentro da infraestrutura de nuvem da Amazon Web Services. 


## Conceitos Teóricos

**Amazon EC2 (Elastic Compute Cloud)**

O Amazon EC2 é o serviço de computação em nuvem sob demanda da AWS. Ele permite criar e gerenciar instâncias virtuais (VMs) para executar aplicações, hospedar sistemas ou processar dados.

### Principais Conceitos

- Instância EC2: é uma máquina virtual configurável, onde você escolhe sistema operacional, memória, CPU, armazenamento e rede.
- Imagens (AMIs – Amazon Machine Images): são modelos prontos de sistemas operacionais (como Linux ou Windows) usados para criar novas instâncias.
- Tipos de instâncias: otimizados para diferentes finalidades — computação, memória, armazenamento ou GPU.
- Elasticidade: permite aumentar ou reduzir a capacidade de processamento de forma automática ou manual, conforme a demanda.

### Armazenamento em EC2

- Amazon EBS (Elastic Block Store): funciona como um disco rígido virtual anexado à instância EC2.

    -Pode ser desconectado e reconectado a outra instância.

    - Garante persistência dos dados mesmo após o desligamento da instância.

    - Suporta snapshots (cópias de segurança).

- Instance Store: armazenamento temporário, usado apenas enquanto a instância está ativa (os dados são perdidos quando ela é desligada).

### Gerenciamento e Segurança

- Security Groups: atuam como firewall virtual, controlando o tráfego de entrada e saída da instância.
- Chaves SSH ou senhas: utilizadas para acessar instâncias com segurança.
- Auto Scaling: ajusta automaticamente o número de instâncias conforme a carga.
- Elastic Load Balancer (ELB): distribui o tráfego entre múltiplas instâncias para garantir alta disponibilidade.

### Casos de Uso

- Hospedagem de sites e APIs.
- Execução de aplicações empresariais.
- Ambientes de teste e desenvolvimento.
- Processamento de dados em larga escala (big data e machine learning).

## Amazon S3 (Simple Storage Service)

O Amazon S3 é um serviço de armazenamento de objetos que permite guardar praticamente qualquer tipo de dado de forma escalável, segura e acessível pela internet.

### Como Funciona

- Os dados são armazenados em "buckets" (baldes), que funcionam como contêineres de objetos.
- Cada objeto é composto por:
    - Um arquivo (dado).
    - Metadados (informações sobre o arquivo).
    - Uma chave única (nome).
- O acesso é feito via interface web, linha de comando (AWS CLI) ou API REST.

### Classes de Armazenamento

Cada classe tem um custo e um desempenho diferentes, adequando-se ao tipo de dado:

- S3 Standard → alta durabilidade e disponibilidade; ideal para dados acessados com frequência.
- S3 Standard-IA (Infrequent Access) → menor custo para dados acessados ocasionalmente.
- S3 One Zone-IA → mais barato, mas armazenado em uma única zona de disponibilidade.
- S3 Glacier → armazenamento de baixo custo para arquivamento e backup de longo prazo.
- S3 Glacier Deep Archive → ainda mais econômico, usado para dados raramente acessados.

### Gerenciamento e Otimização

- Lifecycle Rules: automatizam a movimentação de objetos entre classes de armazenamento (por exemplo, mover arquivos antigos para Glacier).
- Versionamento: permite manter várias versões de um mesmo objeto, útil para recuperação de dados.
- Replication: copia objetos automaticamente entre regiões (para redundância e backup).
- Encryption: os dados podem ser criptografados em repouso (no S3) e em trânsito (via HTTPS).

### Segurança e Controle

- IAM Policies e Bucket Policies controlam quem pode acessar ou modificar objetos.
- Access Control Lists (ACLs) permitem definir permissões individuais por objeto.
- Logs de acesso e auditoria podem ser ativados para rastrear operações.

### Casos de Uso

- Armazenamento de backups e logs de sistemas.
- Hospedagem de sites estáticos.
- Repositório para dados de análise, machine learning e big data.
- Armazenamento e distribuição de conteúdos multimídia (imagens, vídeos, PDFs etc.).

## Integração EC2 + S3

Esses dois serviços se complementam:
- Instâncias EC2 processam dados e armazenam resultados no S3.
- Logs e backups de EC2 podem ser enviados automaticamente ao S3.
- O S3 serve como base de dados para aplicações hospedadas em EC2, permitindo alta escalabilidade e baixo custo.

## Representação Arquitetural no Diagrama

Após compreender os conceitos teóricos, elaborou-se um diagrama no Draw.io para ilustrar a forma como esses serviços podem se conectar em um fluxo real.
No modelo proposto (imagem do diagrama disponível em /imagens):

1. O usuário envia um arquivo por meio de uma aplicação hospedada na instância EC2
2. A instância EC2 recebe o arquivo e o armazena no volume D - EBS
3. A aplicação processa o arquivo, podendo gerar novos dados ou resultados.
4. Esses resultados são armazenados no volume E - EBS.
5. Informações relevantes são registradas no banco de dados gerenciado RDS.

Todo o processo ocorre dentro da infraestrutura da AWS, garantindo escalabilidade, disponibilidade e segurança.


## Referências Bibliográficas

AMAZON WEB SERVICES. Amazon EC2 Documentation. Disponível em: https://docs.aws.amazon.com/ec2/
. Acesso em: 22 out. 2025.

AMAZON WEB SERVICES. Amazon EBS Documentation. Disponível em: https://docs.aws.amazon.com/ebs/
. Acesso em: 22 out. 2025.

AMAZON WEB SERVICES. Amazon RDS Documentation. Disponível em: https://docs.aws.amazon.com/rds/
. Acesso em: 22 out. 2025.

AMAZON WEB SERVICES. Amazon S3 Documentation. Disponível em: https://docs.aws.amazon.com/s3/
. Acesso em: 22 out. 2025.

DIO. Formação AWS Cloud Foundations – Materiais de apoio do curso. Digital Innovation One. 2025.



