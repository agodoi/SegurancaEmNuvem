# Segurança em Nuvem

Neste encontro iremos abordar a proteção de dados na nuvem no contexto de ambiente corporativo com múltiplas contas de usuário. Aspectos relevantes incluem: autenticação forte, auditoria, controles de permissões e gerenciamento.

## Assuntos:

- Gerenciamento e segurança de redes
- Segurança de Conexão
- Segurança de Sistemas
- Segurança em nuvem

## Atividade 1:
Assista o vídeo a seguir e escreva 2 fatores de segurança que te chamou a atenção e escreva no post-it. Vamos discutir

## [Entre no Miro](https://miro.com/welcomeonboard/MENKWDJFUmNDWjdoQ0d0eG45RU1xeDJBdmdsN1dLUVB5SEY5c1NGbnlMT1ZTV3dkQWs0ekxWb2puY284QzVsbHwzNDU4NzY0NTY1NDkwOTcxMTQ4fDI=?share_link_id=181798000725)

## [Acesse esse vídeo](www.youtube.com/watch?v=zDAYZU4A3w0)
Esse vídeo explica como funciona a segurança de um Data Center, no caso, do Google.

Após o vídeo, vamos discutir os itens de segurança explícitos mostrados no vídeo e os implícitos, mas de forma conceitual.


## Modelo de Responsabilidade Compartilhada da AWS

Observe a figura para entender qual é o papel do cliente e qual é o papel da arquitetura AWS em termos de responsabilidades. Esse modelo é chamado de **Modelo de Responsabilidade Compartilhada**.

O Modelo de Responsabilidade Compartilhada da AWS é um conceito fundamental na computação em nuvem que descreve como as responsabilidades de segurança são distribuídas entre o provedor de serviços em nuvem, no caso a AWS, e os clientes que utilizam os serviços da AWS. Esse modelo é projetado para garantir a segurança dos dados e das operações na nuvem, estabelecendo claramente quem é responsável pelo o quê.

Aqui está uma descrição mais detalhada do modelo de responsabilidade compartilhada da AWS:

1. **Responsabilidade da AWS (Provedor de Serviços em Nuvem):**
   - A AWS é responsável pela segurança da infraestrutura da nuvem. Isso inclui os data centers, servidores, redes, armazenamento e a virtualização subjacente que suportam seus serviços;
   - A AWS também é responsável por garantir que seus serviços básicos estejam protegidos e operando de forma segura. Isso inclui serviços como Amazon EC2 (computação em nuvem), Amazon S3 (armazenamento em nuvem) e Amazon RDS (banco de dados relacional);
   - A AWS fornece medidas de segurança física, como controles de acesso físico aos data centers, sistemas de detecção de intrusões e proteção contra falhas de hardware;
   - Desativação de hardware

2. **Responsabilidade do Cliente:**
   - Os clientes da AWS são responsáveis por configurar e proteger suas próprias aplicações, sistemas operacionais, dados e rede, senhas;
   - Isso inclui a configuração adequada de firewalls, detector de instrusos, acesso a servidores e aplicações, gerenciamento de identidade e acesso, e a implementação de práticas de segurança adequadas;
   - Configurações de sub-redes;
   - Criptografia de dados;
   - Os clientes também são responsáveis por manter seus sistemas operacionais e aplicativos atualizados com patches de segurança.
   - A AWS fornece ferramentas e serviços que os clientes podem usar para fortalecer sua segurança, como grupos de segurança, IAM (Identity and Access Management), AWS WAF (Web Application Firewall) e muito mais.

<picture>
   <source media="(prefers-color-scheme: light)" srcset="https://github.com/agodoi/SegurancaEmNuvem/blob/main/imgs/responsaCompartilhada.png">
   <img alt="Região e Zonas AWS" src="[YOUR-DEFAULT-IMAGE](https://github.com/agodoi/SegurancaEmNuvem/blob/main/imgs/responsaCompartilhada.png)">
</picture>

