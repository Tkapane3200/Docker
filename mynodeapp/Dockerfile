# Stage1: Build
FROM node AS build
WORKDIR /usr/src/app
COPY package.json .
COPY . .
RUN npm install

# Stage2: Production
FROM node AS production
WORKDIR /usr/src/app
COPY --from=build /usr/src/app/ ./dist
COPY --from=build /usr/src/app/package*.json ./
RUN npm install 
EXPOSE 3000
CMD ["node", "dist/index.js"]
