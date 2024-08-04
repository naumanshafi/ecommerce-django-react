# pull official base image
FROM node:16-slim

# set work directory
WORKDIR /srv/app/frontend

# add to $PATH
ENV PATH /srv/app/node_modules/.bin:$PATH

# install app dependencies
COPY package.json ./
COPY package-lock.json ./
RUN npm install react-scripts@3.4.1 -g --silent
RUN npm install

# add app
COPY . ./

# Start app
CMD ["npm", "start"]