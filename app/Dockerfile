#Requerimientos del sistema
#Descarga versión requerida
#Build stage 1
ARG version=node:alpine 

#Base para la imagen
FROM ${version} AS base

# Define default ports and host for app and db
ARG app_port=3000
ARG db_host=mysql_db
ARG db_port=3306

# Add important environment variables that the server consumes
ENV APP_PORT=${app_port}
ENV DB_HOST=${db_host}
ENV DB_PORT=${db_port}

#Directorio de trabajo para cualquier instrucción
WORKDIR /app

#Copiar archivos
COPY package*.json ./

#Ejecuta cualquier comando en una nueva capa encima de la imagen actual 
RUN npm install 

COPY . .

#Build stage 2
FROM ${version} AS build

#Añade funcionanlidades principales
COPY . .

EXPOSE ${app_port}

#Ejecutar proyecto
CMD ["node", "app.js"]
