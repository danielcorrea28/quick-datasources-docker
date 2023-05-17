# Example how to get Ngrok host and port to make connections.

```console
appsmith@ngrok:~$ ngrok tcp 3306
Session Status   
online                                                                                   
Account                       Appsmith-svg (Plan: Free)                                                                  
Version                       3.1.0                                                                                     
Region                        Europe (eu)                                                                               
Latency                       164ms                                                                                    
Web Interface                 http://127.0.0.1:4040                                                                     
Forwarding                    tcp://0.tcp.eu.ngrok.io:16696 -> localhost:3306 
Connections                  
ttl     opn     rt1     rt5     p50     p90                                                                            
0       0       0.00    0.00    0.00    0.00                                                                                 
```

- For example, the host and the port to make that connection would be.

`host: 0.tcp.eu.ngrok.io`

`port: 16696`