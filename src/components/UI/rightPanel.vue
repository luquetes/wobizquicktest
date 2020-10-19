<template>
    <div class="position relative vh-100">
        <img src="@/assets/fondo.png" alt="" class="vh-100 position-relative vw-img">
        <div class="row text-button d-none d-lg-inline-flex">
          <p class="greenish-blue-text mr-3 mt-2">No tenes una cuenta?</p>
          <a href="">
              <button class="btn btn-transparent btn-outline">Crea tu cuenta</button>
          </a>
        </div>
    </div>
</template>

<style scoped>

.text-button {
  position: absolute;
  top: 42px;
  right: 10%;
  font-size: 13px;
}
.greenish-blue-text {
  color: #163a49;
}
.vw-img {
  width: 100%;
  object-fit: cover;
  object-position: right;
}

button {
  border: 1px solid #163a49;
  font-size: 13px;
  font-weight: 600;
  height: 35px;
  transition: all .3s;
}
button:hover {
  background: #163a49;
  color: white;
}
</style>