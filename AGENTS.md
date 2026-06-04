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
- `20260521 - Features-V1.txt`: backlog complementar com STRY0016 a STRY0020 e REFACTOR-001 de padronizacao.
- `20260521 - Features-V2.txt`: backlog complementar com STRY0021 e STRY0022 para Record Producers core de Financeiro e Secretaria.
- `20260522 - Features.txt`: backlog complementar com STRY0023 a STRY0029 para usuarios de teste, referencias, autopreenchimento, User Criteria, UI Policy, vinculacao ao portal e Meta Tags.
- `20260522 - FIX.txt`: correcoes pontuais de Variable Sets, autopreenchimento de contato e categorias duplicadas.
- `20260525 - Features.txt`: backlog complementar com STRY0030 a STRY0040 para UI Policies financeiras, ajustes do perfil academico, mapeamento de Secretaria, Assignment Rules, notificacoes e SLA.
- `20260525 - Feature-V1.txt`: backlog complementar com STRY0041 a STRY0047 para ACL/GlideAjax, autopreenchimento e processo financeiro (campos, mapeamento, assignment, notificacoes e SLA).
- `20260526 - Features.txt`: backlog complementar com STRY0048, STRY0049, STRY0051, STRY0052, STRY0053, STRY0054 e STRY0055 para flows internos, validacoes de fechamento, assignment, notificacoes e SLA de Suporte.
- `20260526 - Features-V1.txt`: backlog complementar com REFACTOR002, REFACTOR003, REFACTOR004 e STRY0056 para padronizacao de formularios e filtros de My Requests.
- `20260527 - Features.txt`: backlog complementar com STRY0057 a STRY0061 para ajustes de UX dos formularios (Select Box e Catalog UI Policies de Suporte e Secretaria).
- `20260527 - Features-V1.txt`: backlog complementar com STRY0062, STRY0063 e STRY0064 para wireframes, ACLs e base do portal.
- `20260528 - Features.txt`: backlog complementar com STRY0065 a STRY0069 e REFACTOR005 para home/paginas/widgets do portal e padronizacao de scripts da Secretaria.
- `20260528 - Features-V1.txt`: backlog complementar com STRY0070 a STRY0078 e REFACTOR006/REFACTOR007 para tema, widgets, SLA final de suporte, dashboards, base de conhecimento e relatorio gerencial.
- `20260529 - Features.txt`: backlog complementar com STRY0079 e STRY0081 a STRY0089 para modelo academico do professor, cadastro academico pela Secretaria, ACLs, home do professor, redirecionamento por perfil, usuarios de teste e pesquisa de satisfacao.
- `20260601 - Features.txt`: backlog complementar com STRY0090 a STRY0099 para massa de dados academicos, listas administrativas, identidade visual da instancia, role operacional, formulario da Secretaria, choices/mapeamento e notificacoes.
- `20260602 - Features.txt`: backlog complementar com STRY0100 a STRY0104 para melhoria de Catalog Items, homes operacionais da Secretaria/Financeiro/Suporte e home gerencial do Gestor Academico.
- `Features - Pages/edtech_aulas.pdf`: backlog complementar com STRY0105 a STRY0109 para widgets base do portal, pagina de aulas, atividades pendentes, resumo academico do aluno e banner reutilizavel.
- `Features/Features.txt`: backlog consolidado oficial do projeto, reunindo as features dos arquivos de dias e as features extraidas da pasta `Features - Pages`.
- `padrao update sets.pdf`: padrao documentado de nomeacao de update sets por story e parent por modulo.
- Informacoes atualizadas pelo time em 2026-06-04 sobre as features ja implementadas, planejadas e em refinamento.

Quando houver conflito entre documentos, priorize:

1. O que ja foi implementado na instancia ServiceNow.
2. O backlog/features mais recente informado pelo time.
3. O enunciado do PDF.
4. Este `AGENTS.md` como guia consolidado.

## 3. O Que E O Sistema

O sistema e um **portal academico de servicos** em ServiceNow. Ele permite que alunos e professores abram solicitacoes de forma digital, acompanhem o andamento e recebam atendimento das areas corretas.

A entrega funcional atual sera centrada em um **portal unico customizado**, desenvolvido do zero em ServiceNow (Service Portal), para solicitantes e equipes internas.

Na pratica, o sistema deve oferecer:

- Portal unico customizado (Service Portal) para abertura, acompanhamento e atendimento de chamados (My Requests).
- Catalogos separados por departamento.
- Categorias para organizar os servicos.
- Record Producers para criar registros nas tabelas corretas.
- Variable Sets para padronizar os formularios.
- Grupos e roles para separar responsabilidades.
- Tabelas departamentais para Financeiro e Secretaria.
- Uso de `Incident [incident]` para Suporte Tecnico.
- Area ADM/operacional dentro do portal para Secretaria, Financeiro, Suporte e Gestor Academico.
- Widgets e paginas por perfil para aluno, professor, areas operacionais e gestor.
- Base para futuras notificacoes, SLAs, pesquisas e dashboards.

### 3.1 Identidade Visual Do Portal

O portal unico customizado deve seguir a identidade visual definida pelo time para a fase atual.

Paleta oficial, baseada no widget da Home do Aluno:

- `#fdfdfd`
- `#f2f3f4`
- `#d4dbe9`
- `#7c9fee`
- `#2665f9`
- `#0149f9`

Regra de uso da paleta:

- `#fdfdfd`: fundo principal das paginas e areas amplas.
- `#f2f3f4`: fundo secundario de secoes, blocos leves e cards neutros.
- `#d4dbe9`: bordas, divisores, estados desabilitados e fundos de apoio.
- `#7c9fee`: destaque secundario, hover, icones de apoio e elementos informativos.
- `#2665f9`: botoes principais, links importantes, badges de destaque e acoes do usuario.
- `#0149f9`: azul principal da marca, cabecalhos, elementos ativos e destaques fortes.

### 3.2 Skill De Design Para Portal E Widgets

Quando uma IA ou desenvolvedor atuar em paginas, widgets, theme, CSS ou UX do Portal EdTech, deve seguir este skill visual:

- Usar a paleta oficial `#fdfdfd`, `#f2f3f4`, `#d4dbe9`, `#7c9fee`, `#2665f9`, `#0149f9`.
- Seguir o padrao visual do widget da Home do Aluno como referencia principal de cards, espacamento, destaque azul e hierarquia visual.
- Manter o portal com aparencia limpa, academica e moderna, sem criar outra identidade visual paralela.
- Reaproveitar estilos, classes e estrutura dos widgets ja criados sempre que possivel.
- Evitar cores fora da paleta, exceto quando forem necessarias para status funcionais, como sucesso, alerta, erro ou criticidade.
- Garantir contraste suficiente entre texto e fundo, principalmente em botoes azuis e cards informativos.
- Manter linguagem visual consistente entre Home do Aluno, Home do Professor, pagina de Aulas, homes operacionais e dashboard do Gestor.
- Antes de considerar um widget pronto, validar se ele segue a paleta, se fica responsivo e se nao quebra o layout quando nao houver dados.

