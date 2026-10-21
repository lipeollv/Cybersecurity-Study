_Tipos de BASH_
	*sh* - Bourne Shell
	*bash* - Bourne Again Shell
	*rbash* - Restricted Bash
	*dash* - Shell padrão do BSD
	*zsh* - (z-shell) Zero Shell
	*fish* - Friendly Interactive Shell

_Comandos Bash_
	`help` - Informa comandos "builtin".
	`type` - Informa sobre o tipo do comando e principalmente como ele seria interpretado se fosse executado.
	`echo` - Escreve argumentos na saída padrão (tela do terminal).
	[comando arquivo]; `echo $?` - Testa se no comando anterior, a execução dele foi bem sucedida ou não, usando $0$ (sem erros) ou $≠ 0$ (com erros).
	`declare -i` - Declara que a variável é do tipo inteiro.
	`declare -A` - Declara arrays associativas.
	`declare - p` - Exibe os atributos da variável
	`readonly` - Declara que uma variável não pode ser mudada (durante a execução do shell).
	`unset` - Remove uma variável.
	`variavel=$(comando)` - Atribuir a saida de um comando em uma variável.
	`read -p` `"mensagem"` `variável` = Um tipo de imput pro usuário.
______________________________
*Scripts*
	`#!/usr/bin/env bash` - Linha que indica quem vai enterpretar o script. (hashbang)

	para executar um script que você esteja na mesma pasta que ele =  
	./nomedoarquivo

______________________________
*Variáveis Especiais*
	`$$` - Armazena PID da sessão corrente do shell. 

______________________________
*Operadores Shell*
	`-eq` - Operador de comparação de dois números.
	 `&&` `(^ = e)`  - Executa um comando se o comando anterior não der erro.
	 `| |` `(v = ou)` - Executa um comando mesmo se o outro der erro.

