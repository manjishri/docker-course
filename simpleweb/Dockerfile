# Specify a base Image
FROM node:alpine

# Set working directory
WORKDIR /usr/app

# Copy local files inside container
COPY ./package.json ./

# Install some dependencies
RUN npm config set registry http://registry.npmjs.org/
RUN npm install
COPY ./ ./

# Default command
CMD ["npm", "start"] 
