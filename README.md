# 🧭 Guia de Git Flow 

> Este guia é voltado para quem vai contribuir no projeto atual. O fluxo Git Flow **já está configurado**. Aqui explicamos como usá-lo no dia a dia.

## 🧠 O que é Git?

Imagina que você está desenhando com seus amigos em um grande caderno. Cada pessoa trabalha em uma folha diferente, e no final vocês juntam tudo para formar um livro. O **Git** é como um sistema que ajuda a organizar essas folhas, mostrar quem desenhou o quê, e permitir que todo mundo trabalhe junto **sem bagunçar** o caderno.

 
Em outras palavras **Git é um sistema de controle de versão**. Ele guarda o histórico de todas as mudanças feitas em um projeto, permite que várias pessoas trabalhem ao mesmo tempo e ajuda a evitar conflitos entre as alterações.

## 🧩 Conceitos Básicos

| Conceito            | Explicação Simples                                                                 |
|---------------------|------------------------------------------------------------------------------------|
| **Repositório**     | É uma pasta onde ficam guardados todos os arquivos e o histórico do projeto.      |
| **Repositório local** | É a cópia do projeto que está no seu computador.                                  |
| **Repositório remoto (origin)** | É o projeto guardado em um servidor online, como o GitHub.                     |
| **Branch (ramo)**   | É uma linha separada de trabalho, onde você pode fazer alterações sem afetar o principal. |
| **Checkout**        | É o comando usado para mudar de uma branch para outra.                             |
| **Commit**          | É quando você salva uma ou mais alterações no projeto com uma mensagem explicando o que foi feito. |
| **Push**            | Envia as alterações do seu repositório local para o repositório remoto.           |
| **Pull**            | Baixa as alterações mais recentes do repositório remoto para o seu computador.    |
| **Merge**           | Junta as alterações de uma branch com outra.                                       |
| **Pull Request (PR)** | É um pedido para que suas alterações sejam revisadas e adicionadas ao projeto principal. |

## 📌 O que é Git Flow?

Git Flow é uma estratégia de ramificação que organiza o desenvolvimento em diferentes tipos de branches:

| Tipo de Branch | Função |
|----------------|--------|
| `main`         | Código em produção |
| `release/*`    | Versões de entrega (homol) |
| `develop`      | Código em desenvolvimento |
| `feature/*`    | Funcionalidades novas |
| `hotfix/*`     | Correções urgentes |

## 📌 Pré-requisitos
- Git instalado na sua maquina
- Acesso ao repositório remoto ✅
- Conta configurada com SSH ou autenticação por token

## 📌 Instalando e Configurando o Git

### 🔵 Windows

