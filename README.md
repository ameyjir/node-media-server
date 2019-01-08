# node-media-server

[![Build Status](https://travis-ci.org/pipll/node-media-server.svg?branch=master)](https://travis-ci.org/pipll/node-media-server)
[![Maintainability](https://api.codeclimate.com/v1/badges/830b5f04b8b895a4c543/maintainability)](https://codeclimate.com/github/pipll/node-media-server/maintainability)
[![GitHub License](https://img.shields.io/github/license/pipll/node-media-server.svg)](https://github.com/pipll/node-media-server/blob/master/LICENSE)

Node.js Media Server / VOD / HLS / DRM

## Installation

```bash
git clone https://github.com/pipll/node-media-server.git
cd node-media-server
npm install
```

## Configuration

Config is located in the `config/index.js` file.

```javascript
const config = {
    // Host and port for bidding
    host: '0.0.0.0',
    port: 3000,

    // Path to static files
    publicPath: path.resolve('./public'),
    // Path to video files
    mediaPath: path.resolve('./media'),
    // Path to index files
    indexPath: path.resolve('./index'),
    // Path to log files
    logsPath: path.resolve('./logs'),

    // Video chunk duration
    fragmentDuration: 10,

    // DRM configuration
    drmEnabled: false,
    drmSeed: 'DRM SEED',

    // Logger configuration
    logLevel: intel.DEBUG,
    logSize: '50m',
    logKeep: 10,

    shutdownInterval: 1000,

    workers: {
        // Server Worker
        web: {
            enabled: true,
            count: require('os').cpus().length,
            shutdownTimeout: 5000,
        },
        // Movie indexer Worker
        indexer: {
            enabled: true,
            count: 1,
            timeout: 5000,
        },
    },
};
```

## Running

```bash
npm start
```

## Usage

Use such URL to play a video file using HLS protocol:

```text
http://host:port/vod/FILE_NAME/playlist.m3u8
```
