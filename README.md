
## 👩‍🔬 Persona

**Nome:** Ana Souza  
**Cargo:** Técnica de laboratório – Fatec Jacareí  
**Objetivo:** Acompanhar a temperatura das estufas e reagir rapidamente a qualquer variação fora do padrão.  
**Dificuldade:** Nem sempre está no campus; depende do app e dos alertas para agir.

---

## 🧭 Fluxo de Usuário

### 1. Acesso ao Aplicativo
- Ana abre o aplicativo no celular.
- Faz login (usuário e senha ou autenticação Fatec).

**Decisão alternativa:**  
Se o celular estiver sem conexão com a internet, o app exibe:

> “Sem conexão. Exibindo os últimos dados armazenados.”  

E mostra as informações mais recentes em modo offline (somente leitura).

---

### 2. Tela Inicial – Visão Geral das Estufas
- O app exibe as duas estufas com:
  - Temperatura atual (ou última leitura)
  - Indicadores de status
  - Última atualização  

Ana toca em "Estufa 1" para visualizar detalhes.

---

### 3. Tela de Detalhes da Estufa
- Exibe gráfico com a variação de temperatura ao longo do tempo.
- Mostra os limites definidos e botões para alterar.

**Decisão alternativa:**  
Se não há dados recentes (ex: sensor perdeu a conexão), aparece:

> “Aviso: Sensor da Estufa 1 sem comunicação há 2h.”

Ana pode escolher:
- **Tentar atualizar agora** → O app envia uma requisição manual.
- **Manter dados anteriores** → Continua visualizando o histórico.

---

### 4. Configuração de Limites
- Ana ajusta os limites (ex: Mín: 18°C / Máx: 30°C).
- O app envia a nova configuração ao servidor.

**Decisão alternativa:**  
Se a conexão falhar durante o envio, o app salva a configuração localmente e tenta reenviar assim que a internet voltar.

---

### 5. Recebimento de Alertas
- Quando a temperatura excede os limites, o sistema envia **SMS** automaticamente.
- Ana recebe a notificação:

> “Estufa 2 — Temperatura crítica: 34°C às 02:15.”

Ela clica no link para abrir o app e verificar a causa.

---

### 6. Consulta de Histórico
- Ana acessa o histórico do experimento.
- Pode filtrar por datas e gerar gráficos comparativos.
- Exporta relatório em PDF para a disciplina.

---

### 7. Encerramento
- Ana encerra a sessão.
- O sistema continua coletando dados automaticamente na nuvem.

---

## 🗺️ Fluxo Visual Simplificado
Início / App aberto  
↓  

Login  
↓  

Conexão disponível?  
┌───────┐  
│ Sim │ Não │  
↓       ↓  
Tela Inicial   Modo Offline (últimos dados)  
↓  

Selecionar Estufa  
↓  

Sensor enviando dados?  
┌───────┐  
│ Sim │ Não │  
↓       ↓  
Ver Gráfico   Aviso: Sensor offline  
↓  

Configurar Limites  
↓  

Salvar Limites (online ou offline)  
↓  

Receber alerta SMS se exceder limite  
↓  

Consultar histórico / Exportar dados  
↓  

Encerrar sessão


# Relação entre Fluxo de Usuário e Mapa de Jornada

Abaixo, cada etapa do **fluxo de usuário** está associada às colunas do **Mapa de Jornada**:  
1. **Etapas**  
2. **Ações da Ana (Usuária)**  
3. **Pontos de Contato (Sistema/App)**  
4. **Emoções / Experiência**  
5. **Oportunidades de Melhoria**

---

