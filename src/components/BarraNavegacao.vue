<template>
<nav class="navbar navbar-expand bg-body-tertiary">
  <div class="container-fluid">
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
        <li class="nav-item">
          <RouterLink class="nav-link active" to="/">Geração1</RouterLink>
        </li>
        <li class="nav-item">
          <RouterLink class="nav-link active" to="/geracao2">Geração2</RouterLink>
        </li>
        <li class="nav-item dropdown">
          <RouterLink class="nav-link active" to="/geracao3">Geração3</RouterLink>
        </li>
      </ul>
    </div>
  </div>
</nav>
</template>