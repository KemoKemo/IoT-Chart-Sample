# IoT-Chart-Sample

A Chart project for the temperature sensor's data.

## Prerequisite

It is necessary that the [db-api](https://github.com/kemokemo/IoT-DB-Sample/tree/master/db-api) service is running at the URL of `http://localhost:9000`.

## Build

```sh
# install dependencies
npm install

# build for production with minification
npm run build
```

## Run

```sh
cd server
go run main.go
```

Open `http://localhost:8090` with a browser.