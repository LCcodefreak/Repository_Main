# Atlassina Account 
lc.codefreak@gmail.com



# GitHUB - Regras de organização :

Neste ficheiro eu vou apresentar as regras de organização que vou utilizar para poder controlar o percurso dos projectos no GitHub.


INDICE :

01.Estas regras são baseadas nos princípios definidos pelo Gustavo Sales :

- LINK : https://github.com/guscsales
- LINK : https://www.youtube.com/watch?v=oVnenyWTndY
- LINK : https://www.tabnews.com.br/guscsales/uma-maneira-de-organizar-suas-branches-commits-e-pull-requests

02. Atlassina "smart commits" policy ;

03.Comandos principais do Git ;

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

Quando gere os repositórios do seu projeto no Bitbucket ou no GitHub, ou utiliza o Fisheye para navegar e pesquisar os seus repositórios, pode processar os problemas do Jira Software utilizando comandos especiais, denominados "Smart Commits", nas suas mensagens de confirmação.

É possível:

- comentar problemas
- registar informações de controlo do tempo em relação a questões
- fazer a transição de problemas para qualquer estado definido no fluxo de trabalho do projeto Jira Software.

Há outras ações disponíveis se você usar o "Crucible" para revisões de software. 
Veja Usando Smart Commits na documentação do "Crucible".

Um comando "Smart Commit" não deve abranger mais de uma linha (ou seja, não pode usar retornos de carruagem no comando), mas pode adicionar vários comandos à mesma linha. Veja este exemplo abaixo.



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
