<div class='complex-parallax'>
  <div class='parallax-layer layer1'></div>
  <div class='parallax-layer layer2'></div>
  <slot />
</div>

<style>
  .complex-parallax {
    height: 40vh;
    width: 100%;
    overflow-x: hidden;
    overflow-y: scroll;
    perspective: 1px;
  }

  .parallax-layer {
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    overflow: scroll;
  }

  .layer1 {
    transform: translateZ(0);
    width: 100%;
    background-image: url("space.jpg");
    background-size: cover;
    height: 50rem;
  }

  .layer2 {
    transform: translateZ(-1px);
    width: 100%;
    background-image: url("moon.png");
    background-size: cover;
    height: 1000px;
    background-position: top;
    background-repeat: no-repeat !important;
    transition: 1s;
  }

  @media (max-width: 1200px) {
    .layer2 {
      height: 800px;
      top: 200px;
    }
  }
  @media (max-width: 1000px) {
    .layer2 {
      height: 500px;
      top: 500px;
    }
  }
  @media (max-width: 640px) {
    .layer2 {
      height: 400px;
      top: 600px;
    }
  }
  @media (max-width: 500px) {
    .layer2 {
      height: 350px;
      top: 640px;
    }
  }
</style>
