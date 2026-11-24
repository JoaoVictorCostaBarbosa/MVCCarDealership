# MVCCarDealership

Projeto Java desktop baseado no padrão Model-View-Controller (MVC), adaptado
para compilação com Maven e análise estática no SonarQube.

## Pré-requisitos

- JDK 17 ou mais recente (o código continua sendo compilado para Java 8)
- Uma instância do SonarQube acessível (por padrão,
  `http://localhost:9000`)

O Maven não precisa estar instalado globalmente: o Maven Wrapper incluído no
repositório baixa a versão necessária na primeira execução.

## Compilar e empacotar

No Linux/macOS:

```bash
./mvnw clean verify
```

No Windows:

```powershell
mvnw.cmd clean verify
```

O JAR executável será criado em
`target/mvc-car-dealership-1.0.0.jar`. Para abrir a aplicação:

```bash
java -jar target/mvc-car-dealership-1.0.0.jar
```

## Analisar com SonarQube Cloud pelo GitHub Actions

O workflow `.github/workflows/sonarqube.yml` compila o projeto com Maven e
envia a análise para o projeto
`JoaoVictorCostaBarbosa_MVCCarDealership`. Ele é executado em pushes para
`master`, em pull requests destinados a `master` e manualmente pela aba
**Actions** do GitHub.

Antes da primeira execução:

1. No SonarQube Cloud, acesse **Administration > Analysis Method** e desative
   **Automatic Analysis**. Para Java, deve ser usada a análise baseada em CI.
2. No GitHub, acesse **Settings > Secrets and variables > Actions** e crie um
   *Repository secret* chamado `SONAR_TOKEN`, usando o token gerado pelo
   SonarQube Cloud.

Para testar a mesma análise localmente:

```bash
SONAR_TOKEN=SEU_TOKEN ./mvnw clean verify sonar:sonar
```

Depois da execução, o log deve informar que os oito arquivos Java foram
indexados e analisados. O resultado fica disponível na interface do SonarQube
Cloud.

O código original permanece em `src/` para preservar o layout do projeto de
terceiros. O `pom.xml` configura esse diretório como fonte do Maven; os arquivos
antigos do NetBeans/Ant foram mantidos apenas como referência histórica.


