# clavePublica-Privada

Proceso escrito de como creamos una SSH Key

# 1. Enlazar la Terminnal de Debian con tu cuenta GitHub

gh auth login

? What account do you want to log into? GitHub.com

? You're already logged into github.com. Do you want to re-authenticate? Yes

? What is your preferred protocol for Git operations? HTTPS

? Authenticate Git with your GitHub credentials? No

? How would you like to authenticate GitHub CLI? Login with a web browser


! First copy your one-time code: ****-****

Press Enter to open github.com in your browser... 

✓ Authentication complete.

- gh config set -h github.com git_protocol https

✓ Configured git protocol

✓ Logged in as 'Tu GitHub'

# 2. Crear SSH Key

1. Generar la clave SSH

En la terminal:

ssh-keygen -t ed25519 -C "tu_email@ejemplo.com"

👉 Si tu sistema no soporta ed25519, usá:

ssh-keygen -t rsa -b 4096 -C "tu_email@ejemplo.com"
📂 2. Guardar la clave

Te va a preguntar dónde guardarla:

👉 Presioná Enter (usa la ruta por defecto):

/home/tu_usuario/.ssh/id_ed25519

Luego:

Podés poner una contraseña (opcional, recomendado)
O dejar vacío
🚀 3. Activar el agente SSH
eval "$(ssh-agent -s)"
➕ 4. Agregar la clave al agente
ssh-add ~/.ssh/id_ed25519
📋 5. Copiar la clave pública
cat ~/.ssh/id_ed25519.pub

👉 Copiá TODO lo que aparece (empieza con ssh-ed25519)

🌐 6. Agregar la clave en GitHub

En GitHub:

Ir a Settings
Entrar en SSH and GPG keys
Click en New SSH key
Pegás la clave
Guardás
✅ 7. Probar la conexión
ssh -T git@github.com

👉 Si todo está bien, verás algo como:

Hi usuario! You've successfully authenticated...


















