
```
██████╗ ██╗ ██████╗ ██████╗██╗ ██████╗ ███╗   ██╗ █████╗ ██████╗ ██╗ ██████╗ ███████╗
██╔══██╗██║██╔════╝██╔════╝██║██╔═══██╗████╗  ██║██╔══██╗██╔══██╗██║██╔═══██╗██╔════╝
██║  ██║██║██║     ██║     ██║██║   ██║██╔██╗ ██║███████║██████╔╝██║██║   ██║███████╗
██║  ██║██║██║     ██║     ██║██║   ██║██║╚██╗██║██╔══██║██╔══██╗██║██║   ██║╚════██║
██████╔╝██║╚██████╗╚██████╗██║╚██████╔╝██║ ╚████║██║  ██║██║  ██║██║╚██████╔╝███████║
╚═════╝ ╚═╝ ╚═════╝ ╚═════╝╚═╝ ╚═════╝ ╚═╝  ╚═══╝╚═╝  ╚═╝╚═╝  ╚═╝╚═╝ ╚═════╝ ╚══════╝
```

# diccionarios — Wordlists para pentesting web

Colección de **diccionarios (wordlists)** en texto plano pensados para pruebas de seguridad web: fuerza bruta de usuarios/contraseñas, descubrimiento de ficheros y carpetas, fuzzing de parámetros, payloads de XSS/SQLi/Path Traversal/SSRF, Google Dorks y enumeración de subdominios.

| Objetivo de la prueba | Diccionario(s) | Herramienta sugerida |
|---|---|---|
| Fuerza bruta de login (usuario) | `usuarios.txt`, `usuarios0.txt`, `usuarios1.txt` | `hydra`, `medusa`, `patator` |
| Fuerza bruta de login (password) | `claves.txt`, `claves0.txt`, `claves2.txt`, `claves3.txt` | `hydra`, `medusa`, `john` |
| Login en castellano / objetivo hispanohablante | `diccionario.txt` | `hydra`, `wpscan` |
| Dispositivos Cisco | `clavescisco.txt` | `hydra` (módulo cisco) |
| VPN IPsec / IKE (PSK) | `ike.txt` | `ike-scan`, `psk-crack` |
| Descubrir carpetas | `carpetas.txt`, `carpetas2.txt`, `directorios.txt` | `dirsearch`, `dirb`, `ffuf` |
| Descubrir ficheros sueltos | `ficheros.txt`, `ficheros2.txt`, `archivos.txt` | `ffuf`, `wfuzz`, `fuzzer.sh` |
| Objetivo IIS | `archivos_iis.txt` | `dirsearch`, `ffuf` |
| Endpoints de API | `api.txt` | `ffuf`, `wfuzz` |
| Objetivo ASP/ASP.NET | `asp.txt`, `apsx.txt` | `dirsearch -e asp,aspx` |
| Objetivo PHP | `php.txt` | `dirsearch -e php` |
| Objetivo Java/JSP | `jsp.txt` | `dirsearch -e jsp` |
| Objetivo HTML estático | `htm.txt` | `dirsearch -e htm,html` |
| Ficheros JavaScript | `js.txt` | `ffuf`, `dirsearch -e js` |
| Config/XML/WSDL | `xml.txt` | `dirsearch -e xml` |
| Scripts CGI antiguos | `cgi.txt` | `dirsearch`, `nikto` |
| Descubrir parámetros ocultos | `parametros.txt` | `ffuf` (modo parámetro), `Arjun` |
| Probar XSS | `xss.txt` | `dalfox`, `xsser`, Burp Intruder |
| Probar SQLi | `sqli.txt` | `sqlmap`, Burp Intruder |
| Probar SSRF | `ssrf.txt` | Burp Intruder, `ffuf` |
| Probar Path Traversal | `pathtraversal.txt` | `ffuf`, `wfuzz`, Burp Intruder |
| Enumerar subdominios | `subdominios.txt`, `subdominios2.txt`, `subdominios3.txt` | `httpx`, `gobuster dns`, `amass` |
| Reconocimiento OSINT vía buscador | `GoogleHackingDorks.txt` | búsqueda manual en Google/Bing |
| Fingerprinting HTTP con Nmap | `http-fingerprints.lua.zip` | Nmap NSE |


