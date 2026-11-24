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

## Analisar com SonarQube

Inicie o SonarQube e execute:

```bash
./mvnw clean verify sonar:sonar \
  -Dsonar.host.url=http://localhost:9000 \
  -Dsonar.token=SEU_TOKEN
```

O projeto será publicado no SonarQube com a chave
`MVCCarDealership`. Tanto a URL quanto a chave podem ser sobrescritas na linha
de comando, por exemplo com `-Dsonar.projectKey=outra-chave`.

O código original permanece em `src/` para preservar o layout do projeto de
terceiros. O `pom.xml` configura esse diretório como fonte do Maven; os arquivos
antigos do NetBeans/Ant foram mantidos apenas como referência histórica.


