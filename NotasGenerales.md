# Comandos de configuración

## Guardar configuración
```
// Guerdar
Switch/Router/...# copy running-config startup-config
//Verificar
show running-config
show startup-config
```

## Creacion de Vlan
Crear la vlan en el switch conectado a computadoras
```
enable
configure terminal
vlan <X>
name <NAME>
end
```

Asignación del puerto a una vlan
```
enable
configure terminal
interface fa0/<X>
switchport mode access
switchport access vlan <X>
exit
```

Enlace troncal
```
enable
configure terminal
interface fa0/<X>
switchport mode trunk
switchport trunk allowed vlan <Y>, <Z>...

```

Verificar VLANs
```
show vlan brief
```

## Puerta de enlace(Switch - Router)
Comandos necesarios para el router
```
enable
configure terminal
interface gigabit0/<X>
ip address 192.168.<Y>.1 255.255.255.0
no shutdown
```

## Interfaz serial(Router - Router)
Comandos para cada puerto de los routers
```
enable
configure terminal
interface serial0/<X>/<Y>
ip address 10.0.0.<A> 255.255.255.<B>
```

considerar la dirección de la red y del broadcast al asignar la ip

## Configuración de Ethernet PAgP

Switch negociador
```
enable
configure terminal
interface range fa0/<X>-<Y>
switchport mode trunk
channel-group <Z> mode desirable
no shutdown
end
```

Switch receptor
```
enable
configure terminal
interface range fa0/<X>-<Y>
switchport mode trunk
channel-group <Z> mode auto
no shutdown
end
```

Confirmación en cada switch
```
show etherchannel summary
```

## Configuración de Rapid PVST+
Activar Rapid PVST+ en cada uno de los switches
```
enable
configure terminal
spanning-tree mode rapid-pvst
end
```

Verificación
```
show spanning-tree
```


## Configurar VTP
Configuración del switch server
```
enable
configure terminal
vtp mode server
vtp domain <Nombre_dominio>
vtp password <Contraseña>
end
```

Configuración de los switches clientes
```
enable
configure terminal
vtp mode client
vtp domain <Nombre_dominio>
vtp password <Contraseña>
end
```

Configuración del enlace troncal en los clientes
```
enable
configure terminal
int f0/<Puerto a switch>
switchport mode trunk
end
```

configuración del enlace troncal en el server
```
enable
configure terminal
int range fa0/<X> - <Y>
switchport mode trunk
end
```