#Build Phase for production

# Specify a base image
FROM node:alpine as builder

WORKDIR /app

# Install some depenendencies
COPY ./package.json ./
RUN npm install
COPY ./ ./

# Default command
RUN npm run build

#Run Phase for production

# Specify a base image
FROM nginx
#only understood by the elastic beanstalk not on local
EXPOSE 3000 
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
