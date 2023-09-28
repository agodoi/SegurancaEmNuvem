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

- Quando você trabalha no PaaS, se preocupa com serviços gerenciados pela AWS: Lambda, RDS ou Beanstalk. No PaaS, a AWS gerencia o sistema operacional, aplicação de patches em banco de dados, configuração de firewall e recuperação de desastres. O cliente se concentra no gerenciamento de código ou dados.

- Quando você trabalha com IaaS, se preocupa com serviços não gerenciados pela AWS: EC2, EBS e VPC.

- Quando você trabalha com SaaS, se preocupa com serviços como AWS Trusted Advisor, AWS Shield e Amazon Chime, onde os softwares são hospedados de maneira centralizada, licenciado em um modelo de assinatura ou pagamento conforme o uso, acessados por meio de um navegador Web ou um app móvel ou uma API. Os clientes não gerenciam infra que oferece suporte ao serviço.

- A infra é amplamente invisível e gerenciada pelo provedor e o desenvolvedor foca no desenvolvimento do seu código. Por exemplo, para usar um RDS, vc não precisa de preocupar com camada mais baixa, como aplicação de patches, capacidade, softwares de manutenção. Você só precisa armazenar e recuperar dados nos pontos finais.


## MFA - Autenticação Multifator

A autenticação multifator (MFA) é um processo de login de conta com várias etapas que obriga o usuário a inserir informações que vão além de uma simples senha. Por exemplo, juntamente com a senha, os usuários podem ser solicitados a inserir um código que foi enviado para o e-mail deles, responder a uma pergunta secreta ou verificar uma impressão digital. Em caso de comprometimento de uma senha do sistema, uma segunda forma de autenticação pode ajudar a impedir o acesso não autorizado à conta.

## IAM - Identity and Access Management

Serve para gerenciar recursos da AWS. Um recurso é uma entidade em uma conta AWS: EC2 ou um bucket do S3. Quem pode acessar? Quais recursos pode acessar? Como os recursos podem ser acessados? O IAM é gratuito e está disponível em todas as regiões. Ele autentica e verifica o acesso de usuário, gerencia centralmente o acesso à execução de configuração, encerra recursos


