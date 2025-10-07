🧱 Guia Completo de Commits Semânticos
🧩 Estrutura geral
<tipo>(escopo opcional): descrição curta e objetiva


tipo → indica a natureza da mudança (obrigatório)

escopo → indica o módulo, pacote ou parte do sistema afetada (opcional)

descrição → resumo breve do que foi feito (até 72 caracteres recomendados)

Exemplo:

feat(auth): adiciona autenticação com Google

🔖 Tipos principais
1. feat — Feature / Nova funcionalidade

Adição de uma nova funcionalidade ou recurso ao sistema.

📘 Exemplos:

feat(api): adiciona endpoint para cadastro de usuários
feat(ui): implementa tema escuro no painel de controle
feat(reports): gera relatórios em formato PDF

2. fix — Correção de erro

Corrige um bug ou comportamento inesperado.

📘 Exemplos:

fix(login): corrige erro de validação de senha
fix(api): ajusta retorno de status HTTP incorreto
fix(ui): corrige alinhamento do botão de salvar

3. docs — Documentação

Alterações apenas em documentação (README, Wiki, comentários, etc.)

📘 Exemplos:

docs(readme): adiciona instruções de instalação
docs(api): atualiza exemplos de uso da API
docs: corrige erro de digitação no guia de contribuição

4. style — Estilo / Formatação

Mudanças que não afetam o funcionamento do código (formatação, espaços, indentação, lint).

📘 Exemplos:

style: aplica padrão PEP8 no código
style(ui): ajusta espaçamento dos elementos da navbar
style: renomeia variáveis para melhorar legibilidade

5. refactor — Refatoração

Reestrutura o código sem alterar o comportamento externo.

📘 Exemplos:

refactor(core): separa lógica de negócio em funções auxiliares
refactor(auth): melhora legibilidade do fluxo de login
refactor(db): remove código duplicado nas queries

6. perf — Performance

Melhora o desempenho ou otimiza recursos.

📘 Exemplos:

perf(api): reduz tempo de resposta ao cachear resultados
perf(images): otimiza carregamento de imagens no frontend
perf(core): usa estrutura de dados mais eficiente

7. test — Testes

Adiciona, corrige ou melhora testes automatizados.

📘 Exemplos:

test(unit): adiciona teste para função de cálculo de desconto
test(api): corrige mocks incorretos no teste de integração
test: aumenta cobertura de testes no módulo utils

8. build — Build / Dependências

Alterações que afetam o processo de build, dependências ou ferramentas externas.

📘 Exemplos:

build: atualiza dependências do projeto
build(ci): ajusta configuração do Dockerfile
build: adiciona script de compilação automatizado

9. ci — Integração Contínua (CI/CD)

Mudanças em pipelines, workflows ou automações de entrega contínua.

📘 Exemplos:

ci(github): adiciona pipeline de testes no GitHub Actions
ci(jenkins): corrige variável de ambiente no pipeline
ci: melhora logs de build para depuração

10. chore — Tarefas de manutenção

Tarefas diversas sem impacto direto na aplicação (scripts, configurações, housekeeping).

📘 Exemplos:

chore: adiciona .gitignore e configurações básicas
chore(deps): atualiza versão do Python para 3.12
chore(lint): adiciona configuração do flake8

11. revert — Reversão de commit anterior

Desfaz um commit específico.

📘 Exemplos:

revert: desfaz commit "feat(api): adiciona endpoint de usuários"

12. merge — Integração de branches

Usado em fusões de branches, especialmente em projetos colaborativos.

📘 Exemplos:

merge: integra branch 'feature/login' na 'develop'
merge: une correções de bug da hotfix v1.0.1

13. deps — Dependências (alternativo a build/chore)

Mudanças exclusivamente relacionadas a bibliotecas ou pacotes usados.

📘 Exemplos:

deps: adiciona biblioteca requests à lista de dependências
deps: remove pacote obsoleto do requirements.txt

⚡️ Complementos úteis
🧠 BREAKING CHANGE

Indica alteração que quebra compatibilidade (mudança drástica na API, estrutura ou contrato de uso).

📘 Exemplo:

feat(api)!: altera formato de resposta dos endpoints


Ou no corpo da mensagem:

feat(auth): altera método de autenticação
BREAKING CHANGE: tokens antigos não são mais válidos

🧾 Resumo geral
Tipo	Propósito	Exemplo
feat	Nova funcionalidade	feat(ui): adiciona tema escuro
fix	Correção de bug	fix(api): corrige erro 500
docs	Documentação	docs(readme): adiciona seção de instalação
style	Formatação / estilo	style: aplica PEP8
refactor	Reestruturação sem mudar comportamento	refactor(core): simplifica função de cálculo
perf	Otimização de performance	perf(api): melhora tempo de resposta
test	Testes	test: adiciona teste de integração
build	Build / dependências	build: atualiza Dockerfile
ci	Integração contínua	ci(github): adiciona pipeline de deploy
chore	Manutenção / tarefas gerais	chore: adiciona .editorconfig
revert	Reversão de commit	revert: desfaz commit anterior
merge	Fusão de branch	merge: integra branch de correção
deps	Gerenciamento de dependências	deps: atualiza biblioteca requests