| Etapa do Fluxo de Usuário | Ações da Ana (Usuária) | Pontos de Contato (Sistema/App) | Emoções e Experiência | Oportunidades / Melhorias |
| --- | --- | --- | --- | --- |
| **1. Acesso ao App e Login** | Abre o app, faz login e acessa as estufas. | Tela de login, autenticação Firebase. | Espera praticidade e rapidez; frustração se a internet estiver instável. | Implementar login offline temporário e autenticação automática. |
| **2. Visualização Geral das Estufas** | Observa status atual (temperatura e alerta). | Dashboard inicial com indicadores coloridos. | Sensação de controle e confiança; tranquilidade ao ver tudo “normal”. | Incluir gráficos simplificados ou alertas visuais no dashboard. |
| **3. Decisão Alternativa – Sem Conexão Wi-Fi** | App informa “Sem conexão. Exibindo últimos dados”. | Modo offline do app. | Frustração inicial, mas alívio ao poder ver dados antigos. | Mostrar tempo da última atualização e opção “tentar novamente”. |
| **4. Visualizar Detalhes da Estufa** | Clica na estufa e analisa gráfico e limites. | Tela de gráfico, API de dados da nuvem. | Curiosidade e interesse em ver o histórico. | Permitir ampliar o gráfico e comparar dias. |
| **5. Ajustar Limites de Temperatura** | Configura novos limites (ex: 18–30 °C). | Tela de configuração e salvamento no servidor. | Sente-se responsável pelo controle; preocupação em acertar os valores. | Oferecer sugestões automáticas baseadas em médias anteriores. |
| **6. Receber Alerta SMS (Fluxo Paralelo)** | Recebe SMS “Temperatura crítica: 34 °C”. | Serviço Twilio / AWS SNS + app. | Alerta e urgência — reação imediata. | Incluir link direto no SMS para abrir o app no gráfico da estufa. |
| **7. Consultar Histórico e Gerar Relatório** | Acessa dados de períodos passados. | Tela de histórico, banco de dados na nuvem. | Satisfação e segurança ao visualizar dados completos. | Adicionar exportação em PDF e compartilhamento direto. |
| **8. Encerrar Sessão / Finalizar Uso** | Fecha o app; coleta continua automática. | Logout ou fechamento automático. | Tranquilidade por saber que o sistema segue monitorando. | Enviar breve resumo semanal por e-mail. |

---

## Como o Fluxo e a Jornada se Conectam

- **O Fluxo de Usuário** mostra o _“o que Ana faz”_ — as ações concretas dentro do app e do sistema.  
- **O Mapa de Jornada** mostra o _“como Ana vive isso”_ — suas emoções, expectativas e dificuldades em cada passo.  
- **A Conexão:** cada **etapa do fluxo** corresponde a uma **fase da jornada**, onde os _pontos de contato_ (app, SMS, nuvem) moldam a experiência emocional da usuária.

**Exemplo de conexão prática:**

> Fluxo: “Receber alerta por SMS”  
> Jornada: “Momento de tensão → sistema precisa responder rápido e claramente.”  
> Melhoria: Incluir link direto no SMS para abrir o gráfico da estufa.


# Sistema de Monitoramento de Temperatura das Estufas – Fatec Jacareí

Este projeto descreve um sistema de monitoramento contínuo de temperatura em estufas laboratoriais, com envio de alertas automáticos e histórico de dados acessível via aplicativo mobile.

---

## 🔍 Escolha do Fluxo

O fluxo mais central do sistema representa a rotina principal da usuária **Ana Souza**:

> **Fluxo: Monitorar temperatura e configurar limites das estufas**  
> Inclui login, visualização de dados, alertas e ajustes de limites.

---

## 🧭 Fluxo Escolhido
1. Acessar o aplicativo e fazer login  
2. Visualizar a temperatura geral das estufas  
3. Selecionar uma estufa específica  
4. Consultar gráfico e detalhes  
5. Ajustar limites de temperatura  
6. Receber alerta (SMS ou notificação)  
7. Consultar histórico  
8. Encerrar sessão  

---

## 📱 Telas Necessárias para o Fluxo

| Nº | Nome da Tela | Descrição / Função Principal | Elementos Importantes |
| --- | --- | --- | --- |
| 1 | Tela de Splash / Abertura | Exibe o logotipo da Fatec e inicializa o app | Logo, carregamento, verificação de login automático |
| 2 | Tela de Login / Autenticação | Permite login com e-mail/senha ou conta Google/Fatec | Campos de login, botão “Entrar”, link “Esqueci a senha” |
| 3 | Tela de Cadastro (opcional) | Novo usuário se registra (professores/técnicos) | Formulário com nome, e-mail, senha |
| 4 | Tela Principal / Dashboard | Mostra todas as estufas e seus status em tempo real | Cartões de estufas (Temperatura atual, status, último envio) |
| 5 | Tela de Detalhes da Estufa | Exibe gráfico de variação da temperatura | Gráfico de linha, temperatura atual, botão “Configurar limites” |
| 6 | Tela de Configuração de Limites | Usuária ajusta temperatura mínima e máxima | Campos numéricos, botão “Salvar”, aviso de sucesso/falha |
| 7 | Tela de Histórico | Permite visualizar dados anteriores e exportar relatório | Filtros de data, gráfico resumido, botão “Exportar PDF” |
| 8 | Tela de Alerta / Notificação (popup) | Mostra aviso de temperatura fora do limite | Mensagem “Temperatura crítica”, botão “Ver detalhes” |
| 9 | Tela de Falha de Conexão (Modo Offline) | Exibida se o app estiver sem internet | Mensagem “Sem conexão”, botão “Tentar novamente” |
| 10 | Tela de Perfil / Configurações | Exibe dados da conta e permite logout | Nome, e-mail, botão “Sair”, preferências de alerta (SMS, push) |

