---
wts:
    title: '12 – Implementar Azure Key Vault (5 min)'
    module: 'Módulo 04: Descreva a segurança geral e os recursos de segurança da rede'
---
# 12 – Implantar o Azure Key Vault (5 min)

Neste passo a passo, criaremos um Azure Key Vault e, em seguida, criaremos um segredo de senha dentro desse cofre de chaves, fornecendo uma senha armazenada com segurança e gerenciada centralmente para uso com aplicativos.

# Tarefa 1: Criar um Azure Key Vault 

1. Entre no [portal do Azure](https://portal.azure.com).

2. Na folha **Todos os serviços**, procure e selecione **Cofres de chaves** e, em seguida, selecione **+Adicionar +Novo +Criar**.

3. Configure o cofre de chaves (substitua **xxxx** no nome do cofre de chaves por letras e dígitos de forma que o nome seja globalmente exclusivo). Mantenha os padrões para todo o resto.

    | Configuração | Valor | 
    | --- | --- |
    | Assinatura | **Use a padrão fornecida** |
    | Grupo de recursos | **Criar novo grupo de recursos** |
    | Nome do cofre de chaves | **keyvaulttestxxx** |
    | Local | **Leste dos EUA** |
    | Tipo de preço | **Standard** |
    
    **Observação** substitua **xxxx** para ter um nome exclusivo.
4. Clique em **Revisar + criar** e, em seguida, clique em **Criar**. 

5. Depois que o novo cofre de chaves for provisionado, clique em **Ir para o recurso**. Ou você pode localizar seu novo cofre de chaves procurando por ele. 

6. Selecione a guia **Visão geral** do cofre de chaves e anote o **URI do Cofre**. Os aplicativos que usam o cofre por meio de APIs REST vão precisar desse URI.

7. Reserve um momento para navegar por algumas das outras opções de cofre de chaves. Em **Configurações**, revise **Chaves**, **Segredos**, **Certificados**, **Políticas de Acesso**, **Firewalls e redes virtuais**.

    **Observação**: Sua conta do Azure é a única autorizada a realizar operações neste novo cofre. Você pode modificar isso se desejar nas **Configurações** e, em seguida, na seção **Políticas de acesso**.

# Tarefa 2: Adicionar um segredo ao cofre de chaves
        
Nesta tarefa, adicionaremos uma senha ao cofre de chaves. 

1. Em **Configurações**, clique em **Segredos** e, em seguida, clique em **+ Gerar/Importar**.

2. Configure o segredo. Mantenha os outros valores com seus padrões. Observe que você pode definir uma data de ativação e de validade. Observe que você também pode desabilitar o segredo.

    | Configuração | Valor | 
    | --- | --- |
    | Opções de upload | **Manual** |
    | Nome | **ExamplePassword** |
    | Valor | **hVFkk96** |

3. Clique em **Criar**.

4. Assim que o segredo tiver sido criado com sucesso, clique em **ExamplePassword** e observe que ele tem o status **Habilitado**

5. Selecione o segredo que acabou de criar e observe o **Identificador de Segredo**. Este é o valor de URL que agora você pode usar com aplicativos. Ele fornece uma senha gerenciada centralmente e armazenada com segurança. 

6. Clique no botão **Mostrar valor secreto** para exibir a senha que você especificou anteriormente.


Parabéns! Você criou um Azure Key Vault e, em seguida, criou um segredo de senha nesse cofre de chaves, fornecendo uma senha armazenada com segurança e gerenciada centralmente para uso com aplicativos.

**Observação**: Para evitar custos adicionais, você tem a opção de remover este grupo de recursos. Procure grupos de recursos, clique em seu grupo de recursos e, em seguida, clique em **Excluir grupo de recursos**. Verifique o nome do grupo de recursos e clique em **Excluir**. Monitore as **Notificações** para ver como a exclusão está ocorrendo.
