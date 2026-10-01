# ATS Career Analyzer

Uma aplicação web desenvolvida para auxiliar candidatos no processo de candidatura a vagas de emprego, utilizando Inteligência Artificial para analisar a compatibilidade entre o perfil profissional e uma vaga, identificar lacunas e gerar um currículo personalizado e otimizado para leitura por sistemas ATS.

O projeto foi desenvolvido utilizando **Lovable** como plataforma de desenvolvimento assistido por IA, com foco em transformar uma necessidade real de candidatura em uma aplicação funcional.

---

## Problema

Durante um processo seletivo, adaptar o currículo para cada vaga pode ser uma tarefa demorada.

Além de identificar quais experiências e competências são relevantes para determinada oportunidade, o candidato precisa organizar essas informações de forma clara, destacar palavras-chave importantes e manter o currículo compatível com sistemas de rastreamento de candidatos (ATS).

Outro desafio é evitar que a personalização do currículo ultrapasse os limites das experiências reais do candidato.

A proposta do ATS Career Analyzer é centralizar esse processo em uma única aplicação:

- analisar uma vaga;
- comparar a vaga com o perfil profissional;
- identificar competências encontradas e lacunas;
- gerar um currículo personalizado;
- preservar a integridade das informações profissionais;
- facilitar a preparação do candidato para a candidatura.

---

## Solução

O ATS Career Analyzer permite que o usuário forneça seu perfil profissional a partir de um currículo em PDF e, posteriormente, informe os dados da vaga desejada.

A aplicação utiliza Inteligência Artificial para analisar as informações e gerar uma visão estruturada da compatibilidade entre candidato e oportunidade.

O fluxo principal é:

**Perfil profissional → Vaga → Análise de compatibilidade → Lacunas e recomendações → Currículo personalizado → Candidatura personalizada**

Um dos princípios centrais do projeto é a regra de **zero invenção**:

> A aplicação não deve inventar experiências, cargos, empresas, ferramentas, cursos, competências, resultados ou outras informações que não estejam presentes no perfil do candidato.

A descrição da vaga pode ser utilizada para identificar requisitos e palavras-chave, mas não é considerada evidência de que o candidato possui determinada competência.

---

# Desenvolvimento com Lovable

O projeto foi construído utilizando o **Lovable**, uma plataforma de desenvolvimento assistido por Inteligência Artificial.

A estratégia utilizada foi descrever a aplicação, suas funcionalidades, regras de negócio e critérios técnicos por meio de um **Mega Prompt**, permitindo que a plataforma estruturasse a aplicação.

A construção aconteceu de forma iterativa:

1. criação da primeira versão da aplicação;
2. análise do resultado gerado;
3. identificação de problemas;
4. criação de prompts específicos de melhoria;
5. nova implementação no Lovable;
6. validação do resultado.

Dessa forma, o desenvolvimento não terminou na primeira geração da aplicação. Os resultados foram analisados e utilizados para orientar novas alterações.

---

# Mega Prompt

O Mega Prompt inicial foi utilizado para orientar o Lovable na construção da aplicação completa.

Ele especificava:

- objetivo da aplicação;
- autenticação de usuários;
- upload do currículo em PDF;
- análise do perfil profissional;
- entrada da descrição da vaga;
- análise de compatibilidade;
- identificação de palavras-chave;
- identificação de lacunas;
- recomendações;
- geração de currículo;
- exportação para PDF e DOCX;
- dashboard com histórico de análises;
- regras de segurança;
- estrutura de banco de dados;
- controle de acesso aos dados;
- utilização de IA no backend;
- regras de integridade das informações.

A arquitetura proposta utilizou tecnologias como:

- React + TypeScript + Vite;
- Tailwind CSS;
- shadcn/ui;
- Supabase;
- Supabase Auth;
- Supabase Database;
- Supabase Storage;
- Edge Functions;
- modelo de Inteligência Artificial;
- processamento de PDF;
- geração de documentos.

### Regra principal do Mega Prompt

Uma das partes mais importantes foi a definição da regra de integridade:

**A IA nunca deve inventar informações sobre o candidato.**

Caso uma competência apareça na descrição da vaga, mas não exista evidência correspondente no perfil do candidato, ela deve ser tratada como uma lacuna ou informação não identificada — e não como uma competência do candidato.

---
# Prompts utilizados

Durante o desenvolvimento, utilizei prompts no Lovable para orientar a construção da aplicação e, posteriormente, para solicitar melhorias a partir dos problemas identificados nos testes.

## 1. Mega Prompt — Primeira versão

O primeiro prompt foi utilizado para orientar a construção inicial da aplicação.

