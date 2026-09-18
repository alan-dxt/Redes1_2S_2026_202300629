# Configuración de portchannel con LACP
Configuración de LACP entre dos switches utilizando los puertos Gig0/1 y Gig0/2 correspondiente a cada equipo.

Aplicar los siguientes comandos para cada equipo:

1. Modo privilegiado
    ```
    enable
    ```

2. Modo de configuracion global
    ```
    configure terminal
    ```

3. Creación del port-channel 1
    ```
    interface port-channel 1
    ```

4. Selección del primer puerto
    ```
    int g0/1
    ```

5. Asignación del primer puerto
    ```
    channel-group 1 mode active    
    ```

6. Selección del segundo puerto
    ```
    int g0/2
    ```

7. Asignación del segundo puerto
    ```
    channel-group 1 mode active    
    ```

8. Verificación de la configuración
    ```
    sh etherchannel summary   
    ```

9. Salida esperada
    ```
    1      Po1(SU)           LACP   Gig0/1(P) Gig0/2(I)  
    ```
