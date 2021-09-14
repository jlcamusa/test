Integrantes: José Luis Camus y José Luis Camus, nadie mas en realidad

"Procesamiento de input"
El input es adquirido por la funcion getcmd() la cual guarda el input en buf, posteriormente buf es colocado como parametro en la funcion parsecmd la cual parsea el comando (lo va dividiendo en las distintas instrucciones que lo componen) y coloca las instrucciones pertinentes al interior del struct cmd, separandolo las instrucciones por pipes, listas, etc..

Por ultimo se entrega cmd a la funcion runcmd la cual ve el caso a caso de cada instruccion y se encarga de ejecutarlas.

"Redirección de entrada y salida"

Al realizar el parseo se ve si la instruccion ingresada corresponde a una redireccion de entrada, o de salida o ambas, dependiendo de esto cambiaran las instrucciones pertinentes antes de ingresar a la funcion runcmd 

"Pipes"

Para el caso de los pipes al pasar a la funcion runcmd se hace un fork al momento de abrir los extremos de entrada y salida, luego se escribe y se lee la informacion correspondiente y por ultimo se cierran respectivamente ambos extremos del pipe despues de haber ingresado o recibido la informacion.

Cuando las instrucciones obtenidas por getcmd pasan por la funcion parsecmd, la funcion peek ve si existe la presencia del simbolo "|" al momento de parsear por pipes, en casode existir se agregan a cmd las instrucciones pertinentes  
