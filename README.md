# websocket-php
This library doesn't weigh much.<br>
Echo server<br>
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
client js<br>
```javascript
function addserverphp(){//the function that starts the server and if it is running it does nothing
	const xhr = new XMLHttpRequest();
	xhr.open("GET", "/serverphp/serverstart.php");//here we specify the file to the php server
	xhr.send();	
}
addserverphp();
const socket = new WebSocket("ws://localhost:8000");//connect websocket
socket.addEventListener("message", (event) => {//send msg
  console.log("Message from server ", event.data);
});
```
