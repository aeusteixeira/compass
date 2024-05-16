![Logo](https://i.postimg.cc/TYyLZP0m/Compass-1.jpg)

## Compass

O script `compass` é uma ferramenta de linha de comando projetada para simplificar a interação com projetos Docker Compose, especialmente focado em projetos Laravel. Ele fornece uma interface conveniente para executar comandos comuns de desenvolvimento e manutenção diretamente através de um único ponto de entrada.

## Por que criei se existe o Sail?

O Compasso nasceu da minha experiência em um projeto Laravel que utilizava Docker, mas onde o Sail não era uma opção viável. A constante necessidade de acessar o shell do Docker para executar comandos básicos me motivou a criar uma ferramenta mais ágil e eficiente.

O Compasso oferece uma interface de linha de comando simplificada, permitindo executar comandos Artisan, rodar testes, gerenciar serviços e muito mais, tudo sem a necessidade de entrar no container.

Se você também já se sentiu frustrado com a complexidade de gerenciar um ambiente Laravel com Docker sem o Sail, o Compasso pode ser a solução que você procurava!

## Requisitos

- Docker e Docker Compose instalados.
- Projeto configurado para usar Docker Compose.

## Instalação

1. **Clone o repositório:**

   ```bash
   git clone https://github.com/aeusteixeira/compass.git compass
   ```

   Certifique-se de executar este comando na **raiz do seu projeto Laravel**. O repositório será clonado em uma pasta chamada `compass`.

2. **Dê permissão de execução ao script:**

   ```bash
   chmod +x compass/compass
   ```

3. **(Opcional) Crie um alias:**

   Para facilitar o uso, você pode criar um alias para o script:

   ```bash
   alias compass='./compass/compass'  # Alias temporário (Bash/Zsh)
   ```

   Para tornar o alias permanente, adicione a linha acima ao seu arquivo de configuração do shell (`~/.bashrc`, `~/.zshrc`, etc.).

4. **Configuração:**

   - **IMPORTANTE:** Abra o arquivo `compass/compass` e verifique se o nome do serviço PHP definido na variável `SERVICE_NAME` corresponde ao nome do serviço no seu arquivo `docker-compose.yml`. Por padrão, o valor é "app", mas pode ser diferente no seu projeto.

   ```bash
   # Nome do serviço PHP definido no docker-compose.yml
   SERVICE_NAME="app"  # Adapte este valor se necessário
   ```

## Uso

Para executar um comando com o `compass`, navegue até a raiz do seu projeto e execute:

```bash
./compass/compass [comando]
```

Substitua `[comando]` pelo comando desejado listado abaixo.

## Comandos Disponíveis

### Docker

- `up` - Inicia todos os serviços em modo detached.
- `down` - Para e remove todos os containers e redes.
- `restart` - Reinicia todos os serviços.
- `build` - Reconstrói as imagens dos serviços.
- `logs` - Exibe os logs dos serviços.
- `pause` - Pausa todos os serviços.
- `unpause` - Retoma os serviços pausados.
- `ps` - Lista os containers.
- `images` - Lista as imagens do Docker.
- `exec <serviço> <comando>` - Executa um comando no container.
- `down --volumes` - Para os serviços e remove volumes.
- `prune` - Remove containers, redes, volumes e imagens não utilizados.

### Laravel

- `artisan` - Executa um comando Artisan.
- `tinker` - Abre o Tinker.
- `routes` - Exibe as rotas do Laravel.
- `test` - Executa os testes.
- `test --filter <nome>` - Executa um teste específico.
- `test-all` - Executa os testes em todas as branches.
- `migrate` - Executa as migrations.
- `db:seed` - Executa os seeders.
- `queue:work` - Inicia o worker da fila.
- `queue:listen` - Inicia o listener da fila.
- `schedule:run` - Executa as tarefas agendadas.
- `storage:link` - Cria um link simbólico para storage/app/public.

### Laravel - Criação

- `make <nome>` - Cria um modelo, migration, controller, factory e testes.
- `make:controller <nome>` - Cria um controlador.
- `make:model <nome>` - Cria um modelo.
- `make:command <nome>` - Cria um comando.
- `make:migration <nome>` - Cria uma migração.
- `make:middleware <nome>` - Cria um middleware.
- `make:seeder <nome>` - Cria um seeder.
- `make:factory <nome>` - Cria uma factory.
- `make:policy <nome>` - Cria uma policy.
- `make:resource <nome>` - Cria um resource.
- `make:observer <nome>` - Cria um observer.
- `make:request <nome>` - Cria um request.
- `make:job <nome>` - Cria um job.
- `make:event <nome>` - Cria um event.
- `make:listener <nome>` - Cria um listener.
- `make:channel <nome>` - Cria um channel.
- `make:mail <nome>` - Cria um mail.
- `make:notification <nome>` - Cria uma notification.

### Gerenciamento de Projeto

- `install` - Instala as dependências do projeto.
- `update` - Atualiza as dependências do Composer e npm.
- `optimize` - Otimiza o desempenho do aplicativo.
- `fresh` - Redefine o banco de dados.
- `analyze` - Executa análise estática de código (Larastan).
- `format` - Formata o código automaticamente (Pint).

### Outros

- `shell` - Abre um shell interativo no container.
- `php <comando>` - Executa um comando PHP.
- `composer <comando>` - Executa um comando Composer.
- `npm <comando>` - Executa um comando npm.

## Configurando Alias

Para tornar o uso do `compass` ainda mais conveniente, você pode configurar um alias em seu shell. Isso permite que você execute o `compass` de qualquer lugar no seu terminal, sem precisar navegar até a pasta do script ou digitar o caminho completo.

### Alias Temporário

Um alias temporário só dura até o final da sessão do terminal atual. Para configurar um alias temporário para o `compass`, execute:

```bash
alias compass='./compass/compass'
```

### Alias Permanente

Para criar um alias que persiste entre as sessões do terminal, você precisará adicionar o comando de alias ao arquivo de configuração do seu shell, como `~/.bashrc` ou `~/.zshrc`, dependendo do shell que você usa.

1. Abra o arquivo de configuração do shell em um editor de texto. Por exemplo, para Bash:

```bash
nano ~/.bashrc
```

Ou para Zsh:

```bash
nano ~/.zshrc
```

2. Adicione a linha de alias ao final do arquivo:

```bash
alias compass='./compass/compass'
```

3. Salve e feche o arquivo. Para que as alterações tenham efeito, você pode recarregar o arquivo de configuração ou abrir um novo terminal. Para recarregar, use:

Para Bash:

```bash
source ~/.bashrc
```

Para Zsh:

```bash
source ~/.zshrc
```

Agora, você pode simplesmente digitar `compass` seguido pelo comando desejado em qualquer lugar no seu terminal para executar os comandos do script `compass`.

## Customização

O script pode ser customizado para incluir novos comandos conforme necessário. Edite o script e adicione novos casos no switch-case para suportar suas operações específicas.
