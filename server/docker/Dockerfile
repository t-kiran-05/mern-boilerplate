FROM node:16.19.0-alpine

# Set non-root user
ENV USER=node

# Create app directory and set permissions
RUN mkdir -p /home/node/app && \
    mkdir /home/node/.npm-global && \
    chown -R node:node /home/node

WORKDIR /home/node/app

# Copy package files first for better Docker caching
COPY package*.json ./

# Set up global npm path
ENV PATH=/home/node/.npm-global/bin:$PATH
ENV NPM_CONFIG_PREFIX=/home/node/.npm-global

# Switch to non-root user
USER node

# Set npm global user config
RUN npm --global config set user "${USER}"

# Install global PM2
RUN npm install --location=global pm2

# Install project dependencies
RUN npm install

# Copy rest of the app
COPY --chown=node:node . .

# Build the app
ENV NODE_ENV=production
RUN npm run build

# Run using PM2
CMD ["pm2-runtime", "--no-auto-exit", "npm", "--", "run", "docker:start:prod"]
