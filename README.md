# GitHUB - Regras de organização :

Neste ficheiro eu vou apresentar as regras de organização que vou utilizar para poder controlar o percurso dos projectos no GitHub.


INDICE :

01. Regras de organização baseadas nos princípios definidos pelo Gustavo Sales :

- LINK : https://github.com/guscsales
- LINK : https://www.youtube.com/watch?v=oVnenyWTndY
- LINK : https://www.tabnews.com.br/guscsales/uma-maneira-de-organizar-suas-branches-commits-e-pull-requests

02. Regras de organização baseadas na "Atlassina 'smart commits' policy" ;

03. Regras de organização baseadas nos comandos principais do Git ;
_______________________________________________________________________________________________________________________________

## Atlassina Account :

- Atlassina :
https://id.atlassian.com/login?continue=https%3A%2F%2Fadmin.atlassian.com%2F%3Fare%3Daid

- Jira : https://lccodefreak.atlassian.net/jira/your-work

- account : https://lccodefreak.atlassian.net
  
- emaill : lc.codefreak@gmail.com

- password :Lmprsc.pessoal2022
  
_______________________________________________________________________________________________________________________________

## 01. Regras principais para organizar o GitHub :

### Organizar Suas Branches, Commits e Pull Requests


#### Passo 1 - Nome da Branch :

Normalmente usamos algum provedor de gerenciamento de tarefas, seja JIRA, Trello, Asana ou qualquer outro. O ponto é: provavelmente você vai ter algum tipo de identificador que esteja atrelado à aquela tarefa, no caso do JIRA ele sempre cria um sufixo seguido de um número. Um ponto legal é que existem integrações entre o GitHub e o JIRA por exemplo (e também entre outras aplicações) então fica tudo conectado quando se cria uma branch num estilo mais ou menos assim:

```bash
 Padrão:
<id-da-sua-tarefa>/<super-resumo-da-feature>

# Exemplo:
git checkout -b TL-100/create-post-api

Nota - Exemplo de quando seu GitHub está integrado com o JIRA e usando esse padrão acima:
     - Conexão JIRA e GitHub
```


#### Passo 2 - Utilizar Padrões de Commit :

Já não é de hoje que a convenção de commits do Angular é extremamente popular. E sim, ela ajuda demais à organizar os nossos commits, simplesmente porque conseguimos dividir em algo como: "tipo(escopo): descriçao". Nessa ideia temos os mais famosos tipos de commits que são os seguintes:

- feat: Um novo recurso para a aplicação, e não precisa ser algo grande, mas apenas algo que não existia antes e que a pessoa    final irá acessar.
- fix: Correções de bugs
- docs: Alterações em arquivos relacionados à documentações
- style: Alterações de estilização, formatação etc
- refactor: Um codigo de refatoração, ou seja, que foi alterado, que tem uma mudança transparente para o usuário final, porém    uma mudança real para a aplicação
- perf: Alterações relacionadas à performance
- test: Criação ou modificação de testes
- chore: Alterações em arquivos de configuração, build, distribuição, CI, ou qualquer outra coisa que não envolva diretamente    o código da aplicação para o usuário final

```bash
# Exemplo
feat(posts): creating hook to integrate with posts API
test: add missing tests for posts hook

Nota - Vale lembrar que o "escopo" é opcional.
```


#### Passo 3 - Padrão de Título na Pull Request :

Depois que você já subiu sua branch com tudo feito, uma das partes cruciais para se ter uma boa documentação são as pull requests. Quando você executa um "Squash and Merge" dentro do GitHub por exemplo, é o título da sua pull request que fica como commit principal e dentro da mensagem do commit ficam os outros commits. Então um padrão bem interessante é seguir a mesma ideia da convenção, com alguns upgrades:

```bash
# Padrão:
[<id-da-sua-tarefa>] tipo(escopo): descriçao

# Exemplo:
[TL-100] feat(posts): creating hook to integrate with posts API
```


#### Passo 4 - Fazer Uma Boa Descrição na Pull Request :

Eu sei que escrever a parte técnica pode ser muito chato as vezes, mas é parte do trabalho do dia a dia de um dev. Nem sempre faremos só coisas legais. Juntando o título no qual já tem o link para a estória, onde ficam as descrições de regras de negócio, adicionado um breve resumo do escopo no título e mais os detalhes técnicos na descrição seguido de um screenshot da tela (se possível) é um prato cheio para conseguir mitigar problemas e resolve-los rapidamente sem ficar se perdendo no meio do caminho.

