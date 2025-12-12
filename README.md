# Shared Gradle Wrapper

Este repositório contém um **Gradle Wrapper compartilhado** usado por múltiplos projetos.  
Ele existe para padronizar a versão do Gradle entre repositórios, evitando duplicação e mantendo atualizações consistentes.

## 📦 Conteúdo

- `gradlew` — Script de execução do Gradle Wrapper  
- `gradle/wrapper/gradle-wrapper.jar` — Binário do wrapper  
- `gradle/wrapper/gradle-wrapper.properties` — Configuração da versão do Gradle

## 🎯 Objetivo

O objetivo é permitir que outros projetos incluam este repositório como:

- **Submódulo Git (`git submodule`)**, ou  
- **Subtree**, caso prefira copiar os arquivos para dentro do repositório principal.

Assim, todos os projetos utilizam a mesma versão do Gradle, sem necessidade de manter vários wrappers separados.

## 🛠️ Como atualizar o Wrapper

Para atualizar o Gradle wrapper aqui:

```bash
./gradlew wrapper --gradle-version X.Y.Z
```

Depois faça commit das alterações:

git add .
git commit -m "Update Gradle wrapper to X.Y.Z"
git push

Todos os repositórios que usam este wrapper (via submódulo/subtree) podem simplesmente atualizar o submódulo ou sincronizar o subtree.

🔗 Uso como Submódulo

No repositório alvo:

git submodule add https://github.com/usuario/shared-gradle.git gradle_shared
git submodule update --init --recursive

E no workflow (GitHub Actions):

./gradle_shared/gradlew assembleRelease

🔧 Uso como Subtree

git subtree add --prefix=gradle_shared https://github.com/usuario/shared-gradle.git main --squash