---

# 🗺️ Resumo Visual das Conexões entre as Telas

[Splash]
↓
[Login] → [Cadastro]
↓
[Dashboard]
↓
[Detalhes da Estufa]
↓
[Configurar Limites]
↓
[Histórico]
↓
[Perfil / Logout]

Fluxos paralelos:

[Alerta SMS] → abre [Detalhes da Estufa]

[Modo Offline] → exibe [Falha de Conexão]


---

# 📱 Telas do Aplicativo

## 1️⃣ Tela de Login

**Objetivo:** Permitir o acesso seguro da usuária Ana ao aplicativo.



-------------------------------------
|   🌱 Fatec Jacareí - Estufas IoT  |
|-----------------------------------|
|        [Ícone do Sistema]         |
|                                   |
|  E-mail: [_____________________]  |
|  Senha: [_____________________]   |
|                                   |
|   [Entrar]                        |
|                                   |
|  Esqueceu a senha? [Recuperar]   |
|-----------------------------------|
|  Ou entrar com: [Google Icon]     |
-------------------------------------


Elementos-chave:

Campos de login

Botão “Entrar”

Acesso alternativo (Google)

Link para recuperação de senha

Ação principal: Entrar no sistema → vai para o Dashboard.

## 2️⃣ Tela Principal (Dashboard)

Objetivo: Mostrar o estado atual das estufas em tempo real.

-------------------------------------
|  🌡️  Monitoramento de Estufas     |
|-----------------------------------|
| Estufa 1                          |
| Temperatura: 27.5°C               |
| Status: 🟢 Dentro do limite        |
| Última atualização: 10:42         |
| [Ver detalhes]                    |
|-----------------------------------|
| Estufa 2                          |
| Temperatura: 33.2°C               |
| Status: 🔴 Acima do limite!       |
| Última atualização: 10:40         |
| [Ver detalhes]                    |
|-----------------------------------|
| [Histórico]   [Perfil]           |
-------------------------------------


Elementos-chave:

Cartões com dados de cada estufa

Indicador visual (verde/vermelho)

Acesso rápido a detalhes e histórico

Ação principal: Escolher uma estufa → abre Tela de Detalhes da Estufa.

## 3️⃣ Tela de Detalhes da Estufa

Objetivo: Visualizar gráfico de temperatura e configurar limites.

-------------------------------------
|  🌡️ Estufa 1 - Detalhes          |
|-----------------------------------|
| Temperatura atual: 27.5°C         |
| Limites: 18°C - 30°C              |
|-----------------------------------|
| 📊  [Gráfico de linha da temp.]   |
|     dia 1    dia 2    dia 3       |
|-----------------------------------|
| [Configurar Limites]              |
| [Histórico Completo]              |
|-----------------------------------|
| ⚠️ Alerta recente: Nenhum         |
|-----------------------------------|
| [Voltar]                          |
-------------------------------------


Elementos-chave:

Gráfico de variação da temperatura (últimas 24h)

Dados atuais e limites

Botão para alterar limites

Ação principal: Ajustar os limites → abre Tela de Configuração de Limites.

## 4️⃣ Tela de Configuração de Limites

Objetivo: Permitir que Ana defina faixas seguras de temperatura.

-------------------------------------
|  ⚙️ Configurar Limites - Estufa 1 |
|-----------------------------------|
| Temperatura mínima: [__18__] °C   |
| Temperatura máxima: [__30__] °C   |
|                                   |
| [Salvar alterações]               |
|-----------------------------------|
| Dica: valores ideais entre 18°C e 30°C. |
|-----------------------------------|
| [Cancelar]                        |
-------------------------------------


Elementos-chave:

Campos numéricos editáveis

Botão “Salvar alterações”

Mensagem de ajuda

Ação principal: Salvar → retorna para Detalhes da Estufa com os novos limites aplicados.

🔗 Conexão entre as Telas
[Login] 
    ↓
[Dashboard] 
    ↓
[Detalhes da Estufa] 
    ↓
[Configurar Limites]


Fluxos secundários:

[Dashboard] → [Histórico]

[Dashboard] → [Perfil]

[SMS de alerta] → [Detalhes da Estufa]

---

Validação das Telas com Base na Persona

## 1️⃣ Tela de Login

