*Arquivo de dispositivo*
     é um objeto do sistema que oferece uma interface para o dispositivo (hardware/driver)
     o Kernel sempre associa os drivers de dispositivos aos arquivos de dispositivos
*Descritores de arquivos*
     Abstração para localizar/acessar um arquivo
     
      Entrada Padrão 0 (stdin) - Fluxo para entrada de texto (teclado)
      Saída Padrão 1 (stdout) - Fluxo para saída normal dos programas (terminal)
	  Erro Padrão 2 (stderr) - Fluxo para saída de texto, para mensagens de erros       (terminal) 
______________________________
*Pipe*
     |  - permite juntar dois ou mais comandos

*Redirecionamentos*
     > - operador de redirecionamento (cria um arquivo)
     >> - operador para anexar em um arquivo já existente
     < - recebe algo

*Comando tee*
	- Permite enviar a saída de um comando para um arquivo e para tela ao mesmo tempo.

	tee [opções] arquivos
	-a Anexa os arquivos, em vez de sobreescreve-los -