```txt
# PROMPT MESTRE — ATS CAREER ANALYZER

## 1. CONTEXTO DO PROJETO

Quero construir uma aplicação web full-stack chamada provisoriamente de **ATS Career Analyzer**.

O objetivo da aplicação é permitir que um candidato:

1. crie uma conta ou faça login;
2. envie um PDF exportado diretamente do seu perfil do LinkedIn;
3. informe o nome da vaga e da empresa;
4. cole a descrição completa da vaga;
5. faça uma análise de compatibilidade entre seu perfil profissional e a vaga;
6. visualize um diagnóstico detalhado;
7. identifique palavras-chave encontradas e ausentes;
8. receba recomendações práticas;
9. gere uma versão otimizada e ATS-friendly do currículo;
10. visualize esse currículo;
11. copie o conteúdo;
12. exporte o currículo para PDF;
13. exporte o currículo para Word (.docx);
14. consulte posteriormente todo o histórico de análises realizadas.

A aplicação deve ser funcional, persistente e segura. Não quero apenas um protótipo visual ou dados mockados.

---

# 2. STACK TECNOLÓGICA

Utilize preferencialmente:

* React
* TypeScript
* Vite
* Tailwind CSS
* shadcn/ui
* Supabase
* Supabase Authentication
* Supabase PostgreSQL
* Supabase Storage
* Supabase Edge Functions
* OpenAI ou Anthropic/Claude através de chamadas server-side
* bibliotecas apropriadas para leitura de PDF
* biblioteca apropriada para geração de arquivos DOCX
* solução apropriada para exportação de PDF

Utilize componentes reutilizáveis e mantenha a arquitetura organizada.

Não exponha nenhuma chave de API de IA no frontend.

Todas as chamadas para OpenAI/Anthropic devem ocorrer de forma segura através de uma Supabase Edge Function.

---

# 3. OBJETIVO PRINCIPAL DO PRODUTO

A aplicação deve comparar:

SOURCE 1:
Perfil profissional do candidato extraído do PDF do LinkedIn.

SOURCE 2:
Descrição da vaga fornecida pelo usuário.

O resultado deve conter:

* score de compatibilidade;
* resumo da compatibilidade;
* palavras-chave encontradas;
* palavras-chave ausentes;
* competências encontradas;
* requisitos da vaga atendidos;
* requisitos não comprovados pelo perfil;
* pontos fortes;
* lacunas;
* recomendações;
* currículo ATS-friendly reescrito.

A aplicação deve deixar extremamente claro que o currículo gerado é baseado exclusivamente nas informações comprovadas no perfil do candidato.

---

# 4. REGRA DE OURO — INTEGRIDADE DOS DADOS

Esta é uma regra crítica e deve ser implementada em toda a aplicação.

## REGRA:

A IA NUNCA pode inventar, assumir, completar ou inferir como fato:

* experiências profissionais;
* cargos;
* empresas;
* datas;
* responsabilidades;
* resultados;
* números;
* ferramentas;
* linguagens de programação;
* tecnologias;
* cursos;
* certificações;
* idiomas;
* formação acadêmica;
* projetos;
* competências;
* cargos desejados;
* qualquer outra informação biográfica ou profissional.

A IA somente pode utilizar informações explicitamente presentes no conteúdo extraído do PDF do LinkedIn.

A IA pode:

* reorganizar informações;
* melhorar a redação;
* corrigir gramática;
* tornar descrições mais objetivas;
* combinar informações explicitamente existentes;
* destacar palavras-chave que realmente aparecem no perfil;
* reorganizar experiências;
* adaptar a linguagem ao contexto da vaga;
* resumir informações existentes.

A IA NÃO pode:

* criar uma experiência para preencher uma lacuna;
* transformar uma habilidade semelhante em uma habilidade não declarada;
* assumir conhecimento de uma ferramenta;
* criar métricas;
* criar resultados;
* inventar responsabilidades;
* adicionar palavras-chave apenas porque aparecem na vaga;
* afirmar que o candidato possui um requisito apenas porque ele parece compatível.

### Exemplo:

Se a vaga exige:

"Experiência com Python, SQL e Power BI."

E o perfil possui apenas:

"Experiência com Power BI."

O sistema NÃO deve escrever:

"Experiência com Python, SQL e Power BI."

Deve reconhecer:

* Power BI: encontrado;
* Python: não comprovado;
* SQL: não comprovado.

---

# 5. ARQUITETURA GERAL

Estruture a aplicação aproximadamente assim:

Frontend:

React
→ páginas
→ componentes
→ hooks
→ serviços
→ autenticação Supabase
→ chamadas às Edge Functions

Backend:

Supabase
→ Auth
→ PostgreSQL
→ Storage
→ Edge Functions

IA:

Frontend
→ Edge Function
→ OpenAI/Anthropic API
→ resposta JSON estruturada
→ validação
→ persistência no PostgreSQL
→ frontend

NUNCA:

Frontend → OpenAI API diretamente.

---

# 6. AUTENTICAÇÃO

Utilize Supabase Authentication.

Implementar:

* cadastro;
* login;
* logout;
* recuperação de senha;
* persistência da sessão;
* proteção de rotas.

Preferencialmente oferecer:

* Email + senha;
* Magic Link, caso seja simples de implementar.

Criar uma estrutura de perfil associada ao usuário autenticado.

Cada usuário deve acessar SOMENTE seus próprios dados.

---

# 7. ROTAS

Criar pelo menos as seguintes rotas:

PUBLIC:

/login
/register

PROTECTED:

/dashboard
/analyze
/analysis/:id
/analysis/:id/resume

Opcionalmente:

/profile
/settings

Usuários não autenticados não podem acessar as rotas protegidas.

Se um usuário não autenticado tentar acessar uma rota protegida, redirecionar para /login.

---

# 8. BANCO DE DADOS SUPABASE

Criar uma estrutura relacional organizada.

## Tabela profiles

Campos sugeridos:

* id UUID PRIMARY KEY
* user_id UUID REFERENCES auth.users
* full_name TEXT
* created_at TIMESTAMP
* updated_at TIMESTAMP

Cada usuário deve possuir seu próprio perfil.

---

## Tabela source_documents

Representa o PDF do LinkedIn enviado pelo usuário.

Campos sugeridos:

* id UUID PRIMARY KEY
* user_id UUID
* file_name TEXT
* storage_path TEXT
* extracted_text TEXT
* parsed_profile JSONB
* created_at TIMESTAMP

Não armazenar arquivos de usuários de maneira pública.

Utilizar Supabase Storage com acesso controlado.

---

## Tabela analyses

Representa cada análise realizada.

Campos sugeridos:

* id UUID PRIMARY KEY
* user_id UUID
* source_document_id UUID
* job_title TEXT
* company_name TEXT
* job_description TEXT
* match_score NUMERIC
* analysis_result JSONB
* created_at TIMESTAMP
* updated_at TIMESTAMP

---

## Tabela resumes

Representa o currículo ATS gerado.

Campos sugeridos:

* id UUID PRIMARY KEY
* analysis_id UUID
* user_id UUID
* resume_content JSONB
* resume_text TEXT
* created_at TIMESTAMP
* updated_at TIMESTAMP

Se necessário, também armazenar referências aos arquivos exportados.

---

# 9. ROW LEVEL SECURITY

Ativar RLS em todas as tabelas que contenham dados de usuários.

Regra fundamental:

Um usuário só pode:

SELECT:
seus próprios registros.

INSERT:
seus próprios registros.

UPDATE:
seus próprios registros.

DELETE:
seus próprios registros.

Nunca permitir que um usuário consulte análises, documentos ou currículos pertencentes a outro usuário.

As políticas devem utilizar o usuário autenticado do Supabase.

---

# 10. SUPABASE STORAGE

Criar um bucket privado para documentos enviados pelos usuários.

Exemplo:

linkedin-resumes

O arquivo não deve ficar publicamente acessível.

O frontend deve utilizar mecanismos seguros para upload e acesso.

Validar:

* extensão;
* MIME type;
* tamanho máximo.

Aceitar inicialmente somente PDF.

Se o arquivo não for PDF, mostrar uma mensagem clara ao usuário.

---

# 11. FLUXO DE UPLOAD

Na página /analyze criar uma área de upload.

Interface:

"Envie seu perfil do LinkedIn em PDF"

Aceitar:

PDF

Mostrar:

* nome do arquivo;
* tamanho;
* status do upload;
* botão para remover;
* botão para iniciar análise.

Após o upload:

1. armazenar no Supabase Storage;
2. registrar o documento no banco;
3. enviar o documento para processamento;
4. extrair o texto;
5. estruturar as informações;
6. validar se foi possível extrair conteúdo;
7. somente então executar a análise da vaga.

Se o PDF estiver vazio, corrompido ou não for possível extrair texto, mostrar erro amigável.

---

# 12. PARSING DO PDF

Criar uma Supabase Edge Function responsável por processar o PDF.

Objetivo:

PDF
→ texto bruto
→ perfil estruturado.

Tentar identificar, quando presentes:

* nome;
* título profissional;
* localização;
* resumo/sobre;
* experiências;
* empresas;
* cargos;
* datas;
* descrições;
* formação;
* instituições;
* certificações;
* cursos;
* competências;
* idiomas;
* projetos;
* outras informações relevantes.

IMPORTANTE:

A estruturação NÃO deve adicionar informações que não estejam no PDF.

Se determinada informação não estiver presente:

retornar null, string vazia ou array vazio.

Nunca preencher por inferência.

O texto original extraído também deve ser preservado para rastreabilidade.

---

# 13. DESCRIÇÃO DA VAGA

Na página /analyze criar:

Campo:

Nome da vaga

Campo:

Empresa

Campo:

Descrição da vaga

A descrição deve possuir uma textarea ampla.

Validar:

* nome da vaga obrigatório;
* descrição obrigatória;
* PDF obrigatório.

Não executar a análise enquanto os dados necessários não estiverem presentes.

---

# 14. PIPELINE DE IA

O fluxo deve ser:

PDF
↓
extração do texto
↓
estruturação do perfil
↓
descrição da vaga
↓
Edge Function
↓
modelo de IA
↓
JSON estruturado
↓
validação da resposta
↓
persistência no banco
↓
resultado da análise
↓
currículo ATS

A chamada à IA deve ocorrer SOMENTE no backend.

---

# 15. CHAMADA DA IA

Criar uma Edge Function, por exemplo:

analyze-resume

Ela deve receber:

* parsed_profile;
* extracted_text;
* job_title;
* company_name;
* job_description.

A API key deve ser armazenada em variável de ambiente/secret.

Nunca colocar API key:

* no React;
* no código client-side;
* no GitHub;
* em arquivos públicos.

---

# 16. VALIDAÇÃO DA RESPOSTA DA IA

A resposta deve obrigatoriamente ser JSON válido.

Validar o JSON antes de salvar no banco.

Se a resposta não obedecer ao schema esperado:

* não salvar como resultado final;
* tentar uma nova chamada de correção se apropriado;
* ou retornar erro controlado ao frontend.

Não exibir JSON bruto para o usuário.

---

# 17. SCORE DE MATCH

Criar um score de 0 a 100.

O score deve representar somente a correspondência entre requisitos da vaga e evidências presentes no perfil.

Não considerar como "atendido" algo que não esteja comprovado no perfil.

O score deve ser acompanhado de uma explicação.

Evitar apresentar o score como uma previsão de contratação.

Ele representa apenas compatibilidade documental entre o perfil fornecido e os requisitos identificados na vaga.

---

# 18. DASHBOARD

Criar dashboard moderno, limpo e profissional.

No topo:

"Olá, [nome]"

CTA principal:

"+ Nova Análise"

Cards:

### Total de análises

Quantidade total de análises realizadas pelo usuário.

### Match médio

Média dos scores das análises do usuário.

### Última análise

Data da análise mais recente.

---

# 19. HISTÓRICO

Criar tabela/lista com:

* data;
* vaga;
* empresa;
* score;
* ações.

Ações:

* Visualizar análise;
* Visualizar currículo;
* Baixar/exportar;
* Excluir, se implementado.

Ordenar da análise mais recente para a mais antiga.

Se não houver análises:

mostrar estado vazio amigável:

"Você ainda não realizou nenhuma análise."

CTA:

"Fazer minha primeira análise"

---

# 20. TELA DE RESULTADO

Criar página:

/analysis/:id

Mostrar:

## Score

Grande indicador visual de 0 a 100.

## Resumo

Explicação curta sobre a compatibilidade encontrada.

## Palavras-chave encontradas

Mostrar badges/tags.

## Palavras-chave ausentes

Mostrar separadamente.

IMPORTANTE:

"Ausente" significa que não foi encontrado no perfil fornecido.

Não significa necessariamente que o candidato não possua aquela habilidade na vida real.

Utilizar linguagem cuidadosa.

---

# 21. REQUISITOS DA VAGA

Criar seção:

"Requisitos analisados"

Cada requisito deve possuir status:

* Encontrado;
* Parcialmente evidenciado;
* Não encontrado;
* Não foi possível determinar.

Quando possível, mostrar a evidência correspondente encontrada no perfil.

Não inventar evidências.

---

# 22. LACUNAS

Criar seção:

"Lacunas identificadas"

Mostrar:

* requisito;
* motivo;
* evidência disponível ou ausência dela.

Não transformar automaticamente uma lacuna em uma afirmação sobre a capacidade real do candidato.

Exemplo:

"SQL não foi identificado no perfil enviado."

E NÃO:

"O candidato não sabe SQL."

---

# 23. RECOMENDAÇÕES

Criar seção:

"Recomendações"

As recomendações devem ser práticas.

Exemplos:

* destacar uma experiência que já existe;
* reorganizar uma seção;
* utilizar determinada palavra-chave somente se ela já estiver presente;
* desenvolver determinada habilidade;
* adicionar evidências reais que o candidato possua, caso ele queira atualizar seu perfil futuramente.

NÃO adicionar automaticamente habilidades ausentes ao currículo.

---

# 24. AVISO DE INTEGRIDADE

Exibir claramente na tela de resultado:

"Integridade do currículo: 100% baseada nas informações fornecidas."

A aplicação deve explicar que:

* nenhuma experiência foi inventada;
* nenhuma empresa foi criada;
* nenhuma ferramenta foi adicionada sem evidência;
* o conteúdo foi reorganizado e otimizado com base nas informações fornecidas.

IMPORTANTE:

Esse aviso deve ser baseado na validação do pipeline e não apenas em uma frase gerada pela IA.

---

# 25. CURRÍCULO ATS

Criar página:

/analysis/:id/resume

O currículo deve possuir layout ATS-friendly.

Características:

* uma única coluna;
* sem tabelas complexas;
* sem múltiplas colunas;
* sem elementos gráficos necessários para interpretação;
* sem excesso de ícones;
* títulos claros;
* texto selecionável;
* hierarquia semântica;
* tipografia profissional;
* espaçamento consistente.

Seções possíveis:

* Nome;
* Contato;
* Resumo profissional;
* Experiência profissional;
* Formação acadêmica;
* Certificações;
* Competências;
* Idiomas;
* Projetos.

Somente incluir seções para as quais existam dados.

Não criar conteúdo para preencher espaços vazios.

---

# 26. REESCRITA DO CURRÍCULO

O currículo deve:

* preservar a verdade factual;
* melhorar clareza;
* utilizar verbos de ação;
* reduzir redundância;
* destacar resultados já presentes;
* priorizar palavras-chave reais;
* adaptar a ordem das informações à vaga.

Não criar:

* números;
* porcentagens;
* resultados;
* responsabilidades;
* tecnologias;
* cargos;
* empresas;
* certificações.

Se o perfil disser:

"Criei dashboard no Power BI."

Pode transformar em:

"Desenvolvimento de dashboard em Power BI para acompanhamento de indicadores."

Não pode transformar em:

"Desenvolvimento de dashboards em Power BI que aumentaram a produtividade em 40%."

A segunda versão inventaria um resultado.

---

# 27. PROVENIÊNCIA DAS INFORMAÇÕES

Sempre que possível, manter internamente uma relação entre o conteúdo gerado e sua fonte.

Exemplo conceitual:

resume_item:
"Desenvolvimento de dashboard em Power BI..."

source:
"Experiência na empresa X: criação de dashboard em Power BI..."

Isso será utilizado para validar a regra de integridade.

Não é necessário mostrar toda a proveniência ao usuário final, mas ela deve ser preservada no resultado estruturado quando possível.

---

# 28. COPIAR CURRÍCULO

Adicionar botão:

"Copiar currículo"

Ao clicar:

* copiar o texto ATS completo para clipboard;
* mostrar feedback visual:
  "Currículo copiado!"

---

# 29. EXPORTAÇÃO PDF

Adicionar:

"Exportar PDF"

Gerar PDF utilizando o mesmo conteúdo apresentado no preview.

O PDF deve:

* manter layout ATS;
* permitir seleção de texto;
* possuir boa quebra de páginas;
* não cortar conteúdo;
* possuir margens profissionais;
* preservar hierarquia visual.

Evitar gerar uma imagem do currículo.

O conteúdo deve permanecer como texto.

---

# 30. EXPORTAÇÃO DOCX

Adicionar:

"Exportar Word"

Gerar arquivo:

ATS-Curriculo-[Nome].docx

Utilizar uma biblioteca apropriada para geração de DOCX.

O arquivo deve ser editável.

Manter:

* uma coluna;
* títulos;
* espaçamento;
* ordem das seções;
* texto selecionável/editável.

---

# 31. DESIGN

Visual moderno e profissional.

Referência estética:

* SaaS;
* tecnologia;
* carreira;
* análise de dados.

Utilizar:

* Tailwind;
* shadcn/ui;
* cards;
* badges;
* progress indicators;
* dialogs;
* alerts;
* skeleton loaders;
* toast notifications.

Evitar:

* excesso de gradientes;
* visual infantil;
* excesso de animações;
* interfaces visualmente poluídas.

Priorizar usabilidade.

A interface deve ser responsiva:

* desktop;
* tablet;
* mobile.

---

# 32. ESTADOS DE LOADING

Durante processos demorados, mostrar progresso.

Exemplo:

1. "Enviando currículo..."
2. "Lendo seu perfil..."
3. "Analisando a descrição da vaga..."
4. "Comparando requisitos..."
5. "Gerando diagnóstico..."
6. "Preparando currículo ATS..."

Não deixar a tela aparentemente travada.

---

# 33. TRATAMENTO DE ERROS

Implementar mensagens amigáveis para:

* PDF inválido;
* PDF sem texto;
* erro de upload;
* erro de autenticação;
* erro de IA;
* timeout;
* resposta inválida da IA;
* erro no banco;
* erro na exportação.

Nunca mostrar stack traces ou secrets ao usuário.

Registrar erros técnicos de forma segura quando apropriado.

---

# 34. SEGURANÇA

Implementar:

* RLS;
* Storage privado;
* API keys somente no backend;
* validação de arquivos;
* validação de inputs;
* sanitização de dados;
* proteção das rotas;
* autenticação Supabase.

Nunca confiar apenas na validação do frontend.

Toda autorização deve também ser validada no backend/banco.

---

# 35. PERFORMANCE

Evitar chamadas desnecessárias à IA.

Não chamar IA a cada alteração de campo.

A análise deve ser executada somente quando o usuário clicar:

"Analisar compatibilidade"

Mostrar loading durante processamento.

Evitar baixar novamente o PDF quando o documento já tiver sido processado.

---

# 36. EXPERIÊNCIA DO USUÁRIO

Fluxo ideal:

LOGIN
↓
DASHBOARD
↓
"NOVA ANÁLISE"
↓
UPLOAD DO PDF
↓
NOME DA VAGA
↓
EMPRESA
↓
DESCRIÇÃO DA VAGA
↓
"ANALISAR"
↓
PROCESSAMENTO
↓
RESULTADO
↓
DIAGNÓSTICO
↓
"VER CURRÍCULO ATS"
↓
PREVIEW
↓
COPIAR / PDF / DOCX

---

# 37. PRIMEIRA EXPERIÊNCIA DO USUÁRIO

Se o usuário ainda não tiver análises:

Dashboard deve apresentar:

"Comece sua primeira análise"

Texto:

"Envie seu perfil do LinkedIn e compare suas experiências com uma vaga."

Botão:

"Nova Análise"

---

# 38. DADOS MOCKADOS

Durante o desenvolvimento inicial, dados mockados podem ser utilizados APENAS para estruturar componentes visuais.

Porém, antes de considerar o produto funcional:

* remover dados mockados;
* conectar todas as telas ao Supabase;
* conectar autenticação;
* conectar upload;
* conectar banco;
* conectar Edge Functions;
* conectar IA;
* conectar exportação.

Não deixar funcionalidades falsas ou botões que não executam nenhuma ação.

---

# 39. VARIÁVEIS DE AMBIENTE / SECRETS

Nunca colocar secrets diretamente no código.

Utilizar secrets apropriados do Supabase/Lovable para:

* OPENAI_API_KEY

ou:

* ANTHROPIC_API_KEY

O sistema deve ser preparado para utilizar um único provider inicialmente, mas manter a arquitetura suficientemente desacoplada para permitir troca futura entre OpenAI e Anthropic.

---

# 40. ESTRUTURA DE CÓDIGO

Organizar o projeto de forma modular.

Exemplo:

src/
components/
pages/
hooks/
services/
lib/
types/
integrations/

supabase/
functions/
parse-pdf/
analyze-resume/
generate-resume/

Evitar colocar toda a lógica em um único componente.

Criar tipos TypeScript para:

* Profile;
* ParsedProfile;
* JobDescription;
* Analysis;
* AnalysisResult;
* Resume;
* ResumeSection;
* KeywordMatch.

---

# 41. TIPAGEM

Evitar:

any

sempre que possível.

Criar interfaces/types para os objetos recebidos da IA.

Validar runtime do JSON da IA antes de utilizá-lo.

---

# 42. RESPONSIVIDADE

No mobile:

* dashboard deve continuar utilizável;
* tabela pode transformar-se em cards;
* upload deve ocupar largura disponível;
* botões de exportação devem ser acessíveis;
* currículo deve possuir preview adequado.

---

# 43. ACESSIBILIDADE

Utilizar:

* labels;
* aria-label quando necessário;
* contraste adequado;
* navegação por teclado;
* estados de foco;
* mensagens de erro associadas aos campos.

Não depender exclusivamente de cores para indicar status.

---

# 44. CRITÉRIOS DE ACEITAÇÃO

A aplicação será considerada funcional quando:

[ ] Usuário consegue criar conta.

[ ] Usuário consegue fazer login.

[ ] Usuário consegue acessar o dashboard.

[ ] Usuário não autenticado não consegue acessar páginas protegidas.

[ ] Usuário consegue enviar um PDF.

[ ] PDF é armazenado de forma privada.

[ ] Texto do PDF é extraído.

[ ] Perfil é estruturado sem inventar informações.

[ ] Usuário consegue inserir nome da vaga.

[ ] Usuário consegue inserir empresa.

[ ] Usuário consegue inserir descrição da vaga.

[ ] IA recebe os dados através de backend seguro.

[ ] IA retorna JSON estruturado.

[ ] Regra de Ouro é aplicada.

[ ] Score é calculado.

[ ] Palavras-chave encontradas são exibidas.

[ ] Palavras-chave ausentes são exibidas.

[ ] Lacunas são exibidas.

[ ] Recomendações são exibidas.

[ ] Aviso de integridade é exibido.

[ ] Currículo ATS é gerado.

[ ] Currículo pode ser copiado.

[ ] Currículo pode ser exportado em PDF.

[ ] Currículo pode ser exportado em DOCX.

[ ] Análise é salva no banco.

[ ] Dashboard mostra histórico.

[ ] Usuário consegue abrir uma análise antiga.

[ ] Dados de um usuário não podem ser acessados por outro usuário.

---

# 45. ORDEM DE IMPLEMENTAÇÃO

Construa o projeto nesta ordem:

FASE 1 — Estrutura inicial

* React;
* Tailwind;
* shadcn;
* layout;
* rotas.

FASE 2 — Supabase

* conexão;
* Auth;
* banco;
* RLS;
* Storage.

FASE 3 — Dashboard

* cards;
* histórico;
* estados vazios.

FASE 4 — Upload

* PDF;
* Storage;
* validações.

FASE 5 — Parsing

* Edge Function;
* extração;
* estruturação do perfil.

FASE 6 — IA

* Edge Function;
* integração OpenAI/Anthropic;
* system prompt;
* JSON estruturado;
* validação.

FASE 7 — Resultado

* score;
* keywords;
* gaps;
* recomendações;
* integridade.

FASE 8 — Currículo

* ATS preview;
* edição/visualização;
* copiar.

FASE 9 — Exportação

* PDF;
* DOCX.

FASE 10 — Qualidade

* tratamento de erros;
* responsividade;
* acessibilidade;
* segurança;
* remoção de mocks;
* testes do fluxo completo.

---

# 46. INSTRUÇÃO IMPORTANTE PARA O DESENVOLVIMENTO

Não simplifique funcionalidades importantes apenas para criar uma demonstração visual.

Se alguma implementação técnica não for possível da forma inicialmente planejada, explique o problema e proponha uma alternativa tecnicamente segura.

Não invente APIs ou funcionalidades inexistentes.

Priorize uma aplicação funcional e simples em vez de uma interface visualmente sofisticada, porém sem backend real.

Antes de finalizar cada etapa, verifique se o código está consistente com o restante da arquitetura.

Comece agora construindo a aplicação seguindo essa especificação.
```

