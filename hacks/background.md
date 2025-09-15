---
layout: opencs
title: Background with Object
description: Use JavaScript to have an in motion background.
sprite: images/platformer/sprites/flying-ufo.png
background: images/platformer/backgrounds/alien_planet2.jpg
permalink: /background
---

<canvas id="world"></canvas>

<script>
  // Get canvas and 2D rendering context
  const canvas = document.getElementById("world");
  const ctx = canvas.getContext('2d');

  // Create image objects for background and sprite
  const backgroundImg = new Image();
  const spriteImg = new Image();

  // Load paths from page variables
  backgroundImg.src = '{{page.background}}';
  spriteImg.src = '{{page.sprite}}';

  // Counter for tracking when both images are ready
  let imagesLoaded = 0;

  // When background is loaded, increment counter and try to start game
  backgroundImg.onload = function() {
    imagesLoaded++;
    startGameWorld();
  };

  // When sprite is loaded, increment counter and try to start game
  spriteImg.onload = function() {
    imagesLoaded++;
    startGameWorld();
  };

  // Function to start the game only once both images are loaded
  function startGameWorld() {
    if (imagesLoaded < 2) return; // wait for both images

    // Base class for all objects in the game world
    class GameObject {
      constructor(image, width, height, x = 0, y = 0, speedRatio = 0) {
        this.image = image;
        this.width = width;
        this.height = height;
        this.x = x;
        this.y = y;
        this.speedRatio = speedRatio;
        this.speed = GameWorld.gameSpeed * this.speedRatio; // movement speed
      }
      update() {} // default: no update
      draw(ctx) {
        ctx.drawImage(this.image, this.x, this.y, this.width, this.height);
      }
    }

    // Background class that scrolls to the left infinitely
    class Background extends GameObject {
      constructor(image, gameWorld) {
        // Make background fill the entire canvas
        super(image, gameWorld.width, gameWorld.height, 0, 0, 0.1);
      }
      update() {
        // Move background left, wrap around when out of view
        this.x = (this.x - this.speed) % this.width;
      }
      draw(ctx) {
        // Draw two copies of background side by side for seamless loop
        ctx.drawImage(this.image, this.x, this.y, this.width, this.height);
        ctx.drawImage(this.image, this.x + this.width, this.y, this.width, this.height);
      }
    }

    // Player (sprite) class with floating animation
    class Player extends GameObject {
      constructor(image, gameWorld) {
        // Scale sprite to half its natural size
        const width = image.naturalWidth / 2;
        const height = image.naturalHeight / 2;

        // Center player on screen
        const x = (gameWorld.width - width) / 2;
        const y = (gameWorld.height - height) / 2;

        super(image, width, height, x, y);
        this.baseY = y;   // baseline Y position
        this.frame = 0;   // frame counter for sine wave
      }
      update() {
        // Make sprite bob up and down using sine wave
        this.y = this.baseY + Math.sin(this.frame * 0.05) * 20;
        this.frame++;
      }
    }

    // Main game world class
    class GameWorld {
      static gameSpeed = 5; // base speed for moving objects
      constructor(backgroundImg, spriteImg) {
        this.canvas = document.getElementById("world");
        this.ctx = this.canvas.getContext('2d');

        // Match canvas size to window
        this.width = window.innerWidth;
        this.height = window.innerHeight;
        this.canvas.width = this.width;
        this.canvas.height = this.height;

        // Style canvas to fill screen
        this.canvas.style.width = `${this.width}px`;
        this.canvas.style.height = `${this.height}px`;
        this.canvas.style.position = 'absolute';
        this.canvas.style.left = `0px`;
        this.canvas.style.top = `${(window.innerHeight - this.height) / 2}px`;

        // Add background and player objects to game
        this.gameObjects = [
          new Background(backgroundImg, this),
          new Player(spriteImg, this)
        ];
      }

      // Main game loop
      gameLoop() {
        // Clear screen
        this.ctx.clearRect(0, 0, this.width, this.height);

        // Update and draw each object
        for (const obj of this.gameObjects) {
          obj.update();
          obj.draw(this.ctx);
        }

        // Request next frame
        requestAnimationFrame(this.gameLoop.bind(this));
      }

      // Start the game loop
      start() {
        this.gameLoop();
      }
    }

    // Create game world and run it
    const world = new GameWorld(backgroundImg, spriteImg);
    world.start();
  }
</script>
