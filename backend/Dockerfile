FROM python:3.11-slim

# Crear usuario devops y carpetas
RUN useradd -m devops

# Crear carpeta app y data como root, logs también
RUN mkdir -p /home/devops/app/data && \
    touch /home/devops/app/data/access.log /home/devops/app/data/error.log && \
    chown -R devops:devops /home/devops/app

# Cambiar a usuario devops
USER devops
WORKDIR /home/devops/app

# Copiar requirements y crear virtualenv
COPY requirements.txt .
RUN python -m venv venv && \
    ./venv/bin/pip install --upgrade pip && \
    ./venv/bin/pip install -r requirements.txt

# Copiar todo el código
COPY . .

# Variables de entorno
ENV PATH=/home/devops/app/venv/bin:$PATH
ENV LOG_PATH=/home/devops/app/data
VOLUME /home/devops/app/data

# Ejecutar Gunicorn
CMD ["gunicorn", "-b", "0.0.0.0:5000", "app:app", "--access-logfile", "data/access.log", "--error-logfile", "data/error.log"]
