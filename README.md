# 🚗 AutoCuida — Documentação do MVP

Repositório da aplicação MVP do **AutoCuida**, um serviço de assinatura de cuidados e detalhamento automotivo ao domicílio desenvolvido com auxílio de IA e ferramentas No-Code.

---

## 1. A Dor Escolhida e Oportunidade de Negócio

### A Dor
Proprietários de veículos que valorizam a limpeza e conservação do carro enfrentam perda recorrente de tempo em filas de lava-jatos nos fins de semana ou dificuldade para agendar limpezas detalhadas. A falta de previsibilidade e conveniência torna a manutenção estética do veículo um incômodo frequente.

### Por que Vale um Negócio?
* **Alta Recorrência:** Veículos sujeitam-se à sujeira constantemente, exigindo limpeza a cada 7 a 15 dias.
* **Modelo por Assinatura (SaaS/Serviço):** Garante receita previsível (MRR) e melhora a retenção de clientes em comparação ao modelo transacional/avulso.
* **Conveniência Premium:** O serviço vai até o cliente (garagem do condomínio ou casa), eliminando o custo de deslocamento e espera do consumidor.

---

## 2. Tamanho de Mercado e Business Model Canvas

### Estimativa de Mercado (Brasil)
* **TAM (Total Addressable Market):** Frota total de automóveis de passeio em grandes centros urbanos no Brasil.
* **SAM (Serviceable Available Market):** Proprietários de veículos de médio/alto porte em condomínios residenciais e prédios corporativos das capitais.
* **SOM (Serviceable Obtainable Market):** 100 a 300 assinantes iniciais na região de lançamento piloto.

### Business Model Canvas (Resumido)

| Bloco | Descrição |
| :--- | :--- |
| **Proposta de Valor** | Carro limpo e protegido toda semana sem sair de casa, através de assinatura previsível. |
| **Segmento de Clientes** | Donos de veículos (Hatch, SUV, Sedã) que residem em condomínios e buscam praticidade. |
| **Canais** | Landing Page, WhatsApp, Redes Sociais e Indicação em Condomínios. |
| **Relacionamento** | Atendimento humanizado via WhatsApp e lembretes de agendamento automáticos. |
| **Fontes de Receita** | Mensalidade fixa cobrada via link de pagamento (Planos Quincenais e Semanais). |
| **Recursos Chave** | Plataforma Web (MVP), equipe técnica de lavagem a seco, produtos de detalhamento. |
| **Estrutura de Custos** | Insumos de limpeza eco-friendly, transporte/deslocamento e marketing local. |

---

## 3. Tese do MVP e Processos Manuais

### A Tese Testada
> *"Donos de veículos estão dispostos a pagar uma assinatura mensal para ter manutenção automotiva na própria garagem, preferindo a facilidade de contratação online e atendimento via WhatsApp do que ir ao lava-jato."*

### O que Ficou Manual (De Propósito)
Para manter a simplicidade do MVP e acelerar a validação:
1. **Fechamento e Cobrança:** A confirmação do plano e envio de links de pagamento (Stripe/Pix) são feitos manualmente pelo WhatsApp.
2. **Atribuição de Rotas:** O agendamento da equipe em campo é organizado manualmente no painel admin.
3. **Notificações:** O envio de lembretes antes do atendimento é disparado via contato direto pelo WhatsApp.

---

## 4. Prompts Utilizados

### Mega Prompt Inicial (Lovable)

