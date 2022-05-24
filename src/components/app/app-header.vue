<template>
  <nav class="navbar sticky-top navbar-light">
    <div class="container">
      <a class="navbar-brand" href="#">
        <img src="/assets/img/logo.png" />
      </a>
      <div class="navbar__right">
        <p>Game Challenge</p>
        <p>Tic Tac Toe</p>
      </div>
    </div>
  </nav>
</template>

<style lang="scss">
.navbar {
  background-color: lightgrey;
  padding: 15px;
  transition: 0.5s ease-in-out;
  pointer-events: none;

  @media only screen and (min-width: 768px) {
    padding: 20px 150px;
  }

  &.scrolled {
    background-color: transparent;
  }

  &__right {
    text-align: right;
  }

  p {
    margin-bottom: 0;

    &:first-of-type {
      font-weight: bold;
    }

    &:nth-of-type(2) {
      font-style: italic;
    }
  }
}
</style>
