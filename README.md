# SQL-do-Azure
Criar Instância Gerenciada de SQL do Azure

Este guia mostra como provisionar uma **Instância Gerenciada de SQL do Azure** diretamente pelo **Portal do Azure**, sem necessidade de scripts ou ferramentas de linha de comando.

---

## 🛠️ Pré‑requisitos

- **Assinatura do Azure** (ou [conta gratuita](https://azure.microsoft.com/free)) :contentReference[oaicite:0]{index=0}  
- **Permissão**: função **Contribuidor** no escopo da assinatura ou do grupo de recursos alvo :contentReference[oaicite:1]{index=1}  
- **Rede Virtual** com **sub‑rede delegada** a `Microsoft.Sql/managedInstances` (exercite cuidado para não ter outras operações em andamento nesta sub‑rede) :contentReference[oaicite:2]{index=2}  
- Navegador atualizado para acessar o [Portal do Azure](https://portal.azure.com) :contentReference[oaicite:3]{index=3}  

---

## 🚀 Criar Instância Gerenciada de SQL (Portal)

1. **Entrar no Portal**  
   Acesse https://portal.azure.com e autentique-se com sua conta.

2. **Navegar até SQL do Azure**  
   No menu à esquerda, clique em **SQL do Azure**.  
   > Caso não encontre, selecione **Todos os serviços** e pesquise por “SQL do Azure”. :contentReference[oaicite:4]{index=4}

3. **Iniciar criação**  
   Clique em **+ Criar**, escolha **Instâncias gerenciadas de SQL** e depois **Criar**. :contentReference[oaicite:5]{index=5}

4. **Guia Básico – Informações Obrigatórias**  
   Preencha os campos mínimos:  
   
   | Configuração                            | Descrição                                                    |
   |-----------------------------------------|--------------------------------------------------------------|
   | **Assinatura**                          | Sua assinatura do Azure.                                     |
   | **Grupo de recursos**                   | Novo ou existente.                                           |
   | **Nome da instância**                   | Nome válido conforme [nomenclatura](https://aka.ms/azuresql-rn). |
   | **Região**                              | Região desejada (ex: `eastus2`).                             |
   | **Método de autenticação**              | Selecione **SQL** (usuário e senha).                         |
   | **Login de administrador**              | Qualquer nome (mínimo de 16 caracteres na senha).            |
   | **Senha**                               | Atenda aos requisitos de complexidade.                       |
   
   :contentReference[oaicite:6]{index=6}

5. **Computação + Armazenamento**  
   Clique em **Configurar instância gerenciada** e defina:  
   - **Camada de serviço**: Uso Geral (GP)  
   - **Geração do hardware**: Gen5  
   - **vCores**: 8 (padrão)  
   - **Armazenamento**: 256 GB (ou conforme necessidade) :contentReference[oaicite:7]{index=7}  
   Clique em **Aplicar**.

6. **Guia Rede**  
   - **Rede Virtual / Sub‑rede**: selecione a VNet e a sub‑rede delegada.  
   - **Ponto de extremidade público**: **Desabilitar** (recomendado) ou habilitar e restringir acesso posteriormente.  
   - **Permitir acesso de**: **Sem acesso** se ponto de extremidade público estiver habilitado. :contentReference[oaicite:8]{index=8}

7. **Guia Segurança e Configurações Adicionais**  
   Deixe as opções em padrão ou ajuste conforme políticas internas (ordenamento, fuso‑horário, janelas de manutenção, tags etc.). :contentReference[oaicite:9]{index=9}

8. **Revisar e Criar**  
   Na aba **Revisar + criar**, verifique todas as configurações e clique em **Criar**.  

9. **Monitorar implantação**  
   Abra o ícone **Notificações** no canto superior direito e selecione a operação em andamento para acompanhar o progresso. :contentReference[oaicite:10]{index=10}  

10. **Verificar recurso criado**  
    Após a conclusão (30–60 min), vá ao **Grupo de Recursos** e confirme se a Instância Gerenciada de SQL aparece listada.

---

## 📄 Observações

- A criação pode demorar até **60 minutos**, dependendo de outras operações na sub‑rede :contentReference[oaicite:11]{index=11}  
- Se precisar abortar o processo, use o comando **Cancelar** na notificação ou no próprio bloco de implantação :contentReference[oaicite:12]{index=12}  
- Para migrar bancos de dados, configure **Conexão Privada** e **Regras de Firewall/NSG** após a implantação  

---

## 🔗 Referência

- Microsoft Learn: **Início Rápido – Criar Instância Gerenciada de SQL do Azure (Portal)** :contentReference[oaicite:13]{index=13}  