Referencia visual:

- Pasta `wireframes/portal_perfis`.
- Wireframe `wireframe_home_aluno.png`: home do aluno.
- Wireframe `wireframe_home_professor.png`: home do professor.
- Wireframe `wireframe_home_secretaria.png`: home operacional da Secretaria.
- Wireframe `wireframe_home_financeiro.png`: home operacional do Financeiro.
- Wireframe `wireframe_dashboard_gestor.png`: dashboard/home gerencial do Gestor Academico.

Observacao: a home operacional do Suporte deve seguir o mesmo padrao visual das homes operacionais, mesmo que a pasta atual nao tenha um wireframe especifico de Suporte.

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

Status baseado nas features informadas pelo time ate 2026-06-04.

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

### 7.3 Backlog Complementar Documentado

O arquivo `20260521 - Features-V1.txt` documenta:

| Story | Nome | Observacao |
|---|---|---|
| STRY0016 | Criar Update Sets Das Novas Areas | Expansao futura/organizacao |
| STRY0017 | Criar Grupos Das Novas Areas | Expansao futura |
| STRY0018 | Criar Roles Das Novas Areas | Expansao futura |
| STRY0019 | Criar Tabela de Cursos | Base para referencias e perfil academico |
| STRY0020 | Criar Tabela de Campus | Base para referencias e perfil academico |
| REFACTOR-001 | Padronizacao | Padrao de qualidade para RPs, variaveis e Variable Sets |

O arquivo `20260521 - Features-V2.txt` documenta:

| Story | Nome | Observacao |
|---|---|---|
| STRY0021 | Criar Record Producers Financeiros Core | Complementa servicos financeiros core |
| STRY0022 | Criar Record Producers Da Secretaria Core | Complementa documentos academicos core |

O arquivo `20260522 - Features.txt` documenta:

| Story | Nome | Observacao |
|---|---|---|
| STRY0023 | Criar Usuarios nos Grupos | Base para testes por perfil |
| STRY0024 | Atualizar Reference de Curso e Campus nos Record Producers | Padronizacao de dados academicos |
| STRY0025 | Preencher Automaticamente Dados do Aluno | Catalog Client Script + Script Include |
| STRY0026 | Restringir Acesso aos Record Producers por User Criteria | Visibilidade por perfil no portal |
| STRY0027 | Definir Read Only, Hidden e Mandatory no RP Emitir Comprovante de Matricula | Catalog UI Policy |
| STRY0028 | Vincular Catalogos Academicos ao Portal Unico | Publicacao no portal unico customizado (Service Portal) |
| STRY0029 | Incluir Meta Tags nos Record Producers Core | Busca e descoberta no portal |

O arquivo `20260522 - FIX.txt` documenta:

| Fix | Nome | Observacao |
|---|---|---|
| FIX001 | Aplicar Variable Sets no RP Solicitar Declaracao Academica | Corre o RP para usar os Variable Sets corretos da Secretaria |
| FIX002 | Corrigir Auto Preenchimento Contato e Retorno | Corrige preenchimento automatico de e-mail e telefone nos RPs |
| FIX003 | Consolidar Categorias Duplicadas | Mantem categorias oficiais de Financeiro e Secretaria |

O arquivo `20260525 - Features.txt` documenta:

| Story | Nome | Observacao |
|---|---|---|
| STRY0030 | Definir UI Policies nos Record Producers Financeiros | Controla campos por tipo de solicitacao financeira |
| STRY0031 | Ajustar Campos RA e Periodo no Perfil Academico | Ajusta label Matricula para RA e Periodo como Choice |
| STRY0032 | Atualizar Variavel Periodo nos Variable Sets Academicos | Alinha variavel `periodo` ao campo Choice do perfil academico |
| STRY0033 | Adicionar Dados Academicos ao RP Emitir Comprovante de Matricula | Garante dados academicos no comprovante |
| STRY0034 | Atualizar Tabela da Secretaria com Campos da Solicitacao Academica | Cria campos reais para atendimento interno da Secretaria |
| STRY0036 | Mapear Variaveis da Secretaria para Campos da Tabela por Record Producer | Copia variables dos RPs para campos de `u_edu_secretaria` |
| STRY0037 | Criar Assignment Rule para Solicitacoes da Secretaria | Roteia `u_edu_secretaria` para grupo Secretaria |
| STRY0038 | Criar Assignment Rule para Solicitacoes Financeiras | Roteia `u_edu_financeiro` para grupo Financeira |
| STRY0039 | Criar Notificacoes da Secretaria Academica | Notifica aluno sobre abertura, andamento, pendencia e conclusao |
| STRY0040 | Criar SLA de 3 Dias Uteis para Solicitacoes da Secretaria | Controla prazo de documentos da Secretaria |

O arquivo `20260525 - Feature-V1.txt` documenta:

| Story | Nome | Observacao |
|---|---|---|
| STRY0041 | Ajustar ACL do Script Include GetDadosAlunoAjax e Definir Roles para Aluno e Professor | Libera execucao segura do GlideAjax para perfis funcionais |
| STRY0042 | Atualizar Autopreenchimento de Dados do Aluno no GetDadosAlunoAjax | Corrige retorno de dados academicos para formularios |
| STRY0043 | Atualizar Tabela Financeira com Campos da Solicitacao | Cria/valida campos reais para atendimento financeiro |
| STRY0044 | Mapear Variaveis Financeiras para Campos da Tabela | Copia variaveis dos RPs para `u_edu_financeiro` |
| STRY0045 | Criar Assignment Rule para Solicitacoes Financeiras | Roteia `u_edu_financeiro` para grupo Financeira |
| STRY0046 | Criar Notificacoes Financeiras | Notifica aluno no ciclo de atendimento financeiro |
| STRY0047 | Criar SLA de 1 Dia Util para Solicitacoes Financeiras | Controla prazo financeiro conforme regra de negocio |

O arquivo `20260526 - Features.txt` documenta:

| Story | Nome | Observacao |
|---|---|---|
| STRY0048 | Criar Flow do Processo Interno da Secretaria | Inicia solicitacoes da Secretaria em estado Open via Flow Designer |
| STRY0049 | Validar Fechamento da Secretaria com Anexo ou Close Notes | Impede fechamento sem anexo ou justificativa em close notes |
| STRY0051 | Criar Flow do Processo Interno Financeiro | Inicia solicitacoes financeiras em estado Open via Flow Designer |
| STRY0052 | Validar Fechamento Financeiro com Anexo ou Close Notes | Exige anexo no envio de comprovante e close notes em fechamentos sem conclusao |
| STRY0053 | Criar Assignment Rule para Incidentes de Suporte AVA/Moodle | Roteia incidentes do RP AVA/Moodle para grupo Suporte |
| STRY0054 | Criar Notificacoes do Suporte Tecnico | Notifica abertura, andamento, pendencia e resolucao de incidentes de suporte |
| STRY0055 | Criar SLA para Atendimento de Suporte Tecnico | Cria SLA para incidentes AVA/Moodle, com pausa quando aguarda solicitante |

