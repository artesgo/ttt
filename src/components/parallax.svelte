<div class='parallax'>
  <slot />
</div>

<style>
  .parallax {
    height: 300px;
    background-image: url("space.jpg");
    background-attachment: fixed;
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
    color: white;
    width: 100%;
    padding: 1rem;
  }
</style>
