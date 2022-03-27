# Build react app
FROM node:14-alpine as react-build

RUN mkdir /app

WORKDIR /app

COPY package.json ./
#COPY package-lock.json ./
RUN yarn install

COPY . .
#RUN CI=true yarn test
RUN yarn build
ENTRYPOINT ["yarn"]
CMD ["start"]