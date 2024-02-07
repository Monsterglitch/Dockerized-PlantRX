FROM node:18-alpine as BUILD_IMAGE

WORKDIR /fronted_app

COPY package.json .

RUN npm i 
RUN npm audit fix --force

COPY . .

RUN npm run build

FROM node:18-alpine as PRODUCTION_IMAGE

WORKDIR /fronted_app

COPY --from=BUILD_IMAGE /fronted_app/dist /frontend_app/dist/

EXPOSE 8080

COPY package.json .

COPY vite.config.js .

EXPOSE 8080

CMD ["npm", "run", "preview"]