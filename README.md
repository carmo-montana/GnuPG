# Instalação
## Windows:

### Baixe o Gpg4win no site oficial: `gpg4win.org`.

### Siga as instruções do instalador.

## Linux:

- No terminal, execute:

```bash
sudo apt install gnupg
```
#

## MacOS:

- Se você tiver o Homebrew instalado, execute:

```bash
brew install gnupg
```
#

## Obtendo Ajuda
- Para ver uma lista de comandos disponíveis e suas opções, use:

```bash
gpg --help
```
#

## Criptografia Simétrica
- A criptografia simétrica usa a mesma senha para criptografar e descriptografar um arquivo.

- Criptografar um arquivo:

```bash
gpg -c segredo.txt
```
- Isso cria um arquivo criptografado segredo.txt.gpg (binário).

- Especificando um algoritmo de criptografia e um arquivo de saída:

```bash
gpg -c --cipher-algo blowfish -o my_secret.txt.gpg segredo.txt

"--cipher-algo blowfish": # Especifica o algoritmo de criptografia.

"-o my_secret.txt.gpg": # Define o nome do arquivo de saída.
```
- Criando um arquivo criptografado em formato ASCII:

```bash
gpg --armor -c segredo.txt
```
Isso cria segredo.txt.asc, que é um arquivo de texto ASCII.

#

## Descriptografia Simétrica
- Para descriptografar um arquivo criptografado simetricamente:

```bash
gpg -o segredo.txt -d segredo.txt.gpg

"-o segredo.txt": # Define o nome do arquivo de saída descriptografado.

"-d segredo.txt.gpg": # Descriptografa o arquivo.
```
#

## Gerenciamento de Chaves
- Gerando um par de chaves:

```bash
gpg --gen-key
```
- Siga as instruções para criar uma chave pública e privada.

- Listando chaves públicas:

```bash
`gpg --list-keys`
```
- Listando chaves secretas:

```bash
`gpg --list-secret-keys`
```
- Exportando uma chave privada:

```bash
gpg --export-secret-keys --armor B211B48E > private_key.asc

"B211B48E": # Substitua pelo ID da sua chave.

"private_key.asc": # Arquivo de texto contendo a chave privada.
```
- Exportando uma chave pública:

```bash
gpg --export --armor B211B48E > public_key.asc
```
- Excluindo uma chave secreta:

```bash
gpg --delete-secret-keys B211B48E
```
- Excluindo uma chave pública:

```bash
gpg --delete-keys B211B48E
```
- Importando uma chave privada ou pública:

```bash
gpg --import private.asc
gpg --import public.asc
```
- Importando uma chave pública de um servidor de chaves:

```bash
gpg --keyserver pgp.mit.edu --recv 8483C65D
```
- Publicando uma chave pública em um servidor de chaves:

```bash
gpg --keyserver hkp://pgp.mit.edu --send-keys 30E6A0BE
```
- Procurando por uma chave em um servidor de chaves:

```bash
gpg --keyserver pgp.mit.edu --search-keys nome@email.com
```
#

## Criptografia Assimétrica (Chave Pública)
- Criptografar um arquivo usando a chave pública de alguém:

```bash
gpg --encrypt --recipient 95FC2D9E80DB23C0 mensagem.txt

"95FC2D9E80DB23C0": # Substitua pelo ID da chave pública do destinatário.
# Isso cria um arquivo binário criptografado mensagem.txt.gpg.
```
- Criptografar em formato ASCII:

```bash
gpg --encrypt --recipient 95FC2D9E80DB23C0 --armor mensagem.txt
# Isso cria mensagem.txt.asc.
```
- Descriptografar um arquivo criptografado:

```bash
gpg --decrypt -o arquivo.txt mensagem.txt.asc
# Você precisa ter a chave privada correspondente.
```
#

## Assinatura Digital
- Assinar um arquivo com uma assinatura embutida:

```bash
gpg --clear-sign arquivo.txt
# Isso cria arquivo.txt.asc, que contém o texto original e a assinatura.
```
- Assinar um arquivo com uma assinatura binária:

```bash
gpg --sign arquivo.txt
# Isso cria arquivo.txt.gpg.
```
- Criar uma assinatura desanexada (binária):

```bash
gpg --detach-sig --output mensagem.sig mensagem.txt
# Isso cria mensagem.sig, que contém apenas a assinatura.
```
- Criar uma assinatura desanexada (ASCII):

```bash
gpg --detach-sig --armor --output mensagem.sig mensagem.txt
# Isso cria mensagem.sig.asc.
```
- Verificar uma assinatura:

```bash
gpg --verify mensagem.sig mensagem.txt
# Você precisa da chave pública de quem assinou.
```
- Verificar e extrair o documento original:

```bash
gpg --output arquivo.txt --decrypt mensagem.txt.asc
```
#

## Criptografar e Assinar um Arquivo
- Para criptografar e assinar um arquivo:

```bash
gpg --encrypt --recipient PUBLIC_KEY_ID --sign mensagem.txt
"PUBLIC_KEY_ID": # Substitua pelo ID da chave pública do destinatário.

# Isso cria um arquivo criptografado e assinado.
```
#

## Próximos Passos
- Prática: Tente criptografar e descriptografar arquivos simples.

- Gerenciamento de Chaves: Crie e gerencie suas chaves públicas e privadas.

- Assinaturas: Pratique assinar e verificar assinaturas de arquivos.

- Integração: Use GPG em scripts ou integre-o com outras ferramentas.


