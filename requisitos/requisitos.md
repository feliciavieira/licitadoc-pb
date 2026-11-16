# Especificação de Requisitos e Priorização — LicitaDoc

**Projeto:** LicitaDoc (Gestão de Licitações e Conformidade Documental para Empresas)  
**Aluna:** Felícia Kethellyn Vieira De Souza  
**Curso:** Engenharia de Software — Instituto Infnet  

---

## 1. Requisitos Funcionais (RF)

| ID | Requisito Funcional | Descrição e Comportamento Esperado | Fonte (Rastreabilidade) |
| :--- | :--- | :--- | :--- |
| **RF01** | **Cadastro de Atas / Contratos Assinados** | O sistema deve permitir cadastrar uma licitação vencida após a assinatura da Ata/Contrato, registrando: nº do processo/ata, órgão público, objeto resumido, valor global, data de início, data de expiração e indicador se **permite renovação/prorrogação** (Sim/Não). | Entrevista (P1, P3) + Artefato E2 (Lei 14.133/21) |
| **RF02** | **Registro de Pedidos (Empenhos) por Ata** | O sistema deve permitir lançar pedidos (Notas de Empenho / Ordens de Fornecimento) vinculados a uma Ata cadastrada, informando número do empenho, data de emissão, valor do pedido e status (*Pendente*, *Entregue*, *Faturado/Pago*). | Entrevista (P1, P2) |
| **RF03** | **Cálculo Automático de Saldo da Ata** | Ao lançar ou editar um pedido, o sistema deve calcular automaticamente o valor total já consumido e o **saldo financeiro remanescente** da Ata, impedindo ou alertando caso um pedido ultrapasse o saldo disponível. | Entrevista (P2) + Regra de Negócio B2G |
| **RF04** | **Cadastro de Documentos e Certidões** | O sistema deve permitir cadastrar os documentos de regularidade da empresa (ex: CND Receita Federal, CRF/FGTS, CNDT Trabalhista, CND Estadual, CND Municipal, Alvará, Balanço), informando nome, data de emissão, data de expiração, se é renovável e anexo PDF opcional. | Entrevista (P1, P3) + Artefato E2 |
| **RF05** | **Painel de Aptidão Documental (Semáforo)** | O sistema deve classificar e exibir visualmente o status de cada documento e o status geral da empresa em três níveis: **Em Dia / Regular** (Verde), **Próximo do Vencimento** (Amarelo) e **Vencido / Irregular** (Vermelho). | Entrevista (P1, P3) |
| **RF06** | **Alertas Automáticos de Expiração** | O sistema deve exibir alertas destacados na interface (e permitir disparo de notificação) quando qualquer documento ou Ata entrar na janela crítica de vencimento (ex: <= 30 dias para Atas e <= 15 ou <= 5 dias para certidões). | Entrevista (P3) |
| **RF07** | **Fluxo de Renovação (Documentos e Atas)** | O sistema deve permitir renovar um documento vencido/a vencer (atualizando emissão e expiração e preservando o histórico anterior) e registrar a prorrogação de vigência de Atas marcadas como renováveis. | Entrevista (P3) |
| **RF08** | **Dashboard Consolidado** | A tela inicial deve apresentar um resumo executivo contendo: total de contratos ativos, saldo financeiro disponível a faturar, atas próximas da expiração e situação geral das documentações. | Entrevista (P1, P2, P3) |

---

## 2. Requisitos Não Funcionais (RNF)

| ID | Categoria | Requisito Não Funcional | Métrica / Critério Verificável | Fonte |
| :--- | :--- | :--- | :--- | :--- |
| **RNF01** | **Usabilidade** | **Leitura Visual Imediata** | O usuário deve conseguir identificar se há algum documento vencido ou ata expirando em até **5 segundos** após abrir o dashboard, eliminando a necessidade de ler linhas de planilhas. | Entrevista (P2, P3) |
| **RNF02** | **Confiabilidade** | **Precisão de Datas e Valores Monetários** | O cálculo de dias restantes até a expiração (baseado no fuso oficial de Brasília `UTC-3`) e as operações de saldo em Reais (`BRL`) devem ter **100% de exatidão**, sem erros de ponto flutuante. | Artefato E2 (Risco financeiro/legal) |
| **RNF03** | **Segurança** | **Autenticação e Proteção de Dados** | O acesso ao sistema deve exigir autenticação individual por usuário/empresa, garantindo que dados comerciais de contratos e certidões não fiquem expostos publicamente. | Boas práticas B2G / LGPD |
| **RNF04** | **Desempenho** | **Carregamento Rápido do Painel** | As consultas de dashboard, listagem de atas e verificação de status documental devem responder em **menos de 1,5 segundo** em ambiente web padrão. | Experiência do Usuário |
| **RNF05** | **Manutenibilidade** | **Regras de Negócio Desacopladas** | As regras de cálculo de vencimento, status do semáforo e saldo de atas devem estar isoladas em módulos testáveis, permitindo execução de testes unitários automatizados no pipeline CI/CD. | Requisito Técnico do Bloco |

