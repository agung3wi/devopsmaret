FROM node:12 AS builder

WORKDIR /app
COPY ./ /app/
RUN npm install
RUN npm run build

FROM nginx
COPY --from=builder /app/dist /usr/share/nginx/html

