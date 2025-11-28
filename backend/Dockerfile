# backend/Dockerfile
FROM node:18-alpine

WORKDIR /usr/src/app

# copy package files first for caching
COPY backend/package*.json ./

# install dependencies
RUN npm install --production

# copy app source
COPY backend/ .

# port used by backend
ENV PORT=3000
EXPOSE 3000

# start backend (server.js is the entrypoint)
CMD ["node", "server.js"]
