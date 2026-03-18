FROM node:18-slim
WORKDIR /app
COPY package*.json ./
RUN npm install  
COPY . .
ENV NODE_OPTIONS=--openssl-legacy-provider
RUN npm run build
# Step 2: Serve using Nginx
FROM nginx:alpine

COPY --from=build /app/build /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]