---

## 2. Prompt de ajuste — Currículo e exportação PDF

Após testar a primeira versão, identifiquei problemas relacionados à organização das competências, caracteres corrompidos na exportação e paginação do currículo.

Para corrigir esses pontos, utilizei o seguinte prompt:

```txt
Quero fazer uma melhoria específica no currículo ATS gerado pela aplicação, principalmente na visualização e na exportação para PDF.

IMPORTANTE: não quero alterar a lógica de análise da vaga, o cálculo de match ou as informações factuais do candidato. O objetivo deste prompt é melhorar a apresentação, organização, paginação e exportação do currículo que já está funcionando.

1. Organizar melhor a seção de Competências
Atualmente, a seção de competências está sendo exportada como um bloco muito denso de texto, com muitas competências juntas e separadas por "•", o que dificulta a leitura.

Quero que essa seção seja visualmente mais organizada.

Pode, por exemplo:

organizar as competências em pequenos grupos;
utilizar bullets;
distribuir as competências em linhas mais curtas;
ou utilizar categorias visuais quando isso puder ser feito com segurança.
As categorias devem servir somente para organizar visualmente competências que já existem no perfil do candidato.

Não criar, adicionar, inferir ou modificar competências.

Se uma categorização segura não for possível, prefiro uma lista de bullets bem espaçada a um único bloco de texto.

2. Corrigir problema de caracteres/encoding
Existe um problema na exportação do PDF em que alguns caracteres aparecem corrompidos.

Por exemplo, informações com acentos ou caracteres especiais podem aparecer como símbolos ou caracteres estranhos.

Corrigir o problema de encoding para garantir que:

acentos sejam exibidos corretamente;
ç, ã, õ, é, ê, á etc. sejam preservados;
caracteres especiais sejam renderizados corretamente;
o texto exibido no preview seja igual ao texto exportado para PDF.
Verificar especialmente datas, localidades e textos com caracteres acentuados.

3. Garantir consistência entre Preview e PDF
O currículo exibido no preview e o currículo exportado em PDF devem apresentar o mesmo conteúdo e a mesma estrutura.

Garantir consistência em:

nome;
título profissional;
informações de contato;
resumo profissional;
experiências;
formação;
certificações;
competências;
ordem das seções;
espaçamento;
hierarquia visual;
bullets;
quebras de linha.
O PDF não deve alterar, omitir ou corromper informações presentes no preview.

4. Melhorar paginação
Melhorar as quebras de página para que o currículo fique visualmente profissional.

Evitar, sempre que possível:

título de uma seção sozinho no final da página;
título de uma experiência separado de seu conteúdo;
bullet isolado em outra página;
quebra excessiva de uma experiência;
compressão exagerada do conteúdo para tentar caber tudo em uma página.
Um currículo de duas páginas é aceitável.

Não reduzir excessivamente o tamanho da fonte apenas para fazer o conteúdo caber em uma página.

Priorizar legibilidade e organização.

5. Manter padrão ATS-friendly
Manter o currículo em formato simples e compatível com leitura por ATS:

layout de uma coluna;
texto real e selecionável;
hierarquia clara de títulos;
fonte legível;
bullets simples;
sem tabelas complexas;
sem múltiplas colunas;
sem informações importantes exclusivamente em imagens ou elementos gráficos.
Não prometer que o currículo será aprovado por qualquer ATS específico. O objetivo é manter uma estrutura simples e facilmente interpretável.

6. Preservar a integridade das informações
Não alterar o conteúdo factual do currículo durante essa correção.

Não:

inventar experiências;
inventar competências;
adicionar ferramentas;
alterar cargos;
criar resultados;
modificar números;
criar empresas;
criar cursos ou certificações;
inferir experiências que não estejam presentes no perfil.
Apenas reorganizar visualmente e corrigir problemas técnicos de apresentação/exportação.

7. Teste da implementação
Depois de implementar as alterações, teste a geração do preview e do PDF.

Sempre que possível, utilize uma análise/currículo já existente no sistema para realizar esse teste.

Não é necessário refazer uma nova análise de vaga apenas para testar a exportação.

Se a arquitetura atual exigir a regeneração do currículo, utilize os mesmos dados da análise existente e não altere o conteúdo factual.

Durante o teste, verificar especificamente:

Os acentos aparecem corretamente?
Existem caracteres corrompidos?
A seção de competências está legível e organizada?
O preview e o PDF possuem o mesmo conteúdo?
As experiências estão bem distribuídas entre as páginas?
Existem títulos ou bullets órfãos?
O currículo continua com layout de uma coluna e ATS-friendly?
O tamanho da fonte continua confortável para leitura?
Faça as alterações necessárias no código responsável pelo preview e pela exportação para PDF.

Ao finalizar, me informe de forma objetiva quais alterações foram implementadas.
```

