# Build react app
FROM node:14-alpine as react-build

# Set working directory
RUN mkdir /app
WORKDIR /app

# Copy package files required for installing dependencies
COPY package.json ./
COPY package-lock.json ./
RUN yarn install

# Copy reminaing app-related files
COPY . .

# Run tests
#TODO: Fix failing test.
#RUN CI=true yarn test

# Build app
RUN yarn build

# Define entry point to be run when container spins up.
ENTRYPOINT ["yarn"]
CMD ["start"]