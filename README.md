# HMTL---CHARGER

# ⚡ Lumos — Plataforma de Mobilidade Elétrica Sustentável

> **FIAP Global Solution 2026 — Equipe Lumos**

| Nome | RM |
|------|----|
| Pietro Lorande da Silva | 569125 |
| Gustavo Bonamico Piccoli | 569984 |
| Maria Eduarda Medeiros Lemos | 574094 |
| Ana Beatriz Berbel Marini | 574176 | 
| Julian Nayde Moncoski | 572603 | 
| Marcelo Francisco Josafá Ribeiro Martins | 573905 |

---

##  Sobre o Projeto

O **Lumos** é uma plataforma web de mobilidade elétrica sustentável que conecta motoristas de veículos elétricos a uma rede de totens de carregamento alimentados por energia solar. A proposta central é democratizar o acesso ao carregamento limpo, barato e inteligente no Brasil — com tarifas dinâmicas baseadas na disponibilidade de energia solar em tempo real, sistema de créditos pré-pagos e relatórios de impacto ambiental verificáveis.

A plataforma é dividida em dois produtos complementares:

- **Lumos Consumer** — interface para motoristas individuais (o site principal)
- **Lumos Corp / Fleet API** — dashboard e API B2B para gestão de frotas corporativas elétricas

---

##  Estrutura do Site

O projeto é composto por **7 páginas HTML** independentes, todas em HTML/CSS/JavaScript puro (sem frameworks), com design system unificado e navegação por `localStorage`.

```
index.html          → Tela de login / cadastro
home.html           → Dashboard principal do usuário
carregamento.html   → Fluxo de iniciação de recarga
pagamento.html      → Gestão de créditos e métodos de pagamento
consumo.html        → Histórico e gráficos de consumo energético
sustentabilidade.html → Impacto ambiental e calculadora de CO₂
lummi.html          → Chat com a IA assistente Lummi
corp.html           → Portal corporativo Lumos Corp
```

---

##  Páginas — O que cada uma faz

### `index.html` — Login / Cadastro
Ponto de entrada da plataforma. O usuário cria uma conta ou faz login. Os dados são persistidos em `localStorage` (`lm_user`, `lm_credits`, `lm_sessions`). Após login, é redirecionado para o `home.html`. Páginas protegidas verificam a sessão e redirecionam de volta caso não haja usuário autenticado.

---

### `home.html` — Dashboard
Tela central após o login. Exibe:
- Saudação personalizada com o nome do usuário
- Card de status da sessão de carregamento ativa (quando houver)
- Histórico resumido das últimas sessões de recarga
- Ações rápidas: **Iniciar Recarga**, **Pagamento**, **Consumo**
- Navegação para todas as seções da plataforma
- Acesso rápido ao portal **Lumos Corp**

---

### `carregamento.html` — Fluxo de Recarga
Guia o motorista pelo processo de iniciar uma sessão de carregamento em 3 etapas (step indicator visual):

1. **Escolha do pagamento** — Créditos Lumos, PIX, Cartão NFC, Boleto ou TAG Sem Parar
2. **Processamento** — animação de loading contextual por método de pagamento (QR Code para PIX, card 3D para cartão, etc.)
3. **Recarga em andamento** — barra de progresso animada, consumo em kWh e R$ em tempo real
4. **Conclusão** — confirmação com resumo da sessão e opções de nova recarga ou retorno ao menu

---

### `pagamento.html` — Créditos e Pagamentos
Gerenciamento financeiro da conta:
- **Saldo de créditos** em tempo real (lido do `localStorage`)
- **Adição de créditos** via pacotes pré-definidos (R$ 50, R$ 100, R$ 200 + bônus) ou valor personalizado
- **Histórico de transações** — entradas (compras, bônus) e saídas (recargas)
- **Métodos de pagamento cadastrados** — PIX, cartão de crédito/débito, boleto, TAG
- Modais de confirmação com animações de sucesso por método

---

### `consumo.html` — Análise de Consumo
Dashboard analítico com dados de uso energético:
- **Cards de métricas** — kWh total, custo total, CO₂ evitado, sessões realizadas
- **Gráfico de consumo mensal** — evolução ao longo do tempo
- **Gráfico de comparação** — energia solar vs. rede convencional
- **Insights inteligentes** — melhor horário de carga, bandeira mais usada, veículo mais eficiente
- Fontes de dados referenciadas (GoodWe SEMS, ANEEL, IPCC)

---