Esse é o padrão que adaptei de um outro já existente e tem funcionado bem no meu dia a dia:

```bash
## Type of change

- [ ] Bug fix (non-breaking change which fixes an issue)
- [ ] New feature (non-breaking change which adds functionality)
- [ ] Chore (documentation, packages, or tests updates, nothing that affect the final user directly)
- [ ] Release (new version of the application - only for production)

## Description

...

## Screenshots

...

## Tasks

- [task-id](task-link) or N/A

## Checklist

- [ ] My changes have less than or equal 400 lines
- [ ] I have performed a self-review of my own code
- [ ] The existing tests and linter pass locally with my changes
- [ ] I have commented my code in hard-to-understand areas (if applicable)
- [ ] I have created tests for my fix or feature (if applicable)

## Dependencies

This pull request has a dependency on the following others:

- link-to-depency PR or N/A
```

Explicando:

- Item 1: Tipo da alteração, se é bug fix, feature, chore ou uma release (para o caso de fazer releases com alguma branch que    não é a "main")
- Item 2: Descrição com mais detalhes, principalmente se esse recurso altera pontos fundamentais do sistema. Pontos esses que    nós precisaremos lembrar no futuro, uma vez que não podemos confiar em nossas memórias
- Item 3: Se for possível e fizer sentido, capturas de telas que explicam melhor o recurso
- Item 4: Os links para as tarefas na aplicação que gerencia as estórias e tarefas
- Item 5: Checklist básico para subir uma PR:
     - Menos de 400 linhas ;
     - Revisão no próprio código antes de abrir PR ;
     - Todos os testes existentes passaram ;
     - Comentários em lugares necessários foram escritos ;
     - Criação de testes para o novo recurso ;
 - Item 6: Outras pull requests que são dependentes, por exemplo: alguma pull request com uma API do backend que é necessária     estar entregue antes de subir uma tela no frontend.

   
Lembrando que para adicionar padrões de template na pull request você pode utilizar essa forma: criar uma pasta .github na raiz do seu projeto e dentro um arquivo chamado ```bash pull_request_template.md ``` com o template acima. Automaticamente o GitHub vai entender isso e abrir as pull requests com esse template.


#### Dicas - Assignees, Labels e Multiplos Commits :

Em uma pull request procure preencher outros dois campos (exemplos usando o GitHub):

- "Assignees": as pessoas que trabalharam naquele recurso, porque em caso de problemas, é fácil achar quem tem mais contexto     no time.
- "Labels": uma ou mais labels que fazem sentido para aquele recurso (eu gosto de bastante informação, pra mim quanto mais       melhor)
  
Por último crie multiplos commits para suas alterações, procure não alterar uma feature inteira e jogar um número enorme de arquivos (salvo exceções) em um único commit, assim fica mais fácil também de entender o que rolou no processo de desenvolvimento daquele recurso.


_______________________________________________________________________________________________________________________________

## 02. Atlassina "smart commits" policy 

### Ligar o GitHub ao Jira

Conecte facilmente uma ou mais organizações do GitHub ao seu site do Jira e selecione repositórios específicos para reunir o seu trabalho. Use a sintaxe do "Smart Commits" para conectar o GitHub e o Jira :

#### Contexto automático nos seus problemas do Jira 

Obtenha atualizações e links sobre o que está acontecendo com seus repositórios nos problemas do Jira para coisas como:

- Pull Requests
- Commits
- Branches

#### Realizar acções em problemas do Jira

Utilize comandos específicos na sua mensagem de confirmação para realizar acções no Jira, por exemplo:

- Close an issue
- Add a comment
- Update time tracking information
- Transition workflow state

_______________________________________________________________________________________________________________________________

Quando gere os repositórios do seu projeto no "Bitbucket" ou no "GitHub", ou utiliza o "Fisheye" para navegar e pesquisar os seus repositórios, pode processar os problemas do "Jira Software" utilizando comandos especiais, denominados "Smart Commits", nas suas mensagens de confirmação.

É possível:

- comentar problemas
- registar informações de controlo do tempo em relação a questões
- fazer a transição de problemas para qualquer estado definido no fluxo de trabalho do projeto Jira Software.

Há outras ações disponíveis se você usar o "Crucible" para revisões de software. 
Veja Usando Smart Commits na documentação do "Crucible".

Um comando "Smart Commit" não deve abranger mais de uma linha (ou seja, não pode usar retornos de carruagem no comando), mas pode adicionar vários comandos à mesma linha. Veja este exemplo abaixo.

_______________________________________________________________________________________________________________________________
### Smart Commit commands:

The basic syntax for a Smart Commit message is:

```bash <ignored text> <ISSUE_KEY> <ignored text> #<COMMAND> <optional COMMAND_ARGUMENTS>```

Any text between the issue key and the command is ignored.

There are three commands you can use in your Smart Commit messages:

```bash
- comment
- time
- transition
```

### Comment :

<img width="754" alt="Captura de ecrã 2024-03-24, às 15 36 41" src="https://github.com/LCcodefreak/Repository_Main/assets/164329443/5dc11f19-1cc5-4789-a2d7-bf0aa5ea7684">


### Time  :

<img width="752" alt="Captura de ecrã 2024-03-24, às 15 42 06" src="https://github.com/LCcodefreak/Repository_Main/assets/164329443/dc84549a-6536-45aa-a818-97c23c4bf0b8">

### Workflow transitions :

<img width="604" alt="Captura de ecrã 2024-03-24, às 15 42 27" src="https://github.com/LCcodefreak/Repository_Main/assets/164329443/8f4f371f-86ff-4e3b-bc2d-ff2c614f333c">


### View development information on your Jira issues

To view linked development information in a Jira issue :

1. Navigate to the issue.
2. Under Development, select the number of pull requests, branches, or commits to see additional information.


### Advanced examples

#### Multiple commands on a single issue

<img width="752" alt="Captura de ecrã 2024-03-24, às 15 46 53" src="https://github.com/LCcodefreak/Repository_Main/assets/164329443/aaa9a40b-b71f-48f3-89e2-6a952580ca83">

#### Multiple commands over multiple lines on a single issue

<img width="751" alt="Captura de ecrã 2024-03-24, às 15 47 05" src="https://github.com/LCcodefreak/Repository_Main/assets/164329443/f292a763-5b5d-4a85-9723-41f47e1afde9">

#### A single command on multiple issues

<img width="751" alt="Captura de ecrã 2024-03-24, às 15 47 14" src="https://github.com/LCcodefreak/Repository_Main/assets/164329443/74208db8-8139-45a4-b805-d56a09f1bcd8">

#### Multiple commands on multiple issues

<img width="752" alt="Captura de ecrã 2024-03-24, às 15 48 26" src="https://github.com/LCcodefreak/Repository_Main/assets/164329443/4d55addb-4edb-4954-bfa9-de2323a3e64e">

### Get Smart Commits working
It's easy to get Smart Commits working for your instance of Jira Software:

<img width="754" alt="Captura de ecrã 2024-03-24, às 15 49 10" src="https://github.com/LCcodefreak/Repository_Main/assets/164329443/9211be1c-19a5-4df2-8f3b-c8382819d084">

#### Notes:

- Smart Commits only support the default Jira Software issue key format. This format is two or more uppercase letters,         followed by a hyphen and the issue number, for example JRA-123. 

- A DVCS such as Git includes a user's email address in the commit data. Users configure this email address in their local system. Smart Commits requires that this email address match exactly one email address in the Jira Software user base. If the email address matches to multiple users in Jira Software, or the user does not have permissions for the requested action, the Smart Commit action will fail. The commit itself will succeed however, and will show on the issue. Mismatched email addresses is a common reason why Smart Commits fail to work as expected. If a Smart Commit fails, Jira Software sends an email notification to either the Jira Software user, or to the DVCS user (if a Jira Software user can't be identified). In rare cases, Jira Software doesn't have either of these email addresses, and the Smart Commit fails silently.

- Smart commit commands that you execute will appear duplicated under certain circumstances. Altering commit history creates "new" commits, which replace the "old" ones. If those "new" commits contain the same smart commit commands as before the history rewrite, then the same smart commits will be executed again and hence appear to have been duplicated. The commit history altering git commands include git push --force and git merge --squash.

- Earlier Bitbucket was not sending the merge commit flag to Jira during event delivery. So ‘Smart commits’ was treating all commits as regular commits. Now, CommitEvent send to EventDelivery contains COMMIT_MERGED flag. Hence, use the below default merge commit format:

<img width="753" alt="Captura de ecrã 2024-03-24, às 15 50 36" src="https://github.com/LCcodefreak/Repository_Main/assets/164329443/4faffa87-055f-41b2-b2f1-a9cc1a1fe692">


It is recommended not to add the smart commit commands to the PR title that gets added to the merge commit message after merge. Instead, manually edit the merge commit message to get the smart commits working again.

_______________________________________________________________________________________________________________________________

## 03. Comandos principais do Git :

### git clone

