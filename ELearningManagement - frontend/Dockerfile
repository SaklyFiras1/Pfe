
FROM node:alpine as build-stage
WORKDIR /app
COPY package*.json ./
RUN npm install --force
COPY . .
RUN npm run build

# Stage 2: Serve the angular app with Nginx
FROM nginx:alpine
COPY --from=build-stage /app/dist/elearning-management /usr/share/nginx/html
COPY nginx/nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
