# Build stage
FROM node:18-alpine

# set working directory
WORKDIR /app

# copy package manifests first to leverage Docker cache
COPY package.json package-lock.json ./

# install dependencies
RUN npm install

# copy app source
COPY . .

# build production assets
RUN npm run build

# Runtime stage: serve with nginx
FROM nginx:alpine

# copy built files from build stage (stage 0)
COPY --from=0 /app/dist /usr/share/nginx/html

# expose nginx port
EXPOSE 80

# start nginx in foreground
CMD ["nginx", "-g", "daemon off;"]
