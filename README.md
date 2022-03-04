# Configurando o terminal para seu ambiente de desenvolvimento 

### ⚙️ Uma dica se você utiliza windows, é instalar o WSL2, segue abaixo um tutorial detalhado de como fazer isso:
https://www.youtube.com/playlist?list=PLlAbYrWSYTiOpefWtd6uvwgKT1R-94Zfd

#
# Instalando Zsh

Antes de conseguirmos iniciar com qualquer configuração precisamos instalar o Zsh.

```
sudo apt install zsh
```
Com o Zsh instalado deve ser possível você executar:
```
zsh --version 
```
E receber algo como: *zsh 5.0.8 ou mais recente*

# Instalando Oh My Zsh

Para instalar o Oh My Zsh você precisa executar o comando abaixo (você deve ter o cURL instalado para executa-lo):

```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

A partir de agora todas configurações que você quer fazer como adicionar variáveis ambientes ou configurar seu terminal de qualquer forma utilize o arquivo **~/.zshrc** e não mais o **~/.bash_profile** ou derivados.

Agora reiniciando seu terminal você deve ter algo diferente do convencional, parecido com isso:

![alt text](https://ohmyz.sh/img/themes/nebirhos.jpg)

# Instalando Temas (opicional)
Agora vamos instalar um tema que vai modificar um pouco as informações que são exibidas no terminal. Para isso precisamos seguir os passos abaixo

Dentro do arquivo ~/.zshrc vamos alterar a variável ZSH_THEME ficando dessa forma:
1. Abrir o arquivo de configuração: 
```
code ~/.zshrc
```
2. Alterar a variavel do tema:
```
ZSH_THEME="avit"
```
3. Reiniciar o arquivo de configuração
```
source ~/.zshrc
```

![alt text](https://user-images.githubusercontent.com/49100982/108254755-79df0e00-716c-11eb-9069-da947bd4a3dc.jpg)

#### Existem vários outros temas e podem ser visto no link abaixo: 
https://github.com/ohmyzsh/ohmyzsh/wiki/Themes


# Instalando Plugins do ZSH
Para instalar plugins precisamos configurar o ZInit, ferramenta que facilita a instalação e remoção de plugins no Zsh.

```
sh -c "$(curl -fsSL https://git.io/zinit-install)"
```

1. Abrir o arquivo de configuração: 
```
code ~/.zshrc
```

2. Abaixo da linha **### End of ZInit's installer chunk** que foi adicionada automaticamente no arquivo, adicionamos:
```
zinit light zdharma/fast-syntax-highlighting
zinit light zsh-users/zsh-autosuggestions
zinit light zsh-users/zsh-completions
```

- **zdharma/fast-syntax-highlighting**: Adiciona syntax highlighting na hora da escrita de comandos que facilita principalmente em reconhecer comandos que foram digitados de forma incorreta;
- **zsh-users/zsh-autosuggestions**: Sugere comandos baseados no histórico de execução conforme você vai digitando;
- **zsh-users/zsh-completions**: Adiciona milhares de completitions para ferramentas comuns como Yarn, Homebrew, NVM, Node, etc, para você precisar apenas apertar TAB para completar comandos;

3. Reiniciar o arquivo de configuração
```
source ~/.zshrc
```

ou reiniciar o terminal.

# Criando chaves ssh
1. Abrir o terminal
2. Cole o texto abaixo, substituindo em seu endereço de e-mail.
```
ssh-keygen -t ed25519 -C "your_email@example.com"
```
3. Adicionar a chave ao agent
- Abrir o arquivo de configuração
```
code ~/.zshrc
```
- Adicionar 'ssh-agent' aos plugins
```
plugins=(git ssh-agent ...)
```
-Reiniciar o arquivo de configuração
```
source ~/.zshrc
```
4 - Copiar a chave ssh
```
cd .ssh
ls -ls
more id_rsa.pub
```

# Criando um Alias
Criação de alis [e interessante para nos ajudar e facilitar acessar pastas e arquivos.
Dentro do arquivo ~/.zshrc vamos buscar pela palavra **alias** e adicionar novos abaixo dos ja existentes, ficando dessa forma:
1. Abrir o arquivo de configuração: 
```
code ~/.zshrc
```
2. Adicionar novos alias:
```
alias zshconfig="code ~/.zshrc"
alias gitconfig="code ~/.gitconfig"
```
3. Reiniciar o arquivo de configuração
```
source ~/.zshrc
```

# Configurando o NVM e instalando o NodeJS
Com o zsh configurado, já existe um pligin que vai facilitar a configuração do NVM

- Clone este repositório em algum lugar (por exemplo) ~/.zsh-nvm
```
git clone https://github.com/lukechilds/zsh-nvm.git ~/.zsh-nvm
```
- Ativar o plugin
```
source ~/.zsh-nvm/zsh-nvm.plugin.zsh
```
- Para não ficar pedindo ativação toda vez que abrir o terminal, 
1. Abrir o arquivo de configuração: 
```
code ~/.zshrc
```
2. Na última linha cole o seguinte código
```
source ~/.zsh-nvm/zsh-nvm.plugin.zsh
```
3. Reiniciar o arquivo de configuração
```
source ~/.zshrc
```

Para mais detalhes de como usar o NVM, segue um tutorial:
https://www.treinaweb.com.br/blog/instalando-e-gerenciando-varias-versoes-do-node-js-com-nvm




    