O arquivo `20260526 - Features-V1.txt` documenta:

| Story/Fix | Nome | Observacao |
|---|---|---|
| REFACTOR002 | Padronizar Formularios Internos de Financeiro e Secretaria | Padroniza layout interno das tabelas `u_edu_financeiro` e `u_edu_secretaria` |
| REFACTOR003 | Padronizar Mapeamento de Solicitante e Telefone nos Record Producers | Garante padrao de `u_solicitante`, `opened_by` e `u_telefone` |
| REFACTOR004 | Padronizar Localizacao dos Campos nos Record Producers | Organiza sequencia visual de campos no portal |
| STRY0056 | Criar My Request Filters para Solicitacoes Financeiras e Secretaria | Exibe solicitacoes customizadas em My Requests |

O arquivo `20260527 - Features.txt` documenta:

| Story | Nome | Observacao |
|---|---|---|
| STRY0057 | Ajustar Campos de Dispositivo e Navegador no Variable Set de Suporte | Troca campos para Select Box e reduz erro de digitacao |
| STRY0058 | Criar Catalog UI Policy para Campos Obrigatorios e Somente Leitura no Suporte | Define mandatory e read-only no RP de suporte |
| STRY0059 | Criar Catalog UI Policy para Simplificar RP Solicitar Historico Escolar | Oculta campos redundantes e trava dados academicos |
| STRY0060 | Criar Catalog UI Policy para Simplificar RP Solicitar Diploma | Simplifica formulario e remove campos desnecessarios |
| STRY0061 | Criar Catalog UI Policy para Simplificar RP Solicitar Declaracao Academica | Simplifica formulario e ajusta visibilidade de campos |

O arquivo `20260527 - Features-V1.txt` documenta:

| Story | Nome | Observacao |
|---|---|---|
| STRY0062 | Criar Wireframes e Templates do Portal Academico | Define estrutura visual inicial do portal unico |
| STRY0063 | Criar ACLs para Acompanhamento no Portal | Controla acesso de visualizacao/acompanhamento por perfil |
| STRY0064 | Criar Portal EdTech Base | Cria base estrutural do novo portal no Service Portal |

O arquivo `20260528 - Features.txt` documenta:

| Story/Fix | Nome | Observacao |
|---|---|---|
| STRY0065 | Criar Home do Aluno e Vincular ao Portal EdTech | Define homepage principal do aluno no portal |
| STRY0066 | Criar Pagina de Aulas do Aluno no Portal EdTech | Cria pagina dedicada para experiencia academica do aluno |
| STRY0067 | Copiar e Ajustar Widget SP Header Menu do Portal EdTech | Ajusta navegacao principal do portal customizado |
| STRY0068 | Criar Widget Reutilizavel de Perfil Academico do Usuario | Exibe dados academicos do usuario de forma reutilizavel |
| STRY0069 | Criar Update Sets Pais V2 por Modulo do Projeto EdTech | Estrutura governanca de update sets para fase V2 |
| REFACTOR005 | Padronizar Scripts dos Record Producers da Secretaria | Unifica padrao de script entre RPs da Secretaria |

O arquivo `20260528 - Features-V1.txt` documenta:

| Story/Fix | Nome | Observacao |
|---|---|---|
| STRY0070 | Clonar Theme do Service Portal para o Portal EdTech | Isola identidade visual do portal sem afetar `/sp` padrao |
| STRY0071 | Copiar e Ajustar Widget Quick Links Reutilizavel do Portal EdTech | Organiza acessos rapidos principais do aluno |
| STRY0072 | Copiar e Ajustar Widget My Requests para o Aluno | Ajusta acompanhamento de solicitacoes no portal unico |
| REFACTOR006 | Criar Campos Tecnicos de Suporte na Tabela Incident | Estrutura campos tecnicos para atendimento de suporte |
| REFACTOR007 | Mapear Variaveis Tecnicas do Record Producer de Suporte para Incident | Persiste dados tecnicos no incidente para operacao/SLA |
| STRY0073 | Ajustar SLA de Suporte para 3h de Resposta e 8h de Resolucao | Alinha SLA ao problema core do PDF |
| STRY0074 | Criar Dashboard Operacional da Secretaria | Cria visao gerencial da fila da Secretaria |
| STRY0075 | Criar Dashboard Operacional Financeiro | Cria visao gerencial da fila Financeira |
| STRY0076 | Criar Dashboard Operacional de Suporte Tecnico | Cria visao gerencial da fila de Suporte |
| STRY0077 | Criar Base de Conhecimento Academica Inicial | Estrutura artigos iniciais de autoatendimento |
| STRY0078 | Criar Relatorio Gerencial Consolidado do Gestor Academico | Consolida indicadores das areas core em visao unica |

O arquivo `20260529 - Features.txt` documenta:

| Story | Nome | Observacao |
|---|---|---|
| STRY0079 | Ajustar Modelo Academico do Professor | Prepara perfil academico/profissional do professor para portal e filtros |
| STRY0081 | Criar Home do Professor no Portal EdTech | Cria experiencia inicial especifica para professores |
| STRY0082 | Redirecionar Home do Portal por Perfil do Usuario | Direciona aluno/professor para a home correta |
| STRY0083 | Permitir Cadastro Academico pela Secretaria | Permite que Secretaria cadastre/atualize dados academicos |
| STRY0084 | Criar ACLs para Cadastro Academico da Secretaria | Controla permissao de escrita da Secretaria no cadastro academico |
| STRY0085 | Criar ACLs de Consulta Gerencial para Gestor Academico | Permite visao gerencial sem liberar edicao indevida |
| STRY0086 | Atualizar Usuarios de Teste com Nomes e Dados Realistas por Grupo | Melhora testes e apresentacao por perfil |
| STRY0087 | Criar Pesquisa de Satisfacao Apos Encerramento da Solicitacao | Mede qualidade apos fechamento do atendimento |
| STRY0088 | Criar Widget de Pesquisa de Satisfacao no Portal | Exibe pesquisa de satisfacao no portal unico |
| STRY0089 | Criar Relatorios de Satisfacao por Area e para o Gestor | Consolida indicadores de satisfacao por departamento |

O arquivo `20260601 - Features.txt` documenta:

