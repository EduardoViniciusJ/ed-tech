# Project Context - TCC Rocket EdTech ServiceNow

## 1. Visao Geral

Este projeto e uma implementacao academica em **ServiceNow** para uma Instituicao de Ensino Superior ficticia do programa **Alpar Rocket**.

O objetivo e substituir processos manuais, lentos e pouco transparentes por uma plataforma de atendimento academico baseada em **ESM - Enterprise Service Management**. O ServiceNow sera usado para organizar servicos de diferentes areas da instituicao, principalmente:

- Suporte Tecnico.
- Financeiro.
- Secretaria Academica.

O usuario principal e o **Aluno**, mas o sistema tambem atende Professores, equipes internas e Gestores Academicos.

Este arquivo serve como documentacao viva para o grupo de desenvolvedores e para outras IAs que ajudarem no desenvolvimento, estudo, design, backlog, testes ou apresentacao do TCC.

## 2. Fontes Usadas Para Esta Versao

- `TCC Rocket - Ed Tech.pdf`: enunciado do problema, areas impactadas e expectativas do TCC.
- `20260520 - Features.txt`: backlog inicial com as historias STRY0001 a STRY0009.
- `20260521 - Features.txt`: backlog complementar com as historias STRY0010 a STRY0015.
- `padrao update sets.pdf`: padrao documentado de nomeacao de update sets por story e parent por modulo.
- `RELATORIO_REQUISITOS_CADASTROS.md`: requisitos de cadastro e campos complementares.
- Informacoes atualizadas pelo time em 2026-05-21 sobre as features ja implementadas.

Quando houver conflito entre documentos, priorize:

1. O que ja foi implementado na instancia ServiceNow.
2. O backlog/features mais recente informado pelo time.
3. O enunciado do PDF.
4. Este `AGENTS.md` como guia consolidado.

## 3. O Que E O Sistema

O sistema e um **portal academico de servicos** em ServiceNow. Ele permite que alunos e professores abram solicitacoes de forma digital, acompanhem o andamento e recebam atendimento das areas corretas.

Na pratica, o sistema deve oferecer:

- Portal de servicos para abertura e acompanhamento de chamados.
- Catalogos separados por departamento.
- Categorias para organizar os servicos.
- Record Producers para criar registros nas tabelas corretas.
- Variable Sets para padronizar os formularios.
- Grupos e roles para separar responsabilidades.
- Tabelas departamentais para Financeiro e Secretaria.
- Uso de `Incident [incident]` para Suporte Tecnico.
- Base para futuras notificacoes, SLAs, pesquisas e dashboards.

## 4. Escopo Core Do Projeto

O escopo principal do TCC cobre tres areas:

| Area | Papel no sistema |
|---|---|
| Suporte Tecnico | Atender problemas de AVA/Moodle, portal do aluno, aulas, videos e envio de atividades |
| Financeiro | Atender boleto, 2a via, pagamentos, comprovantes, multas e duvidas financeiras |
| Secretaria Academica | Atender documentos academicos, comprovante de matricula, declaracoes, historico e diploma |

Outras areas como RH, Comercial, Ouvidoria, Infraestrutura e Pesquisa/Extensao podem ser tratadas como expansao futura, mas nao sao o foco principal do PDF.

## 5. Personas Principais

- **Aluno**: usuario principal. Abre solicitacoes, acompanha status, visualiza seu proprio cadastro e espera linguagem clara.
- **Professor**: tambem abre solicitacoes, principalmente de suporte tecnico ou apoio academico.
- **Suporte Tecnico**: resolve problemas tecnicos de AVA/Moodle, portal, aulas, videos e envio de atividades.
- **Financeiro**: resolve demandas de boleto, pagamento, comprovante e contestacao de multas.
- **Secretaria Academica**: resolve demandas de documentos, comprovante de matricula, declaracoes, historico e diploma.
- **Gestores Academicos**: acompanham processos, atrasos, aprovacoes, indicadores e qualidade de atendimento.
- **Administrador ServiceNow**: configura tabelas, campos, grupos, roles, catalogos, Record Producers, flows, ACLs e update sets.

## 6. Problemas Core Do PDF

### 6.1 Suporte Tecnico

Problemas relatados:

- Aula nao abre.
- Video nao carrega.
- Erro no envio de atividade.
- Dificuldade de acesso ao portal do aluno ou AVA.
- Resposta prometida em ate 3 horas, mas resposta real em torno de 8 horas.
- Resolucao prometida em 8 horas, mas demora mais.
- Falta de visibilidade para o aluno.

O sistema deve:

- Permitir abertura de chamado tecnico pelo portal.
- Criar registro em `Incident [incident]`.
- Coletar dados tecnicos suficientes para investigacao.
- Direcionar para o grupo `Suporte`.
- Futuramente medir tempo de resposta e resolucao por SLA.

### 6.2 Financeiro

Problemas relatados:

- Boleto nao chega automaticamente.
- 2a via depende de e-mail.
- Prazo prometido de 1 dia util nao e cumprido.
- Boleto chega atrasado e gera multa.
- Comprovante tambem e enviado por e-mail.
- Atendimento so acelera apos reclamacao externa.

O sistema deve:

- Permitir solicitacao de 2a via de boleto pelo portal.
- Permitir envio de comprovante pelo portal.
- Permitir contestacao de multa por atraso de boleto.
- Criar registro em `Solicitacao Financeira [x_edu_financeiro]`.
- Direcionar para o grupo `Financeira`.
- Futuramente aplicar SLA de atendimento financeiro.

### 6.3 Secretaria Academica

Problemas relatados:

- Aluno precisa ir presencialmente para pedir comprovante de matricula.
- Solicitacao de diploma e documentos e manual.
- Prazo prometido de ate 3 dias uteis nao e cumprido.
- Aluno precisa retornar varias vezes para cobrar.
- Processo parece ultrapassado para uma faculdade de tecnologia.

O sistema deve:

- Permitir solicitacao de documentos pelo portal.
- Criar registro em `Solicitacao Secretaria [x_edu_secretaria]`.
- Direcionar para o grupo `Secretaria`.
- Cobrir comprovante de matricula, declaracao, historico e diploma.
- Futuramente aplicar SLA de documentos academicos.

## 7. Estado Atual Do Sistema

Status baseado nas features informadas como implementadas pelo time ate 2026-05-21.

### 7.1 Features Implementadas

| Story | Nome | Estado |
|---|---|---|
| STRY0001 | Criar Grupos de Usuarios | Implementada |
| STRY0002 | Criar Roles e Vincular aos Grupos | Implementada |
| STRY0003 | Criar Tabela Perfil Academico | Implementada |
| STRY0004 | Criar Tabelas Core dos Departamentos | Implementada |
| STRY0005 | Criar Catalogos Departamentais | Implementada |
| STRY0006 | Criar Categorias dos Catalogos | Implementada |
| STRY0007 | Criar Record Producer de Suporte Tecnico | Implementada |
| STRY0008 | Criar Record Producer Financeiro | Implementada |
| STRY0009 | Criar Record Producer da Secretaria | Implementada |
| STRY0010 | Expandir Tabela Perfil Academico/Cadastro | Implementada |
| STRY0011 | Criar Variable Sets Comuns dos Formularios | Implementada |
| STRY0012 | Criar Variable Set de Suporte Tecnico | Implementada |
| STRY0013 | Criar Variable Set Financeiro | Implementada |
| STRY0014 | Criar Variable Set da Secretaria Academica | Implementada |
| STRY0015 | Ajustar Record Producer de Suporte Tecnico | Implementada |

### 7.2 Features Do Arquivo 20260521

O arquivo `20260521 - Features.txt` e a fonte mais recente para as features STRY0010 a STRY0015.

| Story | Nome | Update Set informado | Parent | Estado |
|---|---|---|---|---|
| STRY0010 | Expandir Tabela Perfil Academico/Cadastro | `EDTECH_01_CORE_STRY0013_CAMPOS_CADASTRO` | `EDTECH_01_CORE` | Implementada |
| STRY0011 | Criar Variable Sets Comuns dos Formularios | `EDTECH_05_PORTAL_STRY0014_VARIABLE_SETS_COMUNS` | `EDTECH_05_PORTAL` | Implementada |
| STRY0012 | Criar Variable Set de Suporte Tecnico | `EDTECH_02_SUPORTE_STRY0015_VS_SUPORTE_TECNICO` | `EDTECH_02_SUPORTE` | Implementada |
| STRY0013 | Criar Variable Set Financeiro | `EDTECH_03_FINANCEIRO_STRY0016_VS_FINANCEIRO` | `EDTECH_03_FINANCEIRO` | Implementada |
| STRY0014 | Criar Variable Set da Secretaria Academica | `EDTECH_04_SECRETARIA_STRY0017_VS_SECRETARIA` | `EDTECH_04_SECRETARIA` | Implementada |
| STRY0015 | Ajustar Record Producer de Suporte Tecnico | `EDTECH_02_SUPORTE_STRY0018_RP_SUPORTE_CORE` | `EDTECH_02_SUPORTE` | Implementada |

