---
wts:
    title: '10- Criar uma VM com o PowerShell (10 min)'
    module: 'Módulo 03: Descrever as principais soluções e ferramentas de gerenciamento'
---
# 10 – Criar VM com o PowerShell (10 min)

Neste passo a passo, vamos configurar o Cloud Shell, usar o módulo Azure PowerShell para criar um grupo de recursos e máquina virtual e analisar as recomendações do Assistente do Azure. 

# Tarefa 1: Configurar o Cloud Shell 

Nesta tarefa, vamos configurar o Cloud Shell. 

1. Entre no [portal do Azure](https://portal.azure.com). **Você encontra as credenciais de logon na guia de recursos (bem ao lado desta guia de Instruções!)**
2. No portal do Azure, abra o **Azure Cloud Shell** clicando no ícone no canto superior direito do portal do Azure.

    ![Captura de tela do ícone do Azure Cloud Shell no portal do Azure.](../images/1002.png)

3. Quando solicitado a selecionar **Bash** ou **PowerShell**, selecione **PowerShell**.

4. Na tela **Não há armazenamentos montados**, selecione **Exibir configurações avançadas** e preencha as informações abaixo

    | Configurações | Valores |
    |  -- | -- |
    | Grupo de Recursos | **Criar novo grupo de recursos** |
    | Conta de armazenamento (Criar nova conta e usar um nome globalmente exclusivo (ex.: cloudshellstoragemystorage)) | **cloudshellxxxxxxx** |
    | Compartilhamento de arquivo (criar novo) | **shellstorage** |

5. Selecione **Criar Armazenamento**

# Tarefa 2: Criar um grupo de recursos e uma máquina virtual

Nesta tarefa, usaremos o PowerShell para criar um grupo de recursos e uma máquina virtual.  

1. Certifique-se de que o **PowerShell** esteja selecionado no menu suspenso superior esquerdo do painel do Cloud Shell.

2. Verifique o novo grupo de recursos executando os comandos a seguir na janela do PowerShell. Pressione **Enter** para executar o comando.

    ```PowerShell
    Get-AzResourceGroup | Format-Table
    ```

3. Crie uma máquina virtual colando o comando a seguir na janela do terminal. 

    ```PowerShell
    New-AzVm `
    -ResourceGroupName "myRGPS" `
    -Name "myVMPS" `
    -Location "East US" `
    -VirtualNetworkName "myVnetPS" `
    -SubnetName "mySubnetPS" `
    -SecurityGroupName "myNSGPS" `
    -PublicIpAddressName "myPublicIpPS"
    ```
    
4. Quando solicitado, insira o nome de usuário (**azureuser**) e a senha (**Pa$$w0rd1234**), que serão configurados como a conta de Administrador local nessas máquinas virtuais.

5. Quando a VM for criada, feche o painel Cloud Shell da sessão do PowerShell.

6. No portal do Azure, procure **Máquinas virtuais** e verifique se o **myVMPS** está em execução. Isso pode levar alguns minutos.

    ![Captura de tela da página de máquinas virtuais com myVMPS em estado de execução.](../images/1001.png)

7. Acesse a nova máquina virtual e analise a Visão geral e as configurações de rede para verificar se suas informações foram implantadas corretamente. 

# Tarefa 3: Executar comandos no Cloud Shell

Nesta tarefa, praticaremos a execução de comandos do PowerShell no Cloud Shell. 

1. No portal do Azure, abra o **Azure Cloud Shell** clicando no ícone no canto superior direito do portal do Azure.

2. Certifique-se de que o **PowerShell** esteja selecionado no menu suspenso superior esquerdo do painel do Cloud Shell.

3. Recupere informações sobre sua máquina virtual, incluindo nome, grupo de recursos, localização e status. Observe que o PowerState está **em execução**.

    ```PowerShell
    Get-AzVM -name myVMPS -status | Format-Table -autosize
    ```

4. Interrompa a máquina virtual usando o seguinte comando: 

    ```PowerShell
    Stop-AzVM -ResourceGroupName myRGPS -Name myVMPS
    ```
5. Quando solicitado, confirme (Sim) para a ação. Aguarde o status de **Êxito**.

6. Verifique o estado da sua máquina virtual. O PowerState agora deve ser **desalocado**. Você também pode verificar o status da máquina virtual no portal. Feche o Cloudshell.

    ```PowerShell
    Get-AzVM -name myVMPS -status | Format-Table -autosize
    ```

# Tarefa 4: Analisar recomendações do Assistente do Azure

**Observação:** Esta mesma tarefa está no laboratório Criar uma VM com a CLI do Azure. 

Nesta tarefa, revisaremos as recomendações do Assistente do Azure para nossa máquina virtual. 

1. Na folha **Todos os serviços**, procure e selecione **Assistente**. 

2. Na folha **Assistente**, selecione **Visão geral**. As recomendações de aviso são agrupadas por Alta disponibilidade, Segurança, Desempenho e Custo. 

    ![Captura de tela da página Visão geral do Assistente. ](../images/1003.png)

3. Selecione **Todas as recomendações** e reserve um tempo para ver cada recomendação e as ações sugeridas. 

    **Observação:** Dependendo de seus recursos, suas recomendações serão diferentes. 

    ![Captura de tela da página Todas as recomendações do Assistente. ](../images/1004.png)

4. Observe que você pode baixar as recomendações como um arquivo CSV ou PDF. 

5. E também pode criar alertas. 

6. Se você tiver tempo, continue experimentando o Azure PowerShell. 

Parabéns! Você configurou o Cloud Shell, criou uma máquina virtual usando o PowerShell, praticou com comandos do PowerShell e viu as recomendações do Advisor.

**Observação**: Para evitar custos adicionais, você tem a opção de remover este grupo de recursos. Procure grupos de recursos, clique em seu grupo de recursos e, em seguida, clique em **Excluir grupo de recursos**. Verifique o nome do grupo de recursos e clique em **Excluir**. Monitore as **Notificações** para ver como a exclusão está ocorrendo.
