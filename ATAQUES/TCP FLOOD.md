- funciona como uma inundação de pacotes SYN para um servidor

normalmente uma conexão TCP funciona em HandShake. o usuário pede uma conexão com o servidor (SYN), o servidor retorna a resposta dizendo que a conexão pode ser estabelecida aguardando a solicitação do usuário (SYN/ACK), o usuário retorna a solicitação (ACK) e a conexão é estabelecida para a troca de dados.

no ataque, o invasor envia várias solicitações SYN (normalmente em vários dispositivos diferentes ou com vários IP's falsos), o servidor retorna as solicitações SYN/ACK, porém o servidor não tem a reposta do usuário e mantém a porta aberta até o limite de tempo. nesse tempo em que a porta está aberta, o servidor não pode estabelecer novas conexões nessa porta, fazendo assim o servidor ficar incapaz de receber novas conexões. 


. TIPOS DE ATAQUES .

 **_Ataque Direto:_** 
o ataque direto é quando um invasor usa somente o seu dispositivo, sem mascarar seu IP ou tentar esconder quem é. raramente usado, além de deixar rastros, é facilmente contido apenas bloqueando o IP com acesso ao servidor. porém poderia ser usado como uma "distração".

 **_Ataque Falsificado:_**
basicamente a mesma coisa que o ataque direto, porém dessa vez o invasor tenta esconder seu IP. porém ainda é possível rastrear através dos pacotes mandados para o servidor. um bom investigador consegue rastrear.

 ***Ataque Distribuído de Negação de Serviço (DDOS):***
um ataque mais sofisticado com botnet, tornando quase impossível de rastrear a origem do ataque. o invasor também pode usar ferramentas para cada bot esconder ou usar um IP mascarado.

. TIPOS DE DEFESAS .

 **_Aumentar a fila de registros acumulados:_**
claro que existem limitações, porém um método óbvio seria aumentar quanto o servidor pode colocar na fila de tentativas de conexões. mas se caso aumentando ele acaba sobrecarregando a memória do servidor, o desempenho cai.

 **_Reciclar a conexão TCP entreaberta mais antiga:_**
uma outra estratégia seria o servidor identificar mais rápido que o limite de registros chegue o que seria uma tentativa de conexão verdadeira ou falsa. porém não é eficiente caso o volume do ataque seja maior que a fila.

 **_Cookies SYN:_**
um servidor inteligente, recebe as solicitações SYN e devolve o SYN/ACK, porém logo depois de enviar o SYN/ACK, excluí a solicitação do SYN da memória para liberar espaço, deixando a porta aberta para receber mais tentativas de acesso. se ele recebe o ACK daquele endereço, ele reconstrói o SYN (não totalmente preciso) para estabelecer uma conexão.