### Por que esse ajuste foi necessário?

A primeira versão apresentava problemas na apresentação do currículo exportado. A seção de competências estava muito extensa e pouco organizada, além de haver problemas de caracteres especiais no PDF.

O prompt foi criado para corrigir esses problemas sem alterar o conteúdo factual do currículo.

---

## 3. Prompt de ajuste — Seleção de competências

Após a primeira correção, percebi que a seção de competências continuava apresentando uma quantidade muito grande de informações.

A aplicação estava organizando visualmente as competências, mas ainda utilizava praticamente todas as competências disponíveis no perfil.

Por isso, foi criado um novo prompt para tornar a seleção de competências específica para cada vaga:

```txt
Gostei da correção visual e da padronização do currículo. Agora quero fazer uma segunda melhoria especificamente na seleção das competências exibidas no currículo gerado para cada vaga.

Atualmente, a seção de competências está visualmente organizada, porém ainda apresenta uma lista muito extensa, praticamente reproduzindo todas as competências identificadas no perfil do candidato.

Quero que o currículo seja mais estratégico e personalizado para cada vaga.

1. Não listar todas as competências do perfil
O currículo NÃO deve simplesmente copiar todas as competências existentes no perfil do candidato.

O perfil pode continuar armazenando todas as competências identificadas, mas o currículo gerado para uma vaga específica deve apresentar apenas as competências mais relevantes para aquela candidatura.

2. Selecionar competências de acordo com a vaga
Utilizar a descrição da vaga que está sendo analisada para identificar quais competências do candidato são mais relevantes para aquela oportunidade.

Priorizar competências que:

aparecem explicitamente como requisitos ou responsabilidades da vaga;
possuem relação direta com as atividades descritas;
estão comprovadamente presentes no perfil do candidato;
são coerentes com as experiências profissionais, projetos, formação ou certificações do candidato.
A seleção deve ser feita somente entre competências que já existem no perfil do candidato.

3. Limitar a quantidade
Evitar listas excessivamente longas.

Como regra geral, utilizar aproximadamente 10 a 15 competências mais relevantes para a vaga.

Se houver menos competências realmente relevantes, utilizar apenas as que forem justificadas pelo perfil.

Não preencher a lista artificialmente para atingir um número mínimo.

4. Regra de integridade — não inventar competências
Esta regra é obrigatória e deve permanecer alinhada com a regra de integridade do restante da aplicação:

A descrição da vaga NÃO é evidência de que o candidato possui determinada competência.

Por exemplo:

Se a vaga solicitar SQL, mas SQL não estiver presente no perfil/evidências do candidato, o sistema NÃO pode adicionar SQL à seção de competências apenas para aumentar o match.

Nesse caso, SQL deve continuar sendo tratado como uma lacuna/não identificada.

A IA pode:

selecionar;
priorizar;
reorganizar;
agrupar visualmente;
mas não pode:

inventar competências;
inferir competências sem evidência;
adicionar ferramentas apenas porque aparecem na vaga.
5. Personalização por candidatura
A seleção das competências deve ser dinâmica.

O mesmo candidato pode ter diferentes conjuntos de competências no currículo dependendo da vaga analisada.

Exemplo:

Para uma vaga de dados, competências relacionadas a análise de dados, Power BI, Power Query, Python, Excel, ETL, KPIs e Business Intelligence podem ser priorizadas se estiverem presentes no perfil.

Para uma vaga de processos/qualidade, competências relacionadas a mapeamento de processos, melhoria contínua, PDCA, análise de causa raiz, auditoria e padronização podem ser priorizadas se estiverem presentes no perfil.

Esses exemplos são apenas ilustrativos. A seleção deve ser feita com base na vaga real e nas evidências reais do candidato.

6. Manter o perfil completo separado
Não remover competências do perfil original apenas porque elas não foram selecionadas para determinado currículo.

O sistema deve diferenciar:

Perfil completo do candidato → contém todas as competências identificadas.

Currículo personalizado para a vaga → contém apenas as competências mais relevantes para aquela candidatura.

Isso permitirá que o mesmo perfil seja utilizado para gerar diferentes currículos personalizados.

7. Manter o restante do currículo inalterado
Não modificar:

experiências;
cargos;
empresas;
datas;
formação;
certificações;
resultados;
números;
informações de contato;
regras de integridade;
layout já corrigido;
exportação para PDF.
A alteração solicitada neste prompt é especificamente a seleção e priorização das competências exibidas no currículo personalizado.

8. Teste
Depois de implementar, utilize uma análise/currículo já existente, se possível, para verificar o resultado.

Confirme que:

O currículo não apresenta mais uma lista excessivamente longa de competências.
As competências selecionadas possuem relação com a vaga.
Todas as competências exibidas existem no perfil do candidato.
Nenhuma competência foi inventada a partir da descrição da vaga.
O perfil completo continua preservado.
O PDF continua funcionando corretamente.
O preview e o PDF apresentam a mesma seleção de competências.
Ao finalizar, informe objetivamente o que foi alterado.
```

