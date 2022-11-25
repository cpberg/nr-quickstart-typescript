FROM node:14.17.0-alpine as build-stage

# set working directory
WORKDIR /app

RUN set -x \
	&& chmod -R 777 /app

# add `/app/node_modules/.bin` to $PATH
ENV PATH /app/node_modules/.bin:$PATH

RUN mkdir /.npm
RUN chown -R 1000870000:0 "/.npm"

RUN apk update && apk upgrade && \
  apk add --no-cache bash git openssh

# install app dependencies
COPY package.json ./
#COPY package-lock.json ./

RUN npm install
RUN npm install react-scripts -g
#RUN npm run build

# add app
COPY . /app

EXPOSE 3000:3000
CMD ["npm", "run", "start"]