Observacao importante: o arquivo de 2026-05-21 possui divergencias entre o numero da story e o numero escrito dentro do nome de alguns update sets. Para documentacao e apresentacao, use a **story** como sequencia funcional do backlog. Para auditoria na instancia, respeite o **nome real do update set implementado**, caso ele ja exista na PDI.

### 7.3 O Que Esta Pronto Na Pratica

O sistema ja possui:

- Grupos principais.
- Roles principais.
- Tabela de perfil academico/cadastro expandida.
- Tabelas departamentais de Financeiro e Secretaria.
- Catalogos departamentais.
- Categorias departamentais.
- Record Producers principais das tres areas.
- Variable Sets comuns.
- Variable Sets especificos de Suporte, Financeiro e Secretaria.
- Record Producer de Suporte revisado para cobrir os problemas tecnicos core.

Ainda nao considerar como pronto:

- Notificacoes completas.
- SLA completo.
- Pesquisa de satisfacao.
- Dashboards finais.
- Automacao completa de roteamento, se ainda nao validada na instancia.
- Record Producers financeiros adicionais.
- Record Producers adicionais da Secretaria.

## 8. Grupos E Roles

### 8.1 Grupos Atuais

- `Alunos`: usuarios alunos que abrem solicitacoes no portal.
- `Professores`: usuarios professores que abrem solicitacoes no portal.
- `Suporte`: equipe responsavel por chamados tecnicos.
- `Financeira`: equipe responsavel por chamados financeiros.
- `Secretaria`: equipe responsavel por chamados academicos e documentos.
- `Gestores Academicos`: usuarios que visualizam, acompanham e aprovam informacoes/processos academicos.

### 8.2 Roles Atuais

- `u_edu_suporte`: vinculada ao grupo `Suporte`.
- `u_edu_financeiro`: vinculada ao grupo `Financeira`.
- `u_edu_secretaria`: vinculada ao grupo `Secretaria`.
- `u_edu_gestor`: vinculada ao grupo `Gestores Academicos`.

Regras importantes:

- `Alunos` e `Professores` nao devem receber roles administrativas customizadas.
- Gestores Academicos podem receber `admin` apenas na PDI/apresentacao, se necessario para demonstrar Employee Center e fluxos internos.
- Em um ambiente produtivo, o acesso de Gestores deve ser resolvido com ACLs e roles especificas, nao com `admin`.

## 9. Modelo De Dados

### 9.1 Usuario Base

Usar a tabela nativa:

- `User [sys_user]`

Ela armazena dados de acesso e contato basico, como nome, e-mail, user ID e status ativo.

### 9.2 Perfil Academico/Cadastro

Tabela:

- `u_edu_perfil_academico`

Essa tabela nao deve substituir `sys_user`; ela complementa o usuario com dados academicos, profissionais e de cadastro.

Campos base:

- `Usuario`: referencia para `sys_user`.
- `Tipo de Perfil`.
- `RA/Matricula`.
- `Registro Funcional`.
- `Curso`.
- `Campus`.
- `Periodo`.
- `Turno`.
- `Status Academico`.
- `Telefone Celular`.
- `Data de Ingresso`.
- Campos de endereco, se aprovados pela cliente.

Uso esperado:

- Preencher automaticamente dados nos formularios.
- Permitir que aluno/professor nao tenha que digitar informacoes que o sistema ja conhece.
- Servir de base para consultas, relatorios e regras futuras.

### 9.3 Tabelas Departamentais

Suporte Tecnico:

- Usa `Incident [incident]`.
- O Record Producer de Suporte cria incidentes.

Financeiro:

- Tabela funcional: `Solicitacao Financeira`.
- Nome tecnico: `x_edu_financeiro`.
- Estende `Task [task]`.

Secretaria:

- Tabela funcional: `Solicitacao Secretaria`.
- Nome tecnico: `x_edu_secretaria`.
- Estende `Task [task]`.

## 10. Catalogos, Categorias E Record Producers

### 10.1 Catalogos

- `Catalogo de Suporte Tecnico`.
- `Catalogo Financeiro`.
- `Catalogo da Secretaria Academica`.

### 10.2 Categorias

- `Servicos de TI / AVA`: dentro do `Catalogo de Suporte Tecnico`.
- `Boletos e Pagamentos`: dentro do `Catalogo Financeiro`.
- `Documentos e Declaracoes`: dentro do `Catalogo da Secretaria Academica`.

### 10.3 Record Producers Atuais

Suporte Tecnico:

- `Relatar Problema com AVA` ou `Relatar Problema com AVA/Moodle`.
- Cria registro em `Incident [incident]`.
- Usa Variable Sets comuns.
- Usa Variable Set `Detalhes do Problema Tecnico`.
- Deve direcionar para o grupo `Suporte`.

Financeiro:

- `Solicitar 2a Via de Boleto`.
- Cria registro em `Solicitacao Financeira [x_edu_financeiro]`.
- Fica no `Catalogo Financeiro`.
- Fica na categoria `Boletos e Pagamentos`.

Secretaria:

- `Emitir Comprovante de Matricula`.
- Cria registro em `Solicitacao Secretaria [x_edu_secretaria]`.
- Fica no `Catalogo da Secretaria Academica`.
- Fica na categoria `Documentos e Declaracoes`.

## 11. Variable Sets Atuais

### 11.1 Variable Sets Comuns

Criados para reutilizacao em Suporte, Financeiro e Secretaria:

- `Dados do Solicitante`.
- `Dados Academicos do Solicitante`.
- `Contato e Retorno`.
- `Descricao da Solicitacao`.
- `Anexos/Evidencias`.

Campos comuns esperados:

- Solicitante.
- Nome do solicitante.
- E-mail institucional.
- Perfil do solicitante.
- RA/Matricula.
- Curso.
- Campus.
- Periodo.
- Turno.
- Telefone para contato.
- Melhor canal de retorno.
- Assunto.
- Descricao detalhada.
- Urgencia percebida.
- Impacto na rotina academica.
- Anexo/evidencia.

Nem todo campo comum precisa ser persistido na tabela de perfil. Campos como solicitante, RA, curso e campus podem vir do cadastro. Campos como assunto, descricao, urgencia e anexo pertencem a solicitacao.

### 11.2 Variable Set De Suporte Tecnico

Variable Set:

- `Detalhes do Problema Tecnico`.

Campos:

- Sistema afetado.
- Tipo de problema.
- URL ou caminho da tela com erro.
- Dispositivo utilizado.
- Navegador utilizado.
- Mensagem de erro apresentada.
- Data e horario aproximado do problema.
- Anexo de evidencia/print.

Opcoes importantes:

- Sistema afetado: AVA/Moodle, Portal do Aluno, Video/Aula, Envio de Atividade, Outro.
- Tipo de problema: Aula nao abre, Video nao carrega, Erro no envio da atividade, Problema de acesso, Outro.

### 11.3 Variable Set Financeiro

Variable Set:

- `Detalhes da Solicitacao Financeira`.

Campos:

- Tipo de solicitacao financeira.
- Mes/competencia.
- Data de vencimento.
- Valor aproximado.
- Numero do boleto.
- Comprovante de pagamento.
- Descricao da situacao.

Opcoes importantes:

- 2a via de boleto.
- Envio de comprovante.
- Contestacao de multa.
- Duvida financeira.
- Outro.

### 11.4 Variable Set Da Secretaria Academica

Variable Set:

- `Detalhes da Solicitacao Academica`.

Campos:

- Tipo de documento.
- Finalidade do documento.
- Curso.
- RA/Matricula.
- Forma de entrega.
- Observacoes adicionais.

Opcoes importantes:

- Comprovante de matricula.
- Declaracao academica.
- Historico escolar.
- Diploma.
- Outro.

## 12. O Que Cada Area Ja Consegue Fazer

