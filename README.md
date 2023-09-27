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





