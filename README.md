# Para praticar o GitFlow

# 🧭 Guia de Git Flow para Contribuição no Projeto

> Este guia é voltado para quem vai contribuir no projeto atual. O fluxo Git Flow **já está configurado**. Aqui explicamos como usá-lo no dia a dia.

---

## 📌 O que é Git Flow? (Contexto rápido)

Git Flow é uma estratégia de ramificação que organiza o desenvolvimento em diferentes tipos de branches:

| Tipo de Branch | Função |
|----------------|--------|
| `main`         | Código em produção |
| `develop`      | Código em desenvolvimento |
| `feature/*`    | Funcionalidades novas |
| `release/*`    | Versões de entrega |
| `hotfix/*`     | Correções urgentes |

---

## ✅ O que você vai usar no dia a dia

### 1. Criar uma nova feature

Sempre crie sua feature a partir da branch `develop`:

```bash
git checkout develop
git pull origin develop

git flow feature start nome-da-feature

#Ou utilizar o mais comum:

git checkout develop
git pull #ou git pull origin develop

git checkout -b feature/nome-da-feature

```

> Isso criará e moverá você para a branch `feature/nome-da-feature`.

---

### 2. Fazer commits normalmente

Durante o desenvolvimento da feature, faça commits como de costume:

```bash
git add . #ou somente o aquivo que vc quer commitar
git commit -m "feat: descrição clara da sua feature"
```

> Use convenções de [commits semânticos](https://www.conventionalcommits.org/pt-br/v1.0.0/):  
> `feat`, `fix`, `docs`, `refactor`, `test`, `chore`, etc.

> No desenvolvimento utilizaremos pricipalmente as `feat` e `fix` então não se preocupe com os demais.

---

### 3. Subir a feature para o repositório remoto

Se desejar que o time veja seu progresso (ou apenas por segurança):

```bash
git push origin feature/nome-da-feature

# se der errado

git push --set-upstream origin feature/nome-da-feature
```

---


### 5. Atualizar o repositório remoto com a nova develop

A bransh `develop` deve ser atualizada somente via Pull Requests criados automaticamente pela esteira do GitHub.

---

## 💡 Dicas úteis para o dia a dia

### Ver todas as branches (locais e remotas)

```bash
git branch -a
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

---

## 🛠️ Extras (não usados no dia a dia)

Esses comandos **já foram executados durante a configuração inicial** do projeto, mas vale saber o que são:

### Iniciar Git Flow (não use neste projeto)

```bash
git flow init
```

### Criar outras branches se necessário

- **Release:**

```bash
git flow release start nome-versao
```

- **Hotfix:**

```bash
git flow hotfix start nome-do-hotfix
```

---

## 📁 Lembrete: .gitignore por linguagem

Este projeto já possui um `.gitignore`.  
Se precisar adicionar mais linguagens, gere um novo com:

### Usando o site

👉 [https://www.toptal.com/developers/gitignore](https://www.toptal.com/developers/gitignore)

### Exemplo via terminal (Flutter + Linux):

```bash
curl -L -s https://www.toptal.com/developers/gitignore/api/flutter,linux -o .gitignore
```

---

## ✅ Resumo rápido do fluxo diário

```bash
# Sempre parta da develop
git checkout develop
git pull origin develop

# Comece sua feature
git flow feature start nome-da-feature

# Faça commits
git add .
git commit -m "feat: algo novo"

# Suba sua feature (opcional, mas recomendado)
git push origin feature/nome-da-feature

# Finalize a feature quando pronta
git flow feature finish nome-da-feature

```

---

## 🗣️ Comunicação

- Sempre use nomes descritivos para as branches (ex: `feature/tela-login`, `feature/cadastro-usuario`).
- Combine com o time antes de fazer merges importantes.
- Em caso de dúvidas, procure o responsável técnico ou consulte a equipe.

---

## 📘 Vamos práticar 🚀
- Configurar o git na sua maquina
- Clonar o projeto
- Mudar para a branch `develop` e atualizar
- Fazer qualquer inclusão ou alterção
- Criar a sua branch `feature/seu-nome`
- Subir para o GitHub
- Mergear para a `develop` via `pull requests` após um `Code Review`

> Lembrando que não iremos alterar o README.md, e sempre iremos fazer a Pair Programming então o CR é fundamental.