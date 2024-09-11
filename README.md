# Guia Completo sobre Git Flow e Git

## Introdução

Se você está começando a trabalhar com Git ou quer melhorar suas habilidades, você está no lugar certo.

Hoje, vou te ensinar tudo sobre Git Flow, como baixar um repositório, criar uma branch, fazer commits, resolver conflitos e muito mais.

Então, fique até o final, porque eu preparei um bônus especial que vai te ajudar a aplicar tudo o que aprendeu de forma prática.

## Seção 1: Introdução ao Git

### O que é Git? Como instalar

O Git é um sistema de controle de versão distribuído que permite que várias pessoas trabalhem no mesmo projeto ao mesmo tempo, sem perder o histórico de alterações.
É uma ferramenta essencial para qualquer desenvolvedor, pois facilita o trabalho em equipe e a organização do código.

### O que é Git Flow?

Git Flow é uma metodologia que organiza como as branches são criadas e utilizadas no Git, facilitando o fluxo de trabalho em projetos de software.
Com o Git Flow, você consegue definir um padrão para criação de branches, controle de versões e lançamentos. Isso evita conflitos e ajuda na organização do projeto, especialmente em times maiores.

                  +---------------------+
                  |        main         | Homolog/Master
                  +---------------------+
                            |
                            | Merge
                            v
                  +---------------------+
                  |      release/*       | Feature/123456-criar-nova-pagina -> filha task/78945-criar-rota
                  +---------------------+
                            |
                            | Merge
                            v
                  +---------------------+
                  |     Development     | task/78945-criar-rota
                  +---------------------+
                            |
                            | Merge
                            v
                  +---------------------+
                  |      release/*       | Feature/123456-criar-nova-pagina
                  +---------------------+
                            |
                            | Merge
                            v
                  +---------------------+
                  |      develop        | Testada
                  +---------------------+
                /                      \
               /                        \
              v                          v
    +------------------+       +------------------+
    |    feature/*     |       |    hotfix/*      | Bug
    +------------------+       +------------------+
              |                        |
              | Merge                  | Merge
              v                        v
    +------------------+       +------------------+
    |      develop     |       |      feature/*   |
    +------------------+       +------------------+
              |                        |
              | Merge                  | Merge
              v                        v
    +---------------------+   +---------------------+
    |        main         |   |       develop       | ok
    +---------------------+   +---------------------+
                                      |
                                      | Merge
                                      v
                              +---------------------+
                              |        main         | Prod
                              +---------------------+


## Pratica

## Seção 2: Configurando o Git

### Configuração Inicial do Git

Após instalar o Git, você precisa configurá-lo com seu nome e email, que serão usados nos commits. No terminal, digite os seguintes comandos:

```bash
git config --global user.name 'Seu Nome'
git config --global user.email 'seuemail@dominio.com',
```

[Git SCM Downloads](https://git-scm.com/downloads)

## Seção 3: Baixando um Repositório

### Clonando um Repositório

Para baixar o código de um repositório remoto, usamos o comando `git clone`. Por exemplo:

```bash
git clone https://github.com/usuario/nome-do-repositorio.git
```

## Seção 4: Trabalhando com Branches

### Criando uma Branch

Para criar uma nova branch, use o comando:

```bash
git checkout -b nome-da-branch
```

Isso cria uma nova branch e já alterna para ela.

É importante dar nomes descritivos às branches, como feature/nova-funcionalidade ou bugfix/corrigir-erro, para facilitar a identificação.

# Prefixos de Branches no Git

No gerenciamento de branches no Git, é comum utilizar prefixos para categorizar e identificar o propósito de cada branch. Esses prefixos ajudam a organizar o repositório e facilitam a comunicação sobre as mudanças que estão sendo feitas. A seguir, estão os principais prefixos utilizados e seus propósitos:

## Prefixos de Branches

### `feature/`
- **Uso:** Para adicionar novas funcionalidades ou melhorias ao projeto.
- **Exemplo:** `feature/nova-funcionalidade`

### `hotfix/`
- **Uso:** Para corrigir bugs críticos em produção que necessitam de uma correção rápida.
- **Exemplo:** `hotfix/corrigir-bug-crítico`

### `bugfix/`
- **Uso:** Para corrigir bugs que não são críticos e podem ser corrigidos antes de um próximo lançamento.
- **Exemplo:** `bugfix/corrigir-erro-menor`

### `release/`
- **Uso:** Para preparar o código para um novo lançamento, permitindo ajustes finais e testes antes da liberação.
- **Exemplo:** `release/1.0.0`

### `chore/`
- **Uso:** Para tarefas de manutenção ou melhorias que não estão diretamente relacionadas a funcionalidades ou correções de bugs.
- **Exemplo:** `chore/atualizar-dependencias`

## Benefícios do Uso de Prefixos

- **Organização:** Mantém o repositório organizado e facilita a identificação do propósito de cada branch.
- **Comunicação:** Melhora a comunicação entre os membros da equipe sobre o que está sendo desenvolvido ou corrigido.
- **Gestão de Projeto:** Facilita o gerenciamento do fluxo de trabalho e o acompanhamento das tarefas e correções.

Utilizar esses prefixos de forma consistente ajuda a manter um fluxo de trabalho claro e eficiente no gerenciamento de branches no Git.

## Mudar de branche
  ```bash
    git checkout develop
    git checkout -b feature/nova-funcionalidade
    ```

### Comitando Mudanças

Após fazer alterações no código, você precisa comitar essas mudanças para que elas sejam salvas no histórico do Git. O processo é simples:

```bash
git add .
git commit -m 'Descrição clara do que foi alterado'
```

O **`git add .`** adiciona todas as mudanças ao staging, e o git commit salva essas mudanças no repositório local. Lembre-se de escrever mensagens de commit claras e descritivas.

Puxe as alterações mais recentes do repositório remoto (se necessário):

```bash
git pull origin nome-da-branch
```
Empurre suas alterações para o repositório remoto:

```bash
git push origin nome-da-branch
```

## Seção 5: Resolving Conflitos

### Como Resolver Conflitos no Git

```bash
git merge origin nome-da-branch
```

#### Como Fazer um Merge no Git

Quando você tentar mesclar uma branch e houver um conflito, o Git irá te alertar. Para resolver o conflito:

1. Abra o arquivo que contém o conflito. Você verá as mudanças conflitantes marcadas por `<<<<<<<`, `=======`, e `>>>>>>>`.
2. Edite o arquivo para resolver o conflito, mantendo as mudanças que fazem sentido.
3. Após resolver, adicione o arquivo com:

    ```bash
    git add nome-do-arquivo
    ```

4. Finalmente, finalize o processo com:

    ```bash
    git commit -m 'Resolvendo conflito no arquivo tal'
    ```

Isso irá registrar a resolução do conflito no histórico do Git.

# Como Usar `git commit --amend`

O comando `git commit --amend` permite alterar o último commit feito. Isso é útil para corrigir mensagens de commit ou adicionar mudanças esquecidas.

## Passos para Usar `git commit --amend`

1. **Faça Alterações Adicionais (se necessário):**
   Se você precisar adicionar novas alterações ao commit, primeiro adicione essas mudanças ao staging area:
   ```bash
   git add nome-do-arquivo
    ```
## Modificar o Último Commit

Para editar o último commit, use o comando `--amend`:

```bash
git commit --amend
```
Isso abrirá seu editor de texto para você modificar a mensagem do commit, se necessário.

##Finalizar o Commit
Salve e feche o editor para concluir o amend. O commit será atualizado com as novas alterações ou com uma nova mensagem.

##Empurrar as Alterações
Se você já enviou o commit para o repositório remoto, precisará forçar o push para atualizar o commit remoto:

```bash
git push --force
```
Nota: Use o --force com cuidado, pois ele sobrescreve o histórico de commits no repositório remoto.

## Mover arquivos sem perder o histórico

```bash
git mv nome do arquivo  caminho do arquivo
```


## Seção 6: Explorando o Git Flow em Detalhes

### O Que é o Git Flow e Por Que Usá-lo?

Git Flow é um modelo de ramificação proposto por Vincent Driessen, que segue uma estrutura predefinida para organizar o trabalho em equipe de forma eficiente. Ele define como e quando criar branches (ou ramificações) e qual o papel de cada branch dentro de um projeto de software.

O principal objetivo do Git Flow é ajudar a gerenciar o ciclo de vida de um projeto com:

- **Branches principais e estáveis para código de produção.**
- **Branches de desenvolvimento para novas funcionalidades e correções.**
- **Branches de lançamento para preparar novas versões e garantir que elas estejam prontas para produção.**

### As Principais Branches do Git Flow

Vamos começar entendendo quais são as branches principais no Git Flow e a função de cada uma.

- **main (ou master):** Esta branch contém o código que está em produção. Ela sempre reflete o estado mais recente e estável do projeto. Todo o código que entra nessa branch deve ser completamente testado e livre de bugs.

- **develop:** Aqui é onde acontece o desenvolvimento contínuo. A branch `develop` é uma ramificação da `main` e serve como base para todas as novas features. Toda vez que uma nova funcionalidade é concluída, ela é mesclada com a branch `develop`.

Essas são as duas branches sempre presentes no repositório. Mas para organizar o desenvolvimento de novas funcionalidades, correções de bugs e lançamentos de versões, o Git Flow introduz outras três categorias de branches temporárias, que são criadas para fins específicos e, depois, removidas.

### Branches Temporárias no Git Flow

Agora vamos ver como funcionam essas branches temporárias.

- **feature/*:** Usada para desenvolver novas funcionalidades ou aprimorar o sistema. Cada nova funcionalidade deve ser desenvolvida em uma branch separada, que se ramifica de `develop` e, ao final, é mesclada de volta a `develop`. Por exemplo:

    ```bash
    git checkout develop
    git checkout -b feature/nova-funcionalidade
    ```

Essa branch fica isolada enquanto você trabalha na nova funcionalidade, o que evita que o código instável interfira no restante do projeto. Ao concluir a funcionalidade, ela é mesclada de volta para develop:

    ```bash
    git checkout develop
    git merge feature/nova-funcionalidade
    git branch -d feature/nova-funcionalidade
    ```

- **release/*:** Depois que várias funcionalidades foram adicionadas à branch `develop`, e o código está pronto para uma nova versão, criamos uma branch de release. A branch de release permite que o time faça ajustes finais, como correções de bugs e testes, antes de enviar o código para produção. Para criar uma branch de release, você faz:

    ```bash
    git checkout develop
    git checkout -b release/nova-versao
    ```

Após fazer os ajustes finais e testar a nova versão, a branch de release é mesclada com a branch `main` e com a branch `develop` para garantir que todas as correções sejam integradas.

- **release/*:** Depois que várias funcionalidades foram adicionadas à branch `develop`, e o código está pronto para uma nova versão, criamos uma branch de release. A branch de release permite que o time faça ajustes finais, como correções de bugs e testes, antes de enviar o código para produção. Para criar uma branch de release, você faz:

    ```bash
    git checkout develop
    git checkout -b release/1.0.0
    ```

Depois que todos os ajustes foram feitos, a branch de release é mesclada tanto na branch `main` (código estável) quanto na `develop` (para garantir que os ajustes finais estejam também no código em desenvolvimento). Para fazer isso, use os seguintes comandos:

    ```bash
    git checkout main
    git merge release/1.0.0

    git checkout develop
    git merge release/1.0.0
    ```

- **release/*:** Depois que várias funcionalidades foram adicionadas à branch `develop`, e o código está pronto para uma nova versão, criamos uma branch de release. A branch de release permite que o time faça ajustes finais, como correções de bugs e testes, antes de enviar o código para produção. Para criar uma branch de release, você faz:

    ```bash
    git checkout develop
    git checkout -b release/1.0.0
    ```

Depois que todos os ajustes foram feitos, a branch de release é mesclada tanto na branch `main` (código estável) quanto na `develop` (para garantir que os ajustes finais estejam também no código em desenvolvimento). Para fazer isso, use os seguintes comandos:

```bash
git checkout main
git merge release/1.0.0

git checkout develop
git merge release/1.0.0
git branch -d release/1.0.0
```

- **hotfix/*:** O que acontece quando um bug crítico surge em produção? Usamos a branch `hotfix`. Isso permite que o time conserte o bug rapidamente, sem precisar interromper o desenvolvimento atual em `develop`. Para criar uma branch `hotfix` diretamente da `main`, você faz:

    ```bash
    git checkout main
    git checkout -b hotfix/corrigir-bug-crítico
    ```

Depois de resolver o bug, fazemos o merge da branch `hotfix` tanto na `main` quanto na `develop`, para garantir que o bug não reapareça no código em desenvolvimento. Utilize os seguintes comandos para isso:

```bash
git checkout main
git merge hotfix/corrigir-bug-crítico

git checkout develop
git merge hotfix/corrigir-bug-crítico

git checkout main
git merge hotfix/corrigir-bug-crítico
git checkout develop
git merge hotfix/corrigir-bug-crítico
git branch -d hotfix/corrigir-bug-crítico
```

### O Fluxo Completo no Git Flow

Vamos revisar o fluxo completo do Git Flow com um exemplo prático:

1. **Nova Funcionalidade:** Você começa desenvolvendo uma nova funcionalidade na branch `feature/*` que se ramifica de `develop`.

2. **Integração da Funcionalidade:** Após finalizar a funcionalidade, você a mescla de volta para `develop`.

3. **Preparação para Lançamento:** Quando o código em `develop` está pronto para lançamento, cria-se uma branch `release/*` para ajustes finais e correções.

4. **Lançamento:** Após concluir a release, você mescla a branch `release/*` na `main` e também em `develop` para garantir que todas as correções estejam presentes.

5. **Correção de Bugs:** Se surgir um bug crítico em produção, cria-se uma branch `hotfix/*` a partir de `main`, faz-se o conserto e mescla-se de volta tanto em `main` quanto em `develop`.

Esse modelo organiza o trabalho, facilita a colaboração e garante que o código em produção esteja sempre estável e bem testado.

### Seção 7: Usando o Git no Seu Projeto

#### Aplicando o Git Flow

Para começar a usar o Git Flow em seu projeto, você precisa instalá-lo. Se você estiver usando o Git Flow CLI, execute:

- **Para macOS (usando Homebrew):**

    ```bash
    brew install git-flow
    ```

- **Para distribuições baseadas em Debian:**

    ```bash
    sudo apt-get install git-flow
    ```

Depois de instalar, inicialize o Git Flow em seu repositório com:

```bash
git flow init
```

Isso criará a estrutura de branches padrão para você.

### Seção 8: Dicas Finais

#### Mantenha Suas Branches Pequenas e Focadas

Não deixe as branches crescerem muito. Mantenha-as focadas em uma única tarefa para facilitar a revisão e a integração. Branches menores e mais específicas ajudam a evitar conflitos e tornam o processo de merge mais simples e seguro.

#### Comunique-se com Sua Equipe

Certifique-se de que todos na equipe entendem e seguem o mesmo fluxo de trabalho para evitar confusão e conflitos. Uma comunicação clara e constante ajuda a manter o projeto organizado e a garantir que todos estejam alinhados com as práticas e processos estabelecidos.

### Seção 8: Dicas Finais

#### Mantenha Suas Branches Pequenas e Focadas

Não deixe as branches crescerem muito. Mantenha-as focadas em uma única tarefa para facilitar a revisão e a integração. Branches menores e mais específicas ajudam a evitar conflitos e tornam o processo de merge mais simples e seguro.

#### Comunique-se com Sua Equipe

Certifique-se de que todos na equipe entendem e seguem o mesmo fluxo de trabalho para evitar confusão e conflitos. Uma comunicação clara e constante ajuda a manter o projeto organizado e a garantir que todos estejam alinhados com as práticas e processos estabelecidos.

#### Revise Suas Mensagens de Commit

Escreva mensagens de commit claras e informativas. Isso facilita o rastreamento das mudanças e a colaboração. Mensagens de commit bem escritas são essenciais para entender o histórico do projeto e para colaborar eficazmente com sua equipe.

### Encerramento

Espero que este guia completo sobre Git Flow tenha sido útil para você. Agora você tem todas as ferramentas e conhecimentos necessários para gerenciar suas branches de forma eficaz e resolver conflitos com confiança. Lembre-se de usar o Git Flow para manter seu projeto organizado e facilitar a colaboração em equipe.

### Bônus

E para o bônus especial, eu preparei um exercício prático que você pode usar para aplicar tudo o que aprendeu hoje. No final do vídeo, acesse o link na descrição para baixar um repositório de exemplo com um tutorial passo a passo para praticar o Git Flow.

Se você gostou deste vídeo, não se esqueça de se inscrever no canal, curtir o vídeo e ativar o sininho para não perder nenhuma atualização. E, claro, confira o vídeo anterior para mais dicas sobre programação. Até a próxima!




























## SEÇÃO 1: INTRODUÇÃO AO GIT


Para começar, vamos entender o que é o Git. O Git é um sistema de controle de versão distribuído que permite que várias pessoas trabalhem no mesmo projeto ao mesmo tempo, sem perder o histórico de alterações. É uma ferramenta essencial para qualquer desenvolvedor, pois facilita o trabalho em equipe e a organização do código.

### 1.1. O que é Git Flow?

Git Flow é uma metodologia que organiza como as branches são criadas e utilizadas no Git, facilitando o fluxo de trabalho em projetos de software. Com o Git Flow, você consegue definir um padrão para criação de branches, controle de versões e lançamentos. Isso evita conflitos e ajuda na organização do projeto, especialmente em times maiores.

# Git Flow: Guia Completo

Este documento explica o fluxo de trabalho Git Flow, como gerenciar branches e as melhores práticas para garantir um desenvolvimento eficiente e organizado.

## O Que é Git Flow?

Git Flow é um modelo de ramificação que organiza o ciclo de vida de desenvolvimento de software. Ele define um processo claro para trabalhar com branches, permitindo que você desenvolva novas funcionalidades, prepare lançamentos e corrija bugs de maneira organizada, sem comprometer o código em produção.

## Branches Principais

- **`main` (ou `master`)**: Contém o código estável, pronto para produção. Todo código que chega a essa branch precisa estar completamente testado.

- **`develop`**: Esta é a branch de desenvolvimento. Ela serve como base para todas as novas funcionalidades. As novas features são mescladas de volta para `develop` após a conclusão.

## Branches Temporárias

Além das branches principais, o Git Flow usa branches temporárias para funcionalidades específicas:

### Branches de Funcionalidade (`feature/*`)

Usada para desenvolver novas funcionalidades, se ramifica a partir de `develop`:

```bash
git checkout develop
git checkout -b feature/nome-da-funcionalidade
git checkout develop
git merge feature/nome-da-funcionalidade
git branch -d feature/nome-da-funcionalidade
```