### `sustentabilidade.html` — Impacto Ambiental
Página educativa e de engajamento com foco em ESG:
- **Hero com stats coletivos** — CO₂ evitado pela rede, % energia renovável, árvores equivalentes
- **Seção de bandeiras tarifárias** — explica o sistema verde/amarela/vermelha e a lógica solar
- **Calculadora de impacto** — o usuário insere seus dados (km/mês, veículo) e vê a economia em R$ e kg de CO₂
- **Cards educativos** — mobilidade elétrica e o planeta, emissões evitadas, matriz energética
- CTA para engajamento com o movimento

---

### `lummi.html` — Lummi IA (Assistente Conversacional)
Chat em tempo real com a Lummi, a assistente virtual da plataforma, integrada à API da Anthropic (Claude). Funcionalidades:
- Interface de chat completa com bolhas de mensagem, avatar animado e scroll automático
- **Base de conhecimento** com 10+ tópicos cobertos por lógica de triggers por palavras-chave:
  - Onde usar os totens e melhores horários
  - Sistema de bandeiras tarifárias (verde, amarela, vermelha)
  - Tempos de carregamento por modelo de veículo e tipo de totem
  - Impacto ambiental e cálculo de CO₂ evitado
  - Sistema de créditos e pagamentos
  - Compatibilidade de conectores (Tipo 2, CCS, CHAdeMO)
  - Tecnologia da Bateria Lynx
  - Comparativo de economia vs. gasolina
  - Autonomia por modelo de EV
  - Dicas para prolongar a vida útil da bateria
- **Sugestões rápidas** (chips clicáveis) para os tópicos mais comuns
- Fallback para respostas genéricas quando a pergunta não tem match direto

---

### `corp.html` — Lumos Corp (Portal Empresarial)
Dashboard B2B para gestão de frotas elétricas corporativas:
- **Tela de login corporativo** — acesso separado, credenciais de empresa (ex: Dash Entregas)
- **Dashboard de frota** — visão geral de veículos ativos, em carga e disponíveis
- **Painéis de sessões** — sessões de recarga por veículo, motorista e centro de custo
- **Relatórios mensais** — custo total, kWh consumido, CO₂ evitado por CNPJ
- **Mapa de regiões** — cobertura de totens por área (Grande SP, ABC Paulista, Baixada Santista, Interior SP)
- Preparado para integração com a **Lumos Fleet API**

---

##  Como a Ideia Funciona

### O Problema
Empresas e motoristas com veículos elétricos no Brasil carecem de uma solução integrada que una infraestrutura de carregamento, dados de sustentabilidade verificáveis e gestão financeira em um único lugar. Quem tem frota elettrificada paga mais por não saber quando carregar, não tem relatórios ESG auditáveis e não consegue integrar os dados de carga com seus sistemas internos (ERP, RH).

### A Solução em 3 Camadas

```
┌─────────────────────────────────────────────┐
│  CAMADA DE HARDWARE                         │
│  Totens GoodWe HCA + Bateria Lynx           │
│  Medição física de kWh via Smart Meter      │
│  Comunicação OCPP 2.0                       │
└────────────────────┬────────────────────────┘
                     │
┌────────────────────▼────────────────────────┐
│  CAMADA DE BACKEND                          │
│  ChargeGrid (open source, OCPP/OCPI)        │
│  Gestão de sessões, CDRs, roaming           │
│  GoodWe SEMS — monitoramento solar          │
└────────────────────┬────────────────────────┘
                     │
┌────────────────────▼────────────────────────┐
│  LUMOS FLEET API (B2B)                      │
│  Agrega dados por CNPJ, veículo, motorista  │
│  Tarifa dinâmica via SEMS em tempo real     │
│  Certificados de CO₂ auditáveis             │
│  Endpoints REST para ERP/SAP/RH             │
└────────────────────┬────────────────────────┘
                     │
┌────────────────────▼────────────────────────┐
│  LUMOS CONSUMER (este site)                 │
│  Interface web para motoristas              │
│  App-like, sem frameworks, mobile-first     │
│  Lummi IA como assistente integrada         │
└─────────────────────────────────────────────┘
```

### Sistema de Bandeiras Tarifárias
A Lumos usa um sistema de 3 bandeiras que reflete a disponibilidade de energia solar e o nível da bateria Lynx de cada totem:

