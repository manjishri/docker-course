FROM node:alpine
RUN apk --no-cache upgrade && apk --no-cache add ca-certificates

ADD ./crt/SyngentaCA.crt /usr/local/share/ca-certificates/SyngentaCA.crt 
ADD ./crt/SyngentaIssuingCA4.crt /usr/local/share/ca-certificates/SyngentaIssuingCA4.crt
ADD ./crt/SyngentaRootCA.crt /usr/local/share/ca-certificates/SyngentaRootCA.crt
ADD ./crt/ZscalerCA.crt /usr/local/share/ca-certificates/ZscalerCA.crt
ADD ./crt/ZscalerRootCA.crt /usr/local/share/ca-certificates/ZscalerRootCA.crt
ADD ./crt/registry.npmjs.org.crt /usr/local/share/ca-certificates/registry.npmjs.org.crt

RUN cat /usr/local/share/ca-certificates/SyngentaCA.crt >> /etc/ssl/cert.pem
RUN cat /usr/local/share/ca-certificates/SyngentaIssuingCA4.crt  >> /etc/ssl/cert.pem
RUN cat /usr/local/share/ca-certificates/SyngentaRootCA.crt >> /etc/ssl/cert.pem
RUN cat /usr/local/share/ca-certificates/ZscalerCA.crt  >> /etc/ssl/cert.pem
RUN cat /usr/local/share/ca-certificates/ZscalerRootCA.crt >> /etc/ssl/cert.pem
RUN cat /usr/local/share/ca-certificates/registry.npmjs.org.crt >> /etc/ssl/cert.pem

RUN update-ca-certificates

# Copy local files inside container
COPY ./ ./

# Install some dependencies
RUN npm config set registry http://registry.npmjs.org/  
RUN npm install

# Default command
CMD ["npm", "start"]

