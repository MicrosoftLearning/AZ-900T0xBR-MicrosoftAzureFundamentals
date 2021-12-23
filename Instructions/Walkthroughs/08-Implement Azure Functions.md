---
wts:
    title: '08 – Implementar Funções do Azure (5 min)'
    module: 'Módulo 03: Descrever as principais soluções e ferramentas de gerenciamento'
---
# 08 – Implementar Funções do Azure (5 min)

Neste passo a passo, criaremos um aplicativo de funções para exibir uma mensagem Olá quando houver uma solicitação HTTP. 

# Tarefa 1: Criar um aplicativo de funções 

Nesta tarefa, criaremos um aplicativo de funções.

1. Entre no [portal do Azure](https://portal.azure.com).

2. Na barra **Pesquisar** na parte superior do portal, pesquise e selecione **Aplicativo de Funções** e, na folha **Aplicativo de Funções**, selecione **+ Adicionar**, **+ Criar**, **+ Novo**.

3. Na guia **Básico** da folha do **Aplicativo de Funções**, especifique as seguintes configurações (substitua **xxxx** no nome da função por letras e dígitos de forma que o nome seja globalmente exclusivo e mantenha todas as outras configurações com seus valores padrão): 

    | Configurações | Valor |
    | -- | --|
    | Assinatura | **Mantenha a padrão fornecida** |
    | Grupo de recursos | **Criar novo grupo de recursos** |
    | Nome do aplicativo de funções | **function-xxxx** |
    | Publicar | **Código** |
    | Pilha de runtime | **NET** |
    | Versão | **3.1** |
    | Região | **Leste dos EUA** |

    **Observação** - Lembre-se de alterar o **xxxx** para que tenha um **Nome de aplicativo de funções** exclusivo

4. Clique em **Revisar + Criar** e, após a validação bem-sucedida, clique em **Criar** para começar a provisionar e implantar seu novo Aplicativo de Funções do Azure.

5. Aguarde a notificação de que o recurso foi criado.

6. Quando a implantação for concluída, selecione Ir para o recurso na folha de implantação. Se preferir, navegue de volta para a folha **Aplicativo de Funções**, selecione **Atualizar** e verifique se o status do aplicativo de funções recém-criado é **Em execução**. 

    ![Captura de tela da página Aplicativo de Funções com o novo aplicativo de Funções.](../images/0701.png)

# Tarefa 2: Criar uma função disparada por HTTP e testar

Nesta tarefa, usaremos a função Webhook + API para exibir uma mensagem quando houver uma solicitação HTTP. 

1. Na folha **Aplicativo de Funções**, clique no aplicativo de funções recém-criado. 

2. Na folha do aplicativo de funções, na seção **Funções**, selecione **Funções** e **+ Adicionar**, **+ Criar**, **+ Novo**.

    ![Captura de tela da etapa de escolha de um ambiente de desenvolvimento nas funções do Azure para o painel de introdução dot net dentro do portal do Azure. Os elementos de exibição para a criação de uma nova função no portal são destacados. Os elementos destacados são: expandir o aplicativo de funções, adicionar nova função, no portal e o botão continuar.](../images/0702.png)

3. Uma janela pop-up para **Adicionar função** será exibida à direita. Na seção **Selecionar modelo**, escolha **Gatilho HTTP**. Selecione **Adicionar** 

    ![Captura de tela da etapa de criar uma função nas funções do Azure para o painel de introdução dot net dentro do portal do Azure. O cartão do gatilho HTTP está destacado para ilustrar os elementos de exibição usados para adicionar um novo webhook a uma função do Azure.](../images/0702a.png)

4. Na folha **HttpTrigger1**, na seção **Desenvolvedor**, clique em **Código + Teste**. 

5. Na folha **Código + Teste**, analise o código gerado automaticamente e observe que ele foi desenvolvido para executar uma solicitação HTTP e registrar informações. Além disso, observe que a função responde com uma mensagem de Olá, com um nome. 

    ![Captura de tela do código da função. A mensagem Olá aparece destacada.](../images/0704.png)

6. Clique em **Obter URL de função** na seção superior do editor de função. 

7. Certifique-se de que o valor na lista suspensa **Chave** esteja definido como **padrão** e clique em **Copiar** para copiar o URL da função. 

    ![Captura de tela do painel obter URL de função dentro do editor de funções no portal do Azure. Os elementos de exibição – o botão Obter URL de função; o menu suspenso Definir chave e o botão Copiar URL – são destacados para indicar como obter e copiar o URL de função do editor de função.](../images/0705.png)

8. Abra uma nova guia do navegador e cole o URL da função copiado na barra de endereços do seu navegador Web. Quando a página for solicitada, a função será executada. Observe a mensagem retornada informando que a função requer um nome no corpo da solicitação.

    ![Captura de tela da mensagem Forneça um nome.](../images/0706.png)

9. Acrescente **&name=*yourname*** ao final do URL.

    **Observação**: Por exemplo, se seu nome for Cindy, o URL final será semelhante a: `https://azfuncxxx.azurewebsites.net/api/HttpTrigger1?code=X9xx9999xXXXXX9x9xxxXX==&name=cindy`

    ![Captura de tela de um URL de função destacado e um nome de usuário de amostra anexado na barra de endereços de um navegador Web. A mensagem Olá e o nome de usuário também são destacados para ilustrar a saída da função na janela principal do navegador.](../images/0707.png)

10. Ao pressionar o enter, sua função é executada e todas as invocações são rastreadas. Para visualizar os rastreamentos, volte à folha **HttpTrigger1 \| Código + Teste** do Portal e clique em **Monitorar**. Você pode **configurar** o Application Insights selecionando o registro de data e hora e clique em **Executar consulta no Application Insights**.

    ![Captura de tela de um log de informações de rastreamento resultante da execução da função dentro do editor de funções no portal do Azure.](../images/0709.png) 

Parabéns! Você criou um aplicativo de funções para exibir uma mensagem Olá quando houver uma solicitação HTTP. 

**Observação**: Para evitar custos adicionais, você tem a opção de remover este grupo de recursos. Procure grupos de recursos, clique em seu grupo de recursos e, em seguida, clique em **Excluir grupo de recursos**. Verifique o nome do grupo de recursos e clique em **Excluir**. Monitore as **Notificações** para ver como a exclusão está ocorrendo.
