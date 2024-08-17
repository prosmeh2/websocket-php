# websocket-php
This library doesn't weigh much.<br>
```php
<?php
//setting unlimited time for uninterrupted script operation
set_time_limit(0);
//connecting the library
include "websocket.php";
//creating a web socket with port 8000
$server =new WebSocketServer("127.0.0.1",8000);
//we create a function when a message is received and send messages to all sockets
$server->handler = function($self,$connect, $data) {
  //$self->connects this is an array with all sockets
	foreach ($self->connects as $vv){
      //sending a message to a socket
		   WebSocketServer::response($vv, $data);
	}

};
//creating the start function, it is called when the server starts successfully
$server->startServerevent= function($self){

};
//startserver
$server->startServer();
//if something goes wrong, messages are written
echo "yestserver"
?>
```
