<template>
  <nav class="navbar sticky-top navbar-light">
    <div class="container">
      <a class="navbar-brand" href="#">
        <img src="/public/assets/logo.png" width="256" height="57" />
      </a>
      <div class="navbar--right">
        <p>Ana Sofia Russo</p>
        <p>Tic Tac Toe Game</p>
      </div>
    </div>
  </nav>
</template>

<style>
.navbar {
  background-color: lightgrey;
  padding: 15px;
  transition: 0.5s ease-in-out;
  pointer-events: none;
}

.navbar.scrolled {
  background-color: transparent;
}

.navbar--right {
  text-align: right;
}
.navbar--right p {
  margin-bottom: 0;
}

.navbar--right p:first-of-type {
  font-weight: bold;
}

.navbar--right p:nth-of-type(2) {
  font-style: italic;
}

@media only screen and (min-width: 768px) {
  .navbar {
    padding: 20px 150px;
  }
}
</style>
