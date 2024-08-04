# Pull official base image
FROM node:16-slim

# Set working directory
WORKDIR /srv/app/frontend

# Add to $PATH
ENV PATH /srv/app/frontend/node_modules/.bin:$PATH

# Copy package.json and package-lock.json first to leverage Docker cache
COPY package.json package-lock.json ./

# Install app dependencies and create necessary directories with permissions
RUN npm install react-scripts@3.4.1 -g --silent && \
    npm install
    
RUN mkdir -p /srv/app/frontend/node_modules/.cache

# Copy the rest of the application code
COPY . .

RUN chmod -R 777 /srv/app/frontend/node_modules/.cache

# Start the app
CMD ["npm", "start"]
