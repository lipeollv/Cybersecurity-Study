- funciona como uma inundação de pacotes SYN para um servidor

normalmente uma conexão TCP funciona em HandShake. o usuário pede uma conexão com o servidor (SYN), o servidor retorna a resposta dizendo que a conexão pode ser estabelecida aguardando a solicitação do usuário (SYN/ACK), o usuário retorna a solicitação (ACK) e a conexão é estabelecida para a troca de dados.

no ataque, o invasor envia várias solicitações SYN (normalmente em vários dispositivos diferentes ou com vários IP's falsos), o servidor retorna as solicitações SYN/ACK, porém o servidor não tem a reposta do usuário e mantém a porta aberta até o limite de tempo. nesse tempo em que a porta está aberta, o servidor não pode estabelecer novas conexões nessa porta, fazendo assim o servidor ficar incapaz de receber novas conexões. 


. TIPOS DE ATAQUES .

**ataque direto:** 
o ataque direto é quando um invasor usa somente o seu dispositivo, sem mascarar seu IP ou tentar esconder quem é. raramente usado, além de deixar rastros, é facilmente contido apenas bloqueando o IP com acesso ao servidor. porém poderia ser usado como uma "distração".

