# Security Policy

Este documento descreve as medidas de segurança adotadas pelo **OpenCode Professional Git Agent**, bem como recomendações para utilização segura.

---

# Objetivo

O agente foi desenvolvido para automatizar tarefas relacionadas ao Git sem comprometer a segurança do repositório, do ambiente de desenvolvimento ou dos dados do usuário.

Seu princípio fundamental é:

> **Automatizar tarefas repetitivas mantendo o usuário no controle das operações críticas.**

---

# Operações permitidas

O agente pode executar automaticamente operações de leitura, como:

- git status
- git diff
- git log
- git branch
- git remote
- git rev-parse
- git rev-list
- git symbolic-ref
- git ls-files

Esses comandos não modificam o repositório.

---

# Operações que exigem aprovação

As operações abaixo exigem confirmação do usuário:

- git commit
- git push

O agente nunca executará essas ações automaticamente enquanto estiver configurado com:

```yaml
ask
```

---

# Operações bloqueadas

Por padrão, o agente bloqueia comandos potencialmente destrutivos, incluindo:

- git reset
- git reset --hard
- git clean
- git checkout
- git switch
- git pull
- git merge
- git rebase
- rm

Esses comandos podem alterar ou remover trabalho existente.

---

# Push protegido

O agente nunca envia alterações ao repositório remoto sem:

- identificar a branch atual;
- identificar o repositório remoto;
- mostrar quais commits serão enviados;
- solicitar aprovação explícita.

Push forçado é proibido.

Os seguintes comandos permanecem bloqueados:

```
git push --force
git push --force-with-lease
```

---

# Arquivos sensíveis

Antes de preparar arquivos para commit, o agente procura possíveis informações sensíveis.

Exemplos:

- .env
- .env.local
- .env.production
- .env.development
- certificados
- chaves privadas
- tokens
- senhas
- credenciais
- arquivos PEM
- arquivos KEY

Caso algum seja encontrado:

- o arquivo não é preparado;
- o conteúdo não é exibido;
- o usuário é informado sobre o risco.

---

# Git Add

O agente evita utilizar:

```
git add .
```

Sempre que possível, prepara apenas os arquivos relacionados ao objetivo do commit.

Isso reduz o risco de incluir arquivos não intencionais.

---

# Validação antes do commit

Antes de criar um commit, o agente:

- analisa o git diff;
- identifica o objetivo das alterações;
- verifica arquivos preparados;
- revisa o conteúdo do staging;
- gera mensagens seguindo Conventional Commits.

---

# Separação lógica

O agente procura dividir alterações independentes em commits separados.

Exemplo:

```
feat(auth)

fix(api)

docs(readme)
```

Isso melhora a rastreabilidade do histórico.

---

# Integridade do histórico

O agente evita:

- commits vazios;
- mensagens genéricas;
- alterações misturadas sem necessidade.

O objetivo é manter um histórico limpo e compreensível.

---

# Responsabilidade do usuário

Embora o agente automatize parte do fluxo de trabalho, a responsabilidade final sobre o código permanece com o usuário.

Antes de aprovar um commit ou push, recomenda-se revisar:

- arquivos modificados;
- mensagens de commit;
- destino do push.

---

# Boas práticas recomendadas

Recomenda-se:

- revisar alterações antes do commit;
- utilizar branches por funcionalidade;
- manter o .gitignore atualizado;
- não armazenar credenciais no repositório;
- utilizar Secrets ou variáveis de ambiente;
- executar testes antes do push.

---

# Limitações

Este agente não substitui:

- revisão de código;
- testes automatizados;
- análise de segurança;
- auditorias de dependências;
- ferramentas de CI/CD.

Ele atua como um assistente para o fluxo de Git.

---

# Reportando vulnerabilidades

Caso identifique algum comportamento inseguro ou uma vulnerabilidade, abra uma Issue ou envie um Pull Request descrevendo:

- comportamento observado;
- comportamento esperado;
- versão do agente;
- passos para reprodução.

Evite publicar informações sensíveis em Issues públicas.

---

# Licença

Este projeto é distribuído sob a licença MIT.

Não há garantia de funcionamento ou adequação para um propósito específico.

Utilize por sua conta e risco.
