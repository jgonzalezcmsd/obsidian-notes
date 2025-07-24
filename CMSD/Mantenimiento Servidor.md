# ✅ MANTENIMIENTO REGULAR DE SERVIDOR LINUX

---

## 🛡️ SEGURIDAD

### 📅 Diario

- Revisar accesos recientes:
  
```bash
last
who
w
```

- Ver intentos de acceso fallidos:

```bash
sudo cat /var/log/auth.log     # En Debian/Ubuntu
sudo cat /var/log/secure       # En RHEL/CentOS
```

- Revisar eventos recientes del sistema:

```bash
journalctl -xe
```

### 📅 Semanal

- Listar usuarios con permisos sudo/root:

```bash
getent group sudo
```

- Ver puertos abiertos y servicios expuestos:

```bash
ss -tuln
# o
netstat -tuln
```

- Ver estado del firewall:

```bash
sudo ufw status
# o
sudo iptables -L
```

- Estado de Fail2ban (si se usa):

```bash
sudo fail2ban-client status
```

---

## 📊 RENDIMIENTO Y RECURSOS

### 📅 Diario

- Ver uso actual de CPU, RAM y procesos:

```bash
top
# o
htop
```

- Estado de la memoria:

```bash
free -h
```

- Uso general del disco:

```bash
df -h
```

### 📅 Semanal

- Ver carpetas que consumen mucho:

```bash
du -sh /var/log/*
```

- Ver actividad de disco (opcional):

```bash
iotop
# o
iostat
```

- Ver carga del sistema:

```bash
uptime
```

---

## 📦 SERVICIOS

### 📅 Diario

- Ver estado de todos los servicios:

```bash
systemctl list-units --type=service
```

- Ver que servicios clave estén activos:

```bash
systemctl status nginx
systemctl status postgresql
# Agrega los que correspondan
```

### 📅 Semanal

- Revisar logs de servicios específicos:

```bash
journalctl -u nombre_del_servicio
```

---

## 🔁 ACTUALIZACIONES Y MANTENIMIENTO

### 📅 Semanal

- Ver actualizaciones pendientes:

```bash
# Debian/Ubuntu
nala list --upgradable

# RHEL/CentOS
dnf check-update
```

- Revisar tareas programadas en cron:

```bash
crontab -l
cat /etc/crontab
ls /etc/cron.*
```

### 📅 Mensual

- Eliminar kernels antiguos:

```bash
# Debian
dpkg --list | grep linux-image

# RHEL
rpm -q kernel
```

---

## 🧪 INTEGRIDAD DEL SISTEMA (Opcional)

### 📅 Mensual

- Verificar integridad de archivos (si usas AIDE o Tripwire)
- Revisar rootkits:

```bash
chkrootkit
rkhunter
```

---

## 📦 EXTRA (Si aplica)

### 📅 Mensual

- Revisar caducidad de certificados SSL:

```bash
openssl x509 -enddate -noout -in cert.pem
```

- Verificar existencia y funcionamiento de respaldos:

```bash
ls -lh /backups
# + revisar los logs correspondientes
```

- Revisar estado de contenedores (Docker):

```bash
docker ps
docker stats
```

---

## 🗓️ RESUMEN DE FRECUENCIAS

| Tarea                               | Frecuencia  |
|------------------------------------|-------------|
| Recursos del sistema (CPU/RAM)     | Diario      |
| Accesos e intentos de login        | Diario      |
| Estado de servicios                | Diario      |
| Estado de disco y logs             | Semanal     |
| Actualizaciones del sistema        | Semanal     |
| Cronjobs y firewall                | Semanal     |
| Certificados y respaldos           | Mensual     |
| Limpieza de kernels viejos         | Mensual     |
| Escaneo de rootkits (opcional)     | Mensual     |
