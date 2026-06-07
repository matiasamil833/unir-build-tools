FROM jenkins/inbound-agent:latest

USER root

# Instalar dependencias necesarias
RUN apt-get update && apt-get install -y \
    ca-certificates \
    curl \
    gnupg \
    lsb-release

# Agregar la clave GPG oficial de Docker
RUN install -m 0755 -d /etc/apt/keyrings && \
    curl -fsSL https://download.docker.com/linux/debian/gpg -o /etc/apt/keyrings/docker.asc && \
    chmod a+r /etc/apt/keyrings/docker.asc

# CORREGIDO: Configurar el repositorio de Docker usando sources.list.d
RUN echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/debian \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  tee /etc/apt/sources.list.d/docker.list > /dev/null

# Instalar únicamente el CLI de Docker, Make y Git
RUN apt-get update && apt-get install -y docker-ce-cli make git

# Volver al usuario jenkins por seguridad
USER jenkins    