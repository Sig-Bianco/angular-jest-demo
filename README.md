# Instalando e Configurando o Jest no Angular

Este tutorial fornecerá instruções passo a passo para instalar e configurar o Jest como framework de testes unitários em
um projeto Angular

> Esse tutorial utiliza o suporte experimental do Jest para versão 16 do Angular. Optamos por apresentar o framework de testes Jest devido à sua capacidade de executar testes sem a necessidade de um navegador real, proporcionando vantagens significativas, especialmente em ambientes de Integração Contínua (CI). Isso simplifica e acelera a execução dos testes unitários em projetos Angular.

### Passo 1: Remover Dependências Antigas

Remova as dependências antigas relacionadas aos testes Jasmine e Karma:

```bash
yarn remove @types/jasmine jasmine-core karma karma-chrome-launcher karma-coverage karma-jasmine karma-jasmine-html-reporter
```

> Verificar se existe alguma outra dependência relacionada aos testes Jasmine e Karma e remova-a também.

### Passo 2: Adicionar o Jest e Definições de Tipo

Adicione o Jest e suas definições de tipo ao projeto:

```bash 
yarn add jest @types/jest -D
```

### Passo 3: Atualizar tsconfig.spec.json

Atualize o trecho do arquivo tsconfig.spec.json para incluir as configurações do Jest:

```json
{
  "extends": "./tsconfig.json",
  "compilerOptions": {
    "outDir": "./out-tsc/spec",
    "types": [
      "jest"
    ]
  },
  "include": [
    "src/**/*.spec.ts",
    "src/**/*.d.ts"
  ]
}
```

### Passo 4: Atualizar angular.json

Atualize o arquivo `angular.json` para configurar o Jest como builder de testes:

```json
{
  "projects": {
    "my-app": {
      "architect": {
        "test": {
          "builder": "@angular-devkit/build-angular:jest",
          "options": {
            "tsConfig": "tsconfig.spec.json",
            "polyfills": ["zone.js", "zone.js/testing"]
          }
        }
      }
    }
  }
}
```

### Rodando os Testes

Execute os testes unitários com o comando:

```bash
ng test
```
