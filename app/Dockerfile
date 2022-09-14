# base image
FROM node

# label
LABEL MAINTAINER=Haider

# inside the container what would be the default working directory
WORKDIR /usr/src/app

# copy dependencies
COPY package*.json ./
COPY . .

# run some commands such as npm install
RUN apt update
RUN npm install -g npm@7.20.6

# expose port 3000
EXPOSE 3000

# cmd ["node", "app.js"] (move Dockerfile to app folder)
CMD ["node","app.js"]
