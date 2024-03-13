# Step 1: Build Angular Application
FROM node:21 AS build
WORKDIR /app
COPY package*.json ./
RUN apt-get update
RUN apt-get install -y build-essential libcairo2-dev libpango1.0-dev libjpeg-dev libgif-dev librsvg2-dev
RUN npm install --force
RUN npm install -g @angular/cli
RUN npm install http-server -g

COPY . .
RUN ng build

FROM node:21
WORKDIR /app
RUN npm install http-server -g


COPY --from=build /app/dist/ ./dist/


EXPOSE 8080

CMD ["http-server", "dist/"]