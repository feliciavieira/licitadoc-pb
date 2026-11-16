# Jornada do Usuário, Stakeholders e Evidências de Pesquisa — LicitaDoc

**Projeto:** LicitaDoc (Gestão de Licitações e Conformidade Documental para Empresas)  
**Aluna:** Felícia Kethellyn Vieira De Souza  
**Curso:** Engenharia de Software — Instituto Infnet  

---

## 1. Mapeamento de Stakeholders

| Classificação | Stakeholder | Papel na Operação | Dor |
| :--- | :--- | :--- | :--- |
| **Principal (Usuário)** | **Analista / Operador de Licitações** | Lança atas assinadas, controla pedidos (empenhos) e monitora datas das certidões. | Evitar esquecimentos em planilhas manuais e ter alertas antes de um documento expirar. |
| **Principal (Decisor)** | **Sócio-Administrador** | Assina contratos, responde legalmente pela empresa e decide sobre renovações/aditivos. | Ter visão clara do saldo financeiro contratado e segurança jurídica de que a empresa está regular. |
| **Secundário (Interno)** | **Setor de Faturamento / Adm.** | Emite Notas Fiscais vinculadas aos empenhos recebidos. | Precisa saber se as certidões estão válidas antes de faturar (certidão vencida retém pagamento). |
| **Secundário (Externo)** | **Contador / Despachante** | Emite e renova certidões negativas (FGTS, Receita, Trabalhista, Estadual/Municipal) e balanços. | Recebe as demandas de renovação quando os prazos estão próximos do fim. |
| **Secundário (Regulador)** | **Órgão Público Contratante** | Emite Atas, Ordens de Fornecimento/Empenhos e fiscaliza a regularidade fiscal. | Exige cumprimento de prazos de entrega e manutenção da habilitação durante toda a vigência. |

---

## 2. Contexto Operacional Atual ("As-Is")

* **Ferramentas atuais:** Planilhas manuais (Excel/Google Sheets) e pastas locais de arquivos.
* **Gargalos operacionais:**
  1. **Descontrole de Atas:** Após a assinatura, o valor global e a validade (ex: 12 meses prorrogáveis) ficam anotados em planilhas estáticas; os pedidos (empenhos) chegam por e-mail e são abatidos manualmente, gerando risco de erro de saldo ou perda do prazo de renovação.
  2. **Risco Documental:** Certidões têm prazos curtos e diferentes (ex: FGTS dura 30 dias; Receita Federal dura 180 dias). Hoje, a conferência costuma ser reativa (só olham quando vão disputar um pregão ou emitir uma NF), gerando correria e risco de inabilitação ou bloqueio de pagamento.
* **Fluxo atual:**
  `[Ata Assinada] → [Anotação em Planilha] → [Chegada de Empenho por E-mail] → [Conferência Manual de Certidões] → [Risco de Esquecimento/Bloqueio]`

---

## 3. Evidências de Pesquisa Coletadas

### Fonte 1 — Entrevista Semi-estruturada (Artefato E1)
* **Perfil do Entrevistado:** Gerente real de licitações em MPE.
* **Registro da Entrevista:**
  * **Pergunta 1:** *Qual a maior dificuldade hoje para uma empresa de licitação?*
    * **Resposta (P1):** "Gerenciar contrato e documentação."
  * **Pergunta 2:** *Os dados de todas as licitações são salvos em algum lugar?*
    * **Resposta (P2):** "Sim, em planilhas manuais."
  * **Pergunta 3:** *Uma automatização de gerenciamento de licitação e acompanhamento com prazo de documentação ajudaria o dia a dia da empresa?*
    * **Resposta (P3):** "Sim, facilitaria saber quando um contrato expira, e se é possível renovar tanto um contrato como as documentações."

### Fonte 2 — Análise Documental e Regulatória (Artefato E2)
* Análise prática do fluxo de Atas de Registro de Preços (**Lei nº 14.133/2021, Art. 84**) e ciclos de validade de certidões exigidas para habilitação e faturamento (**CRF/FGTS** de 30 dias; **CND Federal e CNDT** de 180 dias; **Certidões Estaduais/Municipais** de 30 a 90 dias).

---

## 4. Mapa da Jornada do Usuário

