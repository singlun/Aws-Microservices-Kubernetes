## Build
FROM beevelop/ionic AS ionic
# Create app directory
WORKDIR /usr/src/app
# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
# where available (npm@5+)
COPY package*.json ./
RUN npm install --save-dev  --unsafe-perm sass
RUN npm ci
# Bundle app source
COPY . .
RUN ionic build

## Run 
FROM nginx:alpine
#COPY www /usr/share/nginx/html
#COPY nginx.conf /etc/nginx/nginx.conf
COPY --from=ionic  /usr/src/app/www /usr/share/nginx/html
COPY nginx.conf /etc/nginx/nginx.conf

EXPOSE 8100