1. Baixe e instale o [Git](https://git-scm.com/downloads/win)
2. Durante a instalação, aceite as opções padrão.
3. Após instalar, abra o **Git Bash**.

### 🍎 macOS
1. Instale o Git:

```bash
brew install git
```
### 🐧 Linux

```bash
sudo apt update
sudo apt install git
```
### 💻 Configurando

```bash
git config auto.pushSetupRemote true
git config --global user.name "Seu Nome"
git config --global user.email "seu@email.com"
```
> **NOTE:** Com isso você já deve conseguir clonar o projeto e trabalhar normalmente, porem existem configurações adicionais como o Token e o SSH


## Comandos utilizados

| Comando                       | Explicação Simples                                                                                  |
|-------------------------------|-----------------------------------------------------------------------------------------------------|
| **git clone**                 | Faz o download do projeto e cria uma cópia local no seu computador.                                 |
| **git checkout**              | Troca para outra branch existente.                                                                  |
| **git checkout -b**           | Cria uma nova branch e já muda para ela.                                                            |
| **git status**                | Mostra o que foi alterado, adicionado ou ainda não está salvo.                                      |
| **git add***                  | Adiciona as alterações para serem salvas no próximo commit.                                         |
| **git commit -m**             | É quando você salva uma ou mais alterações no projeto com uma mensagem explicando o que foi feito.  |
| **git push**                  | Envia as alterações do seu repositório local para o repositório remoto.                             |
| **git pull**                  | Baixa as alterações mais recentes do repositório remoto para o seu computador.                      |
| **git pull origin develop**   | Baixa as alterações mais recentes de um repositório remoto expecifico                               |

> Quando utilizamos o `git add .` adicionamos todas as alterações já o `git add <caminho-e-nome-arquivo>` adiciona somente o arquivo indicado.


## ✅ Utilizando na pratica

### 1. Clonando e iniciando

Crie uma pasta para armazenar os repos do projeto e abra essa pasta no terminal.

```bash
cd projetos #pasta de sua preferencia

git clone <my-project> #clone o repositório
cd my-project #entre na pasta do projeto

code . #abra em uma IDE de sua preferencia

git checkout develop* #alterar para a branch develop
git pull #ou git pull origin develop

git checkout -b feature/nome-da-feature #cria e altera para a nova branch

#A partir de agora vc pode fazer a sua implementação
```

> **IMPORTANT:** Sempre iniciaremos uma nova feature **a partir da develop** por ser a branch mais atualizada com as alterações dos outros integrantes.

### 2. Fazendo commit 

Durante o desenvolvimento da feature, faça commits para ter um histórico do desenvolvimento.

```bash
git status #para vizualizar os arquivos modificados
git add . #ou somente o aquivo que vc quer commitar

git commit -m "feat: descricao clara da sua feature ou alteracao"
```

> **IMPORTANT:** Use convenções de [commits semânticos](https://www.conventionalcommits.org/pt-br/v1.0.0/):  
> `feat`, `fix`, `docs`, `refactor`, `test`, `chore`, etc.
>
> No desenvolvimento utilizaremos pricipalmente o `feat` e o `fix` então não se preocupe com os demais.


### 3. Subir a feature para o repositório remoto

Se desejar que o time veja seu progresso (ou apenas por segurança):

```bash
git push #para branchs que já estão criadas remotamente

git push origin feature/nome-da-feature #para criar a branch remotamente e empurrar as alterações

git push --set-upstream origin feature/nome-da-feature #outra forma de criar e empurrar as alterações para o remoto
```

> **IMPORTANT:** Nunca devemos fazer um push direto para as branchs `main`, `master`, `develop`, ou `release/*`, somente para as `feature/*`

> **NOTE:** Com o **_git config auto.pushSetupRemote true_** você conseguirá utilizar somente o `git push` em todos os cenairos.

### 5. Atualizar develop remoto com as suas alterações

A bransh `develop` deve ser atualizada somente via Pull Requests criados automaticamente pela esteira do GitHub.

---

### 💡 Dicas úteis para o dia a dia

```bash
git branch -a # Ver todas as branches (locais e remotas)
```

### Deixar seu repositório local atualizado com o remoto

```bash
git checkout develop
git pull origin develop
```

### Ver status atual do repositório

```bash
git status
```


## 📁 Lembrete: .gitignore

Este projeto já possui um `.gitignore`.  
Se precisar adicionar mais arquivos ou diretórios que não são necessarios no desenvolvimento, não fique com medo de inserilos no **git ignore**.


## ✅ Resumo rápido do fluxo diário

```bash
# Sempre parta da develop
git checkout develop
git pull origin develop

# Comece sua feature
git checkout -b feature/nome-da-feature

# Faça commits
git add .
git commit -m "feat: algo novo"

# Suba sua feature
git push origin feature/nome-da-feature

# Finalize a feature quando pronta por Pull Request
```

# 🗣️ Comunicação Importante

- Sempre use nomes descritivos para as branches (ex: `feature/tela-login`, `feature/cadastro-usuario`).
- Combine com o time antes de fazer merges importantes.
- Em caso de dúvidas, procure o responsável técnico ou consulte a equipe.
- Sempre tenha em mente os padrões/convenções da tecnologia que está utilizando.


# 📘 Vamos práticar
- Configurar o git na sua maquina
- Clonar o projeto
- Mudar para a branch `develop` e atualizar
- Fazer qualquer inclusão ou alterção
- Criar a sua branch `feature/seu-nome`
- Subir para o GitHub
- Mergear para a `develop` via `pull requests` após um `Code Review`

> Lembrando que não iremos alterar o README.md, e sempre iremos fazer a Pair Programming então o CR é fundamental