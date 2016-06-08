assets-loader
===

A simple batch assets loader.
This is a fork from (Ian McGregor's assets-loader)[https://github.com/ianmcgregor/assets-loader].

### Install

```
npm install watsondg/assets-loader --S
```

### Usage

```javascript
var AssetsLoader = require('assets-loader');

// load some assets:

var loader = new AssetsLoader({
        assets: [
            // image
            '/images/picture.png',
            // image with crossorigin
            { url: '/images/picture.jpg', crossOrigin: 'anonymous' },
            // image as blob
            { url: '/images/picture.webp', blob: true },
            // specify id for retrieval
            { id: 'picture', url: '/images/picture.jpg' },
            // json
            'data.json',
            { url: 'data.json' },
            { url: '/endpoint', type: 'json' },
            // jsonp
            { url: '/endpoint', type: 'jsonp' },
            { url: 'data.json', type: 'jsonp', callback: 'dataCallback', timeout: 5000 },
            // video
            'video.webm',
            { url: 'video.mp4', blob: true },
            // audio
            'audio.ogg',
            { url: 'audio.ogg', blob: true },
            { url: 'audio.mp3', webAudioContext: audioContext },
        ]
    })
    .on('complete', function(assets) {
        console.log(loader.get('picture'));
    })
    .start();
```

More usage and examples on the (original project's page)[https://github.com/ianmcgregor/assets-loader].

See [all supported formats here](https://github.com/watsondg/assets-loader/blob/6cef8e19be7a0ae3b76ddbb028b6488f472eee72/src/loader.js#L29-L62).

## Instance Methods

### new AssetsLoader([options])

Create a new instance of VideoCache.
* `options` - (OPTIONAL) - configuration parameters. Can be an URL or an object containing the following properties:
- assets: an array of files to load. It can be a string (url) or an object containing an `url ` property as well as an `id` for easier retrieval, as well as any of the following parameters.
- basePath: the base URL to prepend to the file URL.
- blob: force loading by Blob if supported.
- crossOrigin: for image loading.
- webAudioContext: a pre-existing audio context to use.

### add([options])

Add a subloader.
* `options` - (OPTIONAL) - configuration parameters, same as constructor.

### start()

Start loading the assets.

### getLoader(id)

Return a subloader.

### destroy()

Stop loading and dispose the instance.

## Instance Events

### error
### progress
### complete
### childcomplete
### destroy

## License
MIT.
