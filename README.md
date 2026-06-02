# Desafio Técnico Sensedia — Analista de Suporte a Infraestrutura Jr

## Objetivo
Disponibilizar a aplicação httpbin em ambiente local utilizando Docker
e validar seu funcionamento através de requisições HTTP.

## Tecnologias utilizadas
- Docker
- Git
- curl

## Processo

### 1. Subindo a aplicação
```bash
docker run -d -p 8080:80 kennethreitz/httpbin
```

### 2. Verificando o container
```bash
docker ps
```
![docker run](assets/docker-run-funcionando.png)

### Execução do httpbin

![docker run](assets/exec_httbin.png)

## Testes realizados

### Teste 1 — GET simples
```bash
curl http://localhost:8080/get
```
![teste get ](assets/request-get.png)

### Teste 2 — POST com dados
```bash
curl -X POST http://localhost:8080/post \
  -H "Content-Type: application/json" \
  -d '{"nome": "Eduardo", "vaga": "Sensedia"}'
```
![teste post](assets/Teste_postComDados.png)

### Teste 3 — Verificar status HTTP
```bash
curl -i http://localhost:8080/status/200
```
![teste status](assets/verificar_statusHTTP.png)

### Teste 4 — Ver headers da requisição
```bash
curl http://localhost:8080/headers
```
![teste headers](assets/request-verificacaoHeaders.png)

## Dificuldades encontradas

### Porta 80 com permissão negada
Ao tentar subir o container mapeando a porta 80, o sistema retornou erro de permissão por ser uma porta privilegiada no Linux:

![Error de permissão na Porta 80](assets/docker-run-error.png)

**Solução:** utilizei a porta 8080 no lugar da 80, mapeando 
corretamente com `-p 8080:80`:

```bash
docker run -d -p 8080:80 kennethreitz/httpbin
```

A aplicação ficou acessível normalmente em `http://localhost:8080`.

## Como reproduzir

### Usando docker run
```bash
docker run -d -p 8080:80 kennethreitz/httpbin
```

### Usando docker-compose
```bash
docker-compose up -d
```

Acesse em: http://localhost:8080