| Story | Nome | Observacao |
|---|---|---|
| STRY0090 | Criar Dados das Novas Tabelas Academicas | Cria massa de dados realista para portal, professor e apresentacao |
| STRY0091 | Criar Listas Administrativas da Secretaria | Organiza filas internas da Secretaria no backoffice |
| STRY0092 | Criar Listas Administrativas do Financeiro | Organiza filas internas do Financeiro no backoffice |
| STRY0093 | Criar Listas de Cadastros Academicos | Cria listas para cursos, campus, disciplinas, turmas, aulas e atividades |
| STRY0094 | Criar Listas Gerenciais para Gestao Academica | Cria consultas gerenciais de atendimento e dados academicos |
| STRY0095 | Personalizar Identidade Visual da Instancia ServiceNow | Ajusta nome, icone, logo e apresentacao da instancia |
| STRY0096 | Criar Role Operacional de Atendimento para Secretaria e Financeiro | Libera atendimento operacional sem `admin` amplo |
| STRY0097 | Padronizar Formulario Interno da Secretaria | Organiza dados da solicitacao e atendimento interno |
| STRY0098 | Padronizar Choices e Mapeamento dos Documentos da Secretaria | Garante labels amigaveis e values corretos para documentos |
| STRY0099 | Criar Notificacoes In-App e Revisar E-mails da Secretaria | Ajusta notificacoes da Secretaria para aluno e equipe |

O arquivo `20260602 - Features.txt` documenta:

| Story | Nome | Observacao |
|---|---|---|
| STRY0100 | Melhorar Short Descriptions e Icones dos Catalog Items | Melhora descoberta dos servicos no portal |
| STRY0101 | Criar Home Operacional da Secretaria no Portal EdTech | Cria area ADM/operacional da Secretaria no portal |
| STRY0102 | Criar Home Operacional do Financeiro no Portal EdTech | Cria area ADM/operacional do Financeiro no portal |
| STRY0103 | Criar Home Operacional do Suporte no Portal EdTech | Cria area ADM/operacional do Suporte no portal |
| STRY0104 | Criar Home Gerencial do Gestor Academico no Portal EdTech | Cria home/dashboard gerencial do Gestor Academico no portal |

O arquivo `Features - Pages/edtech_aulas.pdf` documenta:

| Story | Nome | Observacao |
|---|---|---|
| STRY0105 | Padronizar Widgets Base do Portal EdTech | Define padrao de widgets reutilizaveis do portal, seguindo a identidade visual da Home do Aluno |
| STRY0106 | Criar Widget EDTech - Minhas Aulas | Exibe aulas do aluno logado na pagina de aulas |
| STRY0107 | Criar Widget EDTech - Atividades Pendentes | Exibe atividades pendentes do aluno logado |
| STRY0108 | Criar Widget EDTech - Resumo Academico do Aluno | Exibe indicadores academicos do aluno, como aulas da semana e atividades por status |
| STRY0109 | Criar Widget Reutilizavel de Banner de Aulas no Portal EdTech | Cria banner reutilizavel para a area de aulas com dados academicos do aluno |

Observacao: o backlog possui saltos de numeracao (ex.: STRY0035, STRY0050 e STRY0080 nao aparecem nos arquivos). Manter exatamente a numeracao usada no backlog oficial do time.

Antes de afirmar que uma dessas stories esta pronta, conferir a instancia ServiceNow e o update set correspondente.

### 7.4 O Que Esta Pronto Na Pratica

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
- Record Producers financeiros adicionais, se ainda nao validados na instancia.
- Record Producers adicionais da Secretaria, se ainda nao validados na instancia.
- Vinculacao final dos catalogos academicos ao portal do aluno, se ainda nao validada.
- User Criteria final por perfil, se ainda nao validado.
- Mapeamento final das variaveis para campos reais nas tabelas departamentais, se ainda nao validado.
- Assignment Rules de Secretaria e Financeiro, se ainda nao validadas.
- SLA e notificacoes da Secretaria, se ainda nao validados.
- Flows internos de Secretaria e Financeiro (STRY0048 e STRY0051), se ainda nao validados.
- Validacoes de fechamento com anexo/close notes (STRY0049 e STRY0052), se ainda nao validadas.
- Assignment Rule, notificacoes e SLA de Suporte (STRY0053, STRY0054 e STRY0055), se ainda nao validados.
- My Request Filters de Financeiro e Secretaria (STRY0056), se ainda nao validados no portal.
- Ajustes de UX do suporte (STRY0057 e STRY0058), se ainda nao validados com aluno/professor.
- UI Policies de simplificacao da Secretaria (STRY0059, STRY0060 e STRY0061), se ainda nao validadas ponta a ponta.
- Wireframes, ACLs e portal base da fase V2 (STRY0062, STRY0063 e STRY0064), se ainda nao validados.
- Home do aluno, pagina de aulas e widgets V2 (STRY0065, STRY0066, STRY0067 e STRY0068), se ainda nao validados.
- Governanca V2 de update sets (STRY0069), se ainda nao validada na instancia.
- Theme e widgets de navegacao/requests da V2 (STRY0070, STRY0071 e STRY0072), se ainda nao validados.
- SLA de suporte 3h/8h (STRY0073), se ainda nao validado em execucao real.
- Dashboards operacionais por area (STRY0074, STRY0075 e STRY0076), se ainda nao homologados.
- Base de conhecimento e relatorio consolidado do gestor (STRY0077 e STRY0078), se ainda nao homologados.
- Refactors recentes (REFACTOR005, REFACTOR006 e REFACTOR007), se ainda nao revisados ponta a ponta.
- Modelo academico do professor e home do professor (STRY0079 e STRY0081), se ainda nao validados.
- Redirecionamento de home por perfil (STRY0082), se ainda nao validado com aluno e professor.
- Cadastro academico pela Secretaria e ACLs associadas (STRY0083 e STRY0084), se ainda nao validados.
- ACLs de consulta gerencial para Gestor Academico (STRY0085), se ainda nao validadas.
- Usuarios de teste com nomes/dados realistas (STRY0086), se ainda nao revisados para apresentacao.
- Pesquisa de satisfacao, widget e relatorios de satisfacao (STRY0087, STRY0088 e STRY0089), se ainda nao homologados ponta a ponta.
- Dados das novas tabelas academicas (STRY0090), se ainda nao criados/validados.
- Listas administrativas da Secretaria, Financeiro, cadastros academicos e gestao academica (STRY0091 a STRY0094), se ainda nao validadas por perfil.
- Personalizacao visual da instancia (STRY0095), se ainda nao aplicada.
- Role operacional de atendimento para Secretaria e Financeiro (STRY0096), se ainda nao validada sem `admin`.
- Formulario interno, choices/mapeamento e notificacoes da Secretaria (STRY0097, STRY0098 e STRY0099), se ainda nao homologados.
- Melhoria de short descriptions/icones dos Catalog Items (STRY0100), se ainda nao revisada no portal.
- Homes operacionais da Secretaria, Financeiro e Suporte (STRY0101, STRY0102 e STRY0103), se ainda nao validadas.
- Home gerencial do Gestor Academico (STRY0104), se ainda nao validada.
- Widgets base e widgets da pagina de Aulas (STRY0105 a STRY0109), se ainda nao validados no portal com usuario aluno.
- Uso da paleta oficial e dos wireframes de `wireframes/portal_perfis`, se ainda nao aplicado nas paginas/widgets.
- Publicacao final do portal unico customizado com navegacao/homologacao completa, se ainda nao validada.

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
- Gestores Academicos podem receber `admin` apenas na PDI/apresentacao, se necessario para demonstrar o portal unico e fluxos internos.
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
- `RA/Matricula`: label esperada `RA` apos STRY0031, mantendo o nome tecnico se ja estiver em uso.
- `Registro Funcional`.
- `Curso`.
- `Campus`.
- `Periodo`: deve ser Choice apos STRY0031, com opcoes `Tecnologo`, `Licenciatura` e `Bacharelado`.
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
- Nome tecnico citado nos documentos iniciais: `x_edu_secretaria`.
- Nome tecnico usado nas stories mais recentes: `u_edu_secretaria`.
- Estende `Task [task]`.