Portanto, a AWS possui as seguintes obrigações: infraestrutura física que contém seus recursos de segurança física:

- Acesso local super controlado
- Câmeras de segurança para detecção de instrusos
- Alarmes de segurança
- Portas automáticas
- Biometria para vários níveis de autenticação


Uma instância EC2 de um cliente é totalmente isolado de outro cliente. Assim tem-se:

- Isolamento de ataques
- Isolamento lógico dos dados
- Porém, não há 100% isolamneto físico entre as máquinas, pois elas podem ser compartilhadas fisicamente, mas isoladas logicamente.


## Dicas importantes:

- Quando você trabalha com IaaS, se preocupa com serviços não gerenciados pela AWS: EC2, EBS e VPC.
  
- Quando você trabalha no PaaS, se preocupa com serviços gerenciados pela AWS: Lambda, RDS ou Beanstalk. No PaaS, a AWS gerencia o sistema operacional, aplicação de patches em banco de dados, configuração de firewall e recuperação de desastres. O cliente se concentra no gerenciamento de código ou dados.

- Quando você trabalha com SaaS, se preocupa com serviços como AWS Trusted Advisor, AWS Shield e Amazon Chime, onde os softwares são hospedados de maneira centralizada, licenciado em um modelo de assinatura ou pagamento conforme o uso, acessados por meio de um navegador Web ou um app móvel ou uma API. Os clientes não gerenciam infra que oferece suporte ao serviço. A infra é amplamente invisível e gerenciada pelo provedor e o desenvolvedor foca no desenvolvimento do seu código. Por exemplo, para usar um RDS, vc não precisa de preocupar com camada mais baixa, como aplicação de patches, capacidade, softwares de manutenção. Você só precisa armazenar e recuperar dados nos pontos finais.


## MFA - Autenticação Multifator

A autenticação multifator (MFA) é um processo de login de conta com várias etapas que obriga o usuário a inserir informações que vão além de uma simples senha. Por exemplo, juntamente com a senha, os usuários podem ser solicitados a inserir um código que foi enviado para o e-mail deles, responder a uma pergunta secreta ou verificar uma impressão digital. Em caso de comprometimento de uma senha do sistema, uma segunda forma de autenticação pode ajudar a impedir o acesso não autorizado à conta.

<picture>
   <source media="(prefers-color-scheme: light)" srcset="https://github.com/agodoi/SegurancaEmNuvem/blob/main/imgs/aws_mfa_iam_api_1.png">
   <img alt="MFA" src="[YOUR-DEFAULT-IMAGE](https://github.com/agodoi/SegurancaEmNuvem/blob/main/imgs/aws_mfa_iam_api_1.png)">
</picture>

### Etapas do MFA:

- O sistema solicita apenas a senha e mais uma identificação. Isso é conhecido como autenticação de dois fatores ou autenticação em duas etapas.

- Em vez do sistema, a identidade do usuário é verificada por um aplicativo de terceiros, normalmente chamado de autenticador. Exemplo:


<picture>
   <source media="(prefers-color-scheme: light)" srcset="https://github.com/agodoi/SegurancaEmNuvem/blob/main/imgs/MFA-microsoft2.png">
   <img alt="MFA" src="[YOUR-DEFAULT-IMAGE](https://github.com/agodoi/SegurancaEmNuvem/blob/main/imgs/MFA-microsoft2.png)">
</picture>



- O usuário insere o código de acesso no autenticador e o aplicativo faz a confirmação do usuário para o sistema.

- Durante a verificação, o usuário insere informações biométricas mediante a leitura de uma impressão digital, retina ou outra parte do corpo.

- Talvez o sistema só exija várias autenticações quando você acessá-lo pela primeira vez usando um novo dispositivo. Depois disso, ele lembrará da máquina e solicitará apenas sua senha.



## IAM - Identity and Access Management

É um serviço que desempenha um papel crítico em garantir a segurança e controle sobre a infraestrutura na nuvem AWS.

