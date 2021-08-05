# threejsStarter
Setting up my first scene in threejs

A general walkthrough of the pertinent code is given below:

First I had to download the threejs master.zip from threejs.org. After unzipping I had to go inside the build folder and use one of the 3 js files there to allow access to threejs - I used the three.minjs file. After copying it to the file tree I next imported it using a script tag - always load 3js 1st.
```JavaScript
    <script src="./three.min.js"></script>
    <script src="/Intro/index.js"></script>
```


Now access has been attained to the 3js library. I next console logged to view the library classes.
```JavaScript
console.log(THREE);
```


Next I created my 1st scene using objects, a camera and a renderer. First I created a mesh to provide a shape and material to my object.
```JavaScript
const geometry = new THREE.BoxGeometry(1, 1, 1);
const scene = new THREE.Scene();
const geometry = new THREE.BoxGeometry(1, 1, 1);
const material = new THREE.MeshBasicMaterial({ color: 0x0000ff });
const mesh = new THREE.Mesh(geometry, material);
scene.add(mesh);
```

Next I set up the camera to serve as a point of view on the object to make it visible.
```JavaScript
const camera = new THREE.PerspectiveCamera(75,);
scene.add(camera)
```

Before I could set the 2nd parameter of my perspectiveCamera I had to set the sizes of the object to be rendered.
```JavaScript
const sizes = {
  width: 800,
  height: 600,
};
```

After the size has been set the aspect ratio can be determined and used as the 2nd parameter in PerspectiveCamera.
```JavaScript
const camera = new THREE.PerspectiveCamera(75, sizes.width / sizes.height);
scene.add(camera);
```

Next the renderer is provided to render the scene onto the screen from the cameras point of view. First I had to insert a <canvas> tag into the HTML elements.
```HTML
    <canvas class="webgl"></canvas>
```

Next I created the WebGLRenderer
```JavaScript
const canvas = document.querySelector(".webgl");
const renderer = new THREE.WebGLRenderer({
  canvas: canvas,
});
```

At this point there is a black box rendered to my screen but the size of the box is wrong and needs to be resized - it will automatically rezise the canvas.
```JavaScript
renderer.setSize(sizes.width, sizes.height);
```

Next the first render is carried out.
```JavaScript
renderer.render(scene, camera);
```

At this point the scene renders all black because the camera and the cube are both at the center of the scene - the camera is inside the cube! The camera needs to be moved.
```JavaScript
const camera = new THREE.PerspectiveCamera(75, sizes.width / sizes.height);
camera.position.z = 4.5;
camera.position.x = 1;
camera.position.y = 1.3;
scene.add(camera);
```

***Walkthrough finished
