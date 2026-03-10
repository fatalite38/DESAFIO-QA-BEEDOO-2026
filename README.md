# DESAFIO-QA-BEEDOO-2026

Aplicação Testada:
URL: https://creative-sherbet-a51eac.netlify.app/
Módulo Alvo: Cadastro e Listagem de Cursos

Funcionalidades Disponíveis:
✅ Cadastro de novos cursos
✅ Listagem de cursos cadastrados
❌ Edição de cursos (não implementada)
⚠️ Exclusão de cursos (não funcional)

## 2.1. Objetivo da Aplicação
A aplicação é um sistema web simples de gestão educacional focado no módulo de cadastro e de listagem de cursos. O objetivo principal é permitir que administradores e gestores educacionais realizem operações de gerenciamento de cursos de forma centralizada, incluindo:

- Cadastramento de novos cursos com informações estruturadas
- Visualização e consulta de cursos cadastrados
- Manutenção e atualização de dados dos cursos
- Controle de informações críticas como nome, descrição, tipo de curso, número de vagas, data de início, fim e instrutor

O sistema visa proporcionar uma interface intuitiva para gestão acadêmica, facilitando o planejamento e a organização de ofertas educacionais.

## 2.2. Principais Fluxos Disponíveis
Fluxo 1: Cadastro de Curso
Permite ao usuário criar um novo curso no sistema através de um formulário com os seguintes campos esperados:

- Nome do curso
- Descrição
- Instrutor
- Url da imagem de capa
- Data de início e fim ( formato de data)
- Número de vagas (obrigatório, numérico)
- Tipo de Curso (Presencial, Online)
  - Se presencial -> Colocar o endereço
  - Se online -> Colocar o link de inscrição

Ação principal: Submissão do formulário, com validação de campos obrigatórios e formatos esperados.

Fluxo 2: Listagem de Cursos
Exibe todos os cursos cadastrados no sistema, apresentando:

- Informações resumidas de cada curso
  - Modalidade, Curso, Descrição, data de início, fim e quantidade de vagas.
  - Botão de exclusão

Ação principal: Visualização consolidada dos dados cadastrados.
Nota importante: Não existe funcionalidade de edição de cursos na aplicação atual. A exclusão apresenta problemas de funcionamento (exibe mensagem em um alert, mas não executa a ação).


## 2.3. Pontos Críticos para teste
  2.3.1 Ausência de Validações de Obrigatoriedade
  Justificativa: A aplicação permite cadastro de cursos completamente vazios, sem nenhum campo        preenchido. Isso compromete    totalmente a integridade dos dados e a finalidade do sistema.
  Impacto: Sistema perde sua função principal ao permitir registros sem informações mínimas           necessárias. Impossibilita        filtros, buscas e relatórios confiáveis.
  
  2.3.2 Ausência de Validações de Tipo de Dados
  Justificativa: Campos de texto (Nome, Descrição, Instrutor) aceitam valores numéricos, e campos de URL aceitam qualquer     formato. Isso permite entrada de dados inconsistentes e sem sentido.
  Impacto: Dados sem significado semântico, impossibilidade de aplicar regras de negócio adequadas, comprometimento de        integrações e exportações de dados.
  
  2.3.3 Funcionalidade de Exclusão Não Implementada
  Justificativa: O botão de exclusão exibe mensagem de sucesso mas não executa a remoção do curso, criando uma falsa impressão de funcionalidade.
  Impacto: Impossibilita gerenciamento adequado do catálogo de cursos, acúmulo de dados desnecessários, mensagem enganosa     destrói confiança no sistema.
  
  2.3.4 Exibição Incompleta de Dados na Listagem
  Justificativa: O nome do instrutor não é exibido na listagem, apesar de ser um dado fundamental para identificação e        organização dos cursos.
  Impacto: Perda de informação crítica para gestão acadêmica, impossibilidade de identificar responsável pelo curso sem       acessar detalhes individuais.
  
  2.3.5 Validação de URLs e Links
  Justificativa: Campos de URL de imagem e link de inscrição aceitam qualquer string sem validação de formato, podendo        causar quebra de imagens e links inválidos.
  Impacto: Imagens quebradas na interface, links não funcionais para inscrição, má experiência do usuário, possível injeção   de URLs maliciosas.
  
  2.3.6 Impossibilidade de Edição de Cursos
  Justificativa: Sem funcionalidade de edição, qualquer erro no cadastro requer exclusão e recadastramento completo (que      também não funciona).
  Impacto: Inflexibilidade operacional total, impossibilidade de correção de dados, sistema inadequado para uso real.

## 3. Criação de cenários e casos de teste