Serve para gerenciar recursos da AWS. Um recurso é uma entidade em uma conta AWS: EC2 ou um bucket do S3. 

Quem pode acessar? Quais recursos podem acessar? Como os recursos podem ser acessados? Exemplo: quem pode ligar ou desligar um EC2?

O IAM é gratuito e está disponível em todas as regiões. Ele autentica e verifica o acesso de usuário, gerencia centralmente o acesso à execução de configuração, encerra recursos.

Algumas prinicipais funcionalidades do IAM, explicados em detalhes:

1. **Usuários, Grupos e Políticas:**
    - IAM permite criar e gerenciar usuários individuais que podem acessar sua conta AWS.
    - Você pode agrupar usuários em grupos e atribuir políticas de acesso aos grupos.
    - **Políticas IAM** definem as permissões que os usuários ou grupos têm para realizar ações em recursos da AWS.

2. **Autenticação:**
    - IAM suporta autenticação baseada em credenciais, incluindo senha e autenticação multifator (MFA).

3. **Autorização:**
    - Com políticas IAM, você controla quais ações os usuários podem realizar em recursos específicos da AWS.
    - As políticas podem ser altamente granulares, permitindo um controle fino sobre o acesso.

4. **Credenciais de Acesso:**
    - IAM fornece credenciais de acesso temporárias que podem ser usadas por aplicativos, scripts ou serviços para acessar recursos da AWS de forma segura.
    - Evita o uso de credenciais de longa duração, aumentando a segurança.

5. **Rastreamento e Auditoria:**
    - IAM registra atividades de usuário e fornece informações detalhadas sobre quem fez o quê e quando.
    - Isso é vital para fins de conformidade e segurança.

6. **Gerenciamento de Senhas:**
    - IAM permite a definição de políticas de senha e a rotação automática de senhas para os usuários.
    - Também suporta a redefinição de senhas e o bloqueio de usuários após várias tentativas de login malsucedidas.

7. **Assumir Funções (Role):**
    - IAM permite que você crie funções que podem ser assumidas por entidades confiáveis, como serviços AWS ou contas de usuário.
    - Isso é útil para conceder permissões temporárias a recursos, como instâncias EC2.

8. **Políticas Predefinidas:**
    - A AWS fornece políticas predefinidas que cobrem muitos casos de uso comuns, facilitando o controle de acesso.

9. **Integração com Serviços AWS:**
    - IAM está integrado com todos os serviços AWS, o que significa que você pode controlar quem pode acessar, modificar ou excluir recursos em toda a plataforma da AWS.

10. **Integração com Serviços de Diretório:**
    - IAM pode ser integrado com serviços de diretório, como o AWS Directory Service, para autenticação e autorização centralizadas.

12. **Acesso Condicional:**
    - Você pode definir políticas de acesso condicional com base em informações como endereços IP, data e hora, e outros atributos, aumentando a segurança.

13. **Uso com Contas AWS Múltiplas:**
    - IAM pode ser usado para federar o acesso entre contas AWS diferentes, permitindo gerenciar centralmente o acesso em um ambiente multinuvem.


**Atenção: o nome do usuário IAM nao pode ter espaço**. 

O IAM é organizado em:

- **Usuário IAM** --> é uma pessoa ou aplicativo que pode se autenticar com uma conta AWS.
- **Grupo IAM** --> é um conjunto de usuários IAM que recebem autorização idêntica.
- **Política IAM** --> o documento que define quais recursos podem ser acessados e o nível de acesso a cada recurso.
- **Função IAM** --> mecanismo útil para concender um conjunto de permissões para fazer solicitações de serviços AWS. Em outras palavras, o usuário assume uma responsabilidade temporária, é como se fosse o SUDO no Linux.


### Exemplos de Políticas IAM

Seu usuário de laboratório do Learner Lab tem mais de 1000 políticas prédefinidas disponíveis no IAM, nas quais você pode combiná-las para criar suas próprias políticas personalizadas de acordo com as necessidades específicas da sua organização. 