---

## Tabla de contenidos

- [Instalación / descarga](#instalación--descarga)
- [Tabla resumen de diccionarios](#tabla-resumen-de-diccionarios)
- [Descripción detallada por categoría](#descripción-detallada-por-categoría)
  - [Usuarios y contraseñas](#1-usuarios-y-contraseñas)
  - [Ficheros y carpetas](#2-ficheros-y-carpetas)
  - [Tecnologías / extensiones](#3-tecnologías--extensiones)
  - [Payloads de ataque web](#4-payloads-de-ataque-web)
  - [Reconocimiento y enumeración](#5-reconocimiento-y-enumeración)
  - [Otros / dispositivos y protocolos](#6-otros--dispositivos-y-protocolos)
- [Scripts de prueba: cómo usar cada diccionario](#scripts-de-prueba-cómo-usar-cada-diccionario)
- [Integración con el repositorio fuzzer](#integración-con-el-repositorio-fuzzer)
- [Buenas prácticas](#buenas-prácticas)
- [Licencia](#licencia)

---

## Instalación / descarga

Clonar el repositorio completo:

```bash
git clone https://github.com/hackingyseguridad/diccionarios
cd diccionarios
```

O descargar un diccionario suelto sin clonar todo el repositorio:

```bash
wget https://raw.githubusercontent.com/hackingyseguridad/diccionarios/master/diccionario.txt
wget https://raw.githubusercontent.com/hackingyseguridad/diccionarios/master/usuarios.txt
wget https://raw.githubusercontent.com/hackingyseguridad/diccionarios/master/claves.txt
wget https://raw.githubusercontent.com/hackingyseguridad/diccionarios/master/ficheros.txt
wget https://raw.githubusercontent.com/hackingyseguridad/diccionarios/master/xss.txt
wget https://raw.githubusercontent.com/hackingyseguridad/diccionarios/master/GoogleHackingDorks.txt
```

---

## Tabla resumen de diccionarios

| Fichero | Categoría | Contenido | Herramienta |
|---|---|---|---|
| `usuarios.txt`, `usuarios0.txt`, `usuarios1.txt` | Credenciales | Nombres de usuario comunes para fuerza bruta | `hydra`, `medusa`, `patator` |
| `claves.txt`, `claves0.txt`, `claves2.txt`, `claves3.txt` | Credenciales | Contraseñas más comunes para fuerza bruta | `hydra`, `medusa`, `john` |
| `diccionario.txt` | Credenciales | Usuarios y contraseñas más usados, en castellano | `hydra`, `wpscan` |
| `clavescisco.txt` | Credenciales / dispositivos | Contraseñas por defecto/comunes de equipos Cisco | `hydra` (módulo `cisco`) |
| `carpetas.txt`, `carpetas2.txt` | Ficheros y carpetas | Nombres de carpetas comunes en servidores web | `dirsearch`, `dirb`, `ffuf` |
| `directorios.txt` | Ficheros y carpetas | Rutas de directorios (equivalente a `carpetas.txt`) | `dirsearch`, `ffuf`, `wfuzz` |
| `ficheros.txt`, `ficheros2.txt` | Ficheros y carpetas | Nombres de ficheros para descubrir recursos expuestos | `fuzzer.sh`, `ffuf`, `wfuzz` |
| `archivos.txt` | Ficheros y carpetas | Nombres de archivos genéricos comunes | `dirsearch`, `ffuf` |
| `archivos_iis.txt` | Ficheros y carpetas | Ficheros típicos de servidores IIS | `dirsearch`, `ffuf` |
| `api.txt` | Ficheros y carpetas | Rutas/endpoints comunes de APIs REST | `ffuf`, `wfuzz` |
| `asp.txt`, `apsx.txt` | Tecnologías | Rutas/ficheros típicos de entornos ASP / ASP.NET | `dirsearch -e asp,aspx` |
| `php.txt` | Tecnologías | Rutas/ficheros típicos de entornos PHP | `dirsearch -e php` |
| `jsp.txt` | Tecnologías | Rutas/ficheros típicos de entornos Java (JSP) | `dirsearch -e jsp` |
| `htm.txt` | Tecnologías | Rutas/ficheros con extensión `.htm`/`.html` | `dirsearch -e htm,html` |
| `js.txt` | Tecnologías | Nombres de ficheros JavaScript comunes | `dirsearch -e js`, `ffuf` |
| `xml.txt` | Tecnologías | Ficheros/rutas relacionadas con XML (config, sitemap, WSDL) | `dirsearch -e xml` |
| `cgi.txt` | Tecnologías | Scripts CGI comunes (`cgi-bin`) | `dirsearch`, `nikto` |
| `xss.txt` | Payloads de ataque | Vectores/payloads para pruebas de Cross-Site Scripting | `xsser`, `dalfox`, Burp Intruder |
| `sqli.txt` | Payloads de ataque | Payloads para pruebas de inyección SQL | `sqlmap`, Burp Intruder |
| `ssrf.txt` | Payloads de ataque | Payloads para pruebas de Server-Side Request Forgery | Burp Intruder, `ffuf` |
| `pathtraversal.txt` | Payloads de ataque | Payloads de Path/Directory Traversal (`../../etc/passwd`, etc.) | `ffuf`, `wfuzz`, Burp Intruder |
| `parametros.txt` | Payloads de ataque | Nombres de parámetros GET/POST habituales para fuzzing | `ffuf` (modo parámetros), `Arjun` |
| `GoogleHackingDorks.txt` | Reconocimiento | Google Dorks para localizar información/vulnerabilidades expuestas vía buscador | búsqueda manual en Google/Bing |
| `subdominios.txt`, `subdominios2.txt`, `subdominios3.txt` | Reconocimiento | Listas de subdominios comunes para enumeración | `httpx_subdominio.sh`, `gobuster dns`, `amass` |
| `ike.txt` | Protocolos / VPN | Diccionario para ataques a VPNs con IKE (Internet Key Exchange) | `ike-scan`, `psk-crack` |
| `http-fingerprints.lua.zip` | Fingerprinting | Script/base de datos Lua de huellas HTTP (identificación de servidores/dispositivos) | Nmap NSE (`http-fingerprints.lua`) |


---

## Descripción detallada por categoría

### 1. Usuarios y contraseñas

- **`usuarios.txt` / `usuarios0.txt` / `usuarios1.txt`** — variantes con distintos volúmenes/orígenes de nombres de usuario comunes (admin, root, nombres de pila habituales, cuentas de servicio típicas).
- **`claves.txt` / `claves0.txt` / `claves2.txt` / `claves3.txt`** — variantes de contraseñas más filtradas/usadas, útiles para combinarlas con `usuarios.txt` en ataques de fuerza bruta o *credential stuffing* en entornos de prueba.
- **`diccionario.txt`** — combinación de usuarios y contraseñas más usados específicamente en **castellano**, pensado para objetivos hispanohablantes.
- **`clavescisco.txt`** — contraseñas por defecto o históricamente comunes en dispositivos de red Cisco (routers, switches).

### 2. Ficheros y carpetas

- **`carpetas.txt` / `carpetas2.txt` / `directorios.txt`** — nombres de directorios habituales en servidores web (`admin`, `backup`, `uploads`, `config`, `.git`, etc.), usados por `directorios.sh` y `dirb.sh` del repositorio `fuzzer`.
- **`ficheros.txt` / `ficheros2.txt` / `archivos.txt`** — nombres de ficheros sueltos (backups, logs, configuraciones) para localizar recursos no enlazados.
- **`archivos_iis.txt`** — ficheros específicos que aparecen típicamente en instalaciones de Microsoft IIS.
- **`api.txt`** — rutas y nombres de endpoints habituales en APIs REST (`/api/v1/users`, `/api/login`, `/swagger.json`, etc.).

### 3. Tecnologías / extensiones

Diccionarios pensados para acompañar el flag de extensión (`-e`) de herramientas como `dirsearch`, agrupando nombres típicos según la pila tecnológica del objetivo: **`asp.txt`**, **`apsx.txt`** (ASP/ASP.NET), **`php.txt`** (PHP), **`jsp.txt`** (Java/JSP), **`htm.txt`** (HTML estático), **`js.txt`** (JavaScript), **`xml.txt`** (XML/config/WSDL) y **`cgi.txt`** (scripts CGI clásicos, `cgi-bin`).

### 4. Payloads de ataque web

- **`xss.txt`** — vectores de Cross-Site Scripting, desde payloads básicos hasta variantes de evasión de filtros.
- **`sqli.txt`** — payloads para detectar inyección SQL (comillas, comentarios, *time-based*, *boolean-based*, *UNION-based*).
- **`ssrf.txt`** — payloads para provocar peticiones del servidor hacia recursos internos/externos controlados por el auditor.
- **`pathtraversal.txt`** — secuencias de salto de directorio (`../`, codificaciones alternativas) para intentar leer ficheros fuera del directorio raíz web.
- **`parametros.txt`** — nombres de parámetros GET/POST habitualmente usados por aplicaciones (`id`, `page`, `redirect`, `debug`, `token`...), útiles para descubrir parámetros ocultos antes de aplicar los payloads anteriores.

### 5. Reconocimiento y enumeración

- **`GoogleHackingDorks.txt`** — consultas avanzadas de Google (*dorks*) para localizar mediante buscadores ficheros sensibles, paneles de login expuestos, mensajes de error, etc., sin tocar directamente el servidor objetivo.
- **`subdominios.txt` / `subdominios2.txt` / `subdominios3.txt`** — listas de subdominios habituales (`www`, `mail`, `dev`, `staging`, `api`, `vpn`...) para enumeración por fuerza bruta de DNS, usadas por `httpx_subdominio.sh` del repositorio `fuzzer`.

### 6. Otros / dispositivos y protocolos

- **`ike.txt`** — diccionario orientado a ataques sobre el protocolo IKE (VPNs IPsec), típicamente usado con `ike-scan`/`psk-crack` para clave precompartida (PSK).
- **`http-fingerprints.lua.zip`** — script Lua (para el motor de scripts NSE de Nmap) con firmas para identificar servidores/dispositivos por sus respuestas HTTP.

---

## Scripts de prueba: cómo usar cada diccionario

Este repositorio contiene **solo los diccionarios**; los scripts que los consumen viven en [`hackingyseguridad/fuzzer`](https://github.com/hackingyseguridad/fuzzer). A continuación tienes ejemplos de uso directo de cada wordlist con herramientas habituales, útiles como scripts de prueba rápidos.

### Fuerza bruta de credenciales (usuarios + claves)

```bash
# Login form / HTTP básico
hydra -L usuarios.txt -P claves.txt dominio.com http-post-form \
  "/login:user=^USER^&pass=^PASS^:Credenciales incorrectas"

# SSH
hydra -L usuarios.txt -P claves.txt ssh://dominio.com
```

### Descubrimiento de ficheros y carpetas

```bash
# Con dirsearch (usado internamente por fuzzer/directorios.sh)
dirsearch -u https://dominio.com -w carpetas.txt -e php,asp,aspx,jsp,html -x 400-499,500-599

# Con ffuf
ffuf -u https://dominio.com/FUZZ -w ficheros.txt -mc 200,301,302,403
```

### Fuzzing de parámetros

```bash
ffuf -u "https://dominio.com/index.php?FUZZ=1" -w parametros.txt -fs 0
```

### Pruebas de XSS

```bash
# Con dalfox
dalfox url "https://dominio.com/buscar?q=FUZZ" -w xss.txt

# Con curl manual, uno por uno
while read payload; do
  curl -s "https://dominio.com/buscar?q=$payload" | grep -q "$payload" && echo "Posible XSS: $payload"
done < xss.txt
```

### Pruebas de SQL Injection

```bash
sqlmap -u "https://dominio.com/producto?id=1" --level=3 --risk=2
# o usar sqli.txt como diccionario de payloads manuales en Burp Intruder
```

### Path Traversal

```bash
while read payload; do
  curl -s -o /dev/null -w "%{http_code} $payload\n" "https://dominio.com/download?file=$payload"
done < pathtraversal.txt
```

### Enumeración de subdominios

```bash
# Con httpx (ver httpx_subdominio.sh en el repo fuzzer)
sed 's/$/.dominio.com/' subdominios.txt | httpx -silent -status-code
```

### Google Dorks

```bash
# Uso manual: cada línea de GoogleHackingDorks.txt es una consulta a adaptar
# Ejemplo de línea: intitle:"index of" "backup"
# Se recomienda anteponer site:dominio.com y lanzar la búsqueda en el navegador
```

### Diccionario IKE / VPN

```bash
ike-scan -M dominio.com
psk-crack -d ike.txt handshake.psk
```

---

## Integración con el repositorio fuzzer

La forma recomendada de usar estos diccionarios es junto con [`hackingyseguridad/fuzzer`](https://github.com/hackingyseguridad/fuzzer):

```bash
git clone https://github.com/hackingyseguridad/fuzzer
git clone https://github.com/hackingyseguridad/diccionarios
cd fuzzer
cp ../diccionarios/ficheros.txt .
cp ../diccionarios/carpetas.txt ../diccionarios/carpetas2.txt .
sh fuzzer.sh https://dominio.com
sh directorios.sh https://dominio.com
```


## Cómo construir la respuesta

1. **Identifica el objetivo de la prueba** que pide el usuario (login, directorios, XSS, subdominios...) y localiza la fila correspondiente en la tabla.
2. **Elige el diccionario más específico** antes que el genérico: p. ej. si el objetivo es claramente PHP, prioriza `php.txt` sobre `ficheros.txt` genérico; si el usuario ya mencionó `hackingyseguridad/fuzzer`, recuerda que ese repo espera los ficheros `ficheros.txt`, `carpetas.txt` y `carpetas2.txt` en su propio directorio.
3. **Genera el comando concreto** con la herramienta sugerida, sustituyendo `dominio.com`/URL por el objetivo que indique el usuario. Ejemplos de referencia:

```bash
# Fuerza bruta de login
hydra -L usuarios.txt -P claves.txt dominio.com http-post-form \
  "/login:user=^USER^&pass=^PASS^:Credenciales incorrectas"

# Descubrimiento de carpetas
dirsearch -u https://dominio.com -w carpetas.txt -e php,asp,aspx,jsp,html -x 400-499,500-599

# Fuzzing de ficheros
ffuf -u https://dominio.com/FUZZ -w ficheros.txt -mc 200,301,302,403

# Fuzzing de parámetros
ffuf -u "https://dominio.com/index.php?FUZZ=1" -w parametros.txt -fs 0

# XSS
dalfox url "https://dominio.com/buscar?q=FUZZ" -w xss.txt

# SQLi
sqlmap -u "https://dominio.com/producto?id=1" --level=3 --risk=2

# Path Traversal
while read payload; do
  curl -s -o /dev/null -w "%{http_code} $payload\n" "https://dominio.com/download?file=$payload"
done < pathtraversal.txt

# Subdominios
sed 's/$/.dominio.com/' subdominios.txt | httpx -silent -status-code

# IKE/VPN
ike-scan -M dominio.com
psk-crack -d ike.txt handshake.psk
```

4. **Si la tarea combina varias fases** (p. ej. descubrir parámetro y luego probar payload), encadénalas: primero `parametros.txt`, después `xss.txt`/`sqli.txt`/`ssrf.txt` sobre el parámetro encontrado.
5. **Recuerda buenas prácticas**: ajustar hilos/rate-limit para no provocar denegación de servicio, empezar con diccionarios pequeños antes de escalar a variantes ampliadas (`usuarios0/1.txt`, `claves0/2/3.txt`), y guardar la salida (`> resultado.txt`) para correlacionar hallazgos entre fases.

## Integración con hackingyseguridad/fuzzer

Si el usuario también usa el repositorio de scripts [`hackingyseguridad/fuzzer`](https://github.com/hackingyseguridad/fuzzer), indícale que copie los diccionarios relevantes al directorio del fuzzer antes de ejecutarlo:

```bash
git clone https://github.com/hackingyseguridad/fuzzer
git clone https://github.com/hackingyseguridad/diccionarios
cd fuzzer
cp ../diccionarios/ficheros.txt ../diccionarios/carpetas.txt ../diccionarios/carpetas2.txt .
sh fuzzer.sh https://dominio.com
sh directorios.sh https://dominio.com
```




---


#

# 

<p align="center">
  <img src="https://github.com/hackingyseguridad/diccionarios/blob/master/autor.png" alt="@antonio_taboada">
</p>

#

<p align="center">
  <a href="https://www.hackingyseguridad.com/">https://www.hackingyseguridad.com/</a>
</p>
