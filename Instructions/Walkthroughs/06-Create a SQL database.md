---
wts:
    title: '06 – Criar um banco de dados SQL (5 min)'
    module: 'Módulo 02 – Principais serviços do Azure (cargas de trabalho)'
---

# 06 – Criar um banco de dados SQL (5 min)

Neste passo a passo, vamos criar um banco de dados SQL no Azure e depois consultar os dados nesse banco de dados.

# Tarefa 1: Criar o banco de dados 

Nesta tarefa, criaremos um banco de dados SQL baseado no banco de dados de amostra AdventureWorksLT. 

1. Entre no portal do Azure em [**https://portal.azure.com**](https://portal.azure.com).

2. Na folha **Todos os serviços**, procure e selecione **Bancos de dados SQL** e depois selecione **+ Adicionar, + Criar, + Novo**. 

3. Na guia **Básico**, preencha essas informações.  

    | Configuração | Valor | 
    | --- | --- |
    | Assinatura | **Use a padrão fornecida** |
    | Grupo de recursos | **Criar novo grupo de recursos** |
    | Nome do banco de dados| **db1** | 
    | Servidor | Selecione **Criar novo** (Uma nova barra lateral será aberta à direita)|
    | Nome do servidor | **sqlserverxxxx** (deve ser exclusivo) | 
    | Logon de administrador do servidor | **sqluser** |
    | Senha | **Pa$$w0rd1234** |
    | Local | **(EUA) Leste dos EUA** |
    | Clique em  | **OK** |

   ![Captura de tela do painel Servidor e do painel Novo Servidor com os campos preenchidos de acordo com a tabela e com os botões Revisar + criar e OK realçados.](../images/0501.png)

4. Na guia **Rede**, defina as configurações a seguir (deixe os outros campos com os valores padrão) 

    | Configuração | Valor | 
    | --- | --- |
    | Método de conectividade | **Ponto de extremidade público** |    
    | Permitir que serviços e recursos do Azure acessem este servidor | **Sim** |
    | Adicionar endereço IP atual do cliente | **Não** |
    
   ![Captura de tela da guia Rede da folha Criar Banco de Dados SQL com as configurações selecionadas de acordo com a tabela e com o botão Revisar + criar realçado.](../images/0501b.png)

5. Na guia **Segurança**. 

    | Configuração | Valor | 
    | --- | --- |
    | Azure Defender para SQL| **Agora não** |
    
6. Vá para a guia **Configurações adicionais**. Usaremos o banco de dados de amostra AdventureWorksLT.

    | Configuração | Valor | 
    | --- | --- |
    | Usar dados existentes | **Amostra** |

    ![Captura de tela da guia Configurações adicionais da folha Criar Banco de Dados SQL com as configurações selecionadas de acordo com a tabela e com o botão Revisar + criar realçado.](../images/0501c.png)

7. Clique em **Revisar + criar** e selecione **Criar** para implantar e provisionar o grupo de recursos, o servidor e o banco de dados. Pode demorar aprox. 2 a 5 minutos para implantar.


# Tarefa 2: Testar o banco de dados.

Nesta tarefa, vamos configurar o SQL Server e executar uma consulta SQL. 

1. Quando a implantação for concluída, selecione Ir para o recurso na folha de implantação. Se preferir, na folha **Todos os serviços**, procure e selecione **Bancos de Dados** e depois **Bancos de dados SQL**; verifique se o novo banco de dados foi criado. Pode ser necessário **Atualizar** a página.

    ![Captura de tela do banco de dados SQL e do servidor que acabam de ser implantados.](../images/0502.png)

2. Selecione a entrada **db1** representando o banco de dados SQL criado. Na folha db1, selecione **Editor de Consultas (pré-visualização)**.

3. Faça logon como **sqluser** com a senha **Pa$$w0rd1234**.

4. Você não conseguirá fazer logon. Leia o erro com atenção e anote o endereço IP que precisa receber permissão para atravessar o firewall. 

    ![Captura de tela da página de logon do Editor de Consultas com erro de endereço IP.](../images/0503.png)

5. De volta à folha **db1**, selecione **Visão geral**. 

    ![Captura de tela da página do SQL Server.](../images/0504.png)

6. Na folha **Visão geral** do db1, selecione **Definir firewall do servidor** no centro superior da tela.

7. Selecione **+ Adicionar IP do cliente** (barra de menu superior) para adicionar o endereço IP mencionado no erro. (ele deve ser preenchido automaticamente; caso não seja, cole-o nos campos do endereço IP). Certifique-se de **Salvar** suas alterações. 

    ![Captura de tela da página de configurações do firewall do SQL Server com a nova regra de IP realçada.](../images/0506.png)

8. Volte ao banco de dados SQL (deslizar para a esquerda na barra de alternância na parte inferior) e selecione **Editor de Consultas (Pré-visualização)**. Tente fazer logon novamente como **sqluser** com a senha **Pa$$w0rd1234**. Desta vez, você deve conseguir. Observe que pode demorar alguns minutos para que a nova regra de firewall seja implantada. 

9. Quando entrar, o painel de consulta será exibido. Insira a consulta a seguir no painel do editor. 

    ```SQL
    SELECT TOP 20 pc.Name as CategoryName, p.name as ProductName
    FROM SalesLT.ProductCategory pc
    JOIN SalesLT.Product p
    ON pc.productcategoryid = p.productcategoryid;
    ```

    ![Captura de tela do Editor de consultas com o painel consultas e os comandos sendo executados com êxito.](../images/0507.png)

10. Clique em **Executar** e examine os resultados da consulta no painel **Resultados**. A consulta deve ser executada com êxito.

    ![Captura de tela do painel do Editor de Consultas do banco de dados com o código SQL executado com êxito e a saída visível no painel de resultados.](../images/0508.png)

Parabéns! Você criou um banco de dados SQL no Azure e consultou com êxito os dados contidos nele.

**Observação**: Para evitar custos adicionais, você tem a opção de remover este grupo de recursos. Procure grupos de recursos, clique em seu grupo de recursos e, em seguida, clique em **Excluir grupo de recursos**. Verifique o nome do grupo de recursos e clique em **Excluir**. Monitore as **Notificações** para ver como a exclusão está ocorrendo.
