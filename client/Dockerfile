# Build React
FROM node:22-alpine AS build

WORKDIR /client

COPY package*.json ./

RUN npm install

COPY . .

ARG VITE_SERVER_URL=http://127.0.0.1:7999

ENV VITE_SERVER_URL=$VITE_SERVER_URL

RUN npm run build


# Serve React
FROM nginx:alpine

COPY --from=build /client/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