### 12.1 Suporte Tecnico

Ja consegue:

- Receber chamado tecnico pelo portal.
- Criar incidente em `Incident [incident]`.
- Coletar dados tecnicos sobre AVA/Moodle, portal, aula, video e envio de atividade.
- Receber anexo/print de evidencia.
- Ter chamado associado ao grupo `Suporte`, conforme feature STRY0015.

Problemas core ja cobertos no formulario:

- Aula nao abre.
- Video nao carrega.
- Erro no envio da atividade.
- Problema de acesso ao portal/AVA.

Ainda falta para ficar completo:

- SLA de resposta em 3h.
- SLA de resolucao em 8h.
- Notificacao de abertura, andamento e conclusao.
- Escalonamento para gestor em caso de atraso.
- Dashboard de volume, prazo e SLA.
- Pesquisa de satisfacao.

### 12.2 Financeiro

Ja consegue:

- Receber solicitacao de 2a via de boleto.
- Criar registro em `Solicitacao Financeira [x_edu_financeiro]`.
- Usar catalogo e categoria corretos.
- Possui Variable Set financeiro pronto para padronizar os dados.

Problemas core parcialmente cobertos:

- 2a via de boleto: coberta pelo Record Producer atual.
- Dados de boleto, vencimento, valor e comprovante: preparados pelo Variable Set.

Ainda falta para ficar completo:

- Revisar o Record Producer `Solicitar 2a Via de Boleto` para usar o Variable Set financeiro, se ainda nao estiver aplicado.
- Criar Record Producer `Enviar Comprovante de Pagamento`.
- Criar Record Producer `Contestar Multa por Atraso de Boleto`.
- Criar opcao ou servico para `Duvida Financeira`.
- Direcionamento validado para o grupo `Financeira`.
- SLA de 1 dia util para demandas financeiras.
- Notificacoes.
- Dashboard financeiro.
- Pesquisa de satisfacao.

### 12.3 Secretaria Academica

Ja consegue:

- Receber solicitacao de comprovante de matricula.
- Criar registro em `Solicitacao Secretaria [x_edu_secretaria]`.
- Usar catalogo e categoria corretos.
- Possui Variable Set da Secretaria pronto para padronizar documentos.

Problemas core parcialmente cobertos:

- Comprovante de matricula: coberto pelo Record Producer atual.
- Dados para documentos academicos: preparados pelo Variable Set.

Ainda falta para ficar completo:

- Revisar o Record Producer `Emitir Comprovante de Matricula` para usar o Variable Set da Secretaria, se ainda nao estiver aplicado.
- Criar Record Producer `Solicitar Declaracao Academica`.
- Criar Record Producer `Solicitar Historico Escolar`.
- Criar Record Producer `Solicitar Diploma`.
- Direcionamento validado para o grupo `Secretaria`.
- SLA de ate 3 dias uteis.
- Notificacoes.
- Dashboard de documentos e prazos.
- Pesquisa de satisfacao.

## 13. Backlog Atual Consolidado

### 13.1 Features Ja Implementadas

As features STRY0001 a STRY0015 sao consideradas implementadas conforme informacao do time.

## 14. Proximas Entregas Dos Problemas Core

### 14.1 Financeiro

Criar ou revisar Record Producers:

- `Solicitar 2a Via de Boleto`: ja existe, mas deve usar o Variable Set financeiro.
- `Enviar Comprovante de Pagamento`.
- `Contestar Multa por Atraso de Boleto`.
- `Tirar Duvida Financeira`, se o time quiser separar esse atendimento.

Resultado esperado:

- O aluno nao depende mais de e-mail para boleto ou comprovante.
- O Financeiro recebe dados estruturados.
- O sistema fica pronto para SLA, notificacao e relatorio.

### 14.2 Secretaria Academica

Criar ou revisar Record Producers:

- `Emitir Comprovante de Matricula`: ja existe, mas deve usar o Variable Set da Secretaria.
- `Solicitar Declaracao Academica`.
- `Solicitar Historico Escolar`.
- `Solicitar Diploma`.

Resultado esperado:

- O aluno nao precisa ir presencialmente para pedir documentos simples.
- A Secretaria recebe solicitacoes organizadas.
- O sistema fica pronto para SLA, notificacao e relatorio.

### 14.3 Suporte Tecnico