Avaliação:

A tela é simples, clara e direta — adequada para Ana, que busca praticidade.

O login por e-mail e senha é familiar, e o acesso via Google reduz barreiras.

Texto “Esqueceu a senha?” evita frustrações em caso de esquecimento.

Sugestões:

✅ Adicionar login automático (lembrar usuário), pois Ana acessará o app com frequência.

✅ Incluir feedback de conexão (ex: “Sem internet – tente novamente”).

Veredito: Aprovada — interface intuitiva e adequada ao contexto da usuária.

## 2️⃣ Tela Principal (Dashboard)

Avaliação:

Apresenta as duas estufas com informações essenciais (temperatura, status e hora da última atualização).

O uso de cores (verde/vermelho) facilita a leitura rápida — ideal para quem quer um panorama imediato.

Botões de “Ver detalhes” permitem fácil navegação.

Sugestões:

✅ Mostrar ícone de alerta ativo (🔔) se houver algum aviso pendente.

✅ Indicar claramente se os dados são atuais ou offline (“Última atualização há X minutos”).

Veredito: Aprovada com ajustes leves — cumpre o papel de visão geral e status rápido.

## 3️⃣ Tela de Detalhes da Estufa

Avaliação:

Exibe dados atuais e gráfico histórico — ótimo para análise de variação.

Botão “Configurar limites” bem localizado, coerente com a necessidade de ajuste rápido.

A presença do gráfico de linha ajuda Ana a visualizar tendências, não apenas números isolados.

Sugestões:

✅ Garantir que o gráfico seja legível em tela pequena (mobile).

✅ Adicionar botão “Atualizar agora” para forçar leitura instantânea, útil se Ana suspeitar de falha no sensor.

Veredito: Aprovada — atende às necessidades analíticas e operacionais da persona.

## 4️⃣ Tela de Configuração de Limites

Avaliação:

Campos simples e diretos — Ana pode alterar valores sem esforço.

Mensagem de dica (“valores ideais entre 18°C e 30°C”) ajuda usuários menos técnicos.

Fluxo de retorno automático após salvar evita navegação confusa.

Sugestões:

✅ Exibir confirmação visual após salvar (ex: “✔️ Limites atualizados com sucesso”).

✅ Mostrar aviso se valores forem incoerentes (ex: mínima maior que máxima).

Veredito: Aprovada — cumpre o papel funcional de forma clara e sem sobrecarga.

| **Etapa do Fluxo de Usuário**                  | **Tela Correspondente**                    | **Descrição / Função da Tela**                                                        | **Objetivo para a Persona (Ana Souza)**                                                  |
| ---------------------------------------------- | ------------------------------------------ | ------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| **1️⃣ Fazer login no aplicativo**              | 🟩 **Tela de Login**                       | Campos de e-mail e senha, botão “Entrar”, opção de login rápido (Google/Fatec).       | Permitir que Ana acesse rapidamente o sistema sem complicações.                          |
| **2️⃣ Visualizar as estufas e seus status**    | 🟦 **Tela Principal (Dashboard)**          | Lista das estufas com temperatura atual, status (🟢🟥), e hora da última atualização. | Dar uma visão geral imediata das condições das estufas.                                  |
| **3️⃣ Acessar os detalhes de uma estufa**      | 🟨 **Tela de Detalhes da Estufa**          | Mostra gráfico de variação, temperatura atual e limites configurados.                 | Permitir que Ana analise o comportamento térmico da estufa ao longo do tempo.            |
| **4️⃣ Ajustar limites de temperatura**         | 🟧 **Tela de Configuração de Limites**     | Campos para definir temperatura mínima e máxima + botão “Salvar alterações”.          | Permitir ajustes rápidos e garantir segurança dos experimentos.                          |
| **5️⃣ Receber alertas automáticos (paralelo)** | 🟥 **Tela de Alerta / SMS de Notificação** | Exibe mensagem “⚠️ Temperatura fora do limite!” e link direto para a estufa.          | Notificar Ana imediatamente sobre variações críticas, mesmo fora do horário de trabalho. |
| **6️⃣ Consultar histórico (opcional)**         | 🟪 **Tela de Histórico**                   | Gráficos com médias e variações ao longo de dias/semanas.                             | Acompanhar o comportamento térmico durante todo o experimento.                           |
| **7️⃣ Encerrar sessão / sair do app**          | ⚪ **Tela de Perfil / Configurações**       | Exibe dados da conta, opções de alerta e botão “Sair”.                                | Permitir que Ana finalize o uso do app com segurança e personalize preferências.         |