### Por que esse ajuste foi necessário?

O objetivo foi diferenciar o **perfil completo do candidato** do **currículo personalizado para uma vaga específica**.

O perfil pode manter todas as competências identificadas, enquanto o currículo deve priorizar apenas aquelas que possuem maior relação com a vaga e que estejam comprovadamente presentes no perfil do candidato.

---

## 4. Prompt de ajuste — Candidaturas personalizadas

Após implementar as funcionalidades de análise da vaga e geração do currículo personalizado, foi adicionada uma nova área à aplicação para auxiliar o candidato a responder perguntas presentes em processos seletivos.

A funcionalidade utiliza o perfil profissional já cadastrado para gerar respostas personalizadas de acordo com a vaga e com a pergunta apresentada pelo processo seletivo.

Um dos principais requisitos dessa implementação foi manter a mesma regra de **zero invenção** utilizada no restante da aplicação.

O prompt utilizado foi:

```txt

Quero adicionar uma nova funcionalidade à aplicação chamada **Candidaturas**.

O objetivo é permitir que o usuário utilize seu perfil profissional já cadastrado para gerar respostas personalizadas para perguntas presentes em processos seletivos.

Essa funcionalidade deve complementar o fluxo atual de análise de vagas e geração de currículo.

### 1. Nova área: Candidaturas

Adicionar uma nova opção de navegação chamada:

**Candidaturas**

A funcionalidade deve permitir que o usuário informe:

* Nome da empresa;
* Nome da vaga;
* Descrição da vaga;
* Pergunta do processo seletivo;
* Limite de caracteres da resposta.

O usuário também deve poder utilizar o perfil profissional que já está cadastrado na aplicação, evitando a necessidade de fornecer novamente todas as suas informações.

### 2. Exemplo de utilização

Um exemplo de pergunta que deve ser suportado:

> "Fale sobre você e sua trajetória profissional, contando como pode ajudar a empresa no desafio descrito na vaga."

A aplicação deve permitir que o usuário informe, por exemplo:

**Limite:** 1.500 caracteres

E então gerar uma resposta personalizada considerando:

* o perfil profissional do candidato;
* sua trajetória;
* experiências;
* competências;
* formação;
* projetos;
* descrição da vaga;
* responsabilidades;
* requisitos da oportunidade.

### 3. Regra de integridade — zero invenção

Esta funcionalidade deve seguir a mesma regra de integridade utilizada no restante da aplicação.

A IA **NÃO pode inventar ou inferir como fato** informações profissionais que não estejam presentes no perfil do candidato.

Não inventar:

* experiências;
* cargos;
* empresas;
* ferramentas;
* conhecimentos;
* cursos;
* certificações;
* projetos;
* resultados;
* números;
* responsabilidades;
* competências;
* experiências com determinada tecnologia.

A descrição da vaga pode ser utilizada para entender o desafio da empresa e direcionar a resposta, mas **não é evidência de que o candidato possui determinada experiência ou competência**.

Por exemplo:

Se a vaga solicitar experiência com SQL, mas SQL não estiver presente no perfil do candidato, a resposta não deve afirmar que o candidato possui experiência com SQL.

A IA deve trabalhar somente com informações verdadeiras e identificadas no perfil fornecido.

### 4. Personalização da resposta

A resposta não deve ser um texto genérico.

Ela deve conectar:

**Perfil do candidato + experiência profissional + requisitos da vaga + desafio descrito pela empresa**

O objetivo é demonstrar, de forma natural, como a trajetória real do candidato pode contribuir para a oportunidade.

A IA pode:

* reorganizar informações;
* melhorar a redação;
* adaptar o tom;
* destacar experiências relevantes;
* conectar experiências reais aos desafios da vaga;
* priorizar competências relevantes;
* tornar a resposta mais objetiva.

Mas não deve criar informações que não estejam presentes no perfil.

### 5. Limite de caracteres

A aplicação deve respeitar o limite de caracteres informado pelo usuário.

Exemplo:

**1.327 / 1.500 caracteres**

O contador deve atualizar conforme o texto for alterado.

A resposta gerada não deve ultrapassar o limite informado.

Se o usuário editar o texto manualmente e ultrapassar o limite, mostrar visualmente que o limite foi excedido.

### 6. Interface

Criar uma interface simples e coerente com o restante da aplicação.

Sugestão de estrutura:

**Nova candidatura**

Empresa:
`[________________________]`

Vaga:
`[________________________]`

Descrição da vaga:
`[____________________________________________]`

Pergunta do processo seletivo:
`[____________________________________________]`

Limite de caracteres:
`[1500]`

**[ Gerar resposta ]**

Após a geração:

### Resposta gerada

`[texto da resposta]`

**1.327 / 1.500 caracteres**

Botões:

**[ Copiar resposta ]**

**[ Regenerar ]**

### 7. Utilização do perfil existente

Sempre que possível, utilizar o perfil profissional já armazenado na aplicação.

O usuário não deve precisar reenviar seu currículo ou preencher novamente suas informações profissionais para cada candidatura.

A funcionalidade deve aproveitar os dados já existentes no perfil.

### 8. Relação com a análise da vaga

Quando existir uma análise da vaga já realizada na aplicação, permitir que o usuário utilize essa análise para gerar a resposta da candidatura.

Nesse caso, a aplicação já possui informações como:

* requisitos da vaga;
* competências relevantes;
* lacunas;
* pontos de aderência;
* descrição da oportunidade.

Essas informações podem ser utilizadas como contexto adicional para gerar a resposta.

Porém, a regra de integridade deve continuar sendo aplicada.

### 9. Não limitar a funcionalidade à Gupy

Embora um dos principais casos de uso seja responder perguntas presentes em processos seletivos da Gupy, não criar a funcionalidade exclusivamente para a Gupy.

O módulo deve ser genérico o suficiente para funcionar com perguntas de diferentes processos seletivos.

Exemplos:

* "Fale sobre você e sua trajetória profissional."
* "Por que você quer trabalhar conosco?"
* "Como sua experiência pode contribuir para essa posição?"
* "Conte sobre um desafio profissional que você enfrentou."
* "Quais são suas principais competências?"
* "Por que você se interessou por esta oportunidade?"

O usuário deve poder colar qualquer pergunta e informar o limite de caracteres desejado.

### 10. Histórico de candidaturas

Sempre que possível, armazenar as candidaturas geradas pelo usuário para que ele possa consultá-las posteriormente.

Cada registro pode conter:

* empresa;
* vaga;
* pergunta;
* resposta gerada;
* data;
* limite de caracteres.

O usuário deve conseguir visualizar suas próprias candidaturas.

### 11. Privacidade e segurança

As informações das candidaturas devem seguir as mesmas regras de segurança da aplicação.

Um usuário não deve conseguir visualizar candidaturas, perfis ou respostas pertencentes a outro usuário.

Manter as políticas de acesso já existentes no sistema.

### 12. Não alterar funcionalidades existentes

Essa implementação deve ser feita sem prejudicar as funcionalidades que já estão funcionando.

Não alterar desnecessariamente:

* análise de compatibilidade;
* geração do currículo;
* exportação do currículo;
* autenticação;
* perfil profissional;
* histórico de análises;
* regra de integridade.

A nova funcionalidade deve ser integrada ao sistema existente.

### 13. Critérios de aceitação

Considerar a funcionalidade implementada quando for possível:

1. Acessar a área **Candidaturas**.
2. Informar empresa e vaga.
3. Colar uma descrição de vaga.
4. Colar uma pergunta de processo seletivo.
5. Definir um limite de caracteres.
6. Gerar uma resposta utilizando o perfil profissional existente.
7. Garantir que a resposta não ultrapasse o limite.
8. Copiar a resposta.
9. Regenerar a resposta.
10. Editar manualmente a resposta.
11. Visualizar o contador de caracteres.
12. Garantir que nenhuma informação profissional seja inventada.
13. Utilizar a funcionalidade para diferentes empresas e perguntas.
14. Preservar as funcionalidades existentes da aplicação.

Após implementar, me informe objetivamente quais alterações foram realizadas e quais funcionalidades foram adicionadas.

```

