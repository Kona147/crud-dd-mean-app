# frontend/Dockerfile
FROM node:18-alpine AS build

WORKDIR /app
COPY frontend/package*.json ./
RUN npm install
COPY frontend/ .
# build (Angular or fallback)
RUN npm run build -- --output-path=dist --configuration=production || npm run build || echo "No build script"

FROM nginx:stable-alpine
# copy built files (adjust path if your dist uses a subfolder)
COPY --from=build /app/dist/ /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
