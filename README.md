# Segurança em Nuvem

Neste encontro iremos abordar a proteção de dados na nuvem no contexto de ambiente corporativo com múltiplas contas de usuário. Aspectos relevantes incluem: autenticação forte, auditoria, controles de permissões e gerenciamento.

## Assuntos:

- Gerenciamento e segurança de redes
- Segurança de Conexão
- Segurança de Sistemas
- Segurança em nuvem


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


### [Acesse esse vídeo](www.youtube.com/watch?v=zDAYZU4A3w0)
Esse vídeo explica como funciona a segurança de um Data Center, no caso, do Google.

### Dicas importantes:

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



-   O usuário insere o código de acesso no autenticador e o aplicativo faz a confirmação do usuário para o sistema.

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

11. **Acesso Condicional:**
    - Você pode definir políticas de acesso condicional com base em informações como endereços IP, data e hora, e outros atributos, aumentando a segurança.

12. **Uso com Contas AWS Múltiplas:**
    - IAM pode ser usado para federar o acesso entre contas AWS diferentes, permitindo gerenciar centralmente o acesso em um ambiente multinuvem.


**No IAM, o nome do usuário nao pode ter espaço**. 

O IAM é organizado em:

- **Usuário IAM** --> é uma pessoa ou aplicativo que pode se autenticar com uma conta AWS.
- **Grupo IAM** --> é um conjunto de usuários IAM que recebem autorização idêntica.
- **Política IAM** --> o documento que define quais recursos podem ser acessados e o nível de acesso a cada recurso.
- **Função IAM** --> mecanismo útil para concender um conjunto de permissões para fazer solicitações de serviços AWS. Em outras palavras, o usuário assume uma responsabilidade temporária, é como se fosse o SUDO no Linux.


