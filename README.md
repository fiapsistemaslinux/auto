# Infraestrutura como Código 

**Tema do AM segundo semestre**

A idéia base por trás de ***IAC*** ou **infraestructure as a code** é desenvolver e configurar a infraestrutura com base em código e ferramentas de automação de ambiente de forma que sua arquitetura possa ser versionada, testada e principalmente ***reproduzida*** sempre que necessário.

O uso dessa abordagem aumenta consideravelmente a velocidade do deploy de sistemas e a eficiência em processos de escalabilidade, esse formato é muito ligado à cultura de sistemas devops e na maioria dos casos possui como base duas características:

***1. Computação em Núvem:***

O uso de cloud computing gera modelos mais escaláveis e maleáveis de arquiteturas, o que possibilita criar e recriar servidores, load balancers volumes e quaisquer outros recursos necessários a partir do uso de Rest Apis e ferramentas de automação.

***2. Automação de Ambientes:***

A segunda característica é a automação usando ferramentas específicas para essa finalidade, a ideia básica por trás da automação é fornecer ferramentas e meio para comunicação e manipulação de recursos, principalmente recursos de cloud computing.

Hoje em dia existem muitas ferramentas de automação e configuração de ambientes criadas para essa finalidade, entre as mais famosos posso citar seis projetos:

- [Ansible](https://www.ansible.com/)
- [Chef](https://www.chef.io/chef/)
- [Puppet](https://puppet.com/)
- [SaltStack](https://saltstack.com/)
- [CloudFormation](https://aws.amazon.com/pt/cloudformation/)
- [Terraform](https://www.terraform.io/)

## Gerenciamento de Configuração x Orquestração

As ferramentas citadas acima podem ser divididas em dois grupos: ***Gerenciamento de Configuração*** ou ***Orquestração***;

A diferença entre ferramentas de orquestração de ambiente e ferramentas de gerenciamento de configuração está na maneira como manipulamos a infra-estrutura.

***Ferramentas de Orquestração*** como o Terraform ou o CloudFormation da Amazon são utilizadas para automatizar o processo de ***criação*** dos servidores/instâncias e não para configurá-las, deixando esta etapa para outras ferramentas como Ansible, Puppet ou Chef conforme descrito no artigo [Why we use Terraform and not Chef, Puppet, Ansible, SaltStack, or CloudFormation](https://blog.gruntwork.io/why-we-use-terraform-and-not-chef-puppet-ansible-saltstack-or-cloudformation-7989dad2865c) publicado por [Yevgeniy Brikman](https://blog.gruntwork.io/@brikis98?source=post_header_lockup).

***Ferramentas de Gerenciamento de Configuração*** como o Ansible, Puppet, Saltstack ou Chef ficam com a segunda parte do trabalho sendo responsáveis por configurar as instências, instalando pacotes, configurando servidores e adicionando depêndencias como node, PHP ou jvm do java.

## Modelos de serviços em cloud

Quando bem utilizado o conceito de IAC junto a uma plataforma de cloud computing cria um conjunto extremamente eficaz para a construção de arquiteturas ágeis e que atendam às necessidades impostas pelo dinamismo atual dos times de desenvolvimento, existem certas classificações sobre a maneira como serviços de cloud são entregues aos seus usuários vale a pena um resumo sobre duas dessas classificações, aquelas que estão diretamente ligadas a devops:

- ***IAAS ou Infraestruture as a Service:***

Empresas como AWS, Microsoft ou Google e tecnologias como Openstack e Cloudstack se tornaram pioneiras nessa ideia usando um modelo chamado de ***iaas*** ou ***infraestructure as a service*** trata-se da ideia de fornecer plataformas de cloud computing para criação de servidores e serviços de forma dinâmica e escalável, a principal ideia aqui é que o usuário pegue pelos recursos que deseja utilizar. Logo ao inveś de comprar servidores estamos adquirindo processamento, memória e armazenamento sob demanda a idéia é que empresas possam consumir esse recursos abrindo mão dos custos iniciais relacionados a construção de um data center em detrimento de investimentos a serem feitos com base no crescimento da empresa.

- ***SAAS ou software as Service:***

Outro ponto importante é como a nuvem pode entregar valor e ferramentas direto ao desenvolvedor a partir do que chamamos de Saas ou software as a service, o [codedeploy](https://aws.amazon.com/pt/codedeploy/) é um belo exemplo deste modelo, outro exemplo muito famoso é o [Heroku](https://www.heroku.com/) amado por muitos desenvolvedores;

> Todas essas facilidades relacionadas a processos de deploy e automação tem em comum o uso de apis, plataformas de cloud como a AWS e o Google Cloud oferecem um vasto menu de apis entregues como serviços o que perimite o deploy de infra estrutura manipulação de dados auditoria e monitoramento, como exemplo podemos citar o [lambda](https://aws.amazon.com/pt/lambda/) capaz de entregar a desenvolvedores poder computacional com a abstenção de toda a parte de hardware e gerenciamento relacionada;

- ***CAAS ou Container as a Service:***

 Os containers Linux serão nosso próximo assunto e a ferramenta básica ao trabalharmos com MCA (Microservices Architecture), por enquanto podemos simplificar o conceito de um container como um _mecanismo para estabelecer grupos de controle de recursos criando estruturas isoladas para execução de aplicações_ considerando o uso dessa técnologia chamada container temos como consequência o surgimento do termo CAAS, trata-se de plataformas em cloud que oferecem serviços baseados em containers onde é possível desenharmos um arquitetura decompondo grandes sistemas monolíticos em serviços individuais e auto-gerenciáveis, Entre essas plataformas podemos citar o modelo de maior sucesso atualmente o [Kubernetes](https://kubernetes.io/) da Google.

---

## FAQ: Considerações importantes sobre cloud

***O uso de cloud compiting resolverá todos os problemas?***

Definitivamente não, entretanto o uso de cloud pode ser um aliado forte no prcoesso de solução de muitos problemas, cada serviço tem seu custo as vezes deveras elevado o que deve ser levado em conta antes de qualquer migração ou contratação, além disso existem grandes mudanças na maneira como operar esses recursos e na divisão de responsabilidades, assim como devops o uso de cloud computing demanda estudo e cuidado não se trata de uma bala de prata mas de uma parte importante a ser avaliada capaz de ajudar na evolução do negócio em qualquer tipo de empresa.

***Falando em devops, é imprescidivel possuir uma infra-estrutura de cloud?***

Mais uma vez não, conforme citado acima estamos falando de processos diferentes mas que quando utilizados juntos podem vir a produzir resultados melhores, ***é totalmente possível implementar metodologias ágeis e desenvolver uma cultura devops sem cloud*** dito isso, vale ressaltar que apesar de serem questões independentes, o uso de cloud computing tende a otimizar muito a capacidade de gerenciar configuração de ambientes, já que, usando cloud podemos controlar a infraestrutura usando os mesmos _patterns_ que usamos para controlar nosso código, daí o termo ***iac***.

Hoje em dia empresas como Netflix, Spootify ou mesmo empresas menores como as start-ups que surgem todos os dias tendem a utilizar modelos baseados em cloud computing motivadas pelo fato de que na maioria dos _providers_ de cloud você paga pelo recurso utilizado, o que elimina o gerenciamento de máquinas físicas e as consequentes preocupações com obsolescência de hardware, isso sem falar na reduação de mão de obra especializada, uma vez que, um unico arquiteto de cloud ou um developer com conhecimentos equivalentes pode tranquilamente desenvolver e manter o ecossistema inteiro (instâncias, base de dados, serviços, monitoração etc) de uma empresa de pequeno ou até médio porte.

## Material de Referência

Existem inumeras referências para consulta sobre esse assunto, no escopo deste material fizemos um overview bem simples mas para aqueles que quiserem se aprofundar um pouco mais na toca do coelho fica as recomendações abaixo:

Este guide sobre terraform explica de forma sucinta porem bem esclarecedora a diferença entre ferramentas de automação e de gerenciamento de configuração, neste caso em específico a escolha é voltada para o terraform, mas vale entender as argumentações e as motivações para essa escolha:

*[A Comprehensive Guide to Terraform](https://blog.gruntwork.io/why-we-use-terraform-and-not-chef-puppet-ansible-saltstack-or-cloudformation-7989dad2865c)

---

**Free Software, Hell Yeah!**