---

## 3. Priorização e Escopo Inicial (MoSCoW)

| ID | Requisito / Funcionalidade | Prioridade (MoSCoW) | Evidência (Pesquisa & Jornada) | Viabilidade Técnica | Justificativa da Decisão de Escopo |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **RF04** | Cadastro de Documentos e Certidões (Emissão, Expiração, Renovável) | **Must Have** | Entrevista (P1, P3) + Jornada (Etapa 2) | Alta (CRUD padrão com datas) | Sem o cadastro estruturado das datas de emissão e expiração, o sistema não consegue alertar nem validar regularidade. |
| **RF05** | Painel de Aptidão Documental (Semáforo Verde/Amarelo/Vermelho) | **Must Have** | Entrevista (P1) + Jornada (Momento Crítico 1) | Alta (Regra de cálculo de data) | Resolve imediatamente a dor central ("saber se as documentações estão em dia ou não") em menos de 5 segundos. |
| **RF06** | Motor de Alertas de Vencimento (Docs e Atas) | **Must Have** | Entrevista (P3) + Jornada (Etapas 2 e 4) | Alta (Filtro dinâmico + notificações) | Principal diferencial frente às planilhas manuais estáticas; evita inabilitação em pregões e bloqueio de faturamento. |
| **RF01** | Cadastro de Atas / Contratos Assinados (Valor, Vigência, Renovável) | **Must Have** | Entrevista (P1, P3) + Jornada (Etapa 1) | Alta (CRUD padrão) | Núcleo do pós-venda B2G; substitui o controle informal da vigência e sinaliza possibilidade de prorrogação (Lei 14.133/21). |
| **RF02** | Gestão de Pedidos (Empenhos) vinculados à Ata | **Must Have** | Entrevista (P1, P2) + Jornada (Etapa 3) | Alta (Relação 1:N Ata -> Pedidos) | Essencial para acompanhar a execução real da licitação após a assinatura da Ata. |
| **RF03** | Cálculo Automático de Saldo da Ata | **Must Have** | Entrevista (P2) + Jornada (Momento Crítico 2) | Alta (Soma/subtração em backend) | Elimina erros humanos de soma em planilhas e impede aceitar empenhos acima do valor adjudicado. |
| **RF07** | Fluxo de Renovação (Histórico de Docs e Prorrogação de Atas) | **Should Have** | Entrevista (P3) + Jornada (Momento Crítico 3) | Média (Versionamento simples) | Atende diretamente à necessidade validada na entrevista sobre renovar contratos e certidões sem perder o histórico. |
| **RF08** | Dashboard Consolidado (Visão Executiva) | **Should Have** | Entrevista (P1, P2, P3) + Todas as Etapas | Alta (Agregação de consultas) | Entrega visão rápida para o Sócio-Administrador sobre valor contratado, saldo a faturar e pendências documentais. |
| **RF09** | Consulta/Renovação automática via APIs do Gov.br / Receita Federal | **Won't Have (no MVP)** | Análise de Risco Técnico | Baixa (Captchas e instabilidade) | Portais governamentais exigem certificados digitais A1/A3 e captchas que inviabilizam o prazo do bloco. O cadastro manual com alertas resolve o problema no MVP. |
| **RF10** | Extração automática de datas de PDFs usando OCR / IA | **Could Have (Futuro)** | Análise de Escopo | Média/Baixa | Melhora a conveniência no cadastro, mas não impede a entrega de valor do núcleo de prazos e saldos. |
