## Configuración de puerto serial para routers
enable
configure terminal
interface serial0/0/0
ip address 10.0.0.2 255.255.255.252
no shutdown

## Configuración de puertos etherchanel
```
enable
configure terminal
interface range fa0/<X>-<Y>
switchport mode trunk
switchport trunk native vlan <Z>
exit
interface range fastethernet 0/<X>-<Y>
channel-group <A> mode active //estandar abierto
do show ether
``` 

## Aplicar Rapid-PVST
```
enable
configure terminal
spanning-tree mode rapid-pvst
show spanning-tree summary
```

## configurar VTP


### configurar el switch principal
```
vtp mode server
vtp domain <dominio>
vtp password <contrasena>
```

### configurar los otros switches como clientes
```
vtp mode client
vtp domain <dominio>
vtp password <password>
```