As políticas predefinidas do IAM incluem políticas de administrador, políticas de apenas leitura, políticas de acesso a recursos específicos, políticas para serviços específicos da AWS, políticas para funções de serviço, entre outras. Aqui estão alguns exemplos de políticas predefinidas comuns:

1. **AdministratorAccess:** Esta política concede acesso completo a todos os recursos e operações da AWS, tornando um usuário um administrador com controle total sobre a conta.

2. **ReadOnlyAccess:** Esta política concede acesso somente leitura a todos os recursos da AWS, permitindo que os usuários visualizem informações, mas não façam alterações.

3. **AmazonS3FullAccess:** Esta política concede acesso total aos serviços de armazenamento Amazon S3, incluindo a capacidade de criar, listar, excluir e modificar objetos no S3.

4. **AmazonEC2FullAccess:** Esta política concede acesso total aos serviços Amazon EC2, permitindo que os usuários criem, gerenciem e excluam instâncias EC2, entre outras operações.

5. **AmazonRDSFullAccess:** Esta política concede acesso total ao Amazon RDS (Relational Database Service) para criar e gerenciar bancos de dados relacionais.

6. **AWSLambda_FullAccess:** Esta política concede acesso total ao AWS Lambda, permitindo a criação, execução e gerenciamento de funções de Lambda.

7. **AWSLambda_ReadOnlyAccess:** Esta política concede acesso somente leitura ao AWS Lambda, permitindo visualizar as configurações e o estado das funções de Lambda.

## Exemplo de Política em JSON

Os 3 atributos mais comuns no JSON são:

- Effect
- Action
- Resouce

### Detalhando:

Esses 3 atributos principais determinam as permissões concedidas a usuários, grupos e funções dentro da AWS:

1. **Effect (Efeito)**: Este atributo especifica o efeito que a política terá quando associada a um usuário, grupo ou função. Existem dois valores possíveis para o efeito:
     - `Allow`: Permite que a ação especificada seja executada. Se uma política com `Effect` definido como `Allow` for associada a um usuário, ele terá permissão para realizar as ações especificadas na política.
     - `Deny`: Negará explicitamente a permissão para a ação especificada, anulando qualquer permissão `Allow` anterior. Se uma política com `Effect` definido como `Deny` for associada a um usuário, ele não poderá realizar as ações especificadas, mesmo que outras políticas permitam.

2. **Action (Ação)**: Este atributo define a ação ou conjunto de ações que a política permite ou nega. As ações são ações específicas que podem ser realizadas nos serviços da AWS. Por exemplo, a ação pode ser `s3:GetObject` para permitir a recuperação de objetos em um bucket do Amazon S3 ou `ec2:StartInstance` para permitir a inicialização de uma instância do Amazon EC2. Você pode listar múltiplas ações em uma única política.

3. **Resource (Recurso)**: Este atributo especifica os recursos ou objetos específicos aos quais a política se aplica. Um recurso pode ser um bucket no Amazon S3, uma instância no Amazon EC2, uma tabela no Amazon DynamoDB, entre outros. Especificar o recurso ajuda a limitar as permissões apenas aos recursos específicos listados. Por exemplo, você pode limitar uma política que concede permissões para `s3:GetObject` apenas a um bucket específico, definindo o recurso como o ARN (Amazon Resource Name) desse bucket.

Aqui está um exemplo de uma política IAM em JSON que ilustra esses atributos:

```json
{
  "Effect": "Allow",
  "Action": "s3:GetObject",
  "Resource": "arn:aws:s3:::meu-bucket/*"
}
```

