 # Isolamento

Em um cenário em que temos diversas conexões TCP/IP no banco de dados, e cada conexão executa uma ou mais transactions, existe uma chance de uma concorrência ocorrer para as operações de leitura e escrita na mesma região da memória. Então uma transaction pode ver a mudança feita por outras? 