| Bandeira | Condição | Tarifa |
|----------|----------|--------|
| 🟢 Verde | Solar > 70% + bateria Lynx cheia | R$ 0,85/kWh |
| 🟡 Amarela | Solar 40–70%, bateria parcial | R$ 1,20/kWh |
| 🔴 Vermelha | Solar < 40% ou sem geração | R$ 1,60/kWh |

Motoristas que agendam recargas na madrugada economizam R$ 0,20/kWh adicional sobre qualquer bandeira.

### Economia Real
Para 1.000 km/mês rodados:
- **Gasolina** (12 km/L a R$ 6,00): R$ 500,00/mês
- **Lumos bandeira verde**: R$ 153,00/mês
- **Economia: R$ 347/mês → R$ 4.164/ano**

---

##  Lumos Fleet API — Produto B2B

A **Lumos Fleet API** é a camada de produto para empresas com frotas eletrificadas. Documentação completa no arquivo `Lumos_Fleet_API.pdf`.

### Endpoints Principais

| Método | Endpoint | Descrição |
|--------|----------|-----------|
| `POST` | `/fleet/register` | Cadastra empresa e vincula CNPJs |
| `GET` | `/fleet/{cnpj}/sessions` | Lista sessões de recarga da frota |
| `GET` | `/fleet/{cnpj}/report/monthly` | Relatório mensal consolidado |
| `GET` | `/fleet/{cnpj}/vehicles/status` | Status de cada veículo em tempo real |
| `POST` | `/fleet/{cnpj}/schedule` | Agenda recarga em bandeira verde |
| `GET` | `/fleet/{cnpj}/carbon/certificate` | Certificado de CO₂ evitado (PDF) |

### Planos SaaS

| Plano | Frota | Preço/mês | Destaques |
|-------|-------|-----------|-----------|
| Starter | até 10 EVs | R$ 299 | Dashboard básico, relatório PDF mensal |
| Corporativo | até 50 EVs | R$ 890 | API completa, agendamento inteligente, certificado ESG |
| Enterprise | Ilimitado | Sob consulta | SLA 99,9%, webhooks, multi-CNPJ, onboarding dedicado |

---

##  Stack Técnica

| Camada | Tecnologia |
|--------|-----------|
| Frontend | HTML5, CSS3, JavaScript (Vanilla) |
| Tipografia | Syne (headings) + DM Sans (body) — Google Fonts |
| Persistência | `localStorage` (sessão, créditos, histórico) |
| Gráficos | Chart.js |
| IA / Chat | Anthropic Claude API (claude-sonnet-4-6) |
| Backend (planejado) | ChargeGrid (OCPP/OCPI, open source) |
| Hardware | Totens GoodWe HCA + Bateria Lynx |
| Monitoramento solar | GoodWe SEMS API |

---

## Design System

- **Cor primária:** `#1a9e50` (verde escuro) / `#3ecf74` (verde vivo)
- **Background escuro (carregamento):** `#1a202c`
- **Background claro (dashboard):** `#f7f9f8`
- **Alertas:** Amarelo `#f59e0b` / Vermelho `#ef4444`
- **Fontes:** Syne 800 para títulos, DM Sans para corpo
- **Bordas:** `border-radius` 14–22px, glassmorphism em modais
- **Animações:** transições suaves, step indicators, progress bars, spinners contextuais

---

## Como Rodar

O projeto é 100% estático — sem dependências, build ou servidor necessário.

```bash
# Clone o repositório
git clone https://github.com/seu-usuario/lumos.git
cd lumos

# Abra direto no navegador
open index.html
# ou
npx serve .   # para evitar restrições de CORS em localStorage entre páginas
```

> **Atenção:** Se fizer download individual dos arquivos do Claude.ai e abrir diretamente pelo sistema de arquivos (`file://`), o `localStorage` pode não persistir entre páginas. Use um servidor local (`npx serve`, `python -m http.server`, Live Server no VS Code etc.) para a experiência completa.

---

##  Estrutura de Arquivos

```
lumos/
├── index.html              # Login / Cadastro
├── home.html               # Dashboard do usuário
├── carregamento.html       # Fluxo de recarga
├── pagamento.html          # Créditos e pagamentos
├── consumo.html            # Análise de consumo
├── sustentabilidade.html   # Impacto ambiental
├── lummi.html              # Assistente IA
├── corp.html               # Portal corporativo
└── README.md               # Este arquivo
```

---

**Equipe Lumos — FIAP Global Solution 2026**

---

## 📄 Licença

Projeto acadêmico desenvolvido para a Global Solution 2026 da FIAP. Todos os direitos reservados à Equipe Lumos.
