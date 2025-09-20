# Passo a passo — raciocínio por trás do Fluxo Prático de Trabalho com Git/GitHub

# Por que cada comando existe, o que ele faz internamente e boas práticas ao usá-lo.

## 1. git init

O que acontece: cria a pasta .git (o repositório local) e inicializa os metadados do Git.
Por quê: transforma a pasta do seu projeto em um repositório versionado — agora o Git pode rastrear mudanças.
Dica prática: em versões recentes do Git você pode criar já a branch main com:

git init -b main

Se não usar -b, você pode renomear depois (ver próximo passo). Saída típica: Initialized empty Git repository in /caminho/.git/.

## 2. git branch -M main

git branch -M main

O que acontece: renomeia a branch atual para main (o -M força a renomeação).
Por quê: padrão moderno evita master; consistência com repositórios remotos e políticas de equipe.
Atenção/prática: a renomeação pressupõe que exista uma branch atual (isto é, geralmente após um commit inicial). Alternativas seguras:

use git init -b main no passo 1; ou

crie um commit inicial (ex.: README.md) e só então rode git branch -M main.

## 3. git add .

git add .

O que acontece: coloca alterações (todos os arquivos do diretório) na staging area (índice).
Por quê: Git separa “arquivos modificados” do que será incluído no próximo commit; git add escolhe o que vai para o commit.
Dica: prefira git add -p para revisar pedaços de mudanças antes de adicionar; use .gitignore para evitar adicionar arquivos indesejados.

## 4. git commit -m "Mensagem"

git commit -m "Mensagem"

O que acontece: cria um objeto commit que contém o snapshot do índice, autor, data e mensagem.
Por quê: registra uma versão imutável do projeto — seu ponto de restauração.
Boas práticas de mensagem: use verbo no imperativo, resuma em ~50 chars, deixe linha em branco e detalhe quando necessário. Ex.: feat: adicionar endpoint de login.

Se precisar ajustar o último commit (ex.: mensagem ou incluir arquivo esquecido): git commit --amend.

## 5. git remote add origin <url>

git remote add origin git@github.com:usuario/repositorio.git

# ou

git remote add origin https://github.com/usuario/repositorio.git

O que acontece: registra um nome (origin) apontando para o repositório remoto.
Por quê: preciso disso para enviar (push) e receber (pull) alterações do servidor (GitHub/GitLab).
Verificação: git remote -v mostra as URLs configuradas.

## 6. git push -u origin main

git push -u origin main

O que acontece: envia sua branch main para o remoto e define origin/main como upstream (graças ao -u).
Por quê: -u facilita futuros git push/git pull sem precisar repetir origin main.
Observação: se o remoto já tiver commits divergentes, o push pode falhar — geralmente resolvido com git pull/rebase antes de push.

## 7. git checkout -b nova-feature

git checkout -b nova-feature

# (alternativa moderna) git switch -c nova-feature

O que acontece: cria e muda para a branch nova-feature. A partir daqui os commits ficam isolados dessa branch.
Por quê: isolar desenvolvimento de uma feature evita quebrar o código principal (main) e facilita revisão/rollback.
Dica: nomeie branches de forma clara: feature/123-login, fix/bug-321, chore/deps.

## 8. git add + git commit (na branch de feature)

Fluxo repetitivo: faça pequenas alterações → git add → git commit -m "...".
Por quê: commits pequenos e frequentes facilitam revisão e diagnóstico.
Dica: empurre a branch pro remoto para backup/PR:

git push -u origin nova-feature

## 9. git checkout main + git merge nova-feature

git checkout main
git merge nova-feature

# ou preferencialmente faça via Pull Request na plataforma (GitHub)

O que acontece: integra os commits da branch nova-feature à main.
Por quê: incorpora a feature testada para o ramo estável.
Tipos de merge:

Fast-forward: move o ponteiro se não houver commits paralelos.

--no-ff: cria um commit de merge explícito (útil para manter histórico de feature).
Se houver conflitos: abra os arquivos, resolva os trechos <<<<<<< → >>>>>>>, git add e finalize com git commit.
Limpeza pós-merge:

git branch -d nova-feature # deleta local
git push origin --delete nova-feature # deleta remoto

## 10. git pull

# ou (recomendado em muitos fluxos) git pull --rebase

O que acontece: faz fetch do remoto e depois merge (padrão) com sua branch local.
Por quê: mantém seu repositório local sincronizado com mudanças de colegas.
Dica: git pull --rebase mantém histórico linear (reaplica commits locais sobre o que veio do remoto). Alternativa mais controlada:

git fetch origin
git rebase origin/main # ou git merge origin/main

## 11. git log, git status, git diff

Usos rápidos:

git status — mostra estado atual (arquivos modificados, staged, branch e upstream). Sempre cheque antes de commitar.

git diff — vê diferenças não staged.

git diff --staged — diferenças preparadas para commit.

git log --oneline --graph --decorate --all — visão compacta do histórico com grafo.

Essas ferramentas ajudam a entender o que vai para o commit e o histórico do projeto.

# Boas práticas resumidas

## Faça commits pequenos e temáticos.

## Mensagens claras (imperativo).

## Puxe (pull) antes de começar uma nova feature.

## Prefira PRs (pull requests) para revisões e CI antes de merge.

## Proteja main com regras (merge via PR, testes obrigatórios).

## Use git stash para salvar mudanças rápidas sem commitar.

## Limpe branches remotas obsoletas: git fetch --prune.
