FROM node:18-alpine

# set working directory
WORKDIR /app

# copy package manifests first to leverage Docker cache
COPY package.json package-lock.json ./

# install dependencies
RUN npm install

# copy application source
COPY . .

# create directory for SQLite database file
RUN mkdir -p /app/data

# expose backend port
EXPOSE 5001

# start the application
CMD ["npm", "start"]
