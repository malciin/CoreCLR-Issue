FROM node:20 AS sdk

RUN npm install -g @angular/cli@19

COPY . /src
WORKDIR /src

RUN npm i
RUN npm run build

FROM node:20
RUN npm i -g http-server
EXPOSE 80
COPY --from=sdk /src/dist/company.frontend/browser /www/.
WORKDIR /www
ENTRYPOINT [ "http-server", ".", "--port", "80", "-P", "http://localhost:80?" ]
