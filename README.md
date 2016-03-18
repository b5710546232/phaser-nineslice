Phaser Nineslice
================
Phaser-Ninslice plugin adds 9 slice scaling support to Phaser!

Getting Started
---------------
First you want to get a fresh copy of the plugin. You can get it from this repo or from npm, ain't that handy.
```
npm install phaser-nineslice --save-dev
```

Next up you'd want to add it to your list of js sources you load into your game
```html
<script src="node_modules/phaser-nineslice/build/phaser-nineslice.js"></script>
```

Usage
-----
You still need to load the plugin in your game. This is done just like any other plugin in Phaser
```javascript
game.plugins.add(Fabrique.Plugins.NineSlice);
```
The plugin will patch your Phaser game with additional load/add/make methods so the ninslice container fits up in Phaser like any normal object!

### Preloading
Like any other asset in Phaser, you still need to preload the image. It's a bit different then a regular image, in the sence that it requiers some extra data.
Apart from the key and the url, you can also specify the sizes of top, left, right and bottom sides.

If you don't specify a bottom size, it will take the top, same goes for right and left. It's also possible to only give one size, it will use that for the edges

```javascript
//This will load a 9slice texture where all sides are 25px
game.load.nineSlice('my-image', '/images/my-image.jpg', 25);

//This will load a 9slice texture where the
// top is 10, left is 15, right is 20 and bottom is 30 pixels in size
game.load.nineSlice('my-image', '/images/my-image.jpg', 10, 15, 20, 30);
```

### Adding a container
Also adding and creating of 9slice containers is exposed trough Phaser's GameObjectCreator and GameObjectFactory.
So you can add a 9slice container to your game just like any ohter image once it's preloaded!

```javascript
//We specify the x and y position. the key for the image and the width and height of the container. It will be automaticly scaled!
game.add.nineSlice(100, 100, 'my-image', 200, 50);
```

Or if you'd want to do something with it first:
```javascript
//Two options here, first we use Phaser
var container = game.create.nineSlice(0, 0, 'my-image', 200, 50);
container.x = 20;
container.y = 20;
game.add.existing(container);

//Or we use the Constructor
var nineSlice = new Fabrique.NineSlice(game, 0, 0, 'my-image', 200, 50);
nineSlice.x = 50;
nineSlice.y = 50;
game.add.existing(nineSlice);
```


Changelog
---------
### 1.0.0
* Initial release

Disclaimer
----------
We at OrangeGames just love playing and creating awesome games. We aren't affiliated with Phaser.io. We just needed some awesome nine slice containers in our awesome HTML5 games. Feel free to use it for enhancing your own awesome games!