Neste exemplo, a política permite a ação `s3:GetObject` no recurso específico, que é o conteúdo de um bucket chamado "meu-bucket" no Amazon S3. Portanto, os usuários ou funções com essa política terão permissão para buscar objetos dentro desse bucket, mas não terão permissões para realizar outras ações em outros recursos da AWS.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "iam:AddUserToGroup",
                "iam:UpdateGroup",
                "iam:UpdateUser",
                "iam:*LoginProfile",
                "iam:GenerateCredentialReport",
                "iam:RemoveUserFromGroup",
                "iam:List*",
                "iam:Get*",
                "CloudFormation:*",
                "ec2:Get*",
                "ec2:List*",
                "ec2:Describe*",
                "cloudtrail:GetTrailStatus",
                "cloudtrail:DescribeTrails",
                "cloudtrail:LookupEvents",
                "cloudtrail:ListTags",
                "cloudtrail:ListPublicKeys",
                "cloudtrail:GetEventSelectors",
                "s3:ListAllMyBuckets",
                "s3:GetObject",
                "s3:GetBucketLocation",
                "kms:ListAliases",
                "lambda:ListFunctions"
            ],
            "Resource": "*",
            "Effect": "Allow"
        },
        {
            "Action": "iam:*",
            "Resource": [
                "arn:aws:iam::*:user/awsstudent",
                "arn:aws:iam::*:user/root-qwkl*"
            ],
            "Effect": "Deny"
        },
        {
            "Action": "s3:ListAllMyBuckets",
            "Resource": "*",
            "Effect": "Allow"
        },
        {
            "Action": [
                "cloudformation:ListStacks",
                "cloudformation:DescribeStacks",
                "cloudformation:DescribeStackEvents",
                "cloudformation:DescribeStackResource",
                "cloudformation:DescribeStackResources"
            ],
            "Resource": "*",
            "Effect": "Allow"
        },
        {
            "Action": [
                "ec2:*Spot*",
                "ec2:*ReservedInstances*",
                "ec2:*Scheduled*",
                "ec2:*Purchase*",
                "ec2:EnableFastSnapshotRestores"
            ],
            "Resource": "*",
            "Effect": "Deny",
            "Sid": "RestrictActions"
        },
        {
            "Condition": {
                "StringNotEqualsIfExists": {
                    "ec2:PlacementGroupStrategy": "cluster"
                },
                "ForAllValues:StringLikeIfExists": {
                    "ec2:Tenancy": "default",
                    "ec2:InstanceType": [
                        "*.nano",
                        "*.micro",
                        "*.small"
                    ]
                },
                "NumericLessThanEqualsIfExists": {
                    "ec2:VolumeSize": "51"
                },
                "StringNotEqualsIgnoreCaseIfExists": {
                    "ec2:VolumeType": [
                        "io1",
                        "st1"
                    ]
                },
                "StringEqualsIfExists": {
                    "ec2:Owner": "amazon"
                }
            },
            "Action": [
                "ec2:CreateVolume",
                "ec2:ModifyVolume",
                "ec2:ImportVolume",
                "ec2:ModifyVolumeAttribute",
                "ec2:ModifyFleet",
                "ec2:ImportSnapshot",
                "ec2:ResetInstanceAttribute",
                "ec2:CreateFleet",
                "ec2:CreateLaunchTemplateVersion",
                "ec2:EnableVolumeIO",
                "ec2:CreateLaunchTemplate",
                "ec2:ImportInstance",
                "ec2:ModifyInstanceCreditSpecification",
                "ec2:ModifyLaunchTemplate",
                "ec2:ModifyInstanceAttribute",
                "ec2:RebootInstances",
                "ec2:RunInstances",
                "ec2:StartInstances"
            ],
            "Resource": "*",
            "Effect": "Allow",
            "Sid": "RestrictInstanceActions"
        }
    ]
}
```

## Outro Exemplo:

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor0",
            "Effect": "Allow",
            "Action": "iam:CreateServiceLinkedRole",
            "Resource": "*",
            "Condition": {
                "StringEquals": {
                    "iam:AWSServiceName": "robomaker.amazonaws.com"
                }
            }
        },
        {
            "Sid": "VisualEditor1",
            "Effect": "Allow",
            "Action": [
                "cloudwatch:*",
                "cloudformation:*",
                "ec2:AssociateRouteTable",
                "ec2:AttachInternetGateway",
                "ec2:CreateInternetGateway",
                "ec2:CreateNetworkInterfacePermission",
                "ec2:CreateRoute",
                "ec2:CreateRouteTable",
                "ec2:CreateSecurityGroup",
                "ec2:CreateSubnet",
                "ec2:CreateTags",
                "ec2:CreateVpc",
                "ec2:DeleteNetworkInterface",
                "ec2:DeleteSubnet",
                "ec2:DescribeNetworkInterfaces",
                "ec2:DescribeSecurityGroups",
                "ec2:DescribeSubnets",
                "ec2:DescribeVpcs",
                "kinesis:*",
                "kinesisvideo:*",
                "lex:*",
                "logs:*",
                "polly:*",
                "robomaker:*",
                "rekognition:*",
                "s3:*",
                "sns:*",
                "iam:passrole"
            ],
            "Resource": "*"
        }
    ]
}
```
# Prática

