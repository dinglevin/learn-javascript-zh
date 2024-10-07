# 第二十六章·动画资源

Animations in JavaScript are a powerful way to create engaging user experiences on the web. This chapter will cover various resources, including libraries, tutorials, articles, and frameworks, that assist developers in creating animations using JavaScript.

## Introduction to JavaScript Animations

JavaScript animations allow developers to create dynamic, visually appealing web content. Animations can be used for various purposes, such as enhancing user interfaces, providing feedback, and making content more engaging.

### Libraries

JavaScript animation libraries make it easier to create complex animations. Here are some popular libraries:

1. **[GSAP (GreenSock Animation Platform)](https://greensock.com/gsap/)**: A powerful library for creating high-performance animations.
2. **[Anime.js](https://animejs.com/)**: A lightweight library for handling animations.
3. **[Three.js](https://threejs.org/)**: A library for creating 3D animations.
4. **[Velocity.js](http://velocityjs.org/)**: A fast animation engine.

### Tutorials

To get started with JavaScript animations, check out these tutorials:

1. **[MDN Web Docs: Using CSS animations](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Animations/Using_CSS_animations)**: A comprehensive guide on CSS animations.
2. **[JavaScript.info: JavaScript Animations](https://javascript.info/js-animation/)**: An introduction to JavaScript animations.
3. **[GreenSock Learning Resources](https://greensock.com/learning/)**: Tutorials and resources for learning GSAP.

### Frameworks

Frameworks provide a structured approach to building animations. Some popular frameworks include:

1. **[React Spring](https://react-spring.io/)**: A spring-physics based animation library for React.
2. **[Framer Motion](https://www.framer.com/motion/)**: A production-ready motion library for React.

In this chapter, we will explore the following topics in detail:

* [Getting Started with GSAP](./gsap.md)
* [Creating Animations with Anime.js](./animejs.md)
* [3D Animations with Three.js](./threejs.md)
* [Fast Animations with Velocity.js](./velocityjs.md)
* [Using React Spring for Animations](./react-spring.md)
* [Animating with Framer Motion](./framer-motion.md)

Let's dive into each topic to understand how to use these resources effectively.


## Getting Started with GSAP

GSAP (GreenSock Animation Platform) is a powerful library for creating high-performance animations. It is widely used due to its robustness and flexibility.

**Installation**

You can include GSAP in your project using npm:

```bash
npm install gsap
```

Or you can use a CDN:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.7.1/gsap.min.js"></script>
```

**Basic Animation**

Here's a simple example of using GSAP to animate an element:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GSAP Animation</title>
</head>
<body>
    <div id="box" style="width:100px; height:100px; background-color:red;"></div>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.7.1/gsap.min.js"></script>
    <script>
        gsap.to("#box", {x: 100, duration: 1});
    </script>
</body>
</html>
```

**Advanced Animation**

GSAP provides various features for advanced animations, such as timelines, stagger, and easing.


- **Timelines:**
Timelines allow you to sequence animations. Here's an example:

```javascript
const name = "John";
const greeting = `Hello, ${name}!`;
console.log(greeting); // Output: Hello, John!
```


- **Stagger:**
Stagger allows you to animate multiple elements with a delay between each. Here's an example:

```javascript
gsap.to(".box", {x: 100, duration: 1, stagger: 0.2});
```


- **Easing:**
GSAP provides a variety of easing options to make animations look more natural. Here's an example:

```javascript
gsap.to("#box", {x: 100, duration: 1, ease: "bounce"});
```

{% hint style="info" %}
For more details and examples, check out the GSAP documentation.
{% endhint %}

## Creating Animations with Anime.js

Anime.js is a lightweight JavaScript animation library with a simple yet powerful API.

**Installation**

You can include Anime.js in your project using npm:

```bash
npm install animejs
```

Or you can use a CDN:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/animejs/3.2.1/anime.min.js"></script>
```

**Basic Animation**

Here's a simple example of using Anime.js to animate an element:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Anime.js Animation</title>
</head>
<body>
    <div id="box" style="width:100px; height:100px; background-color:red;"></div>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/animejs/3.2.1/anime.min.js"></script>
    <script>
        anime({
            targets: '#box',
            translateX: 250,
            duration: 1000
        });
    </script>
</body>
</html>
```

**Advanced Animation**

Anime.js provides various features for advanced animations, such as keyframes, timeline, and easing.


- **Keyframes:**
Keyframes allow you to define multiple stages of an animation. Here's an example:

```javascript
anime({
    targets: '#box',
    keyframes: [
        {translateX: 100},
        {translateY: 100},
        {translateX: 0},
        {translateY: 0}
    ],
    duration: 4000
});
```


- **Timeline:**
Timelines allow you to sequence animations. Here's an example:

```javascript
var tl = anime.timeline({
    easing: 'easeOutExpo',
    duration: 750
});

tl.add({
    targets: '#box',
    translateX: 250
}).add({
    targets: '#box',
    translateY: 250
}, '-=500'); // Starts 500ms before the previous animation ends
```


- **Easing:**
Anime.js provides a variety of easing options to make animations look more natural. Here's an example:

```javascript
anime({
    targets: '#box',
    translateX: 250,
    duration: 1000,
    easing: 'easeInOutQuad'
});
```

{% hint style="info" %}
For more details and examples, check out the Anime.js documentation.
{% endhint %}

## 3D Animations with Three.js

Three.js is a JavaScript library that makes creating 3D graphics on the web easier. It is widely used for creating immersive 3D experiences.

**Installation**

You can include Three.js in your project using npm:

```bash
npm install three
```

Or you can use a CDN:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
```

**Basic Animation**

Here's a simple example of using Three.js to create a rotating cube:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Three.js Animation</title>
    <style>
        body { margin: 0; }
        canvas { display: block; }
    </style>
</head>
<body>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <script>
        const scene = new THREE.Scene();
        const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);

        const renderer = new THREE.WebGLRenderer();
        renderer.setSize(window.innerWidth, window.innerHeight);
        document.body.appendChild(renderer.domElement);

        const geometry = new THREE.BoxGeometry();
        const material = new THREE.MeshBasicMaterial({ color: 0x00ff00 });
        const cube = new THREE.Mesh(geometry, material);
        scene.add(cube);

        camera.position.z = 5;

        function animate() {
            requestAnimationFrame(animate);

            cube.rotation.x += 0.01;
            cube.rotation.y += 0.01;

            renderer.render(scene, camera);
        }

        animate();
    </script>
</body>
</html>
```

**Advanced Animation**

Three.js provides various features for advanced animations, such as lighting, textures, and physics.


- **Lighting**
Adding lighting to your scene can make it more realistic. Here's an example:

```javascript
const light = new THREE.PointLight(0xffffff);
light.position.set(10, 10, 10);
scene.add(light);
```


- **Textures**
Applying textures to your objects can make them more detailed. Here's an example:

```javascript
const texture = new THREE.TextureLoader().load('path/to/texture.jpg');
const material = new THREE.MeshBasicMaterial({ map: texture });
const cube = new THREE.Mesh(geometry, material);
```


- **Physics**
Integrating physics can make your 3D world more dynamic. One popular physics engine that works with Three.js is Cannon.js.

{% hint style="info" %}
For more details and examples, check out the Three.js documentation.
{% endhint %}

## Fast Animations with Velocity.js

Velocity.js is a high-performance animation engine that is easy to use and works with and without jQuery.

**Installation**

You can include Velocity.js in your project using npm:

```bash
npm install velocity-animate
```

Or you can use a CDN:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/velocity/1.5.2/velocity.min.js"></script>
```

**Basic Animation**
Here's a simple example of using Velocity.js to animate an element:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Velocity.js Animation</title>
</head>
<body>
    <div id="box" style="width:100px; height:100px; background-color:red;"></div>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/velocity/1.5.2/velocity.min.js"></script>
    <script>
        Velocity(document.getElementById('box'), { left: "100px" }, { duration: 1000 });
    </script>
</body>
</html>
```

**Advanced Animation**

Velocity.js provides various features for advanced animations, such as sequences, easing, and SVG animations.


- **Sequences**

Sequences allow you to chain animations together. Here's an example:

```javascript
Velocity(document.getElementById('box'), { left: "100px" }, { duration: 1000 })
    .then(() => {
        return Velocity(document.getElementById('box'), { top: "100px" }, { duration: 1000 });
    });
```


- **Easing**

Velocity.js provides a variety of easing options to make animations look more natural. Here's an example:

```javascript
Velocity(document.getElementById('box'), { left: "100px" }, { duration: 1000, easing: "spring" });
```


- **SVG Animations**

Velocity.js can also animate SVG elements. Here's an example:

```javascript
Velocity(document.querySelector('svg'), { strokeDashoffset: 0 }, { duration: 1000 });
```

{% hint style="info" %}
For more details and examples, check out the Velocity.js documentation.
{% endhint %}

## Using React Spring for Animations

React Spring is a spring-physics-based animation library for React that makes it easy to create animations.

**Installation**

You can include React Spring in your project using npm:

```bash
npm install react-spring
```

**Basic Animation**

Here's a simple example of using React Spring to animate a component:

```javascript
import React from 'react';
import { useSpring, animated } from 'react-spring';

const AnimatedComponent = () => {
    const props = useSpring({ opacity: 1, from: { opacity: 0 } });

    return <animated.div style={props}>I will fade in</animated.div>;
};

export default AnimatedComponent;
```

**Advanced Animation**

React Spring provides various features for advanced animations, such as transitions, trails, and keyframes.


- **Transitions**
Transitions allow you to animate components as they mount and unmount. Here's an example:

```javascript
import React, { useState } from 'react';
import { useTransition, animated } from 'react-spring';

const TransitionComponent = () => {
    const [items, setItems] = useState([]);
    const transitions = useTransition(items, item => item.key, {
        from: { transform: 'translate3d(0,-40px,0)' },
        enter: { transform: 'translate3d(0,0px,0)' },
        leave: { transform: 'translate3d(0,-40px,0)' },
    });

    return (
        <div>
            <button onClick={() => setItems([...items, { key: items.length }])}>
                Add Item
            </button>
            {transitions.map(({ item, props, key }) => (
                <animated.div key={key} style={props}>{item.key}</animated.div>
            ))}
        </div>
    );
};

export default TransitionComponent;
```


- **Trails**
Trails allow you to animate a list of components in sequence. Here's an example:

```javascript
import React from 'react';
import { useTrail, animated } from 'react-spring';

const items = [1, 2, 3];

const TrailComponent = () => {
    const trail = useTrail(items.length, {
        from: { opacity: 0 },
        to: { opacity: 1 },
    });

    return (
        <div>
            {trail.map((props, index) => (
                <animated.div key={index} style={props}>
                    {items[index]}
                </animated.div>
            ))}
        </div>
    );
};

export default TrailComponent;
```

{% hint style="info" %}
For more details and examples, check out the React Spring documentation.
{% endhint %}


## Animating with Framer Motion

Framer Motion is a production-ready motion library for React. It makes it easy to create complex animations.

**Installation**

You can include Framer Motion in your project using npm:

```bash
npm install framer-motion
```

**Basic Animation**

Here's a simple example of using Framer Motion to animate a component:

```javascript
import React from 'react';
import { motion } from 'framer-motion';

const AnimatedComponent = () => {
    return (
        <motion.div animate={{ x: 100 }} transition={{ duration: 1 }}>
            I will move to the right
        </motion.div>
    );
};

export default AnimatedComponent;
```

**Advanced Animation**

Framer Motion provides various features for advanced animations, such as keyframes, gestures, and layout animations.


- **Keyframes:**
Keyframes allow you to define multiple stages of an animation. Here's an example:

```javascript
import React from 'react';
import { motion } from 'framer-motion';

const KeyframeComponent = () => {
    return (
        <motion.div
            animate={{ x: [0, 100, 0] }}
            transition={{ duration: 2, ease: 'easeInOut' }}
        >
            I will move back and forth
        </motion.div>
    );
};

export default KeyframeComponent;
```


- **Gestures**
Framer Motion allows you to create animations based on user gestures. Here's an example:

```javascript
import React from 'react';
import { motion } from 'framer-motion';

const GestureComponent = () => {
    return (
        <motion.div
            drag
            dragConstraints={{ left: -100, right: 100, top: -100, bottom: 100 }}
        >
            Drag me around
        </motion.div>
    );
};

export default GestureComponent;
```


- **Layout Animations**
Framer Motion makes it easy to animate layout changes. Here's an example:

```javascript
import React, { useState } from 'react';
import { motion } from 'framer-motion';

const LayoutAnimationComponent = () => {
    const [isOpen, setIsOpen] = useState(false);

    return (
        <motion.div layout onClick={() => setIsOpen(!isOpen)} style={{ background: 'lightblue', padding: '10px' }}>
            {isOpen ? 'Click to collapse' : 'Click to expand'}
        </motion.div>
    );
};

export default LayoutAnimationComponent;
```

{% hint style="info" %}
For more details and examples, check out the Framer Motion documentation.
{% endhint %}