```markdown
# Projeto MVP: AutoCuida - Assinatura de Cuidados Automotivos ao Domicílio

## Visão Geral
Crie um MVP completo de uma plataforma de assinatura de lavagem e detalhamento automotivo ao domicílio chamada "AutoCuida". A aplicação deve ter um design moderno, responsivo (com foco total em navegação mobile) e ser composta por uma Landing Page pública e um Painel de Administração (`/admin`).

---

## Estilo Visual e UX
- **Design System:** Visual premium, limpo, moderno, com cantos arredondados (rounded-xl) e sombras suaves.
- **Paleta de Cores:** 
  - Primária: Azul Marinho / Grafite (#0F172A)
  - Destaque/CTA: Azul Ciano Neon ou Laranja (#0284C7 ou #EA580C)
  - Fundo: Neutro Claro (#F8FAFC)
- **Componentes:** Use ícones da biblioteca Lucide (carro, calendário, check, escudo, whatsapp) e componentes Shadcn UI para tabelas, modais, formulários e badges de status.

---

## Estrutura da Aplicação (Rotas e Telas)

### 1. Landing Page Pública (`/`)
- **Header:** Logo "AutoCuida", links de navegação suave (Como Funciona, Planos, Depoimentos) e botão "Montar Meu Plano" que faz scroll direto para o formulário.
- **Hero Section:**
  - Título chamativo: "Seu carro sempre limpo, sem você sair de casa."
  - Subtítulo: "Cuidados automotivos profissionais na garagem do seu prédio ou casa. Assine e esqueça as filas do lava-jato."
  - Botão principal de CTA: "Escolher Plano".
- **Seção "Como Funciona":**
  1. *Monte seu plano:* Escolha o porte do veículo e a frequência.
  2. *Agende pelo WhatsApp:* Ajustamos o melhor dia e horário na sua garagem.
  3. *Aproveite o fim de semana:* Seu carro renovado enquanto você descansa.
- **Formulário Interativo de Personalização (Lead/Plano):**
  - **Passo 1: Porte do Veículo** (Cards selecionáveis: Hatch/Sedã, SUV/Picape, Moto/Compacto).
  - **Passo 2: Frequência de Limpeza** (Cards: Quincenal - 2x/mês, Semanal - 4x/mês, Mensal Premium).
  - **Passo 3: Dados para Contato e Agendamento** (Campos: Nome completo, WhatsApp com DDD, Bairro/Endereço e Melhor Período [Manhã/Tarde]).
  - **Ação ao Enviar:** 
    1. Salvar as informações do lead no estado local / Lovable Cloud.
    2. Redirecionar automaticamente para o WhatsApp com uma mensagem pré-formatada contendo o resumo da solicitação.

### 2. Painel de Administração (`/admin`)
- **Cabeçalho com Métricas (KPIs):**
  - Card 1: Total de Leads Recebidos
  - Card 2: Assinantes Ativos
  - Card 3: Faturamento Mensal Estimado (R$)
  - Card 4: Serviços Agendados para a Semana
- **Tabela de Gestão de Leads e Clientes:**
  - Colunas: Nome do Cliente, Telefone/WhatsApp, Porte do Veículo, Plano Escolhido, Status (`Novo Lead`, `Em Negociação`, `Assinante Ativo`, `Cancelado`), Ações.
  - Botão de Ação: "Chamar no WhatsApp" (abre conversa direta com a mensagem de boas-vindas).
  - Opção para alterar o Status do cliente diretamente na tabela.
- **Seção de Lembretes de Atendimento:**
  - Lista simples de próximos carros a serem atendidos no dia/semana com opção de marcar como "Atendido".

---

## Recursos e Dados Mockados
- Utilize o Lovable Cloud para manter os dados cadastrados no formulário visíveis no painel de `/admin`.
- Pré-carregue a tabela do `/admin` com 4 ou 5 registros fictícios de clientes para demonstrar a plataforma totalmente funcional e preenchida.
```

### Prompt de Correção e Ajustes Finos (Aplicado Após Testes)

```markdown
# Prompt de Ajuste e Polimento - AutoCuida

1. **Ajuste no Redirecionamento do WhatsApp:**
   - Garanta que ao enviar o formulário, os campos (Porte do Veículo, Frequência, Nome, Endereço e Horário) sejam codificados corretamente na URL do WhatsApp (`https://wa.me/55...`).

2. **Melhorias de Usabilidade no Admin (`/admin`):**
   - Adicione um filtro rápido por Status do Lead na tabela (`Todos`, `Novo Lead`, `Ativo`).
   - Adicione um botão "Adicionar Lead Manualmente" para quando o contato vier direto pelo WhatsApp sem passar pelo formulário da Landing Page.

3. **Ajustes Visuais:**
   - Adicione badges coloridas para os status: Verde para "Ativo", Amarelo para "Em Negociação" e Azul para "Novo Lead".
```

---

## 5. Aplicação Publicada

* **URL da Aplicação:** (https://service-smile-sync.lovable.app)*

