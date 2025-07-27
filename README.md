# Docker Plex

Um projeto Docker simples para executar o Plex Media Server usando Docker Compose.

## 📋 Descrição

Este projeto fornece uma configuração Docker Compose para executar o Plex Media Server de forma rápida e fácil. O Plex é um servidor de mídia que permite organizar e transmitir seus arquivos de mídia (filmes, séries, músicas, fotos) para qualquer dispositivo.

## 🚀 Pré-requisitos

- Docker
- Docker Compose
- Acesso root ou permissões sudo

## 📁 Estrutura do Projeto

```
docker-plex/
├── docker-compose.yml    # Configuração do Docker Compose
├── config/              # Diretório de configuração do Plex (criado automaticamente)
└── README.md           # Este arquivo
```

## ⚙️ Configuração

### 1. Clone o repositório

```bash
git clone <url-do-repositorio>
cd docker-plex
```

### 2. Ajuste as configurações (opcional)

Edite o arquivo `docker-compose.yml` para personalizar:

- **PUID/PGID**: IDs do usuário e grupo (padrão: 1000/1000)
- **Volumes**: Caminhos para seus arquivos de mídia
- **Porta**: O Plex usa a porta 32400 por padrão

### 3. Execute o container

```bash
docker-compose up -d
```

## 🔧 Configurações Importantes

### Volumes
- `/:/media` - Seus arquivos de mídia (ajuste conforme necessário)
- `./config:/config` - Configurações do Plex
- `/tmp:/transcode` - Diretório temporário para transcodificação

### Variáveis de Ambiente
- `PUID=1000` - ID do usuário
- `PGID=1000` - ID do grupo
- `VERSION=docker` - Versão do Plex

## 🌐 Acesso

Após iniciar o container, acesse o Plex através do navegador:

- **URL**: `http://localhost:32400/web`
- **Primeira execução**: Siga o assistente de configuração

## 📝 Comandos Úteis

```bash
# Iniciar o container
docker-compose up -d

# Parar o container
docker-compose down

# Ver logs
docker-compose logs -f plex

# Reiniciar o container
docker-compose restart plex

# Atualizar a imagem
docker-compose pull
docker-compose up -d
```

## 🔒 Segurança

- O container roda em modo `host` para melhor performance
- Certifique-se de que as permissões dos arquivos estão corretas
- Considere usar um proxy reverso para acesso externo

## 📊 Monitoramento

Para verificar o status do container:

```bash
docker-compose ps
```

## 🛠️ Solução de Problemas

### Problema: Permissões de arquivo
```bash
# Ajuste as permissões dos arquivos de mídia
sudo chown -R 1000:1000 /caminho/para/sua/midia
```

### Problema: Container não inicia
```bash
# Verifique os logs
docker-compose logs plex

# Verifique se a porta 32400 está livre
netstat -tulpn | grep 32400
```

## 📄 Licença

Este projeto está licenciado sob a Licença MIT - veja o arquivo [LICENSE](LICENSE) para detalhes.

## 👨‍💻 Autor

**Simei Thander** - 2025

## 🤝 Contribuições

Contribuições são bem-vindas! Sinta-se à vontade para abrir issues ou pull requests.

## ⚠️ Disclaimer

Este projeto é fornecido "como está", sem garantias. Use por sua conta e risco. 
