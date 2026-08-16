# ---------- Build Stage ----------
FROM node:22-alpine AS builder

WORKDIR /app

COPY package*.json ./

RUN npm install --ignore-scripts

COPY . .

RUN npm run build


# ---------- Runtime Stage ----------
FROM nginxinc/nginx-unprivileged:alpine AS runtime

COPY --from=builder /app/dist /usr/share/nginx/html

EXPOSE 8080

USER nginx

CMD ["nginx", "-g", "daemon off;"]