* **Persona:** **Jefferson Santos** (Gerente Geral de Licitações).
* **Contexto:** Gerencia uma microempresa fornecedora para prefeituras e órgãos estaduais. Acumula funções comerciais, administrativas e de controle contratual.
* **Objetivo Principal:** Garantir que nenhum contrato vença sem aviso, controlar o saldo real de cada Ata assinada e manter 100% das certidões negativas em dia para não perder pregões nem ter pagamentos bloqueados.

| Dimensão | Etapa 1: Vitória e Cadastro da Ata | Etapa 2: Rotina de Vigência Documental | Etapa 3: Recebimento e Controle de Pedidos | Etapa 4: Vencimento e Renovação |
| :--- | :--- | :--- | :--- | :--- |
| **O que o usuário faz (Ações)** | Recebe a Ata assinada pelo órgão; acessa o sistema, cadastra o nº do processo, órgão, valor total, datas de início/fim e marca se permite prorrogação. | Abre o sistema no início do dia para conferir o semáforo de certidões (FGTS, Receita, CNDT, Estadual/Municipal) antes de disputar novos editais ou emitir notas. | Recebe uma Nota de Empenho por e-mail; localiza a Ata no sistema, lança o pedido e verifica quanto ainda resta de saldo naquela licitação. | Recebe alerta de que uma certidão vence em 7 dias ou uma Ata expira em 30 dias; aciona o contador ou o órgão público para renovar e atualiza as datas no sistema. |
| **Pontos de Contato** | E-mail do Órgão / Portal de Compras → Tela de Cadastro de Ata. | Dashboard Principal (Semáforo) → Módulo de Documentos. | E-mail de Empenho → Tela de Detalhes da Ata / Aba de Pedidos. | Banner/Notificação de Alerta → Modal de Renovação de Documento/Ata. |
| **Pensamentos e Emoções** | *"Ganhamos! Preciso registrar logo essa Ata com os prazos certos para não esquecer."* (Alívio / Organização) | *"Que tranquilidade olhar uma tela só e ter certeza de que nenhuma certidão venceu."* (Segurança) | *"Agora sei na hora quanto já faturei e quanto saldo ainda tenho para vender."* (Controle) | *"Ainda bem que fui avisado antes; dá tempo de renovar a certidão e pedir aditivo da Ata."* (Proatividade) |
| **Dores no Cenário Atual (Sem o sistema)** | Anotar em planilha manual e esquecer de calcular a data final ou não sinalizar se a Ata é renovável. | Descobrir que o FGTS ou a CND Municipal venceu **só na hora** de emitir a NF ou na disputa de um pregão (risco de inabilitação). | Somar empenhos manualmente na planilha, errar contas e aceitar pedido acima do limite da Ata. | Perder o prazo legal de renovação da Ata por falta de aviso prévio, perdendo receita garantida. |

---

## 5. Momentos Críticos Identificados

1. **Momento Crítico 1 — O "Susto" da Certidão Vencida (Maior Risco de Frustração/Prejuízo):**
   * **Cenário:** Certidões como o CRF do FGTS vencem a cada 30 dias. Se uma única certidão vencer sem aviso, a MPE é impedida de receber pagamentos de notas já entregues ou é desclassificada na fase de habilitação de um pregão.
   * **Como o produto gera valor:** O **Semáforo Documental (RF05)** combinado com os **Alertas Antecipados (RF06)** transforma um problema reativo (descobrir tarde demais) em uma ação preventiva (renovar 15 ou 5 dias antes).

2. **Momento Crítico 2 — Abatimento de Pedidos sobre o Saldo da Ata (Maior Risco Operacional):**
   * **Cenário:** Uma Ata de R$ 100.000,00 recebe vários empenhos parciais ao longo de 12 meses. Em planilhas manuais, erros de fórmula ou lançamentos duplicados fazem a empresa perder o controle do saldo remanescente.
   * **Como o produto gera valor:** O vínculo direto entre **Pedidos e Ata (RF02)** com **Cálculo Automático de Saldo (RF03)** garante visibilidade financeira instantânea a cada novo empenho recebido.

3. **Momento Crítico 3 — Janela de Renovação da Ata (Maior Oportunidade de Receita):**
   * **Cenário:** Pela Lei nº 14.133/2021, Atas de Registro de Preços podem ser prorrogadas por mais 1 ano se houver saldo e interesse das partes, mas o pedido precisa ser feito antes da expiração.
   * **Como o produto gera valor:** Ao registrar no cadastro inicial se a Ata permite renovação (**RF01**) e disparar alerta com 30 dias de antecedência (**RF06 + RF07**), o sistema atua como gerador de receita recorrente para a MPE.
