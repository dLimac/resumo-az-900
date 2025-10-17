# ☁️ Estudo AZ-900 – Fundamentos de Computação em Nuvem

## 🌐 Conceito de Nuvem

A **computação em nuvem** é o fornecimento de **serviços de computação pela internet** (“a nuvem”), incluindo servidores, armazenamento, bancos de dados, redes, software, análise e inteligência.  
Ela permite **inovações mais rápidas**, **recursos flexíveis** e **economias de escala**.  
Em vez de possuir sua própria infraestrutura de TI ou data center, as organizações podem **alugar acesso a serviços de nuvem** conforme necessário.

---

## ☁️ Modelos de Nuvem

Os modelos de implantação definem **como** e **onde** os recursos de nuvem são hospedados.  
Existem quatro principais modelos:

### 🏢 Nuvem Privada
- A infraestrutura é usada **exclusivamente por uma única organização**.
- Pode estar **localmente no datacenter da empresa** ou hospedada por um provedor terceirizado.
- Oferece **maior controle e segurança**, mas exige **maior custo e gerenciamento**.

### 🌍 Nuvem Pública
- A infraestrutura pertence a um **provedor de nuvem** (como Microsoft Azure, AWS ou Google Cloud).
- Recursos são **compartilhados entre vários clientes**, isolados logicamente.
- Oferece **alta escalabilidade**, **pagamento conforme o uso** e **menor custo inicial**.

### 🔄 Nuvem Híbrida
- Combina **nuvens públicas e privadas**, permitindo que dados e aplicativos sejam **compartilhados entre elas**.
- Ideal para **migrações graduais**, **flexibilidade operacional** e **resiliência**.
- Oferece o **melhor dos dois mundos**, mas com **complexidade de gerenciamento**.

### ☁️☁️ Multicloud
- Uso de **múltiplos provedores de nuvem pública** simultaneamente (ex: Azure + AWS + GCP).
- Permite **evitar dependência de um único provedor (vendor lock-in)**.
- Aumenta a **resiliência** e **flexibilidade**, mas **eleva a complexidade operacional**.

---

## 💰 Modelos de Despesa

A computação em nuvem introduz diferentes formas de gerenciar custos:

### 🏗️ CapEx (Capital Expenditure)
- **Gasto de capital**: investimento inicial em infraestrutura física (servidores, datacenters, hardware).
- Custos fixos e altos no início.
- Vantagem: controle total sobre os recursos.
- Desvantagem: menor flexibilidade e necessidade de manutenção constante.

### 🔁 OpEx (Operational Expenditure)
- **Gasto operacional**: pagamento por produtos e serviços **conforme o uso**.
- Modelo baseado em **assinatura ou consumo** (ex: pagar apenas pelo tempo de uso de um servidor virtual).
- Vantagem: **flexibilidade**, **escalabilidade** e **custos variáveis**.
- Desvantagem: custos podem aumentar dependendo do uso.

---

## 🧩 Comparativo entre Modelos de Nuvem

| Modelo        | Controle | Custo Inicial | Escalabilidade | Segurança | Exemplo de Uso |
|----------------|-----------|----------------|----------------|------------|----------------|
| Privada        | Alto      | Alto           | Limitada       | Alta       | Bancos, governo |
| Pública        | Baixo     | Baixo          | Alta           | Média      | Startups, SaaS |
| Híbrida        | Médio     | Médio          | Alta           | Alta       | Empresas em transição |
| Multicloud     | Médio     | Médio          | Alta           | Alta       | Corporações globais |

---
### ☁️ Criação de máquina virtual

Resumo baseado no [artigo oficial da Microsoft Learn](https://learn.microsoft.com/pt-br/azure/virtual-machines/windows/quick-create-portal).

Este guia rápido mostra como usar o portal do Azure para implantar uma máquina virtual (VM) executando o Windows Server.

### 1. Entrar no Azure

1.  Acesse o [portal do Azure](https://portal.azure.com).

### 2. Criar a Máquina Virtual

1.  Na barra de pesquisa do portal, digite **máquinas virtuais**.
2.  Em **Serviços**, selecione **Máquinas virtuais**.
3.  Na página **Máquinas virtuais**, clique em **Criar** e selecione **Máquina virtual do Azure**.
4.  Na guia **Básico**, configure:
    * **Grupo de Recursos:** Crie um novo (ex: `myResourceGroup`).
    * **Nome da máquina virtual:** Dê um nome (ex: `myVM`).
    * **Região:** Escolha a região desejada.
    * **Imagem:** Selecione uma imagem (ex: `Windows Server 2022 Datacenter: Azure Edition - x64 Gen 2`).
    * **Tamanho:** Escolha um tamanho de VM (o padrão de custo mais baixo geralmente é sugerido).
5.  Em **Conta de administrador**:
    * Defina um **Nome de usuário** (ex: `azureuser`).
    * Crie uma **Senha** (deve ter no mínimo 12 caracteres e atender aos requisitos de complexidade).
6.  Em **Regras de porta de entrada**:
    * Escolha **Permitir portas selecionadas**.
    * Selecione **RDP (3389)** e **HTTP (80)** na lista suspensa.
7.  Clique em **Examinar + criar** na parte inferior da página.
8.  Após a validação, clique em **Criar**.

### 3. Conectar-se à Máquina Virtual (via RDP)

1.  Após a conclusão da implantação, vá para o recurso da VM.
2.  Na página de visão geral, selecione **Conectar** > **RDP**.
3.  Na guia **Conectar-se ao RDP**, mantenha as opções padrão e clique em **Baixar arquivo RDP**.
4.  Abra o arquivo `.rdp` baixado.
5.  Clique em **Conectar**.
6.  Na janela de Segurança do Windows, selecione **Mais opções** e **Usar uma conta diferente**.
7.  Digite o nome de usuário (ex: `localhost\azureuser`) e a senha que você criou.
8.  Clique em **Sim** no aviso do certificado para criar a conexão.

### 4. (Opcional) Instalar o servidor Web (IIS)

Para verificar se a VM está respondendo via HTTP:

1.  Dentro da VM, abra um prompt do **PowerShell**.
2.  Execute o seguinte comando:
    ```powershell
    Install-WindowsFeature -name Web-Server -IncludeManagementTools
    ```
3.  Após a instalação, abra um navegador (no seu computador local) e digite o **Endereço IP público** da sua VM. Você verá a página de boas-vindas padrão do IIS.

### 5. Limpar os Recursos

Quando não precisar mais da VM, exclua o grupo de recursos para evitar cobranças contínuas.

1.  No portal, vá até o **Grupo de Recursos** que você criou.
2.  Selecione **Excluir grupo de recursos**.
3.  Digite o nome do grupo de recursos para confirmar e clique em **Excluir**.

> 💡 *Este repositório tem como objetivo registrar e organizar meus estudos sobre os fundamentos do Microsoft Azure e a certificação AZ-900.*
