
```mermaid
sequenceDiagram
 participant Attacker
 participant BotNet
 participant WebServer
 participant Firewall
 participant IT Team

Attacker->>BotNet: BOTS ASSEMBLE!!!
activate BotNet
BotNet-->>Attacker: here boss
loop every second
 Attacker->>BotNet: Send syn packets to Webserver
end
BotNet-->Attacker: sending syn packets
create WebServer
create Firewall
Note right of Firewall: Influx of irregular IP addresses noticed on IDS.<br/>This would be the start of detection.
critical Maintain established connection with WebServer
 Firewall-->Webserver: connect
 Firewall-->Webserver: verified packets
end
BotNet--xFirewall: packets being sent
note left of Firewall: system is blocking first batch<br/>of IP's being sent to server.
note right of BotNet: Changes IP addresses and keeps trying
BotNet-->Firewall: packets being sent
note right of Firewall: System can not handle the flood of<br/>incoming requests from the Botnet attack.
WebServer->Firewall: I can't handle all this incoming traffic!
create IT Team
Firewall-> IT Team: There has been an issue detected on the network.<br/>IDS has detected a possible breach.
note right of IT Team: IT Team is looking in to the event.<br/>The team had to employ their disaster recovery plan<br/>and has updated protocols to learn from this event.


```