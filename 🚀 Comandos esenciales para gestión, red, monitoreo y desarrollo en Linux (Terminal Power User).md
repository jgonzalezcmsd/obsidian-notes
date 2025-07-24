
## 📂 Gestión de archivos

- `ls -lah` — Lista todo con tamaño legible y archivos ocultos  
- `tree` — Vista en árbol (instalar con `sudo apt install tree`)  
- `mv`, `cp`, `rm` — Mover, copiar y eliminar archivos  
- `rsync -avh --progress origen destino` — Sincronizar carpetas con progreso  
- `find /ruta -name "*.txt"` — Buscar archivos por patrón  
- `fzf` — Fuzzy finder para buscar rápido (requiere instalación)  
- `bat archivo` — `cat` mejorado con colores y paginación (requiere instalación)

---

## 🌐 Red

- `ip a` — Ver interfaces y direcciones IP  
- `ss -tuln` — Ver puertos abiertos y servicios escuchando  
- `ping dominio.com` — Test de conectividad  
- `traceroute dominio.com` — Ruta que siguen los paquetes  
- `nmap -sS 192.168.1.1/24` — Escaneo de red (requiere instalación)  
- `curl -I https://url` — Ver encabezados HTTP  
- `tcpdump -i eth0` — Capturar tráfico (requiere permisos sudo)

---

## 📊 Monitoreo

- `htop` — Monitor interactivo de procesos  
- `glances` — Monitor todo en uno (instalar con pip o apt)  
- `free -h` — Uso de memoria  
- `df -h` — Uso de disco  
- `iotop` — Monitor de IO en disco (sudo necesario)  
- `watch -n 1 comando` — Repetir comando cada segundo para monitoreo en tiempo real

---

## 💻 Desarrollo

- `git` — Control de versiones  
- `vim` o `nvim` — Editores potentes desde terminal  
- `tmux` — Multiplexor de terminal para sesiones persistentes  
- `docker` — Contenerización  
- `gcc`/`g++` — Compiladores para C/C++  
- `python3` y `pip` — Para scripts y manejo de paquetes  
- `curl` y `httpie` — Probar APIs REST desde terminal  
- `jq` — Procesar JSON desde terminal
