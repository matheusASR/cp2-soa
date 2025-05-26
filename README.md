# cp2-soa

## INTEGRANTES:
MATHEUS AUGUSTO SANTOS REGO RM551466
JOÃO PEDRO DE ALBUQUERQUE OLIVEIRA RM551579
PEDRO AUGUSTO CARNEIRO BARONE BOMFIM RM99781

## Estrutura do Projeto

```
Winery/
├── Publisher/
│   └── WinerySys/            # Projeto com os serviços SOAP
├── Consumer/
│   ├── WineStockClient/      # Cliente que consome o método getMenu()
│   └── WineOrderClient/      # Cliente que consome placeOrder() e sendWarn()
```

## Pré-requisitos

- Java 11 ou superior
- Maven 3.6+
- Git

## Como executar

### 1. Subir o serviço (Publisher)

```bash
cd Publisher/WinerySys
mvn clean package
java -cp target/WinerySys-1.0-SNAPSHOT.jar br.com.fiap.winery.Loader
```

Acesse no navegador:

- http://localhost:8085/WineStockService?wsdl
- http://localhost:8086/WineWarningService?wsdl

### 2. Gerar código dos clientes

Os clientes usam `jaxws-maven-plugin` para importar os WSDLs dos serviços. Certifique-se de que os serviços estejam rodando antes de executar o build dos clientes.

```bash
cd Consumer/WineStockClient
mvn clean package

cd ../WineOrderClient
mvn clean package
```

### 3. Executar os clientes

```bash
cd Consumer/WineStockClient
java -cp target/WineStockClient-1.0.jar br.com.fiap.winery.ApplicationClient1

cd ../WineOrderClient
java -cp target/WineOrderClient-1.0.jar br.com.fiap.winery.ApplicationClient2
```