Suporte ja possui a principal revisao do Record Producer, mas ainda deve ser validado:

- Se o incidente esta sendo criado corretamente.
- Se o grupo `Suporte` esta sendo preenchido.
- Se os campos dos Variable Sets aparecem no portal.
- Se anexos funcionam.
- Se a linguagem esta clara para aluno/professor.

Resultado esperado:

- O aluno/professor consegue registrar problemas tecnicos reais sem depender de e-mail.
- O Suporte recebe dados suficientes para diagnostico.
- O sistema fica pronto para SLA e notificacoes.

## 15. Update Sets E Hierarquia

Padrao recomendado:

```text
EDTECH_XX_MODULO
  EDTECH_XX_MODULO_STRY000Y_NOME_DA_FEATURE
```

O arquivo `padrao update sets.pdf` documenta o padrao oficial usado nas primeiras stories:

| Story | Update Set Name | Parent |
|---|---|---|
| STRY0001 - Criar Grupos de Usuarios | `EDTECH_01_CORE_STRY0001_GRUPOS` | `EDTECH_01_CORE` |
| STRY0002 - Criar Roles e Vincular aos Grupos | `EDTECH_01_CORE_STRY0002_ROLES` | `EDTECH_01_CORE` |
| STRY0003 - Criar Tabela Perfil Academico | `EDTECH_01_CORE_STRY0003_PERFIL_ACADEMICO` | `EDTECH_01_CORE` |
| STRY0004 - Criar Tabelas Core dos Departamentos | `EDTECH_01_CORE_STRY0004_TABELAS_DEPARTAMENTAIS` | `EDTECH_01_CORE` |
| STRY0005 - Criar Catalogos Departamentais | `EDTECH_05_PORTAL_STRY0005_CATALOGOS` | `EDTECH_05_PORTAL` |
| STRY0006 - Criar Categorias dos Catalogos | `EDTECH_05_PORTAL_STRY0006_CATEGORIAS` | `EDTECH_05_PORTAL` |
| STRY0007 - Criar Record Producer de Suporte Tecnico | `EDTECH_02_SUPORTE_STRY0007_RP_AVA` | `EDTECH_02_SUPORTE` |
| STRY0008 - Criar Record Producer Financeiro | `EDTECH_03_FINANCEIRO_STRY0008_RP_BOLETO` | `EDTECH_03_FINANCEIRO` |
| STRY0009 - Criar Record Producer da Secretaria | `EDTECH_04_SECRETARIA_STRY0009_RP_COMPROVANTE_MATRICULA` | `EDTECH_04_SECRETARIA` |

Update sets pais atuais:

- `EDTECH_01_CORE`: grupos, roles, tabelas, campos e ACLs.
- `EDTECH_02_SUPORTE`: recursos especificos de Suporte Tecnico.
- `EDTECH_03_FINANCEIRO`: recursos especificos do Financeiro.
- `EDTECH_04_SECRETARIA`: recursos especificos da Secretaria Academica.
- `EDTECH_05_PORTAL`: catalogos, categorias, portal, Employee Center, UX e Variable Sets comuns.
- `EDTECH_06_RELATORIOS`: relatorios e dashboards.
- `EDTECH_07_AUTOMACOES`: flows, assignment, notificacoes, SLA e pesquisas.

Regras:

- Nao desenvolver no `Default`.
- Nao desenvolver diretamente no update set pai quando houver story filha.
- A story filha deve ficar como **Current** durante o desenvolvimento.
- O campo **Parent** deve apontar para o update set pai do modulo.
- No final, os pais podem ser agrupados em uma release/batch.

Para novas features, preferir manter o numero da story dentro do nome do update set. Exemplo:

```text
STRY0016 - Ajustar/Criar Record Producers Financeiros Core
Update Set: EDTECH_03_FINANCEIRO_STRY0016_RP_FINANCEIRO_CORE
Parent: EDTECH_03_FINANCEIRO
```

## 16. Organizacao Sugerida Para 5 Desenvolvedores