Esse comando é utilizado para baixar repositórios existentes, seja no GitHub ou qualquer outra plataforma que usa GIT, mas esse download é feito de forma local dentro da sua máquina.

#### Como utilizar

```bash
git clone <url_do_projeto>

# Exemplo
git clone https://github.com/guscsales/thon-ui.git
```

### git init

O principal comando para inicializar o git é o `git init`. Ao executar esse comando uma pasta chamada `.git` é criada no diretório onde ele foi executado e nessa pasta você pode fazer o link para a origem (origin) remota, que pode ser o GitHub, GitLab, Bitbucket ou qualquer outra plataforma que utilize o Git.

#### Como utilizar

```bash
git init
```

### git add

Esse comando vai transportar todos os arquivos, sejam novos ou modificados para um lugar chamado "stage”. Podemos adicionar arquivo por arquivo, ou então todos de uma vez.

#### Como utilizar

```bash
git add <. ou arquivo ou pasta>

# Adicionando todos os arquivos e pastas
git add .

# Adicionando um arquivo
git add index.html

# Adicionando uma pasta
git add assets
```

### git status

Com ele nós conseguimos ver o que está no "stage” e o que não está, também se um arquivo será adicionado ou deletado. Assim fica mais claro entender o que vai para o commit e o que não vai para o seu commit.

#### Como utilizar

```bash
git status
```

### git commit

O `git commit` cria para você um registro com uma mensagem daquilo que você jogou em "stage” através do comando `add`.

#### Como utilizar

```bash
git commit -m <mensagem_do_commit>

# Exemplo
git commit -m "feat(auth): create login screen"
```

**Dica: Para uma melhor organização é interessante utilizar os padrões de commit chamados [Conventional Commits (Link Oficial)](https://www.conventionalcommits.org/en/v1.0.0/) você também pode ler o artigo em português ["Conventional Commits Pattern"](https://medium.com/linkapi-solutions/conventional-commits-pattern-3778d1a1e657) escrito por Victor Ribeiro.**

### git push

Esse comando faz com que todos os nossos commits sejam empurrados (tipo um upload) na origem do repositório, poe exemplo, dentro do GitHub. Ao executar com o `-u` você está dizendo que essa branch faz parte de um repositório remoto, o `-u` é uma abreviação para o `--set-upstream`.

Não será necessário utilizar o `-u` o tempo todo, apenas quando novas branches forem criadas para joga-las no provedor Git.

Caso o `git push` seja executado sem o `-u` será necessário sempre informar a origem e o nome da branch para que as alterações sejam levadas ao provedor Git.

#### Como utilizar

```bash
# Na primeira vez
git push -u origin <nome_da_branch>

# Nas outras vezes
git push

# Quando executado sem -u
git push origin <nome_da_branch>
```

### git pull

Ao rodar esse comando em qualquer branch, seja na main ou em outra, você consegue pegar a última versão que está na origem remota, ou seja, todos os novos commits das pessoas que trabalharam naquele projeto vai diretamente para a branch em questão.

Uma nota importante, se você fez um push com -u em algum momento, apenas um git pull dentro da branch será necessário, mas caso você não tenha feito isso, para baixar as atualizações será necessário rodar um git pull com `origin <nome_da_branch>`.

#### Como utilizar

```bash
git pull

# Se precisar buscar na origin, quando não foi feito `git push -u`
git pull origin <nome_da_branch>
```

### git checkout

O git checkout acessa branches, ou seja, ramificações existentes (locais ou remotas) e também cria uma nova branch a partir de outra que você já esteja, quando acompanhado do `-b` em sua execução.

As branches normalmente são utilizadas para criar novas features sem precisar afetar a principal, ou seja, a branch `main` (na maior parte dos casos).

#### Como utilizar

```bash
git checkout <nome_da_branch>

# Para criar uma nova branch
git checkout -b <nome_da_branch>
```

### git branch

Lista todas as branches locais ou remotas, também delete branches locais.

#### Como utilizar

```bash
git branch

# Para deletar uma branch local
git branch -D <nome_da_branch>

# Para deletar uma branch remota
git push --delete origin <nome_da_branch>
```

### git rebase

Esse comando alinha todos os commits de uma branch, seja a principal ou qualquer outra que você escokher na branch atual em que você está localizado, porém sem criar um novo commit, como faz o `git merge`, mantendo o histórico linear.

#### Como utilizar

```bash
git rebase <nome_da_branch>

# Exemplo, você atualmente está na branch "tela-de-login"
git rebase main
```






Luis Cordeiro - ultima actualização março 2024
