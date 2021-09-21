---
wts:
    title: '21 – Calcular SLAs compostos (5 min)'
    module: 'Módulo 06: Descreva o gerenciamento de custos do Azure e os acordos de nível de serviço'
---
# 21 – Calcular SLAs compostos (5 min)

Neste passo a passo, determinaremos o SLA de disponibilidade dos serviços do Azure e, em seguida, calcularemos a disponibilidade esperada baseada no SLA composto do aplicativo.

Nosso aplicativo de exemplo consiste nesses serviços do Azure. Não entraremos em configurações e considerações arquitetônicas profundas, a intenção aqui é dar um exemplo de alto nível.

+ **Serviço de aplicativo**: Para hospedar o aplicativo.
+ **Azure AD B2C**: Para autenticar logons de usuários e gerenciar perfis.
+ **Gateway de Aplicativo**: Para gerenciar o acesso e o dimensionamento do aplicativo. 
+ **Banco de Dados SQL do Azure**: Para armazenar dados do aplicativo. 

# Tarefa 1: Determinar os valores de porcentagem de tempo de atividade de SLA para o aplicativo

1. Em um navegador, vá para a página [Resumo do SLA para serviços do Azure](https://azure.microsoft.com/pt-br/support/legal/sla/summary/).

2. Localize o valor de tempo de atividade do SLA do **Serviço de Aplicativo**: **99,95%**. Clique em **Exibir detalhes completos** e expanda os **Detalhes do SLA**. Observe as **Porcentagens de tempo de atividade mensal** e os **Créditos de serviço**.

3. Retorne à página Web do SLA e localize o serviço **Azure Active Directory B2C** e determine o valor do tempo de atividade do SLA: **99,9%**. 

4. Localize o valor de tempo de atividade do SLA do **Gateway de Aplicativo**: **99,95%**. 

5. O banco de dados SQL do Azure usa camadas Premium, mas não está configurado para implantações de zona redundante. Localize o valor de tempo de atividade do SLA do **Banco de Dados SQL do Azure**: **99,99%**. 

    **Observação**: Existem diferentes valores de tempo de atividade para diferentes configurações e implantações do banco de dados SQL do Azure. É importante que você tenha clareza sobre os valores de tempo de atividade necessários, ao planejar e custear sua implantação e configuração. Pequenas mudanças no tempo de atividade podem ter impacto nos custos do serviço, bem como aumentar potencialmente a complexidade da configuração. Alguns outros serviços que podem ser de interesse na página Web de resumo do SLA do Azure incluem **máquinas virtuais**, **contas de armazenamento** e **Cosmos DB**.

# Tarefa 2: Calcular a porcentagem de tempo de atividade do SLA composto do aplicativo

1. Se algum dos serviços que compõem nosso aplicativo não estiver disponível, nosso aplicativo não estará disponível para que os usuários façam logon e usem. Como tal, o tempo de atividade total de nosso aplicativo consiste no seguinte:

    **% do tempo de atividade do serviço de aplicativo** X **% do tempo de atividade do Azure AD B2C** X  **% do tempo de atividade do Gateway de Aplicativo do Azure** X **% do tempo de atividade do Banco de Dados SQL do Azure** = **% do tempo de atividade total**

    que em termos percentuais é o seguinte:

    **99,95%** X **99,9%** X **99,95%** X **99,99%** = **99,79%**

    Esta é a disponibilidade esperada baseada em SLA de nosso aplicativo com os serviços e arquitetura atuais.

Parabéns! Você determinou o tempo de atividade baseado em SLA para cada um dos serviços em nosso aplicativo de amostra e, em seguida, calculou a disponibilidade esperada baseada em SLA composto para o aplicativo.
