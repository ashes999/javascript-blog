There's a great Phaser tutorial here on [making your first game in phaser](http://www.photonstorm.com/phaser/tutorial-making-your-first-phaser-game), including downloadable sample code. It provides really useful sample code.

Unfortunately, the text formatting changed since the tutorial (which used Phaser 2.0.1 -- the current version is 2.1.1). The tutorial suggests you set the font like so:

`scoreText = game.add.text(16, 16, 'score: 0', { fontSize: '32px', fill: '#000' });`

This doesn't work. The correct style is:

`scoreText = game.add.text(16, 16, 'score: 0', { font: '32px Arial', fill: '#000' });`

You can find the specification/grammer in the `setStyle` method of the `Phaser.Text` class' [official documentation](http://docs.phaser.io/Phaser.Text.html#setStyle).