Observacao: quando houver divergencia entre `x_edu_secretaria` e `u_edu_secretaria`, conferir a instancia antes de criar scripts, ACLs, Assignment Rules ou SLAs. Nas stories de 2026-05-25, usar `u_edu_secretaria` como referencia operacional.

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
- Backlog core tambem considera `Enviar Comprovante de Pagamento` e `Contestar Multa por Atraso de Boleto`.

Secretaria:

- `Emitir Comprovante de Matricula`.
- Cria registro em `Solicitacao Secretaria [x_edu_secretaria]`.
- Fica no `Catalogo da Secretaria Academica`.
- Fica na categoria `Documentos e Declaracoes`.
- Backlog core tambem considera `Solicitar Declaracao Academica`, `Solicitar Historico Escolar` e `Solicitar Diploma`.

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

- Sistema afetado: AVA/Moodle, Portal Academico, Video/Aula, Envio de Atividade, Outro.
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
- Forma de entrega.
- Observacoes adicionais.

Opcoes importantes:

- Comprovante de matricula.
- Declaracao academica.
- Historico escolar.
- Diploma.
- Outro.

Regra de modelagem atual: `RA`, `Curso`, `Campus` e `Periodo` pertencem ao Variable Set `Dados Academicos do Solicitante`, nao ao `Detalhes da Solicitacao Academica`, para evitar duplicidade.

Choices de `finalidade_documento` apos STRY0034:

- Comprovacao academica geral.
- Estagio.
- Emprego / Processo seletivo.
- Bolsa / Financiamento.
- Transferencia.
- Orgao publico.
- Consulado / Visto.
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
- UI Policies financeiras por tipo de solicitacao, conforme STRY0030.
- Assignment Rule financeira, conforme STRY0038.
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
- Campos reais em `u_edu_secretaria` e mapeamento dos RPs para a tabela, conforme STRY0034 e STRY0036.
- Assignment Rule da Secretaria, conforme STRY0037.
- Notificacoes da Secretaria, conforme STRY0039.
- SLA de ate 3 dias uteis.
- Dashboard de documentos e prazos.
- Pesquisa de satisfacao.

### 12.4 Area ADM/Operacional No Portal

Objetivo:

- Levar tambem a operacao interna para o portal unico, nao apenas a abertura de chamados pelo aluno.
- Criar homes especificas para Secretaria, Financeiro, Suporte e Gestor Academico.
- Permitir que cada area acompanhe filas, pendencias, atrasos, SLA e solicitacoes recentes em uma experiencia visual propria.

Referencias de wireframe:

- `wireframes/portal_perfis/wireframe_home_secretaria.png`.
- `wireframes/portal_perfis/wireframe_home_financeiro.png`.
- `wireframes/portal_perfis/wireframe_dashboard_gestor.png`.
- `wireframes/portal_perfis/wireframe_home_aluno.png`.
- `wireframes/portal_perfis/wireframe_home_professor.png`.

Stories relacionadas:

- `STRY0101 - Criar Home Operacional da Secretaria no Portal EdTech`.
- `STRY0102 - Criar Home Operacional do Financeiro no Portal EdTech`.
- `STRY0103 - Criar Home Operacional do Suporte no Portal EdTech`.
- `STRY0104 - Criar Home Gerencial do Gestor Academico no Portal EdTech`.

Regra de acesso:

- Cada home operacional deve respeitar roles e ACLs.
- Secretaria acessa somente sua home/fila.
- Financeiro acessa somente sua home/fila.
- Suporte acessa somente sua home/fila.
- Gestor Academico acessa indicadores consolidados, preferencialmente em modo somente leitura.
- Aluno e Professor nao devem acessar homes operacionais internas.

### 12.5 Pagina De Aulas E Widgets Academicos Do Aluno

Objetivo:

- Criar uma experiencia academica dentro do portal, alem da abertura de chamados.
- Permitir que o aluno veja aulas, atividades pendentes e resumo academico em widgets simples.
- Reaproveitar o padrao visual da Home do Aluno, mantendo a paleta oficial do portal.

Stories relacionadas:

- `STRY0105 - Padronizar Widgets Base do Portal EdTech`.
- `STRY0106 - Criar Widget EDTech - Minhas Aulas`.
- `STRY0107 - Criar Widget EDTech - Atividades Pendentes`.
- `STRY0108 - Criar Widget EDTech - Resumo Academico do Aluno`.
- `STRY0109 - Criar Widget Reutilizavel de Banner de Aulas no Portal EdTech`.

Widgets esperados:

- `EDTech - Minhas Aulas`.
- `EDTech - Atividades Pendentes`.
- `EDTech - Resumo Academico Aluno`.
- `EDTech - Banner de Area Academica`.

Tabelas envolvidas:

- `u_edu_perfil_academico`: identifica o aluno logado, curso, RA, campus e periodo.
- `u_edu_aula`: base esperada para aulas exibidas na pagina de aulas, se existir na instancia.
- `u_edu_atividade`: base esperada para atividades pendentes, em correcao e corrigidas.
- `sys_user`: usuario logado usado como referencia para buscar o perfil academico.

Regras de design:

- Usar a paleta oficial do portal: `#fdfdfd`, `#f2f3f4`, `#d4dbe9`, `#7c9fee`, `#2665f9`, `#0149f9`.
- Seguir o visual da Home do Aluno para cards, indicadores, botoes e destaque azul.
- Exibir estado vazio quando nao houver aulas ou atividades.
- Nao quebrar a pagina se o aluno nao tiver perfil academico cadastrado.
- Nao pedir que o aluno digite RA, curso, campus ou periodo se esses dados ja existirem em `u_edu_perfil_academico`.

## 13. Backlog Atual Consolidado

### 13.1 Features Ja Implementadas

As features STRY0001 a STRY0015 sao consideradas implementadas conforme informacao do time.

## 14. Proximas Entregas Dos Problemas Core

### 14.1 Ordem Recomendada Do Backlog Atual

Considerando as dependencias das stories mais recentes, a ordem recomendada e:

1. `STRY0023 - Criar Usuarios nos Grupos`.
2. `STRY0024 - Atualizar Reference de Curso e Campus nos Record Producers`.
3. `STRY0025 - Preencher Automaticamente Dados do Aluno com Catalog Client Script e Script Include`.
4. `STRY0026 - Restringir Acesso aos Record Producers por User Criteria`.
5. `STRY0027 - Definir Read Only, Hidden e Mandatory no RP Emitir Comprovante de Matricula`.
6. `STRY0028 - Vincular Catalogos Academicos ao Portal Unico`.
7. `STRY0029 - Incluir Meta Tags nos Record Producers Core`.
8. `STRY0030 - Definir UI Policies nos Record Producers Financeiros`.
9. `STRY0031 - Ajustar Campos RA e Periodo no Perfil Academico`.
10. `STRY0032 - Atualizar Variavel Periodo nos Variable Sets Academicos`.
11. `STRY0033 - Adicionar Dados Academicos ao RP Emitir Comprovante de Matricula`.
12. `STRY0034 - Atualizar Tabela da Secretaria com Campos da Solicitacao Academica`.
13. `STRY0036 - Mapear Variaveis da Secretaria para Campos da Tabela por Record Producer`.
14. `STRY0037 - Criar Assignment Rule para Solicitacoes da Secretaria`.
15. `STRY0038 - Criar Assignment Rule para Solicitacoes Financeiras`.
16. `STRY0039 - Criar Notificacoes da Secretaria Academica`.
17. `STRY0040 - Criar SLA de 3 Dias Uteis para Solicitacoes da Secretaria`.
18. `STRY0041 - Ajustar ACL do Script Include GetDadosAlunoAjax e Definir Roles para Aluno e Professor`.
19. `STRY0042 - Atualizar Autopreenchimento de Dados do Aluno no GetDadosAlunoAjax`.
20. `STRY0043 - Atualizar Tabela Financeira com Campos da Solicitacao`.
21. `STRY0044 - Mapear Variaveis Financeiras para Campos da Tabela`.
22. `STRY0045 - Criar Assignment Rule para Solicitacoes Financeiras`.
23. `STRY0046 - Criar Notificacoes Financeiras`.
24. `STRY0047 - Criar SLA de 1 Dia Util para Solicitacoes Financeiras`.
25. `STRY0048 - Criar Flow do Processo Interno da Secretaria`.
26. `STRY0049 - Validar Fechamento da Secretaria com Anexo ou Close Notes`.
27. `STRY0051 - Criar Flow do Processo Interno Financeiro`.
28. `STRY0052 - Validar Fechamento Financeiro com Anexo ou Close Notes`.
29. `STRY0053 - Criar Assignment Rule para Incidentes de Suporte AVA/Moodle`.
30. `STRY0054 - Criar Notificacoes do Suporte Tecnico`.
31. `STRY0055 - Criar SLA para Atendimento de Suporte Tecnico`.
32. `STRY0056 - Criar My Request Filters para Solicitacoes Financeiras e Secretaria`.
33. `STRY0057 - Ajustar Campos de Dispositivo e Navegador no Variable Set de Suporte`.
34. `STRY0058 - Criar Catalog UI Policy para Campos Obrigatorios e Somente Leitura no Suporte`.
35. `STRY0059 - Criar Catalog UI Policy para Simplificar RP Solicitar Historico Escolar`.
36. `STRY0060 - Criar Catalog UI Policy para Simplificar RP Solicitar Diploma`.
37. `STRY0061 - Criar Catalog UI Policy para Simplificar RP Solicitar Declaracao Academica`.
38. `STRY0062 - Criar Wireframes e Templates do Portal Academico`.
39. `STRY0063 - Criar ACLs para Acompanhamento no Portal`.
40. `STRY0064 - Criar Portal EdTech Base`.
41. `STRY0065 - Criar Home do Aluno e Vincular ao Portal EdTech`.
42. `STRY0066 - Criar Pagina de Aulas do Aluno no Portal EdTech`.
43. `STRY0067 - Copiar e Ajustar Widget SP Header Menu do Portal EdTech`.
44. `STRY0068 - Criar Widget Reutilizavel de Perfil Academico do Usuario`.
45. `STRY0069 - Criar Update Sets Pais V2 por Modulo do Projeto EdTech`.
46. `STRY0070 - Clonar Theme do Service Portal para o Portal EdTech`.
47. `STRY0071 - Copiar e Ajustar Widget Quick Links Reutilizavel do Portal EdTech`.
48. `STRY0072 - Copiar e Ajustar Widget My Requests para o Aluno`.
49. `REFACTOR005 - Padronizar Scripts dos Record Producers da Secretaria`.
50. `REFACTOR006 - Criar Campos Tecnicos de Suporte na Tabela Incident`.
51. `REFACTOR007 - Mapear Variaveis Tecnicas do Record Producer de Suporte para Incident`.
52. `STRY0073 - Ajustar SLA de Suporte para 3h de Resposta e 8h de Resolucao`.
53. `STRY0074 - Criar Dashboard Operacional da Secretaria`.
54. `STRY0075 - Criar Dashboard Operacional Financeiro`.
55. `STRY0076 - Criar Dashboard Operacional de Suporte Tecnico`.
56. `STRY0077 - Criar Base de Conhecimento Academica Inicial`.
57. `STRY0078 - Criar Relatorio Gerencial Consolidado do Gestor Academico`.
58. `STRY0079 - Ajustar Modelo Academico do Professor`.
59. `STRY0081 - Criar Home do Professor no Portal EdTech`.
60. `STRY0082 - Redirecionar Home do Portal por Perfil do Usuario`.
61. `STRY0083 - Permitir Cadastro Academico pela Secretaria`.
62. `STRY0084 - Criar ACLs para Cadastro Academico da Secretaria`.
63. `STRY0085 - Criar ACLs de Consulta Gerencial para Gestor Academico`.
64. `STRY0086 - Atualizar Usuarios de Teste com Nomes e Dados Realistas por Grupo`.
65. `STRY0087 - Criar Pesquisa de Satisfacao Apos Encerramento da Solicitacao`.
66. `STRY0088 - Criar Widget de Pesquisa de Satisfacao no Portal`.
67. `STRY0089 - Criar Relatorios de Satisfacao por Area e para o Gestor`.
68. `STRY0090 - Criar Dados das Novas Tabelas Academicas`.
69. `STRY0091 - Criar Listas Administrativas da Secretaria`.
70. `STRY0092 - Criar Listas Administrativas do Financeiro`.
71. `STRY0093 - Criar Listas de Cadastros Academicos`.
72. `STRY0094 - Criar Listas Gerenciais para Gestao Academica`.
73. `STRY0095 - Personalizar Identidade Visual da Instancia ServiceNow`.
74. `STRY0096 - Criar Role Operacional de Atendimento para Secretaria e Financeiro`.
75. `STRY0097 - Padronizar Formulario Interno da Secretaria`.
76. `STRY0098 - Padronizar Choices e Mapeamento dos Documentos da Secretaria`.
77. `STRY0099 - Criar Notificacoes In-App e Revisar E-mails da Secretaria`.
78. `STRY0100 - Melhorar Short Descriptions e Icones dos Catalog Items`.
79. `STRY0101 - Criar Home Operacional da Secretaria no Portal EdTech`.
80. `STRY0102 - Criar Home Operacional do Financeiro no Portal EdTech`.
81. `STRY0103 - Criar Home Operacional do Suporte no Portal EdTech`.
82. `STRY0104 - Criar Home Gerencial do Gestor Academico no Portal EdTech`.
83. `STRY0105 - Padronizar Widgets Base do Portal EdTech`.
84. `STRY0106 - Criar Widget EDTech - Minhas Aulas`.
85. `STRY0107 - Criar Widget EDTech - Atividades Pendentes`.
86. `STRY0108 - Criar Widget EDTech - Resumo Academico do Aluno`.
87. `STRY0109 - Criar Widget Reutilizavel de Banner de Aulas no Portal EdTech`.

