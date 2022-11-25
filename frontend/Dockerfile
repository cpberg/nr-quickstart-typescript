FROM node:14.17.0-alpine

# set working directory
WORKDIR /app

# add `/app/node_modules/.bin` to $PATH
ENV PATH /app/node_modules/.bin:$PATH

RUN apk update && apk upgrade && \
  apk add --no-cache bash git openssh

# install app dependencies
COPY package.json ./
COPY package-lock.json ./

RUN npm install
RUN npm install react-scripts -g
RUN npm update

# add app
COPY . ./

EXPOSE 3000

# Non-privileged user
USER app
RUN chown -R $USER:$(id -gn $USER) /.config

# start app
CMD ["npm", "start"]