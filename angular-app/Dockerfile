# Étape 1 : Builder l'application Angular
FROM node:14 as build
WORKDIR /app
COPY . .
RUN npm install
RUN npm run build -- --prod

# Étape 2 : Utiliser Nginx pour servir l'application Angular build
FROM nginx:alpine
COPY --from=build /app/dist/* /usr/share/nginx/html/
COPY nginx.conf /etc/nginx/nginx.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]



