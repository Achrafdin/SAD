# Practica 1: Infraestructura Segura Securecorp (SAD)

## Objetivo de la practica:

El objetivo de la practica es desplegar y configurar la infraestructura base de una empresa ficticia llamada **Securecorp**. Para ello se ha montado un entorno de red basado en contenedores Docker donde los servicios internos se comunican de forma completamente segura.

1. Desplegar un sistema de directorio **LDAP** para centralizar los usuarios y grupos
2. Asegurar las comunicaciones LDAP mediante certificaciones digitales **LDAPS** creando nuestra propia Autoridad Certificadoras (CA)
3. Configurar **Kerberos** para la autenticacion segura (Single Sign-On).
4. Configurar clientes y servicios web adicionales para que confien en nuestra infraestructura y se conecte al dominio "securecorp.local".

## Vision general y arquitectura 

El entorno esta orquestado  con "docker compose" y se compone de las siguientes maquinas (contenedores) con la misma red interna (bridge):

**Servidor (ldap.securecorp.local):** Es el corazon de la empresa. Actua como servidor LDAP (para guardar quien es quien) y como KDC de Kerberos (para repartir los "tickets" de acceso a los servicios).
**Cliente (cliente.securecorp.local):** Una maquina de pruebas que simula a un empleado de SecureCorp intentando conectarse a los servicios usando sus credenciales.
**phpLDAPadmin:** Una interfaz grafica web para ver y gestionar el arbol de usuarios de LDAP de forma comoda.
**Web (web.securecorp.local):** (Añadido en las fases finales) Un servidor web extra que se integra en el dominio y exige autenticacion segura para acceder.


