---
wts:
    title: '20 – Usar o Azure TCO Calculator (10 min)'
    module: 'Módulo 06: Descreva o gerenciamento de custos do Azure e os acordos de nível de serviço'
---
# 20 – Usar o Azure TCO Calculator


Neste passo a passo, você usará a calculadora do custo total de propriedade (TCO) para gerar um relatório de comparação de custos para um ambiente local.

**Observação**: Este passo a passo fornece definições de exemplo de infraestrutura local e cargas de trabalho para um datacenter típico. Para criar um relatório da Calculadora do TCO, use as definições de exemplo ou forneça detalhes de sua infraestrutura local e cargas de trabalho *reais*.

# Tarefa 1: Configurar a calculadora de TCO (10 min)

Nesta tarefa, adicionaremos informações de infraestrutura à calculadora. 

1. Em um navegador, navegue até a página [Calculadora do custo total de propriedade (TCO)](https://azure.microsoft.com/pt-br/pricing/tco/calculator/).

2. Para adicionar detalhes de sua infraestrutura de servidor local, clique em **+ Adicionar carga de trabalho do servidor** no painel **Definir suas cargas de trabalho**.

    | Configurações | Valor |
    | -- | -- |
    | Nome | **Servidores: VMs do Windows** |
    | Carga de trabalho | **Servidor Windows/Linux** |
    | Ambiente | **Máquinas virtuais** |
    | Sistema operacional | **Windows** |  
    | VMs | **50** |
    | Virtualização | **Hyper-V** |
    | Núcleo(s) | **8**|
    | RAM (GB) | **16** |
    | Otimizar por | **CPU** |
    | Windows Server 2008/2008 R2 | **Desativado** |
    | | |

3. Selecione **+ Adicionar carga de trabalho do servidor** para criar uma linha para uma nova definição de carga de trabalho do servidor. 

    | Configurações | Valor |
    | -- | -- |
    | Nome | **Servidores: VMs Linux** |
    | Carga de trabalho | **Servidor Windows/Linux** |
    | Ambiente | **Máquinas virtuais** |
    | Sistema operacional | **Linux** |  
    | VMs | **50** |
    | Virtualização | **VMware** |
    | Núcleo(s) | **8**|
    | RAM (GB) | **16** |
    | Otimizar por | **CPU** |
    | Windows Server 2008/2008 R2 | **Desativado** |
    | | |

4. No painel **Armazenamento**, clique em **Adicionar armazenamento**.

    | Configurações | Valor |
    | -- | -- |
    | Nome | **Armazenamento de servidor** |
    | Tipo de armazenamento | **Disco Local/SAN** |
    | Tipo de disco | **HD** |
    | Capacidade | **60 TB** |  
    | Backup | **120 TB** |
    | Arquivar | **0 TB** |
    | | |

5. No painel **Rede**, adicione largura de banda. 

    | Configurações | Valor |
    | -- | -- |
    | Largura de banda de saída | 15 TB|
    | | |

6. Clique em **Próximo**.

7. Explore as opções e faça os ajustes necessários. 

    | Configurações | Valor |
    | -- | -- |
    | Moeda | **Euro** |
    | | |

8. Clique em **Próximo**.

# Tarefa 2: Revisar os resultados e salvar uma cópia

Nesta tarefa, revisaremos as recomendações de redução de custos e faremos o download de um relatório. 

1. Revise as recomendações e visualizações de economia de custos do Azure.

    | Configurações | Valor |
    | -- | -- |
    | Prazo| **3 anos** |
    | Região | **Norte da Europa** |
    | | |


2. Para modificar as informações fornecidas, vá até o final da página e clique em **Voltar**. 

3. Para salvar ou imprimir uma cópia em PDF do relatório, clique em **Baixar**.

    ![Captura de tela do painel de relatório da calculadora do TCO no Azure. Os campos de entrada destacados e preenchidos indicam como definir o prazo da calculadora do TCO para três anos e a região para o Norte da Europa. Um grafo mostra o custo da infraestrutura local e o deslocamento das cargas de trabalho em relação ao custo reduzido de uso do Azure.](../images/2001.png)

Parabéns! Você usou a Calculadora do TCO para gerar um relatório de comparação de custos para um ambiente local.
