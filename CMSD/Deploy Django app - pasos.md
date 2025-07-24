# 🛠️ Instalación de Apache y WSGI

```bash
sudo apt-get update
sudo apt-get install apache2 libapache2-mod-wsgi-py3
```

---

# ⚙️ Configuración de Apache

## 📝 Archivo `.conf`: `mi_proyecto.conf`

```apache
<VirtualHost *:80>
    ServerAdmin tu@email.com
    ServerName midominio.com  # O usa la dirección IP si no tienes un dominio
    DocumentRoot /ruta/a/tu/proyecto

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /static/ /ruta/a/tu/proyecto/static/
    <Directory /ruta/a/tu/proyecto/static/>
        Require all granted
    </Directory>

    <Directory /ruta/a/tu/proyecto/proyecto/>
        <Files wsgi.py>
            Require all granted
        </Files>
    </Directory>

    WSGIDaemonProcess mi_proyecto python-path=/ruta/a/tu/proyecto python-home=/ruta/a/tu/entorno_virtual
    WSGIProcessGroup mi_proyecto
    WSGIScriptAlias / /ruta/a/tu/proyecto/proyecto/wsgi.py
</VirtualHost>
```

## 🚀 Habilitar sitio y reiniciar Apache

```bash
sudo a2ensite mi_proyecto.conf
sudo systemctl restart apache2
```

## 🔒 Permisos

```bash
chmod -R 755 /ruta/a/tu/proyecto
chown -R www-data:www-data /ruta/a/tu/proyecto
sudo chmod 644 wsgi.py
```

---

# 🛡️ Seguridad

## 🚫 Banear IP con UFW

```bash
sudo ufw deny from 47.239.175.187 to any port 2222
```

## 🔎 Ver puertos usados

```bash
sudo ss -tuln | grep 2222
sudo lsof -i :8000-8999 | grep LISTEN
```

## 🔐 Ver estado de Fail2Ban

```bash
sudo fail2ban-client status sshd
```

---

# 📊 Logs y monitoreo

## 📁 Ver logs de Apache en tiempo real

```bash
sudo tail -f /var/log/apache2/error.log
sudo tail -f /var/log/apache2/access.log
```

## 🔍 Buscar errores específicos

```bash
grep "SIGTERM" /var/log/apache2/error.log | awk '{print $1, $2, $3, ":", $0}'
grep " 500 " /var/log/apache2/access.log | awk '{print $4, $5, ":", $0}'
grep -i "error" /var/log/apache2/error.log | awk '{print $1, $2, $3, ":", $0}'
grep "server reached MaxRequestWorkers setting" /var/log/apache2/error.log | awk '{print $1, $2, $3, ":", $0}'
```

## ⏰ Logs de las últimas 8 horas

```bash
awk -v date="$(date -d '8 hours ago' '+[%d/%b/%Y:%H:%M:%S]')" '$0 ~ date' /var/log/apache2/error.log > error_logs_ultimas_8_horas.txt
```

## 🔎 Log de FTP

```bash
sudo tail -f /var/log/vsftpd.log
```

## 📝 Log de actualizaciones

```bash
cat /var/log/dpkg.log
```

---

# 🐍 Django

## 📦 Colectar archivos estáticos

```bash
python manage.py collectstatic
```

---

# 📈 Matplotlib

## 🗂️ Configuración personalizada

```bash
mkdir ~/matplotlib_config
export MPLCONFIGDIR=~/matplotlib_config
echo "export MPLCONFIGDIR=~/matplotlib_config" >> ~/.bashrc
echo $MPLCONFIGDIR
```

---

# 🧪 JMeter

## 📊 Ejecutar test plan

```bash
java -jar -n -t /home/ubuntu/apache-jmeter-5.5/cfdformacion_test_plan.jmx -l /home/ubuntu/apache-jmeter-5.5/resultados.jtl
```

---

# 📈 Sar (monitor de sistema)

```bash
sar -A > sar_data.txt
csvformat -t sar_data.txt > cpu_data.csv
sar -u 10 > sar_cpu_data.txt
```

---

# 🧰 Utilidades varias

## ✅ Ver servicios activos antes de reiniciar

```bash
systemctl list-units --type=service --state=active > servicios.txt
```

## 🖥️ Iniciar nueva sesión con `screen`

```bash
screen -S session_name
```

## 📂 Copiar contenido de un directorio a otro

```bash
sudo cp -Trv ugo /var/www/ugo/
```

## 🔄 Archivos modificados recientemente

```bash
find /var/www/wordpress -type f -mtime -3
```