Motivo da ordem:

- Primeiro criar usuarios/grupos de teste para validar perfis reais.
- Depois corrigir referencias de Curso/Campus, porque o autopreenchimento depende de dados padronizados.
- Depois preencher dados automaticamente.
- Depois restringir visibilidade por perfil.
- Depois travar/ocultar campos nos formularios.
- Depois publicar os catalogos no portal.
- Por fim melhorar busca com Meta Tags.
- Em seguida, amadurecer os processos internos: campos nas tabelas, mapeamentos, Assignment Rules, notificacoes, SLA e dashboards.
- Fase do dia 2026-05-26: consolidar flows internos, validacoes de fechamento e ciclo completo de suporte (assignment + notificacoes + SLA).
- Fase do dia 2026-05-27: fortalecer a experiencia do portal (My Requests + UI Policies de simplificacao em Suporte e Secretaria).
- Fase do dia 2026-05-28: consolidar Portal V2 (paginas/widgets/theme), finalizar SLA core de suporte e estruturar visao gerencial (dashboards + relatorio + base de conhecimento).
- Fase do dia 2026-05-29: completar experiencia por perfil (aluno/professor), cadastro academico pela Secretaria, ACLs gerenciais, usuarios realistas e pesquisa/relatorios de satisfacao.
- Fase do dia 2026-06-01: criar dados academicos, listas administrativas/gerenciais, role operacional, formulario da Secretaria, choices/mapeamento e notificacoes.
- Fase do dia 2026-06-02: melhorar catalog items e criar area ADM/operacional no portal para Secretaria, Financeiro, Suporte e Gestor.
- Fase do dia 2026-06-04: padronizar widgets base do portal e criar a experiencia de Aulas do Aluno com banner, minhas aulas, atividades pendentes e resumo academico.

### 14.2 Financeiro

Criar ou revisar Record Producers:

- `Solicitar 2a Via de Boleto`: ja existe, mas deve usar o Variable Set financeiro.
- `Enviar Comprovante de Pagamento`.
- `Contestar Multa por Atraso de Boleto`.
- `Tirar Duvida Financeira`, se o time quiser separar esse atendimento.

Resultado esperado:

- O aluno nao depende mais de e-mail para boleto ou comprovante.
- O Financeiro recebe dados estruturados.
- O sistema fica pronto para SLA, notificacao e relatorio.

### 14.3 Secretaria Academica

Criar ou revisar Record Producers:

- `Emitir Comprovante de Matricula`: ja existe, mas deve usar o Variable Set da Secretaria.
- `Solicitar Declaracao Academica`.
- `Solicitar Historico Escolar`.
- `Solicitar Diploma`.

Resultado esperado:

- O aluno nao precisa ir presencialmente para pedir documentos simples.
- A Secretaria recebe solicitacoes organizadas.
- O sistema fica pronto para SLA, notificacao e relatorio.

### 14.4 Suporte Tecnico

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
- `EDTECH_05_PORTAL`: catalogos, categorias, portal unico customizado, UX e Variable Sets comuns.
- `EDTECH_06_RELATORIOS`: relatorios e dashboards.
- `EDTECH_07_AUTOMACOES`: flows, assignment, notificacoes, SLA e pesquisas.

Update sets pais V2 (backlog da segunda fase do portal):

- `EDTECH_01_CORE_V2`: ajustes core da fase de portal unico.
- `EDTECH_02_SUPORTE_V2`: evolucoes de suporte para portal/dashboards/SLA final.
- `EDTECH_03_FINANCEIRO_V2`: evolucoes financeiras da fase V2.
- `EDTECH_04_SECRETARIA_V2`: evolucoes da secretaria na fase V2.
- `EDTECH_05_PORTAL_V2`: paginas, widgets, tema e experiencia do portal EdTech.

Regras:

- Nao desenvolver no `Default`.
- Nao desenvolver diretamente no update set pai quando houver story filha.
- A story filha deve ficar como **Current** durante o desenvolvimento.
- O campo **Parent** deve apontar para o update set pai do modulo.
- No final, os pais podem ser agrupados em uma release/batch.
- Em desenvolvimento paralelo, cada dev deve trabalhar em sua propria story/update set.
- Evitar que dois devs alterem o mesmo Record Producer, Variable Set, Catalog Client Script, UI Policy ou User Criteria ao mesmo tempo.
- Um update set de refatoracao final pode existir para ajustes pequenos de padrao, labels, ordem de campos, descricoes, Meta Tags e limpeza visual.
- Nao usar um update set de refatoracao para corrigir trabalho grande feito no update set errado ou conflitos de modelagem.

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
| Dev 5 | Portal / Qualidade | Portal unico customizado, UX, pesquisas, relatorios, dashboards e apoio a apresentacao |

Cada desenvolvedor deve testar sua entrega no portal unico e depois validar o fluxo integrado.

## 17. Boas Praticas ServiceNow Para Este Projeto

- Preferir **Flow Designer** para automacoes de processo.
- Preferir **Assignment Rules** para roteamento simples de grupo em tabelas Task/custom, como `u_edu_secretaria` e `u_edu_financeiro`.
- Usar **Business Rules** apenas quando a logica server-side exigir.
- Evitar queries sincronas no client-side.
- Usar **GlideAjax** para buscar dados server-side em Client Scripts.
- Evitar hardcode de `sys_id`.
- Nao alterar tabelas nativas sem necessidade.
- Usar `sys_user` para acesso/identidade.
- Usar `u_edu_perfil_academico` para dados academicos/profissionais complementares.
- Manter catalogos, categorias e fluxos separados por departamento.
- Testar sempre pelo portal unico, nao apenas pelo backend.
- Usar linguagem clara para aluno/professor.
- Em Record Producer Script, mapear variables para campos reais da tabela quando a equipe interna precisar filtrar, reportar, aplicar SLA ou atender diretamente pelo registro.
- Nao definir `assignment_group` hardcoded no script do Record Producer quando houver Assignment Rule responsavel pelo roteamento.
- Para notificacoes, usar apenas informacoes publicas e nunca incluir `work_notes` no template enviado ao aluno.