Nessa prática, vamos simular a contratação de 3 funcionários de desenvolvimento, e cada um terá uma função na arquitetura de nuvem, conforme mostra a figura a seguir.

<picture>
   <source media="(prefers-color-scheme: light)" srcset="https://github.com/agodoi/SegurancaEmNuvem/blob/main/imgs/pratica_01.png">
   <img alt="PraticaIAM" src="[YOUR-DEFAULT-IMAGE](https://github.com/agodoi/SegurancaEmNuvem/blob/main/imgs/pratica_01.png)">
</picture>

Então, sua tarefa hoje é criar esses 3 usuários com as políticas indicas na figura.

- Como explorar usuários e grupos do IAM pré-criados?
- Como inspecionar políticas do IAM, conforme aplicadas aos grupos pré-criados?
- Como adotar um cenário real para adicionar usuários a grupos com recursos específicos habilitados?
- Como localizar e usar a URL de login do IAM?
- Como testar os efeitos das políticas no acesso ao serviço?


Como se faz isso? Seguindo os passos:

### Lembrando:

**Gerenciar usuários do IAM e seu acesso:** você pode criar usuários e atribuir a eles credenciais de segurança individuais (chaves de acesso, senhas e dispositivos de autenticação multifator). É possível gerenciar permissões para controlar quais operações um usuário pode executar.

**Gerenciar funções do IAM e suas permissões:** uma função do IAM é semelhante a um usuário, já que é uma identidade da AWS com políticas de permissão que determinam o que a identidade pode e não pode fazer na AWS. Porém, a finalidade de uma função é poder ser assumida por qualquer pessoa que necessite dela, e não associada exclusivamente a um único indivíduo.

**Gerenciar usuários federados e suas permissões:** você pode habilitar a federação de identidades para permitir que os usuários existentes na sua empresa acessem o Console de Gerenciamento da AWS, chamem as APIs da AWS e acessem recursos, sem necessidade de criar um usuário do IAM para cada identidade.


# Passo-01:

Nesse passo, vamos levantar alguns dados do seu perfil de usuário do Learner Lab.

a) No menu de opção do console AWS, digite **IAM**, e depois clique em **Grupos de Usuários**. Quantos grupos você está inserido?

b) Clique em **Usuários**, e verifique quantos cadastrados tem no seu perfil.

c) Clique em **Funções**, quantas vocês possui nesse perfil?

d) Clicando em **Políticas**, quantas estão no seu perfil?

e) Clicando em **Provedores de identidade**, quantos você está inserido? Um IdP (Identity Provider). O AWS IAM permite a integração com vários IdPs para habilitar o Single Sign-On (SSO) e simplificar o gerenciamento de identidades e acesso na AWS. Quando um usuário autenticado solicita acesso a recursos da AWS, o IdP pode ser configurado para gerar tokens de acesso temporário que são usados para autenticar o usuário na AWS. Gerenciamento Centralizado de Identidades: Os IdPs são frequentemente usados em ambientes empresariais para centralizar o gerenciamento de identidades. Isso significa que as informações de usuário, políticas de acesso e autenticação são gerenciadas em um único local, tornando mais fácil a adição, remoção e atualização de usuários e permissões.

