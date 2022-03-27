# Curso básico de programação em bash

## Qual shell estou usando?

```
echo $0
```

Cuidado, o comando acima mostra o nome do programa que está sendo executado. Não necessariamente um shell.

Podemos usar também:

```
echo $SHELL
```

## Alterando o bash padrão

### 1 - Usando usermod

usermod é um utilitário para modificar os detalhes da conta de um usuário, armazenado no arquivo /etc/passwd e a opção -s ou -shell é usada para alterar o Shell de login do usuário.

Neste exemplo, primeiro verificamos as informações da conta do usuário para ver seu Shell de login padrão.

```
grep leonardo /etc/passwd
```

Em seguida, altere seu shell de login, por exemplo, de /bin/bash para /bin/sh da seguinte maneira:

```
sudo usermod --shell /bin/bash leonardo
```

### 2 - chsh

chsh é um utilitário de linha de comando para alterar o Shell de um usuário. Você altera o Shell passando a opção -s ou –shell, depois informando o Shell que vai ser usado e o nome do usuário.


```
sudo chsh --shell /bin/sh leonardo
```

### Alterando diretamente o arquivo /etc/passwd

Neste método, basta abrir o arquivo /etc/passwd usando qualquer editor de texto e alterar o Shell do usuário que você queira.

```
sudo vim /etc/passwd
```

leonardo:x:1000:1000:leonardo,,,:home/leonardo:bin/bash

Quando tiver feito a edição, salve e feche o arquivo.

## comando type

Exibe informação sobre o tipo de comando.
    
Para cada NOME, indica como ele seria interpretado se fosse usado como um nome de comando.

Algumas saídas deste comando:

```
leonardo@leonardo-Aspire-A515-51G:~$ type ls
ls está apelidada para `ls --color=auto'
leonardo@leonardo-Aspire-A515-51G:~$ type script
script é /usr/bin/script
leonardo@leonardo-Aspire-A515-51G:~$ type cd
cd é um comando interno do shell
leonardo@leonardo-Aspire-A515-51G:~$ type apt
apt é /usr/bin/apt
leonardo@leonardo-Aspire-A515-51G:~$ type type
type é um comando interno do shell
leonardo@leonardo-Aspire-A515-51G:~$ type ls
ls está apelidada para `ls --color=auto'
leonardo@leonardo-Aspire-A515-51G:~$ type mkdir
mkdir é /usr/bin/mkdir
leonardo@leonardo-Aspire-A515-51G:~$ type sed
sed é /usr/bin/sed
leonardo@leonardo-Aspire-A515-51G:~$ echo $0
bash
```

