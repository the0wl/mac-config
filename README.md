<h1>mac-config</h1>
Configurações para o ambiente de desenvolvimento no OSX.

</br>

## Sumário

</br>

- [Sumário](#sumário)
- [Usuário](#usuário)
- [Terminal](#terminal)
  - [Fish](#fish)
  - [starship](#starship)
  - [Nerd Font](#nerd-font)

</br>

## Usuário

Crie um usuário a parte caso o computador esteja sendo compartilhado. Isso irá facilitar a instalação de aplicativos sem sobrepor ou apagar configurações de outro usuário.

Configure o usuário com o `username` igual a `kelvin`.

</br>

## Terminal

Instale o Homebrew.

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

Descubra onde o Homebrew foi instalado.

```bash
which brew
```

Utilize o caminho do passo anterior e adicione a seguinte linha ao arquivo `.zshrc`.

```bash
# Supondo que o caminho seja '/opt/homebrew/bin'

export PATH="/opt/homebrew/bin:$PATH"
```

Atualize o seu terminal.

```bash
source ~/.zshrc
```

<br/>

### Fish 

```bash
brew install fish
```

Descubra onde o Fish foi instalado.

```bash
which fish
```

Adicione o caminho retornado ao fim do arquivo em `/etc/shells`.

```bash
nano /etc/shells
```

Altere o terminal padrão para o terminal Fish.

```bash
# Utilize o mesmo endereço que você configurou no passo anterior

sudo chsh -s /opt/homebrew/bin/fish kelvin
```

Configure o terminal Fish.

```bash
nano ~/.config/fish/config.fish
```

Adicione o seguinte comando ao arquivo.

```bash
set -x PATH /opt/homebrew/bin $PATH
```

```
source ~/.config/fish/config.fish
```

</br>

### starship

Fornece um prompt altamente personalizável com suporte a ícones e informações contextuais. No momento não estou utilizando todos os recursos, porém foi mais fácil de chegar no estado que eu queria.

```bash
brew install starship
```

Edite o arquivo de configuração do Fish.

```
source ~/.config/fish/config.fish
```

```bash
set -gx GIT_EDITOR "code --wait"
set -gx STARSHIP_CONFIG ~/.config/starship.toml

# Este deve ser o último comando listado no arquivo
starship init fish | source
```

Edite também o arquivo de configurações do starship.

```
nano ~/.config/starship.toml
```

```toml
"$schema" = 'https://starship.rs/config-schema.json'

add_newline = true

[character]
success_symbol = '[↪](green)'

# Disable the package module, hiding it from the prompt completely
[package]
disabled = true
```

</br>

### Nerd Font

Instale uma Nerd Font como por exemplo a FiraCode. Isso irá permitir ao *starship* exibir todos ícones apropriadamente, sem que ocorra a exibição do caractere �.
