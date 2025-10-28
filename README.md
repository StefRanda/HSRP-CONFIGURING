📘 Descripción del proyecto

Este laboratorio tuvo como objetivo implementar el protocolo HSRP (Hot Standby Router Protocol) para garantizar redundancia y alta disponibilidad en la puerta de enlace predeterminada de una red LAN.
Mediante la configuración de un router activo y otro en espera, se asegura la continuidad del servicio ante fallas del equipo principal.

⚙️ Pasos realizados
🔹 Router R1 – Activo
enable
config t
interface g0/1
 standby version 2
 standby 1 ip 192.168.1.254
 standby 1 priority 150
 standby 1 preempt
end

🔹 Router R3 – En espera
enable
config t
interface g0/0
 standby version 2
 standby 1 ip 192.168.1.254
end

🔹 Switches (S1 y S3)
enable
config t
ip default-gateway 192.168.1.254
end

💻 Configuración adicional en PCs

Se cambió la dirección de gateway de las PC por la IP virtual (192.168.1.254) configurada en HSRP.

Esto permite que las PC usen una puerta de enlace virtual única, independientemente del router que esté activo.

🔍 Verificación y pruebas

Se verificó la operación de HSRP mediante comandos de diagnóstico y tracert hacia el servidor.

Luego, se desconectó el cable que unía el switch S1 con PC A para simular una falla de enlace.

El tráfico continuó sin interrupciones, ya que el router en espera (R3) asumió automáticamente el rol de activo.

✅ Resultado esperado: conmutación automática y continuidad del servicio.

🧩 Conclusión

Con esta práctica se logró comprender el funcionamiento de HSRP, uno de los principales protocolos de redundancia de primer salto (FHRP).
El ejercicio demostró cómo este protocolo contribuye a la resiliencia, alta disponibilidad y estabilidad de las redes empresariales.


👩‍💻 Autor

Stefania Randazzo
💡 Estudiante de redes | Apasionada por la tecnología y la configuración de infraestructura segura y eficiente.
