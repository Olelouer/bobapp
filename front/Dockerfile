FROM node:20-alpine AS build

WORKDIR /usr/local/app
COPY ./ ./

RUN npm install
RUN npm run build

FROM nginx:1.27-alpine-slim AS production

COPY nginx.conf /etc/nginx/conf.d/default.conf
COPY --from=build /usr/local/app/dist/bobapp /usr/share/nginx/html
RUN adduser -D -H -u 1001 -s /bin/false nginx
USER nginx

EXPOSE 80
