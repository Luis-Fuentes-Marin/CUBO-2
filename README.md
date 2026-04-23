<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Rotación de un Cubo en 3D</title>
  <style>
    body { 
      margin: 0; 
      overflow: hidden;
      background: linear-gradient(135deg, #0f2027, #203a43, #2c5364);
      font-family: Arial, sans-serif;
    }

    .titulo {
      position: absolute;
      top: 20px;
      width: 100%;
      text-align: center;
    }

    .titulo h1 {
      margin: 0;
      font-size: 34px;
      color: #00ffff; /* color neón */
      text-shadow: 0 0 10px #00ffff;
    }

    .titulo p {
      margin: 5px 0 0 0;
      font-size: 16px;
      color: #ffffff;
      text-shadow: 0 0 5px #ffffff;
    }
  </style>
</head>
<body>

<!-- TEXTO -->
<div class="titulo">
  <h1>CUBO 3D ROTATORIO</h1>
  <p>HECHO POR LUIS EDWIN FUENTES MARIN</p>
</div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>

<script>
  // ESCENA
  const scene = new THREE.Scene();

  // CÁMARA
  const camera = new THREE.PerspectiveCamera(
    75,
    window.innerWidth / window.innerHeight,
    0.1,
    1000
  );
  camera.position.z = 5;

  // RENDERIZADOR
  const renderer = new THREE.WebGLRenderer({ antialias: true });
  renderer.setSize(window.innerWidth, window.innerHeight);
  document.body.appendChild(renderer.domElement);

  // LUZ
  const light = new THREE.PointLight(0xffffff, 1);
  light.position.set(5, 5, 5);
  scene.add(light);

  // CUBO (COLOR MEJORADO)
  const geometry = new THREE.BoxGeometry(1.5, 1.5, 1.5);
  const material = new THREE.MeshStandardMaterial({
    color: 0xff00ff,   // morado neón
    metalness: 0.7,
    roughness: 0.2
  });

  const cube = new THREE.Mesh(geometry, material);
  scene.add(cube);

  // VELOCIDAD
  let speedX = 0.02;
  let speedY = 0.02;

  // ANIMACIÓN
  function animate() {
    requestAnimationFrame(animate);

    cube.rotation.x += speedX;
    cube.rotation.y += speedY;

    renderer.render(scene, camera);
  }

  animate();

  // RESPONSIVE
  window.addEventListener('resize', () => {
    renderer.setSize(window.innerWidth, window.innerHeight);
    camera.aspect = window.innerWidth / window.innerHeight;
    camera.updateProjectionMatrix();
  });
</script>

</body>
</html>