---

## 5. Evolução dos prompts

A evolução dos prompts acompanhou o processo de desenvolvimento da aplicação:

**Mega Prompt inicial**  

↓  

**Primeira geração da aplicação**  

↓  

**Identificação de problemas no currículo/PDF**  

↓  

**Prompt de correção da exportação**  

↓  

**Novo teste**  

↓  

**Identificação do excesso de competências**  

↓  

**Prompt para seleção de competências por vaga**  

↓  

**Nova necessidade identificada: personalização das respostas de candidatura**  

↓  

**Prompt para criação da área Candidaturas**  

↓  

**Implementação de respostas personalizadas com limite de caracteres e regra de zero invenção**

Essa abordagem permitiu utilizar os resultados de cada etapa para orientar as próximas alterações na aplicação, incluindo a expansão do projeto para além da análise de vagas e geração do currículo.
---

# Como a análise funciona

O fluxo da aplicação foi pensado para funcionar da seguinte maneira:

### 1. Perfil profissional

O usuário fornece seu currículo/perfil profissional em PDF.

A aplicação utiliza esse documento como fonte das informações profissionais do candidato.

A partir dele são identificados dados como:

- resumo profissional;
- experiências;
- formação;
- certificações;
- competências;
- projetos;
- idiomas;
- outras informações profissionais disponíveis.

