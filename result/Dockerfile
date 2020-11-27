FROM 111706684826.dkr.ecr.us-east-1.amazonaws.com/library/node:8.10.0-alpine

RUN mkdir -p /app
WORKDIR /app

RUN npm config set unsafe-perm true
RUN yarn install --production --no-progress
RUN npm config set registry https://registry.npmjs.org
RUN npm install -g nodemon
COPY package.json /app/package.json
RUN npm install \
 && npm ls \
 && npm cache clean --force \
 && mv /app/node_modules /node_modules
COPY . /app

ENV PORT 80
EXPOSE 80

CMD ["node", "server.js"]
