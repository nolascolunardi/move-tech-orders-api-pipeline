# move-tech-orders-api-pipeline

Repositório starter para o **Lab H3 · Ligar a esteira CI/CD** do curso Move Tech (Magalu × Prósper Digital Skills).

## O que tem aqui

| Arquivo / Pasta | O que é |
|----------------|---------|
| `app/main.py` | API de Pedidos em FastAPI (in-memory) |
| `Dockerfile` | Empacota a API em uma imagem Docker |
| `docker-compose.yml` | Sobe a aplicação localmente |
| `tests/test_main.py` | Testes automatizados com pytest |
| `k8s/app.yaml` | Manifesto Kubernetes (usa `$IMAGE` como placeholder) |
| `pyproject.toml` | Dependências gerenciadas com Poetry |

## O que você vai adicionar

No lab, você vai criar:

- `.github/workflows/deploy.yml` — pipeline CI/CD que testa, empacota e faz deploy automaticamente

## Endpoints da API

| Método | Rota | Descrição |
|--------|------|-----------|
| GET | `/health` | Status da aplicação |
| POST | `/orders` | Criar pedido |
| GET | `/orders` | Listar pedidos |
| GET | `/orders/{id}` | Buscar pedido |
| DELETE | `/orders/{id}` | Cancelar pedido |
| POST | `/orders/{id}/items` | Adicionar item |
| GET | `/orders/{id}/items` | Listar itens |

Documentação interativa disponível em `http://localhost:8000/docs` após subir o container.

## Testar localmente

```bash
# Com Docker
docker compose up --build

# Sem Docker (requer Poetry)
poetry install
poetry run uvicorn app.main:app --reload --port 8000

# Rodar testes
poetry run pytest
```

## Secrets necessários no GitHub

Configure os seguintes secrets em **Settings → Secrets and variables → Actions** do seu repositório:

| Secret | Descrição |
|--------|-----------|
| `MGC_REGISTRY_USER` | Usuário do Container Registry da Magalu Cloud |
| `MGC_REGISTRY_PASSWORD` | Senha do Container Registry |
| `MGC_REGISTRY_NAME` | Nome do seu registry (ex: `meu-registry`) |
| `MGC_KUBECONFIG` | Conteúdo do kubeconfig do cluster K3s |

## Próximo passo

Após concluir este lab, avance para o **Lab H4 · Persistência com banco de dados** onde a API será conectada a um banco PostgreSQL.
