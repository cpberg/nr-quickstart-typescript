FROM node:16.17.0-alpine

# set working directory
WORKDIR /app

# add `/app/node_modules/.bin` to $PATH
ENV PATH /app/node_modules/.bin:$PATH

RUN apk update && apk upgrade && \
  apk add --no-cache bash git openssh

# install app dependencies
COPY package.json ./
COPY package-lock.json ./
RUN rm -rf ./config
RUN npm install
RUN npm install react-scripts -g
RUN npm update

# add app
COPY . ./

EXPOSE 3000

# start app
CMD ["npm", "start"]