# Passo-02: criando o grupo EC2-Support

a) Carregue o serviço **IAM**.

b) No menu vertical da esquerda, clique em **Grupos** e crie um grupo chamado **EC2-Support**.

c) Clique na guia **Permissões** e adicione a permissão **AmazonEC2ReadOnlyAccess** e **IAMReadOnlyAccess**. Isso significa que esse grupo terá uma política gerenciada associada a ele, chamada **AmazonEC2ReadOnlyAccess + IAMReadOnlyAccess**. As políticas gerenciadas são políticas criadas previamente (pela AWS ou por seus administradores) que podem ser associadas a usuários e grupos do IAM. Quando a política é atualizada, as alterações à política são imediatamente aplicadas a todos os usuários e grupos associados a ela.

d) Confirme a criação desse Grupo;

e) Volte em **Permissões** e confira a política criada. Uma política define quais ações são permitidas ou negadas para recursos específicos da AWS. Esta política concede permissão para listar e descrever informações sobre EC2, Elastic Load Balancing, CloudWatch e Auto Scaling. **Essa capacidade é para visualizar recursos, mas não os modificar, é ideal para atribuir a uma função de suporte**.

# Passo-03: criando grupo S3-Support

a) No painel de navegação à esquerda, clique em **Grupos**.

b) E crie outro grupo chamado **S3-Support** e adicione a política **AmazonS3ReadOnlyAccess** e **IAMReadOnlyAccess** e confirme. Essa política tem permissões para obter e listar recursos no Amazon S3.

# Passo-04: criando grupo EC2-Admin

a) Novamente, no painel de navegação à esquerda, clique em **Grupos** e crie o 3º grupo chamado **EC2-Admin**. 

b) Associe a esse grupo uma política capaz de conceder permissão para visualizar (Descrever) informações sobre o Amazon EC2 e permite também iniciar e interromper instâncias + **IAMReadOnlyAccess**. Procure a permissão que melhor faça isso e confirme a criação. 

# Passo-05: Confirme os grupos criados

a) EC2-Support → política AmazonEC2ReadOnlyAccess + IAMReadOnlyAccess

b) S3-Support → política AmazonS3ReadOnlyAccess + IAMReadOnlyAccess

c) EC2-Admin → X ? Vc é quem vai decidir + IAMReadOnlyAccess

# Passo-06: criando 3 usuários

a) Ainda no seu perfil root e no serviço IAM, clique em **Usuários**.

b) Crie 3 usuários com os seguintes nomes:

b.1) user1 → sem MFA, coloque a senha estudante@user1 → tome nota do link com 12 dígitos num arquivo TXT a parte

b.2) user2 → sem MFA, coloque a senha estudante@user2 → tome nota do link com 12 dígitos num arquivo TXT a parte

b.3) user3 → sem MFA, coloque a senha estudante@user3 → tome nota do link com 12 dígitos num arquivo TXT a parte

c) Clique em **user1**. Isso levará para uma página de resumo do user1. A guia **Permissões** será exibida. Observe que user1 não tem permissões. Clique na guia **Grupos** e associe o grupo **EC2-Support** ao **user1**.

d) Clique na guia **Grupos** e associe o grupo **S3-Support** ao **user2**.

e) Clique na guia **Grupos** e associe o grupo **EC2-Admin** ao **user3**.

# Passo-07: fazendo testes de segurança

a) Saia do seu perfil root;

b) Abra uma aba ANÔNIMA do seu navegador e na opção usuário IAM, logue com o **user1**

c) Vá em IAM, depois **Usuário** e veja a política dele se está como: **EC2-Support → política AmazonEC2ReadOnlyAccess**

d) Deslogue do **user1**, logue no **user2** e confira se sua política está em **AmazonS3ReadOnlyAccess**

e) Deslogue do **user2**, logue no **user3** e confira se sua política está em X ? que você decidiu no **Passo-05 (c)**.



# Kahoot