### 17.1 Padronizacao REFACTOR-001

Estas regras devem ser consideradas padrao de desenvolvimento para Record Producers, variaveis e Variable Sets, principalmente na Secretaria Academica:

- Todos os Record Producers da Secretaria devem possuir **Short Description** clara e concisa orientando o usuario.
- O campo **Description** deve ser preenchido detalhando regras, prazos de entrega do documento e orientacoes do servico.
- Todos os nomes tecnicos (`Name`) das variaveis devem seguir estritamente o padrao `snake_case`, com letras minusculas, sem acentos, sem espacos e separados por `_`.
- Todas as perguntas ao usuario (`Question/Label`) devem iniciar com letra maiuscula e estar semanticamente corretas.
- Validar e garantir que os Variable Sets estejam corretamente associados e visiveis dentro do respectivo catalogo e categoria no portal.
- Evitar duplicidade de campos locais quando o campo ja existir em um Variable Set reutilizavel.
- Para campos de cadastro e dados academicos, preferir tabelas e referencias padronizadas em vez de texto livre quando existir tabela mestre.
- Dados conhecidos do usuario logado, como solicitante, RA, curso, periodo, e-mail e telefone, devem ser preenchidos automaticamente quando possivel.
- Campos preenchidos automaticamente e sensiveis para integridade do processo devem ficar somente leitura para o aluno, quando fizer sentido para o fluxo.
- Variable Sets reutilizaveis devem ser aplicados aos Record Producers corretos. Evitar campos locais duplicados fora dos Variable Sets.
- `Dados Academicos do Solicitante` deve concentrar `RA`, `Curso`, `Campus` e `Periodo`.
- `Detalhes da Solicitacao Academica` deve concentrar dados do pedido, como `tipo_documento`, `forma_entrega`, `finalidade_documento` e `observacoes_adicionais`.

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
- Homes por perfil estao acessiveis para aluno, professor, Secretaria, Financeiro, Suporte e Gestor, conforme permissao.
- Area ADM/operacional do portal foi validada para equipes internas.
- Paleta oficial do portal foi aplicada nos widgets/paginas principais.
- Pagina de Aulas do Aluno possui widgets de banner, minhas aulas, atividades pendentes e resumo academico, quando essas stories forem consideradas prontas.
- Widgets novos seguem o padrao visual da Home do Aluno e usam a paleta oficial do portal.

## 20. Pontos De Atencao

- Nao usar `Incident` para Financeiro ou Secretaria.
- Nao expor nomes tecnicos ao aluno.
- Nao misturar catalogos e categorias entre departamentos.
- Validar se `u_edu_perfil_academico` esta sendo usado como tabela complementar, nao como substituta do `sys_user`.
- Campos permanentes ficam em tabela; campos especificos da solicitacao ficam em variaveis/registro da solicitacao.
- SLA, notificacoes, dashboards e pesquisa de satisfacao devem ser apresentados como parte do MVP somente depois de validados na instancia.

## 21. Resumo Para Apresentacao

O projeto entrega uma plataforma ServiceNow para atendimento academico, com foco inicial em Suporte Tecnico, Financeiro e Secretaria Academica, com frente principal de entrega em um **portal unico customizado**, desenvolvido do zero.

O aluno passa a abrir solicitacoes pelo portal, usando formularios padronizados e separados por area. O Suporte registra incidentes tecnicos estruturados em `Incident [incident]`. O Financeiro possui Record Producers para boleto, comprovante de pagamento e contestacao de multa, com ajustes de UI Policy e roteamento previstos para o grupo `Financeira`. A Secretaria possui Record Producers para documentos academicos, com dados do aluno preenchidos automaticamente, campos reais em `u_edu_secretaria`, mapeamento das variaveis para a tabela, Assignment Rule para o grupo `Secretaria`, notificacoes e SLA de 3 dias uteis em evolucao.

O estado atual do sistema cobre a base principal do MVP: grupos, roles, tabelas, catalogos, categorias, Record Producers, Variable Sets, autopreenchimento, controle de visibilidade por perfil e padronizacao de dados academicos. O backlog consolidado em `Features/Features.txt` agora inclui stories ate `STRY0109`, com evolucoes de fluxo interno, validacoes de fechamento, assignment, notificacoes, SLA, portal V2 (paginas/widgets/theme), dashboards operacionais por area, base de conhecimento, relatorio gerencial consolidado, cadastro academico pela Secretaria, experiencia do professor, pesquisa de satisfacao, listas administrativas, homes operacionais por area, identidade visual do portal e pagina de Aulas do Aluno com widgets academicos.

### 21.1 O Que O Sistema Faz No MVP

No MVP, o sistema cobre o ciclo principal de atendimento academico da instituicao:

- Aluno e professor acessam um portal unico customizado.
- O portal direciona a experiencia conforme o perfil do usuario.
- Aluno abre solicitacoes financeiras, academicas e de suporte tecnico.
- Professor possui home propria e pode acessar recursos/servicos adequados ao seu perfil.
- Aluno possui experiencia academica no portal, com pagina de aulas, atividades pendentes, resumo academico e banner com dados do curso.
- Suporte Tecnico recebe incidentes sobre AVA/Moodle, aulas, videos, portal e envio de atividades.
- Financeiro recebe demandas de boleto, comprovante, contestacao de multa e duvidas financeiras.
- Secretaria recebe solicitacoes de documentos academicos e pode apoiar cadastro academico.
- Secretaria, Financeiro e Suporte possuem area ADM/operacional no portal para acompanhar filas, pendencias, atrasos e tarefas recentes.
- Gestor Academico possui home gerencial para acompanhar volume, SLA, atrasos, satisfacao e indicadores consolidados.
- Cada area possui grupo responsavel, regras de roteamento e estrutura de atendimento.
- Dados academicos do usuario podem ser reaproveitados nos formularios para reduzir digitacao.
- O usuario acompanha suas solicitacoes pelo portal em My Requests.
- Equipes internas usam registros estruturados para atender, atualizar estado e encerrar solicitacoes.
- Gestores Academicos conseguem acompanhar indicadores, relatorios e satisfacao por area.
- O sistema passa a ter base para SLA, notificacoes, dashboards, base de conhecimento e pesquisa de satisfacao.
- O portal segue a paleta oficial `#fdfdfd`, `#f2f3f4`, `#d4dbe9`, `#7c9fee`, `#2665f9`, `#0149f9`.
- A paleta deve ser aplicada conforme o padrao visual do widget da Home do Aluno.
- Os wireframes de `wireframes/portal_perfis` orientam as homes/widgets por perfil.

Com isso, o MVP resolve o problema central do TCC: tirar o atendimento academico do e-mail/processo manual e levar para um fluxo digital, rastreavel, separado por area e mensuravel dentro do ServiceNow.