---

### 2. Descrição da vaga

O usuário informa:

- empresa;
- cargo/vaga;
- descrição da oportunidade.

A descrição da vaga funciona como referência para identificar:

- requisitos;
- responsabilidades;
- competências;
- palavras-chave;
- conhecimentos esperados.

---

### 3. Análise de compatibilidade

A Inteligência Artificial compara as informações da vaga com o perfil profissional.

A análise considera o que foi **encontrado no perfil** e o que **não foi identificado**.

Entre os resultados estão:

- percentual de compatibilidade;
- palavras-chave encontradas;
- palavras-chave parcialmente relacionadas;
- palavras-chave não identificadas;
- requisitos encontrados;
- lacunas;
- pontos fortes;
- recomendações.

É importante destacar que:

> **"Não identificado" não significa necessariamente que o candidato não possui determinada habilidade. Significa que não foi encontrada evidência suficiente no perfil fornecido.**

---

### 4. Personalização do currículo

Com base na vaga analisada, a aplicação gera uma versão personalizada do currículo.

A personalização busca destacar informações reais do candidato que sejam relevantes para aquela oportunidade.

As competências também são selecionadas de acordo com a vaga, em vez de simplesmente reproduzir toda a lista disponível no perfil.

---

### 5. Exportação

O currículo pode ser visualizado na aplicação e exportado em formato de documento.

