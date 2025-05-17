
# 🐧 Guía Básica de Linux para Desarrolladores Web

Esta guía reúne los **comandos y conceptos básicos de Linux** que todo desarrollador web debe conocer para desenvolverse bien en servidores, entornos de despliegue y administración de proyectos.

> Ideal para quienes desarrollan con **Java Spring Boot**, usan VPS, Docker o herramientas CI/CD.

---

## 📂 Navegación y gestión de archivos

### 📁 Comandos de navegación
```bash
pwd             # Ver ruta actual
ls              # Listar archivos y carpetas
ls -la          # Listar con permisos y ocultos
cd nombre/      # Cambiar de directorio
cd ..           # Retroceder un nivel
```

### 📦 Archivos y carpetas
```bash
touch archivo.txt          # Crear archivo vacío
mkdir nueva_carpeta        # Crear carpeta
rm archivo.txt             # Eliminar archivo
rm -r carpeta/             # Eliminar carpeta y contenido
cp archivo1.txt copia.txt  # Copiar archivo
mv archivo.txt ../         # Mover archivo
```

---

## 🔍 Inspección y lectura de contenido

```bash
cat archivo.txt        # Mostrar contenido
less archivo.txt       # Leer contenido por páginas
head -n 10 archivo.txt # Primeras 10 líneas
tail -n 20 archivo.txt # Últimas 20 líneas
```

### Logs en servidores
```bash
# Ver logs de tu app Spring
tail -f logs/app.log

# Ver logs del sistema
tail -f /var/log/syslog
journalctl -xe          # Eventos importantes del sistema
```

---

## 👤 Gestión de usuarios y permisos

```bash
whoami               # Ver tu usuario actual
id                   # Ver grupos y UID
sudo su              # Convertirse en root
adduser cris         # Crear nuevo usuario
passwd cris          # Cambiar contraseña
```

### Permisos de archivos
```bash
chmod 755 script.sh       # Permisos: rwxr-xr-x
chown usuario:grupo file  # Cambiar propietario
ls -l archivo.txt         # Ver permisos
```

> 🔐 **Importante**: nunca subas tu app `.jar` ni archivos `.env` con permisos públicos (`777`).

---

## 🛰️ Redes y puertos

```bash
ip a                  # Ver IP del servidor
ping google.com       # Probar conexión
curl localhost:8080   # Probar tu API
ss -tulnp             # Ver servicios activos y puertos
```

### Firewall (UFW)
```bash
sudo ufw allow 22/tcp     # Permitir SSH
sudo ufw allow 8080/tcp   # Permitir acceso a tu app
sudo ufw enable           # Activar firewall
sudo ufw status verbose   # Ver estado
```

---

## ⚙️ Procesos y recursos del sistema

```bash
top                     # Ver procesos y consumo
htop                    # Versión mejorada (instalable)
ps aux | grep java      # Buscar procesos por nombre
kill -9 PID             # Matar proceso
```

### Espacio y disco
```bash
df -h                  # Uso del disco
du -sh carpeta/        # Tamaño de una carpeta
free -m                # RAM usada
```

---

## 🚀 Despliegue y ejecución de apps

### Compilar y correr una app Spring Boot
```bash
./mvnw clean package
java -jar target/miapp.jar
```

### Control del servicio
```bash
# Ejecutar en segundo plano
nohup java -jar app.jar &

# Ver procesos Java activos
ps aux | grep java
```

> 📝 También puedes crear un servicio systemd para correr tu app como un demonio (más profesional).

---

## 🧰 Archivos comprimidos

```bash
tar -czvf archivo.tar.gz carpeta/    # Comprimir
tar -xzvf archivo.tar.gz             # Descomprimir

zip archivo.zip archivo.txt          # ZIP
unzip archivo.zip                    # Descomprimir ZIP
```

---

## ⏱️ Automatización básica (cron jobs)

```bash
crontab -e   # Editar tareas programadas

# Ejecutar un script cada día a las 2 AM
0 2 * * * /ruta/a/mi_script.sh
```

---

## 🐳 (Opcional) Comandos Docker básicos

```bash
docker ps               # Ver contenedores activos
docker build -t app .   # Construir imagen
docker run -p 8080:8080 app   # Ejecutar
docker exec -it app bash      # Entrar al contenedor
```

---

## 📦 Instalación de paquetes

```bash
sudo apt update             # Actualizar índice
sudo apt install htop git   # Instalar herramientas
sudo apt remove paquete     # Eliminar
```

> ⚠️ Siempre actualiza tu sistema en entornos productivos:
```bash
sudo apt upgrade -y
```

---

## 🧾 Buenas prácticas como desarrollador en Linux

✅ Usa un usuario sin privilegios para desarrollar o desplegar.  
✅ Asigna permisos justos a tus archivos (`chmod 644` o `600` para `.env`).  
✅ Usa logs estructurados y rotación para tus aplicaciones.  
✅ Protege tus puertos con firewall y acceso restringido por IP.  
✅ Automatiza tareas repetitivas (backups, deploys).  
✅ Usa Git y CI/CD para mantener trazabilidad del código.  

---

## 📚 Recursos útiles

- [The Linux Command Line Book (Gratis)](https://linuxcommand.org/tlcl.php)
- [CheatSheet Linux](https://github.com/cheat/cheat)
- [Explainshell.com](https://explainshell.com/) ← ¡Explica comandos por partes!
