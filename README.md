# Welcome to three-plain-animator

Three-Plain-Animator is a package for threejs developers to support 2D animations.

## Installation

The package is available on npm: [three-plain-animator](https://www.npmjs.com/package/three-plain-animator)
To install the latest stable version type this in your project's root directory:

    npm i three-plain-animator

## Usage
There are two main classes to work with: 

 - plain-animator
 - plain-singular-animator
 
 The first one is for continuous animations like walking. The second one is for animation that should play only once and then stop on the last frame of animation. 

## Example

The simple with Homer Simpson animated [gif for reference](https://ui-ex.com/images/transparent-gifs-simpson-2.gif)
I assume that creating a basic scene using threejs is not a part of this example. So I will show only unnecessary code just to not mess around.

I converted gif to sprite and uploaded this on imgur. 

The first step is to create texture just like every texture using threejs.

    const texturePath =  'https://i.imgur.com/Oj6RJV9.png';
    const spriteTexture = new  THREE.TextureLoader().load(texturePath)

   
Next step is about creating the animator object:

     const animator =  new  PlainAnimator(spriteTexture, 4, 4, 10, 15);
These magic numbers are the follows:
|value| description |
|--|--|
| 4 | number of frames horizontally |
| 4 | number of frames vertically |
| 10 | total number of frames |
| 15 | frames per second (fps) |

Then the finall texture could be get using init() method:

    const texture = animator.init();
    
To animate texture it's required to animate texture in the main loop of rendering

    animator.animate();



Full code:

    const texturePath =  'https://i.imgur.com/Oj6RJV9.png';
    const spriteTexture = new  THREE.TextureLoader().load(texturePath)
    const animator =  new  PlainAnimator(spriteTexture, 4, 4, 10, 15);

	const texture = animator.init();    

    const geometry =  new  THREE.PlaneGeometry(512,  512);
    const material =  new  THREE.MeshBasicMaterial({ map: texture, transparent:  true  });
    
    let mesh =  new  THREE.Mesh(geometry, material)

There is working code on  [stackblitz](https://stackblitz.com/edit/plain-animations) with this example: 


## Requierments

The package requires threejs library r103

## Support
The package supports TypeScript and it also contains typescript definitions. 

## Future work & TODO

 1. More examples
 2. GIF files support
 3. Tests


##  
Feel free to ask any questions. Post on GitHub or write to me: maciejwwojcik@gmail.com