| Dev | Frente | Responsabilidades principais |
|---|---|---|
| Dev 1 | Core / Dados | Grupos, roles, tabelas, campos, ACLs e modelo de dados |
| Dev 2 | Suporte Tecnico | Incident, RP de AVA/Moodle, Variable Set tecnico, SLA e notificacoes de suporte |
| Dev 3 | Financeiro | `x_edu_financeiro`, RPs financeiros, Variable Set financeiro, SLA e notificacoes financeiras |
| Dev 4 | Secretaria | `x_edu_secretaria`, RPs de documentos, Variable Set secretaria, SLA e notificacoes da secretaria |
| Dev 5 | Portal / Qualidade | Portal, Employee Center, UX, pesquisas, relatorios, dashboards e apoio a apresentacao |

Cada desenvolvedor deve testar sua entrega pelo portal/Employee Center e depois validar o fluxo integrado.

## 17. Boas Praticas ServiceNow Para Este Projeto

- Preferir **Flow Designer** para automacoes de processo.
- Usar **Business Rules** apenas quando a logica server-side exigir.
- Evitar queries sincronas no client-side.
- Usar **GlideAjax** para buscar dados server-side em Client Scripts.
- Evitar hardcode de `sys_id`.
- Nao alterar tabelas nativas sem necessidade.
- Usar `sys_user` para acesso/identidade.
- Usar `u_edu_perfil_academico` para dados academicos/profissionais complementares.
- Manter catalogos, categorias e fluxos separados por departamento.
- Testar sempre pelo Portal ou Employee Center, nao apenas pelo backend.
- Usar linguagem clara para aluno/professor.

## 18. Regras Para Outras IAs

Quando uma IA auxiliar este projeto, ela deve:

1. Respeitar ServiceNow como plataforma principal.
2. Manter foco nos problemas core do PDF.
3. Separar Suporte, Financeiro e Secretaria.
4. Conferir nomes de tabelas, grupos, roles e update sets antes de sugerir codigo.
5. Explicar se algo e requisito do PDF, feature implementada ou sugestao futura.
6. Nao inventar features fora do escopo sem marcar como expansao.
7. Escrever textos do portal em linguagem simples e nao tecnica.
8. Ao sugerir scripts, informar onde configurar no ServiceNow.
9. Ao revisar o projeto, procurar falhas de roteamento, permissao, dados obrigatorios, SLA, UX e rastreabilidade.

## 19. Definition Of Done Do MVP

Uma entrega minima deve ser considerada completa quando:

- Grupos e roles estao criados.
- Tabelas core existem.
- Catalogos e categorias aparecem no portal.
- Record Producers principais funcionam.
- Variable Sets comuns e especificos estao aplicados.
- Cada formulario cria registro na tabela correta.
- Cada registro vai para o grupo correto.
- O aluno consegue acompanhar a solicitacao.
- Ha prazo definido por tipo de servico.
- Ha pelo menos controle basico de SLA ou medicao equivalente.
- Ha notificacao basica de abertura/conclusao.
- Ha pesquisa de satisfacao apos conclusao ou proposta clara dela.
- Ha relatorio/dashboard basico para apresentacao.
- O fluxo foi testado pelo portal com usuario aluno.

## 20. Pontos De Atencao

- Nao usar `Incident` para Financeiro ou Secretaria.
- Nao expor nomes tecnicos ao aluno.
- Nao misturar catalogos e categorias entre departamentos.
- Validar se `u_edu_perfil_academico` esta sendo usado como tabela complementar, nao como substituta do `sys_user`.
- Campos permanentes ficam em tabela; campos especificos da solicitacao ficam em variaveis/registro da solicitacao.
- O sistema atual ainda nao deve ser apresentado como completo em SLA, notificacoes ou dashboards.

## 21. Resumo Para Apresentacao

O projeto entrega uma plataforma ServiceNow para atendimento academico, com foco inicial em Suporte Tecnico, Financeiro e Secretaria Academica.

O aluno passa a abrir solicitacoes pelo portal, usando formularios padronizados e separados por area. O Suporte ja recebe incidentes tecnicos estruturados. O Financeiro ja possui base para 2a via de boleto e dados financeiros. A Secretaria ja possui base para comprovante de matricula e documentos academicos.

O estado atual do sistema cobre a estrutura principal: grupos, roles, tabelas, catalogos, categorias, Record Producers e Variable Sets. As proximas entregas devem completar os Record Producers financeiros e da Secretaria, depois adicionar roteamento, SLAs, notificacoes, pesquisas e dashboards.