A estrutura busca manter características compatíveis com leitura por ATS:

- layout de uma coluna;
- texto selecionável;
- hierarquia clara;
- bullets simples;
- ausência de elementos gráficos essenciais;
- estrutura objetiva.

O objetivo é produzir um currículo com estrutura simples e facilmente interpretável, sem afirmar que ele será necessariamente aprovado por qualquer sistema ATS específico.

---

### 6. Candidaturas personalizadas

Além da análise da vaga e da geração do currículo, a aplicação possui uma área chamada **Candidaturas**, criada para auxiliar o candidato a responder perguntas presentes em diferentes processos seletivos.

A funcionalidade utiliza o **perfil profissional já cadastrado** na aplicação, evitando que o usuário precise fornecer novamente suas informações a cada candidatura.

Para gerar uma resposta, o usuário informa:

- empresa;
- vaga;
- descrição da oportunidade;
- pergunta do processo seletivo;
- limite de caracteres da resposta.

A Inteligência Artificial utiliza essas informações em conjunto com o perfil profissional para construir uma resposta personalizada.

O objetivo é conectar:

**Perfil profissional + trajetória + experiências reais + requisitos da vaga + desafio da empresa**

Por exemplo, uma pergunta como:

> "Fale sobre você e sua trajetória profissional, contando como pode ajudar a empresa no desafio descrito na vaga."

pode ser respondida considerando as experiências e competências que realmente constam no perfil do candidato.

A funcionalidade não é limitada a uma plataforma específica de recrutamento. O usuário pode utilizar diferentes tipos de perguntas presentes em processos seletivos.

Alguns exemplos são:

- "Fale sobre você e sua trajetória profissional."
- "Por que você quer trabalhar conosco?"
- "Como sua experiência pode contribuir para esta posição?"
- "Conte sobre um desafio profissional que você enfrentou."
- "Quais são suas principais competências?"

### Limite de caracteres

O usuário pode definir o limite de caracteres exigido pelo processo seletivo.

A aplicação apresenta um contador durante a edição da resposta, por exemplo:

**1.327 / 1.500 caracteres**

A resposta gerada deve respeitar o limite informado. Caso o usuário edite o texto manualmente e ultrapasse o limite, a interface sinaliza essa situação.

Também é possível:

- copiar a resposta;
- editar manualmente;
- regenerar a resposta.

### Integração com a análise da vaga

Quando uma vaga já foi analisada anteriormente, as informações dessa análise podem ser utilizadas como contexto adicional para a candidatura.

Dessa forma, a aplicação pode aproveitar informações como:

- requisitos;
- competências relevantes;
- lacunas;
- pontos de aderência;
- descrição da oportunidade.

Mesmo nesse cenário, a regra de integridade permanece válida.

Um requisito identificado na vaga **não é considerado automaticamente uma experiência do candidato**.

Por exemplo, se a empresa solicita experiência com SQL, mas não existe evidência de SQL no perfil profissional, a aplicação não deve afirmar que o candidato possui essa experiência.

### Histórico de candidaturas

As candidaturas geradas podem ser armazenadas para consulta posterior.

O histórico pode registrar informações como:

- empresa;
- vaga;
- pergunta;
- resposta;
- limite de caracteres;
- data da candidatura.

Assim, a aplicação passa a auxiliar não apenas na preparação do currículo, mas também na elaboração das respostas utilizadas durante o processo seletivo.

---

# Integridade das informações

Uma das principais regras de negócio da aplicação é evitar a criação de informações profissionais que não pertencem ao candidato.

A IA pode:

- reorganizar informações;
- melhorar a redação;
- priorizar competências;
- destacar palavras-chave;
- adaptar a apresentação para a vaga.

Mas não deve:

- inventar experiências;
- criar cargos;
- criar empresas;
- adicionar ferramentas não identificadas;
- inventar resultados;
- inventar números;
- criar cursos;
- criar certificações;
- transformar um requisito da vaga em uma competência do candidato sem evidência.

Essa regra foi definida como um dos princípios centrais do projeto.

---

# Aplicação publicada

**Acesse a aplicação:**  
(https://atscareer.lovable.app)
